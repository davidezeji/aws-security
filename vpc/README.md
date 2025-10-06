# How To Use an Outbound VPC Proxy for Domain Whitelisting and Content Filtering

**Scenario:** You want to secure your outbound traffic from your VPC in AWS. You desire to filter the content that the servers in this VPC can access both at the URL and IP address level. By restricting servers from potentially reaching out to bad actors, you protect the security of your internal network.

## Network Architecture
*** Note: A bastion host is used provisioned to connect to the application instance and check if  
![Alt text](photos/vpc1.png)

## Steps
1. Create a key pair
