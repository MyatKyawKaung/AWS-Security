This lab walkthroughs step by step guide in creating and configuring multiple dashboards in AWS. CloudWatch dashboards built with custom widgets allow you to visually monitor resources and proactively take action, if needed.

# Objectives

Create multiple CloudWatch dashboards to monitor activities in our AWS environment
1. CPU utilization metrics dashboard for bastion host in DMZ Layer, database in DBLayer and Webservers in AppLayer1,2
2. Dashboard to monitor request counts to the Application Load Balancer
3. Inbound network traffics dashboard for database and two Wordpress instances

<img title="Lab Diagram" src="https://github.com/user-attachments/assets/371b3c26-22b5-40bc-8d95-4495aa6cc6bd" >

## Step 1: Create CPU Utilization CloudWatch Dashboards

Search "CloudWatch" in AWS Management Console

![2](https://github.com/user-attachments/assets/e12beffb-573a-4601-acf8-857fe2e75ad4)

Navigate to CloudWatch  → Dashboards → Create dashboard

![3](https://github.com/user-attachments/assets/28eafda3-282a-4166-94ad-a30c31ab8088)

Set dashboard name: "DMZLayer" and Click "Create dashboard"

![4](https://github.com/user-attachments/assets/57339619-afdb-425b-9f64-3141957cc110)

## Add Metric Widget

Add a widget to the dashboard and Configure the widget to display the CPUUtilization metric for the bastion host.
1. Select Add widget → Line (In this case. we choose **Line** to see CPU utilizationmetrics over time)

![5](https://github.com/user-attachments/assets/5667ad72-2d4b-4dbb-86a7-d0e3a2da7bbf)

2. Choose Widget Type

![6](https://github.com/user-attachments/assets/b1618d66-9ca5-4af5-b526-38b704ca136d)

3. Configure data source

![7](https://github.com/user-attachments/assets/accc8c2f-4169-4b36-b95f-074b4e1e830a)

In the **Browse** tab, under **Metrics**, select **EC2**.

![8](https://github.com/user-attachments/assets/b99ac76d-98ce-4a44-98ea-49e0334a0958)

Then, select **Per-Instance Metrics**.

![9](https://github.com/user-attachments/assets/630d58b2-5b65-4ae0-ae79-63a388c25001)

In the search bar, type the instance ID of your bastion host or the name if you have tagged it (e.g., `bastion-host`). Check the box next to the `CPUUtilization` metric for your bastion host instance. *Note: You can select multiple metrics if needed.*

![10](https://github.com/user-attachments/assets/aed11c8a-b8fc-4849-adcf-0f6b6caa8178)

You can adjust the time range (e.g., 1 hour, 3 hours, etc.) and the time zone (UTC by default). You can also set the graph title and other display options as well.

![11](https://github.com/user-attachments/assets/e13c4fe0-af12-4e8e-92dd-f29bb4c4105d)

Click **Create widget** to add the widget to your dashboard. The dashboard will now display the CPU utilization graph for the bastion host.

![12](https://github.com/user-attachments/assets/0b1a1001-fda2-41c6-a881-565c10eb07da)

 Click **Save dashboard** at the top of the page to persist your changes.
 
![13](https://github.com/user-attachments/assets/8bbcda4b-6ca7-4169-af03-3fa97d14625f)

## Step 2: Create Database and Webserver utilization dashboards

This time we will add more Cloudwatch dashboards to monitor, configuration steps are basically the same as the previous one.

In the left navigation menu, select Metrics > All metrics.

![14](https://github.com/user-attachments/assets/ab9dcfde-dc3f-4868-979d-d417204e6969)

Within the Metrics pane, select EC2.

![15](https://github.com/user-attachments/assets/79ae6422-3436-4fc3-91b6-b7809ee36c7c)

Select and add **CPU Utilization** to search.

![16](https://github.com/user-attachments/assets/c8b83dbc-67f2-4a7f-a464-4094216a29a1)

Select **DataBase** and **Wordpress-instances**.

![17](https://github.com/user-attachments/assets/19517696-c79e-4354-9c0a-cb808349659e)

This time, we will use stacked area instead of line widget for better visualization.

![18](https://github.com/user-attachments/assets/6b8e1b89-04f2-4d0e-b7ce-bf4a0e9d5c89)

In "Actions" tab, add them to a dashboard.

![19](https://github.com/user-attachments/assets/64016c80-70b7-4da3-93dd-88ab70756810)

Create a new dashboard named "AppLayer".

![20](https://github.com/user-attachments/assets/1a6f71b2-ed7d-4b76-902c-e1fbdca8cb1f)

## Step 3: Create Request Counts to Application Load Balancer dashboard

In the left navigation menu of CloudWatch Dashboards, select Metrics > All metrics. Then select "ApplicationELB" in the metrics.

![21](https://github.com/user-attachments/assets/ea5d924e-dca0-425c-bb90-86e770c1b95b)

Select "Per AppELB Metrics".

![22](https://github.com/user-attachments/assets/8cd5b8b3-4e0c-48f3-bff8-112ae423b893)

Search for MetricName="RequestCount" and create widget.

![23](https://github.com/user-attachments/assets/08dcbf83-f225-42e3-93c2-19136fdbbed3)

A new dashboard "RequestCount" is created.

![24](https://github.com/user-attachments/assets/5322fc3a-ca8d-4d6c-ba94-f5fdcfd6f919)

## Step 4: Create Inbound network traffics dashboard

This time we will create a dashboard to monitor inbound network traffics for bastion-host, database and wordpress instances. *Note: Configuration steps are basically the same as pervious ones, just select the metrics for NetworkInbound*.

![25](https://github.com/user-attachments/assets/dc0721f0-077c-489b-8cc4-39b8823fee84)
![26](https://github.com/user-attachments/assets/77cbb2fb-517f-435b-acab-9e2139c28db8)

You can adjust the time range to filter near real time events as well.
![27](https://github.com/user-attachments/assets/1d62514f-fec8-4c1f-a7a8-6ffa49bb519f)

## Step 5: Generate traffics to monitor real time events in CloudWatch Dashboards

Since this is a controlled lab-environment, we will need to generate our own traffics to see if the dashboards are working as expected.

![28](https://github.com/user-attachments/assets/83b68e5b-0e8c-4c68-9501-0161dda431c1)
![29](https://github.com/user-attachments/assets/73deb450-8348-454f-8484-5a5d87f68cd0)

Displays all CloudWatch dashboards in real time.

![30](https://github.com/user-attachments/assets/59a55303-5ad8-4602-be35-36b24f68fb67)



