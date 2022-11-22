# M3
Data transfer OUT to the internet has tiered pricing per GB. 
Data transfer OUT to other AWS services has a cost per GB.

AWS Snowball is good for transfering dozens of TB to PB (petabytes) of data to AWS. Local data transfer to a Snowball device is faster than transfering directly to S3 over the internet. Transfer time to AWS depends on physical package shipping times.

When using multipart uploads, an upload failure requires a restart of only failed part uploads instead of restarting the entire file upload. This method provides a better solution for unreliable connections.

# m4

1/ Use EC2 when compete control, down to the OS level, is required. 
EC2 can run any type of workload, including web, app, db, and media servers.
An EC2 instance can run any workload that a physical server can run.

2/ AMIs are point-in-time images of EC2 instances.
You cannot use an AMI to image non-EC2 system.
You cannot patch an AMI, and you cannot modify launched instances through the AMI that was used to launch them. AMIs do not contain security group settings.

AMIs contain EC2 instance configuration, so instances that are launched from the same AMI have the same config .

AMIs are images of EC2 instances, so they can be used as backups.
Vendors sell software solutions that are packaged as AMIs through ÁWS Marketplace.

3/ An EBS-backed instance must be stopped before changing the instance type.
Chnage the instance type of an EBS-backed instance by stopping it first.

**An instance stored-backed instance cannot be stopped**. it can only be rebooted or terminated. Terminate the instance and launch a new one with the new instance type.

4/ A workload requires high **read/write access to large local datasets**. --> which types would perform best for this workload?

This workload is **memory-intensive** or **storage-intensive, or both**.

Compute optimized and accelerated computing instances are better for CPU-intensive workloads.

General purpose instances provide a balance of compute, memory, and networking resources.

Memory optimized instances are designed for processing large datasets in memory.
Storage optimized instances  are designed for workloads that require high, sequential read/write access to very large datasets on local storage.

5/ Because the AWS auto scaling group launches the instances. the MAC (Media Access Control) address of each instance is unpredictable. The user data script can access the MAC address from the instance metadata when the instance starts, and then notify the app.

6/ provisioned IOPS SSD EBS volumes are optimzed for I/O-intensive workloads.

7/ As a fully managed service, Amazon EFS provides high availability. An NFS server on an instance is a single point of failure, which can become overloaded. EFS also scales automatically, and you pay for only what you use. EBS does not scale automatically. 

8/ FSx for windows file server integrates with Microsoft Active Directory (AD), but it does not provide a Microsoft AD.
FSx for windows file server provides fully managed windows file server, which are build on Microsoft file server

9/ with on-demand instances you can pay for compute capacity based on your usage. Also, by using spot instances you can achieve cost saving due to discounted prices.

10/ A company has 3 high-performance computing instances that must communicate with each other. The company would like to achieve max network performance between the instances. The most important requirement is that these system do not share the same rack. Which placement strategy should they use?

Cluster placement maximizes netwwork performance between the instances, but it places them all in the same hardware rack. A failure of the rack would affect all of the instances.

Partition placement spreads instances across logical partition to reduce correlated hardware fail.., but instances in the same partition might be on the same rack. **This strategy is intended for large numbers of instances**.

The spreads placement strategy ensures that the instances are placed in separate hardware racks, each with its own network and power source. This strategy min the risk of correlated hardware faiures.

#  m5

1/ AC 
For data volume, non-relational databases scale horizontally and relational db scale vertically. Non-relational db can hadle data with unpredictable attributes. Relational db use strict schemas, so data attributes must be identified in advance. 

2/ B

AWS provides managed backup capabilities for managed db services, **but you are still responsible for configuring the backups**.

aws patches the db system as part of a managed db service, which enables you to focus on your application. AWS managed db services also provide high availability, scalability, and backup as built-in options that you can configure.


3/ BCE 
Amazon RDS is not serverless; it runs server instances. 
An RDBMS sends writes to the primary server and distributes reads to read replicas. High write activity can overload the primary. RDS is not optimized for data warehouse users; use Amazon Redshift instead. 

