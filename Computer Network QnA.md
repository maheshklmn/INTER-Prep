


### **1. What is a Computer Network?**

* Interconnected devices that share data and resources.
* Examples: LAN, WAN, MAN, Internet.

---

### **2. What are the layers of the OSI model?**

1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

---

### **3. Difference between TCP and UDP?**

| Feature     | TCP                 | UDP            |
| ----------- | ------------------- | -------------- |
| Type        | Connection-oriented | Connectionless |
| Reliability | Reliable (ACKs)     | Unreliable     |
| Speed       | Slower              | Faster         |
| Use         | HTTP, FTP           | DNS, Streaming |

---

### **4. What is IP addressing?**

* Logical address for identifying a device in a network.
* **IPv4:** 32-bit (e.g., 192.168.0.1)
* **IPv6:** 128-bit (e.g., 2001:db8::1)

---

### **5. What is the difference between Hub, Switch, and Router?**

| Device | Layer     | Function                     |
| ------ | --------- | ---------------------------- |
| Hub    | Physical  | Broadcasts data to all ports |
| Switch | Data Link | Forwards based on MAC        |
| Router | Network   | Forwards based on IP         |

---

### **6. What is DNS?**

* **Domain Name System**: Converts domain names → IP addresses.
* Hierarchical and distributed naming system.

---

### **7. What is ARP and RARP?**

* **ARP (Address Resolution Protocol):** IP → MAC.
* **RARP (Reverse ARP):** MAC → IP.

---

### **8. What is the difference between circuit switching and packet switching?**

| Type         | Circuit        | Packet       |
| ------------ | -------------- | ------------ |
| Connection   | Dedicated path | Dynamic path |
| Resource Use | Fixed          | Efficient    |
| Example      | Telephone      | Internet     |

---

### **9. What is congestion control?**

* Regulates data flow to prevent network overload.
* Example algorithms: TCP Tahoe, Reno, AIMD.

---

### **10. What is the difference between HTTP and HTTPS?**

* **HTTP:** Data sent in plain text.
* **HTTPS:** Secured using SSL/TLS encryption.

---
---

### 5 real-world, step-by-step Computer Network scenarios

---

## ⚙️ **Scenario 1: “What happens when you type `google.com` and press Enter?”**

**Step-by-step answer (short and clear):**

1. **DNS Resolution:** Browser checks cache → OS → DNS server to get IP of `google.com`.
2. **TCP Connection:** Client initiates **TCP 3-way handshake** with the server (SYN → SYN-ACK → ACK).
3. **TLS Handshake (if HTTPS):** Encryption keys are exchanged using SSL/TLS.
4. **HTTP Request:** Browser sends an HTTP(S) GET request to the server.
5. **Server Response:** Google’s server processes request and sends back HTML data.
6. **Rendering:** Browser parses HTML, CSS, JS → renders page on screen.

✅ **Concepts involved:** DNS, TCP/IP, HTTP, SSL/TLS, Browser rendering.

---

## 🌍 **Scenario 2: “You send an email to someone — what happens in the background?”**

**Step-by-step:**

1. Email client connects to **SMTP** server of sender.
2. SMTP sends mail to recipient’s **Mail Transfer Agent (MTA)** using DNS MX lookup.
3. Recipient’s **POP3/IMAP** server stores it.
4. Receiver’s client connects to fetch email via POP3/IMAP.

✅ **Concepts:** SMTP, POP3, IMAP, DNS MX record.

---

## 🖧 **Scenario 3: “Two systems on a LAN communicate — explain how data travels.”**

**Steps:**

1. Source checks **ARP table** to find destination MAC.
2. If not found, it broadcasts an **ARP Request**.
3. Destination replies with its MAC → stored in ARP cache.
4. Source encapsulates data → Ethernet frame → sent to switch.
5. Switch forwards frame to destination port using MAC table.

✅ **Concepts:** ARP, MAC address, Ethernet, Switch, Data Link layer.

---

## 🌐 **Scenario 4: “How does routing work when you access a remote website?”**

**Steps:**

1. Packet leaves your local network via **default gateway (router)**.
2. Router checks **routing table** → forwards based on **destination IP**.
3. Each router decrements **TTL (Time to Live)**.
4. Finally reaches destination IP → packet delivered to server’s socket.

✅ **Concepts:** IP routing, TTL, Router, Hop-by-hop forwarding.

---

## 📡 **Scenario 5: “A user complains: Internet is slow. How will you diagnose it?”**

**Step-by-step troubleshooting:**

1. Check **local connectivity** → ping gateway.
2. Check **DNS resolution** (try pinging domain vs IP).
3. Use **traceroute** to detect hop delays.
4. Check **bandwidth usage** or packet loss.
5. Inspect **router logs or interface errors**.

✅ **Concepts:** Ping, DNS, Traceroute, Congestion, Network diagnostics.

---

Would you like me to add **a few more real-world PSU-style OS + CN integrated scenarios**, like
👉 “When a process on one computer communicates with another using sockets — explain step-by-step”?
These are highly favored in **BARC/ISRO viva**.


---
