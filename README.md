# AWS Security Projects
These projects demonstrate AWS security best practices, advanced data protection, AWS compliance controls using automation, proactive measures to defend against security threats and DDoS attacks.

Tech Stack:
- AWS Config
- AWS Security Hub
- AWS Trusted Advisor 
- AWS IAM 
- AWS CloudWatch 
- AWS CloudTrail 
- AWS Secrets Manager
- AWS GuardDuty 
- AWS WAF

## AWS Detective Control using AWS Config
**Overview:** Created two ec2 instances, one with public ports opened (e.g. port 22), and one with 5 ebs volumes attached (some encrypted vs. others that were non-encrypted). I then created config rules to monitor these resources and others created in the future.

Config rules:
- ec2 ports that are open to the public (mark them as “NONCOMPLIANT” )
![Alt text](photos/config-photo1.png)
- EBS volumes are encrypted for all instances across AWS account
![Alt text](photos/config-photo2.png)
- EBS volumes are correctly attached to instances
![Alt text](photos/config-photo3.png)
- Check to see if access keys are older as 90 days (make them as “NONCOMPLIANT”)
![Alt text](photos/config-photo4.png)
- IAM groups have at least one IAM user
![Alt text](photos/config-photo5.png)
- Created an AWS config aggregator to ensure that I can use these same config rules to also monitor resources in another aws account 
![Alt text](photos/aggregator1.png)

Outcome:
- After creating my resources and config rules, 6 resources were marked as noncompliant in my main account.
![Alt text](photos/config-dashboard1.png)
![Alt text](photos/config-dashboard2.png)
- In the aggregated dashboard I see a few more noncompliant resources
![Alt text](photos/aggregator2.png)

AWS Config Remediation