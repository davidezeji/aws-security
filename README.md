# AWS Security Projects
These projects demonstrate AWS security best practices, advanced data protection, AWS compliance controls using automation, proactive measures to defend against security threats and DDoS attacks.

**Tech Stack:**
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

**Config rules:**
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
- I also created an AWS config aggregator to ensure that I can use these same config rules to also monitor resources in another aws account 
![Alt text](photos/aggregator1.png)

Outcome:
- After creating my resources and config rules, 6 resources were marked as noncompliant in my main account.
![Alt text](photos/config-dashboard1.png)
![Alt text](photos/config-dashboard2.png)
- In the aggregated dashboard I see a few more noncompliant resources
![Alt text](photos/aggregator2.png)

**AWS Config Remediation**

I also created some additional config rules via cloudformation to:
- enable s3 bucket versioning
- enable s3 bucket server side encryption
- ensure no public IPs for ec2 instances (stops them, doesn't delete them)
- approve AMI's by tag/ID

** In order to enforce compliance for these rules I added onto the cloudformation scripts auto-remediation steps for noncompliant resources (scripts can be found in the "config-remediation" folder)

Example: Here is my deployment of the cloudformation script to ensure s3 bucket versioning is enabled across my AWS account.

* Deployment of cloudformation...
![Alt text](photos/config-remediation1.png)
![Alt text](photos/config-remediation2.png)
![Alt text](photos/config-remediation3.png)

* S3 buckets that are not versioned are marked as noncompliant...
![Alt text](photos/config-remediation4.png)

* S3 bucket which is noncompliant (non-versioned) is identified and remediation moves it from noncompliant to compliant
![Alt text](photos/config-remediation5.png)
![Alt text](photos/config-remediation6.png)
![Alt text](photos/config-remediation7.png)



