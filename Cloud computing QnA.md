### 10 Most Common Technical Questions (AWS)

1.  **EC2: Stop vs. Terminate:** What is the difference between stopping and terminating an EC2 instance?
    * **Stop:** The instance shuts down, but the EBS volume remains. You are not charged for instance usage but are charged for the storage. You can restart it later.
    * **Terminate:** The instance and its attached EBS volumes (unless configured otherwise) are permanently deleted. You cannot recover it.

2.  **Regions vs. Availability Zones (AZs):** Can you explain the difference?
    * **Region:** A large, separate geographical area (e.g., `us-east-1` in N. Virginia).
    * **Availability Zone (AZ):** One or more discrete data centers within a Region, with redundant power and networking. They are isolated from failures in other AZs.

3.  **What is a VPC?** Explain a Virtual Private Cloud.
    * A VPC is your own logically isolated section of the AWS cloud. It's a virtual network where you can launch AWS resources, controlling its IP address range, subnets, route tables, and network gateways.

4.  **Security Groups vs. Network ACLs (NACLs):** How do they differ?
    * **Security Groups (SG):** Act as a firewall for EC2 instances (stateful). They control *inbound* and *outbound* traffic at the instance level.
    * **NACLs:** Act as a firewall for subnets (stateless). They control *inbound* and *outbound* traffic at the subnet level, acting as an additional layer of defense.

5.  **What is IAM (Identity and Access Management)?**
    * IAM is the service you use to manage access to AWS services and resources securely. You use it to create and manage AWS users, groups, and roles and use permissions (policies) to allow or deny their access.

6.  **S3 vs. EBS:** When would you use one over the other?
    * **S3 (Simple Storage Service):** Object storage. Used for storing files, backups, and static website hosting. It's accessed via APIs and is not a "file system" you can mount.
    * **EBS (Elastic Block Store):** Block storage (like a hard drive). It's a "virtual disk" that you attach to a single EC2 instance and is used for the operating system, databases, and applications.

7.  **What is Auto Scaling?**
    * An Auto Scaling Group automatically adjusts the number of EC2 instances in your fleet based on demand (e.g., high CPU) or on a fixed schedule. It ensures you have the right number of instances to handle your application's load.

8.  **What is an Elastic Load Balancer (ELB)?**
    * An ELB automatically distributes incoming application traffic across multiple targets, such as EC2 instances, in one or more Availability Zones. This increases fault tolerance and availability.

9.  **What is Amazon RDS?**
    * Relational Database Service. It's a managed service that makes it easy to set up, operate, and scale a relational database (like MySQL, PostgreSQL, SQL Server) in the cloud. AWS handles patching, backups, and high availability.

10. **What is AWS Lambda?**
    * A serverless compute service. It lets you run code without provisioning or managing servers. You only pay for the compute time you consume, and it automatically scales your code in response to events (e.g., an image upload to S3).

---

### 3 Scenario-Based Questions

1.  **High Availability Design:** A client wants to deploy a standard 3-tier web application (web, app, database) and needs it to be highly available and fault-tolerant. How would you design this on AWS?
    * **Answer:** Place EC2 instances for the web/app tiers in an **Auto Scaling Group** across **multiple Availability Zones**. Distribute traffic to them using an **Elastic Load Balancer**. For the database, use **RDS in a Multi-AZ configuration**, which creates a standby replica in a different AZ for automatic failover.
    

2.  **Sudden Traffic Spike:** Your e-commerce site expects a massive, sudden traffic spike for a flash sale. How do you prepare your AWS environment to handle this without crashing or over-provisioning (and over-paying) for weeks?
    * **Answer:** Use an **Auto Scaling Group** with a **Dynamic Scaling policy** (e.g., "target tracking" for CPU usage) to automatically add instances as traffic increases and remove them as it subsides. You could also use **Scheduled Scaling** to pre-warm the fleet just before the sale. Use **CloudFront (CDN)** to cache static assets (images, CSS) to reduce load on the servers.

3.  **Securing a VPC:** You have just created a new VPC for a project. It has a public subnet for your web servers and a private subnet for your database. What are the key steps you would take to secure this network?
    * **Answer:**
        1.  **Public Subnet:** Attach an **Internet Gateway (IGW)**. Place web servers here. Use a **Security Group** that only allows HTTP/HTTPS (ports 80/443) from the internet (`0.0.0.0/0`).
        2.  **Private Subnet:** Do *not* attach an IGW. Place the database here. Use a **Security Group** that only allows database traffic (e.g., MySQL port 3306) *only* from the Security Group of your web servers.
        3.  **NACLs:** Use the default NACLs or create stricter rules (e.g., blocking known malicious IPs) at the subnet level.
        4.  **Bastion Host:** To access the database for maintenance, use a **Bastion Host (Jump Box)** in the public subnet and SSH into that first, then connect to the private database.
        5.  