RDS supports Microsoft SQL Server and many other popular relational db engines. It is useful when the application offloads syntax enforcement to the db, and when data queries include complex joins of data from many tables.

(ENFORCE: làm cho mạnh, bắt tuân theo; offloads: giảm tải; )

4/ ACD false; ABD false; 
Managed services provide high availability and backups as configurable options. They can be implemented for EC2 as part of the architecture design.

5/  ADE false; ACE false
DynamoDB is better when data can be stored in a few tables. 
An RDBMS is better suited to joining data from many tables. 

DynamDB is not a graph db; use Amazon Neptune instead.

Do not store BLOBs in DynamoDB; store a link to the BLOB that is stored in S3.

6/ BC true
Because players create their own objects, the obj attributes are unpredictable and the db schema cannot be determined beforehand.
A large number of obj, each with potential different attributes, is a good use case for DynamoDB.

7/ BEF

The RDBMS controls access to tables and data, and IAM does not. 
WHY <-- VPC gateway endpoints are not available for Amazon RDS; use network ACLs, security groups and VPC interface endpoints to restrict traffic. 
A VGW (Virtual gateway?) is used in AWS Direct Connect, not to filter traffic.

Because RDS uses server instances, they deploy in an AmazoN VPC, and you control network access to them by using  security groups. It is always a good idea to use encryption to protect sensitive data in RDS, both at rest and in transit.


8/ CEF false; CDE false
Because DynamoDB is serverless, it does not have instances that deploy in a VPC and use security groups.
A VGW  is used in AWS Direct Connect, not to filter traffic.

9/ C
The schema will most likely not be fully supported in the target db without conversion. Use AWS Schema Conversion Tool (SCT) before AWS DMS.

SCT analyzes the schema of the source fb, does the conversion, and then creates the schema in the target db. AWS DMS then copies the data to the target db.

10/ a
Because AWS SCT connects to a db engine, you should run it locally. The alternative is a homogenous migration to a db in AWS first, which is less efficient.

# m6

1/ C
A VPC is a logically isolated virtual network that you define in the AWS Cloud.

A VPC is a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment.

2/ cde
Running out of addresses might require complicated network re-addressing. 
Adding more CIDR blocks to a VPC is possible, but is not a solution for inadequate planning. 
Distributing subnets and hosts across AZs reduces the chance of correlated failures.

(inadequate: không thỏa đáng, không đủ; correlated: tương quan)

3/ D


4/ C
These CIDR blocks (172.16.0.0/21) are the next larger size from /24.
AWS reserves 5 addresses per subnet, so each CIDR block has 507 usable addresses. This scheme provides room for the growth  requirement.

5/ BDF false, CDF false
A VGW is a virtual private gateway and is used for AWS Direct Connect. 
DNS resolution and VPC domain name configuration are not required for IP traffic.

6/ A
using an Elastic IP address helps to ensure that the instance has the same internet 
address. 

7/ D
A NAT gateway provides the EC2 instances with internet-routable source addresses for sessions that EC2 instances initiate. Hower, it does not enable internet access to the instances.

8/ BD
You must modify the security group of each instnace to allow traffic. Following the principle of least privilege, the SGs should limit traffic to only those systems tha need access. 
You can allow traffic to IP addresses and other SGs.

9/ C

Add rules to the subnet custom network ACL to allow traffic from and to allowed internet addresses.

A **custom network ACL** includes a rule to deny of all traffic (this rule is called implicit deny). You do not need to add a rule to deny all other traffic.


// public subnet >< private subnet, secure subnet ??

the default network ACL >< the subnet ***custom*** network ACL

10/ D false, C false
Although this solution (in the SG, allow traffic only to and from address ranges that exclude the restricted addresses) would work, network masking for CIDR (Classless Inter-Domain Routing) blocks can make this complicated and difficult to manage.
