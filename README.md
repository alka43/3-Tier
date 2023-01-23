# 3-Tier
What is a Three-Tier Architecture? 🤔
A 3-Tier architecture provides a general framework for deploying traditional client/server applications into three logical tiers; the Web, Application, and Database tier. End users interact with the Web tier (e.g., mobile app, website, etc.), which provides them with a user interface they can use to view, modify, or submit information. The Application tier is responsible for handling the requests made by the user. The Application or Middle tier is the brains 🧠 behind the operation. It assists in translating users actions into business logic that allow for data processing by programs. Lastly, the Database or Data tier is where the information processed by the application is stored and managed.

Objective

#Deploy Web Tier

2 public subnets
Public route table
Internet Gateway & NAT Gateway
Internet facing Application Load Balancer with a Security Group allowing inbound permission from the Internet.
Minimum of 2 EC2 instances in an Auto Scaling Group.
EC2 Security Group allowing inbound permission from the the Web Tier Application Load Balancer
Boot strap static web page.
Create a public route table and associate the 2 public subnets

#Deploy Application Tier

2 private subnets
Private route table
Internal Application Load Balancer with a Security Group allowing inbound permission from EC2 instances in the Web Tier
Minimum of 2 EC2 instances in an Auto Scaling Group
EC2 Security Group allowing inbound permission from the Application Tier Application Load Balancer
Associate with private route table
📝Note: This is not a true application tier and we will simply boot strap a static web page on the EC2 instances in the Application tier for demonstration purposes

#Deploy Database Tier

2 private subnets
Public route table
MySql RDS Database with Multi AZ standby instance
The Database Security Group allowing inbound traffic for MySQL from the Application Server Security Group
Deploy Bastion Host

Third public subnet
Public route table
EC2 instance
EC2 Security Group allowing SSH inbound permission from the Internet
Grant the Bastion Host EC2 instance Security Group access to resources in the Web, Application, and Database Tier 😊

📝NOTE: A Bastion Host is a server whose purpose is to provide access to a private network from an external network, such as the Internet. None of the resources we deploy (besides our Bastion Host and Web Tier Application Load Balancer) will be directly accessible from the Internet due to the rules we set on the Security Groups.
