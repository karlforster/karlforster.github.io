---
published: true
---

One of the most common problems with most web applications is that performance of the application is impacted by the RDS database instance in the background. One of the most common problems is that a database query is not optomised correctly and take longer to process the results than anticipated.

Long running queries can cause problems with high CPU usage and memory ussage, can also cause your RDS instance to exceed its designated IOPS capacity that was selected when creating the RDS instance. 

Enabling enhanced monitoring and also performance monitoring will enable you as a cloud ops engineer to delve further into performance probelems and resolve production issues faster.

As of September 2021 the following database RDS versions are supported on the below versions



This is subject to change frequently so best to check the below url 
![RDS Supported Versions]({{site.baseurl}}/images/RDS_Supported_versions.png)

Step 1 - Enabling enhanced monitoring

Navigate to Amazon RDS in the AWS console
Select databases
Choose your database
select Modify

Under Additional configuration section of the database configuration, you will find an 
![Enhanced Monitoring]({{site.baseurl}}/images/enhanced-monitoring.png)

Choose a Granularity level for AWS to watch your database queries
Choose a IAM monitoring role to use for accessing to your RDS instance. 
Click Next
Choose apply imediately
Modify DB Instance


Step 2 - Enabling Performance insights

Choose your database
select Modify

Under Additional configuration section of the database configuration, you will find an 
![Enable performance insights]({{site.baseurl}}/images/performance-insights-enable.png)

Choose a retention period for your performance insight data. 
In my opinion it is best to set this to 7 days as this doesnt cause any extra cost to your aws environment as it is included under the free tier.
By doing this, you are enabling the MySQL or MariaDB performance schema in the database software.

choose an AWS KMS secure key to securely store the logs colated by performance insights. 
Click Next
Choose apply imediately
Click: Modify DB Instance

Once the above steps have been completed, you then navigate to RDS console > Performance insights dashboard.
choose the DB Instance you enabled for Performance insights.
You will see your database has a new dashboard available
![Performance insights dashboard]({{site.baseurl}}/images/performance-insights-dash.png)

Which shows the top database load and vCPU statistics

Scrolling down you can see the top SQL commands being run with the calls/sec & rows/sec counters to help troubleshoot bottlenecks.
![Top SQL]({{site.baseurl}}/images/perf_insights_top_sql.png)


Hopefully this will help you get the more out of AWS RDS console and get to the bottom of problems quicker in the platform.
To view the full AWS documentation of how to use Performance insights click the [Full documentation]

[RDS Supported Versions]: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PerfInsights.Overview.Engines.html
[Full documentation]: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PerfInsights.html
