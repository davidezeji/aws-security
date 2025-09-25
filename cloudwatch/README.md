# Proactively Monitor and Respond to Failed SSH Logins to EC2 Instances Using CloudWatch

**Scenario:** Let's say you want to defend your ec2 instances running critical applications, from intrusion attempts. Within your organization you give developers SSH access to these instances, but you need a proactive method of preventing bad actors from having similar access.

**Security Setup:**
1. Maliscious user tries to ssh into instance 
2. Cloudwatch agent installed on ec2 instance monitors logs of ssh attempts and sends them to cloudwatch logs 
3. In cloudwatch logs custom metrics alert a Lambda function (e.g. using the "ssh_invalid_user" log filter) 
4. A Lambda function will be subscribed to this log group invokes step functions 
5. Step functions check instance to see if there are an abnormal amount of ssh attempts, furthermore isolating the instance and sending a notification to the security team of what is going on.

**Note:** This security setup can be deployed in your aws account using the CloudFromation template called "remediate-ssh-access.template.json" in this repository

## Steps
