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


# m6