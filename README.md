# ec2instancescheduler
EC2 Instance Scheduler CloudFormation Template
Your EC2 instances are running wild at 3 AM. Here's how I cut our AWS bill by 63% without disrupting prod 👀

Last month, I discovered our team was burning through AWS credits faster than expected. The culprit? 

Development instances running 24/7 when our team only works 8 hours a day.

Here's what I implemented:

1. Created an instance scheduler using AWS Lambda + EventBridge
2. Tagged all non-prod instances with 'AutoStop: true'
3. Set up start/stop times aligned with our global team's working hours
4. Added override protection for critical testing periods

The results were immediate:

1. Monthly EC2 costs dropped from $8,500 to $3,145
2. Dev environment uptime matched actual usage patterns
3. Zero impact on production workloads
4. Automated Slack notifications for any manual overrides

Pro tip: Don't just stop instances. Also check for:

1. Orphaned EBS volumes
2. Unused Elastic IPs
3. Over-provisioned RDS instances

Bonus: I created a simple AWS Lambda function that checks for resources without cost allocation tags and sends daily reports. Caught $950 worth of untagged resources in the first week!

Want the CloudFormation template for this setup? Drop a comment below, and I'll share the GitHub repo.
