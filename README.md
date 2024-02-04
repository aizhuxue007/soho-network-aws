# SOHO Network Setup in AWS

## 1. Creating a Virtual Private Cloud (VPC)
Create a new VPC to serve as the foundation of your SOHO network. This VPC will isolate your network within AWS.

1. Navigate to the VPC Dashboard within the AWS Management Console.
2. Click on `Create VPC`.
3. Enter a `Name tag` for your VPC, such as `SOHO-VPC`.
4. Specify an IPv4 CIDR block (e.g., `10.0.0.0/16`).
5. Leave the IPv6 CIDR block setting as `No IPv6 CIDR Block` unless you specifically require IPv6.
6. Select `Default` for the Tenancy.
7. Click `Create`.


## 2. Setting Up Subnets
After creating your VPC, set up subnets to divide your network logically. Each subnet could represent a different office area or use case (e.g., employee devices, guest WiFi).

1. In the VPC Dashboard, click on `Subnets` > `Create subnet`.
2. Select your `SOHO-VPC` from the VPC dropdown.
3. Enter a `Name tag` for your subnet, such as `SOHO-Subnet-1`.
4. Choose an Availability Zone.
5. Specify an IPv4 CIDR block (smaller segment of your VPC's CIDR block, e.g., `10.0.1.0/24`).
6. Repeat the steps to create multiple subnets as needed for your network design.
7. Click `Create`.


## 3. Configuring an Internet Gateway (IGW) and Route Tables
To provide internet access to your SOHO network, attach an Internet Gateway to your VPC and configure route tables appropriately.

1. Go to `Internet Gateways` > `Create internet gateway`.
2. Enter a `Name tag`, such as `SOHO-IGW`, and create.
3. Select the newly created IGW, and attach it to your `SOHO-VPC`.
4. Navigate to `Route Tables` > `Create route table`.
5. Enter a `Name tag`, choose your `SOHO-VPC`, and create.
6. Edit routes for the route table: Add a route where the destination is `0.0.0.0/0` and the target is your IGW.
7. Associate your subnet(s) with this route table to enable internet access.


## 4. Launching EC2 Instances for Network Services
Launch EC2 instances within your subnets to simulate networked devices or services (e.g., file servers, workstations).

1. Go to the EC2 Dashboard > `Launch Instance`.
2. Select an Amazon Machine Image (AMI) suitable for your service (e.g., Windows Server for a file server).
3. Choose an instance type (e.g., `t2.micro` for Free Tier eligibility).
4. Configure instance details: select your `SOHO-VPC` and a subnet.
5. Add storage and tags as needed.
6. Configure a security group to control access (e.g., allow RDP or SSH).
7. Review and launch the instance by selecting an existing key pair or creating a new one.


## 5. Security Groups and Network ACLs
Fine-tune your network's security by configuring security groups and network ACLs to control inbound and outbound traffic.

1. In the VPC Dashboard, navigate to `Security Groups` > `Create security group`.
2. Provide a `Name tag`, description, and associate it with your `SOHO-VPC`.
3. Specify inbound and outbound rules according to your network needs (e.g., allow HTTP/HTTPS for web servers).
4. Apply these security groups to your EC2 instances and other resources as needed.

## Conclusion
This setup outlines the creation of a basic SOHO network within AWS, focusing on a VPC setup, subnetting, internet access configuration, instance deployment, and security configurations. Be sure to add screenshots and detailed descriptions in your Markdown documentation to guide readers through each step effectively.
