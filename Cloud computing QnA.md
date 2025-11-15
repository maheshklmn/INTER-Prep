
# 🔹 **1. EC2: Stop vs. Terminate**

### **🚫 Stop**

* Shuts down the EC2 instance (like powering off a computer).
* **EBS volume stays**, and you pay for storage but **not compute**.
* Instance can be **started again** (same data preserved).

### **❌ Terminate**

* Permanently deletes the EC2 instance.
* Attached EBS volumes are also deleted *(unless "Delete on termination" = false).*
* **Cannot be recovered**.

---

# 🔹 **2. Regions vs. Availability Zones (AZs)**

### **🌍 Region**

* A geographical area (e.g., `us-east-1`).
* Contains multiple AZs.
* Separated for disaster isolation.

### **🏢 Availability Zone**

* An isolated datacenter (or group of datacenters) inside a region.
* Each AZ has **independent power, cooling, and networking**.
* AZs are interconnected with **low-latency links**.

---

# 🔹 **3. What is a VPC?**

### **🔐 Virtual Private Cloud**

* Your own **isolated network** inside AWS.
* You control:

  * IP ranges
  * Subnets
  * Routing
  * Firewalls
  * Internet access

It's like your **private data center** in the cloud.

---

# 🔹 **4. Security Groups vs NACLs**

| Feature                               | Security Group (SG) | Network ACL (NACL)     |
| ------------------------------------- | ------------------- | ---------------------- |
| Level                                 | Instance level      | Subnet level           |
| Type                                  | Stateful            | Stateless              |
| Return traffic allowed automatically? | ✅ Yes               | ❌ No                   |
| Best used for                         | EC2 protection      | Subnet-level filtering |

---

# 🔹 **5. What is IAM?**

### **🧑‍💼 Identity & Access Management**

* Defines **who** can access **what** in AWS.
* Uses:

  * Users
  * Groups
  * Policies
  * Roles

It ensures secure, permission-based access to AWS resources.

---

# 🔹 **6. S3 vs. EBS**

### **🗂️ Amazon S3**

* Object storage
* Unlimited storage
* Access via API
* Ideal for:

  * Backups
  * Logs
  * Images/media
  * Static website hosting

### **💽 Amazon EBS**

* Block storage for EC2 instances
* Acts like a virtual hard drive
* Ideal for:

  * OS disks
  * Databases
  * Applications requiring low-latency storage

---

# 🔹 **7. What is Auto Scaling?**

### **📈 Auto Scaling Group (ASG)**

* Automatically **adds or removes EC2 instances**
* Based on:

  * CPU
  * Network traffic
  * Requests
  * Schedule

Ensures performance **and** reduces cost.

---

# 🔹 **8. What is an Elastic Load Balancer (ELB)?**

### **⚖️ Load Balancer**

* Distributes incoming traffic across multiple targets (EC2, Lambda, containers).
* Supports:

  * High availability
  * Fault tolerance
  * Zero-downtime updates

---

# 🔹 **9. What is Amazon RDS?**

### **🗄️ Managed Database Service**

* Supports: MySQL, PostgreSQL, Oracle, SQL Server, MariaDB.
* AWS handles:

  * Backups
  * Maintenance
  * Patching
  * Multi-AZ failover
  * Monitoring

---

# 🔹 **10. What is AWS Lambda?**

### **⚡ Serverless Compute**

* Run code *without servers*.
* Pay only for **execution time**.
* Automatically scales to any load.

---

---

# 🟦 **Scenario-Based AWS Questions (Beautifully Structured)**

---

## **📌 Scenario 1: High Availability 3-Tier Application**

### **Q:** How do you design a highly available Web–App–Database architecture?

### **✅ Answer:**

1. **Web & App Layer**

   * Use **Auto Scaling Groups** across **multiple AZs**
   * Add an **Application Load Balancer (ALB)**

2. **Database Layer**

   * Use **RDS Multi-AZ** (automatic failover)
   * Private subnet for DB for added security

3. **Network**

   * Public subnet → ALB
   * Private subnet → App + DB

This ensures **fault tolerance + scalability**.

---

## **📌 Scenario 2: Handling Sudden Traffic Spike (Flash Sale)**

### **Q:** Your e-commerce site expects massive sudden traffic. How do you prepare?

### **✅ Answer:**

* Use **Auto Scaling Group with Dynamic Scaling**

  * Target tracking (e.g., maintain CPU at 50%)
* Use **Scheduled Scaling**

  * Scale up 5 minutes *before* the flash sale
* Use **CloudFront CDN**

  * Cache static assets (images, CSS, JS)
* Pre-warm load balancers (if extremely high expected load)

Ensures smooth handling of unpredictable spikes.

---

## **📌 Scenario 3: Securing VPC (Public Web + Private Database)**

### **Q:** How do you secure the architecture?

### **🔒 Answer:**

#### **Public Subnet (Web Servers)**

* Security Group:

  * Allow **80/443** from `0.0.0.0/0`
  * Deny SSH from public

#### **Private Subnet (DB)**

* Security Group:

  * Allow **3306** *only from* web server SG
  * No public internet access

#### **Admin Access**

* Use **Bastion Host** in the public subnet
* Access DB through SSH → Bastion → DB server

This ensures:

* No direct DB exposure
* Minimal attack surface
* Controlled access paths

---
