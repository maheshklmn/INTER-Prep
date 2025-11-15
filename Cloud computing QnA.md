### 10 Most Common Technical Questions (AWS)

1.  **EC2: Stop vs. Terminate:** What is the difference between stopping and terminating an EC2 instance?
    * **Stop:** Shuts down the instance. The EBS volume remains, and you are charged for it, but not for the instance. Can be restarted.
    * **Terminate:** Permanently deletes the instance and (usually) its attached EBS volume. It cannot be recovered.

2.  **Regions vs. Availability Zones (AZs):** Can you explain the difference?
    * **Region:** A large, separate geographical area (e.g., `us-east-1`).
    * **AZ:** One or more isolated data centers within a Region. They have redundant power/networking to protect against local failures.

3.  **What is a VPC?** Explain a Virtual Private Cloud.
    * A VPC is your own logically isolated section of the AWS cloud. It's a virtual network where you control IP ranges, subnets, and route tables.

4.  **Security Groups vs. Network ACLs (NACLs):** How do they differ?
    * **Security Groups (SG):** Act as a stateful firewall for EC2 instances.
    * **NACLs:** Act as a stateless firewall for subnets.

5.  **What is IAM (Identity and Access Management)?**
    * IAM is the service used to securely manage access to AWS services. It controls *who* (users, groups) can do *what* (permissions, roles).

6.  **S3 vs. EBS:** When would you use one over the other?
    * **S3 (Object Storage):** For files, backups, and static website hosting. Accessed via APIs.
    * **EBS (Block Storage):** A "virtual disk" attached to a single EC2 instance, used for the OS, databases, and applications.

7.  **What is Auto Scaling?**
    * An Auto Scaling Group automatically adjusts the number of EC2 instances based on demand or a schedule, ensuring performance and cost-efficiency.

8.  **What is an Elastic Load Balancer (ELB)?**
    * An ELB automatically distributes incoming application traffic across multiple targets (like EC2 instances) in multiple AZs to increase fault tolerance.

9.  **What is Amazon RDS?**
    * Relational Database Service. A managed service for relational databases (like MySQL, PostgreSQL). AWS handles patching, backups, and high availability.

10. **What is AWS Lambda?**
    * A serverless compute service. It lets you run code without provisioning or managing servers, and you only pay for the compute time you use.

---

### 3 Scenario-Based Questions

1.  **High Availability Design:** A client wants to deploy a standard 3-tier web application (web, app, database) and needs it to be highly available. How would you design this on AWS?
    * **Answer:** Place web/app servers in an **Auto Scaling Group** across **multiple AZs**. Use an **Elastic Load Balancer** to distribute traffic. Use **RDS in a Multi-AZ configuration** for automatic database failover.
    [attachment_0](attachment)

2.  **Sudden Traffic Spike:** Your e-commerce site expects a massive, sudden traffic spike for a flash sale. How do you prepare your AWS environment to handle this without crashing?
    * **Answer:** Use an **Auto Scaling Group** with **Dynamic Scaling** (based on CPU/traffic) to automatically add/remove instances. Use **CloudFront (CDN)** to cache static assets and reduce server load.

3.  **Securing a VPC:** You have a public subnet for web servers and a private subnet for a database. What are the key steps to secure this network?
    * **Answer:**
        1.  **Public Subnet:** Use a **Security Group** allowing only HTTP/HTTPS (ports 80/443) from the internet.
        2.  **Private Subnet:** Use a **Security Group** allowing database traffic (e.g., port 3306) *only* from the web server's Security Group.
        3.  **Bastion Host:** Use a Bastion (Jump Box) in the public subnet for any secure admin access to the database.
    * **Answer:** Use an **Auto Scaling Group** with a **Dynamic Scaling policy** (e.g., "target tracking" for CPU usage) to automatically add instances as traffic increases and remove them as it subsides. You could also use **Scheduled Scaling** to pre-warm the fleet just before the sale. Use **CloudFront (CDN)** to cache static assets (images, CSS) to reduce load on the servers.

3.  **Securing a VPC:** You have just created a new VPC for a project. It has a public subnet for your web servers and a private subnet for your database. What are the key steps you would take to secure this network?
    * **Answer:**
        1.  **Public Subnet:** Attach an **Internet Gateway (IGW)**. Place web servers here. Use a **Security Group** that only allows HTTP/HTTPS (ports 80/443) from the internet (`0.0.0.0/0`).
        2.  **Private Subnet:** Do *not* attach an IGW. Place the database here. Use a **Security Group** that only allows database traffic (e.g., MySQL port 3306) *only* from the Security Group of your web servers.
        3.  **NACLs:** Use the default NACLs or create stricter rules (e.g., blocking known malicious IPs) at the subnet level.
        4.  **Bastion Host:** To access the database for maintenance, use a **Bastion Host (Jump Box)** in the public subnet and SSH into that first, then connect to the private database.
        5.  
