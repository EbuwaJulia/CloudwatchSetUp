# CloudwatchSetUp
Amazon CloudWatch is a monitoring and observability service provided by AWS that allows you to track and manage metrics, collect and monitor log files, and set alarms for your AWS resources and applications. Here are key features of CloudWatch: Metric Monitoring, Alarms, Logs, Events and Dashboards.

### Skills
* AWS CloudWatch
* Basic monitoring
* Visualization
* Alarm Setup

### Objective
* To Learn how to set up AWS CloudWatch to monitor metrics like CPU usage, disk space, and network traffic for EC2 instances
* To set alarms.

### Procedure
* Log into AWS Console
* Navigate to EC2 Console and Launch an EC2 Instance
#### How to set up Cloudwatch Monitoring for the EC2 Instance
*  Search for CloudWatch in the aws Console and click on it
* By default, CloudWatch will collect basic EC2 metrics, such as CPUUtilization, NetworkIn, NetworkOut, etc.
* To view these, in the CloudWatch console, click on Metrics > EC2.![Screenshot (770)](https://github.com/user-attachments/assets/4f598aec-3a10-425a-8a56-a72afb467adc)
* Here, you should see metrics for your instance.![Screenshot (771)](https://github.com/user-attachments/assets/bd94e8e3-3d82-483a-a5e5-84f9bb0ba6eb)
* To monitor additional metrics like disk space or memory usage, you need to install the CloudWatch Agent on the EC2 instance.(This steps to achieving this would be documented separately)
#### How to set up a CloudWatch Dashboard
* In the CloudWatch console, click on Dashboards on the left-hand side, then select Create dashboard.
* Enter a descriptive name
* You'll now be asked to add widgets to your dashboard. These widgets will visualize the metrics you're tracking.
* Click Add widget.
* Choose Line as the type of graph.
* Under Metrics, click EC2, then choose Per-Instance Metrics.
* Select your instance and click on CPUUtilization(or any metric you intend to monitor).
* Click Create widget.
* Similarly, create another widget for NetworkIn and one for NetworkOut by clickimg the plus (+) sign at the right hand corner. ![Screenshot (772)](https://github.com/user-attachments/assets/0453a278-e0a1-4c5d-b1ac-a4bba865d91d)
* Navigate back to your instance’s metrics under Per-Instance Metrics, and select NetworkIn and NetworkOut.
* You can drag and drop widgets to rearrange them in the dashboard.![Screenshot (773)](https://github.com/user-attachments/assets/60194785-af7c-4ad0-839a-e5431ac5c2da)
* Once you’ve added all the widgets, click Save dashboard.
#### How to Configure CloudWatch Alarms
* In the CloudWatch console, click Alarms on the left sidebar.
* Click on Create alarm.
* Click Select metric, then EC2 > Per-Instance Metrics.
* Choose the metric for CPUUtilization and click Select metric.![Screenshot (774)](https://github.com/user-attachments/assets/40ea0b9d-4d4a-4026-8d7d-09211e69b82c)
**Set the Alarm Conditions**
*  For Threshold type, choose Static.
*  Set the condition to trigger when CPUUtilization is for example greater than 70% for 5 minutes.![Screenshot (776)](https://github.com/user-attachments/assets/1c3bf79b-de2f-470a-87a4-bf25f5bb3172)
**Configure Actions:**
* Under Configure actions, you can set the alarm to send an email notification via SNS (Simple Notification Service).
* Create a new SNS topic, enter your email, and subscribe to it. Scroll down to click Next![Screenshot (777)](https://github.com/user-attachments/assets/2069b776-2782-467c-a2f2-8f8503bef756)
**NOTE:** *To Subscribe, Click **Confirm Subscription** in the mail sent by AWS Notification to the Email endpoint you provided.*
* Name the Alarm
* Review your settings and click Create alarm.
#### Test the Alarm
* Navigate to the EC2 Dashboard
* Select the Instance and click Connect
* Connect to EC2 instance by preferred option which navigates to the EC2 CLI
**Enable the EPEL repository by:**
1. Install the EPEL repository, which contains the ***stress*** package bu imputting the command:
   ```sudo amazon-linux-extras install epel ```
2. Once the EPEL repository is enabled, you can install the stress tool:
   ``` sudo yum install stress -y ```
  


