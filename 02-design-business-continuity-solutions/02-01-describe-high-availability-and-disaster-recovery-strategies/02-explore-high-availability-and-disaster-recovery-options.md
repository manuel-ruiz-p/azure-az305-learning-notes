
# 📘 Explore High Availability and Disaster Recovery (HADR) Options

---

## ☁️ IaaS vs. PaaS: HADR Differences

### IaaS (Infrastructure-as-a-Service)

* **Full control** over VM and SQL Server.
* Requires **manual configuration** of HADR.
* Allows use of **SQL Server-level HADR features** and **Azure-native options**.

### PaaS (Platform-as-a-Service)

* HADR is **built-in** (e.g., Azure SQL Database, Azure SQL Managed Instance).
* Minimal configuration; **high availability is included**.

---

## 🛡️ SQL Server HADR Features in Azure VMs

| Feature           | Protects | Description                                                    |
| ----------------- | -------- | -------------------------------------------------------------- |
| **Always On FCI** | Instance | Instance-level protection with shared storage & cluster setup. |
| **Always On AG**  | Database | Database-level replication, synchronous/asynchronous.          |
| **Log Shipping**  | Database | Backup, copy, restore cycle for DR; simple and manual.         |

---

## 🔄 Always On Failover Cluster Instance (FCI)

* Instance-level protection; **requires Windows/Linux cluster**.
* Needs **shared storage** (e.g., Azure Shared Disk, iSCSI).
* On failover: **SQL Server restarts** on another node → temporary disconnection.
* **Internal Load Balancer (ILB)** required in Azure.
* **Needs Active Directory (AD DS)** and **DNS**.

---

## 🧩 Always On Availability Groups (AG)

* Introduced in **SQL Server 2012 (Enterprise)** and **2016 (Standard)**.
* Protects **individual databases** (not instance-level).
* **No shared storage** required.
* Uses a **listener** (name + IP) for abstraction.
* Replicas:

  * **Standard Edition**: 1 Primary + 1 Secondary
  * **Enterprise Edition**: Up to 8 Secondaries
* **Asynchronous or synchronous** data movement.
* Secondary replicas may be used for **read-only** or **backups**.

---

## 🔁 Log Shipping

* Backup → Copy → Restore mechanism.
* **Database-level protection**.
* **No automatic failover**; manual intervention required.
* No native listener; use **DNS aliasing** to simplify switching.
* **Warm standby** created using STANDBY or NORECOVERY modes.

---

## 🧠 Key Considerations

| Factor                 | Description                                                                   |
| ---------------------- | ----------------------------------------------------------------------------- |
| **Abstraction**        | FCI uses cluster name; AG uses listener; Log shipping needs manual DNS alias. |
| **Automatic Failover** | FCI & AG (if configured) support it; Log Shipping does not.                   |
| **Data Loss Risk**     | Depends on sync mode and backup schedule.                                     |
| **Storage Needs**      | AGs require **duplicated storage**; FCIs share storage.                       |

---

# 📚 Exam-Level Questions (with Answers)

### **Question 1**

You need an HA solution for an Azure VM running SQL Server. The solution must support automatic failover at the instance level. What should you use?

- **A.** SQL Server Always On Availability Group
- **B.** SQL Server Always On Failover Cluster Instance
- **C.** SQL Server Log Shipping
- **D.** Azure SQL Database

✅ **Answer:** B. SQL Server Always On Failover Cluster Instance
📝 *Explanation: FCI provides instance-level protection with automatic failover capabilities using clustering.*

---

### **Question 2**

You’re designing an HA solution using AGs in SQL Server 2019 Enterprise. Which of the following is true?

- **A.** AGs require shared storage between replicas
- **B.** AGs protect system-level objects like SQL Agent Jobs
- **C.** AGs use a listener to abstract connectivity
- **D.** AGs are limited to a single replica in Enterprise Edition

✅ **Answer:** C. AGs use a listener to abstract connectivity
📝 *Explanation: AGs do not require shared storage and support up to 8 secondaries in Enterprise.*

---

### **Question 3**

Which HADR solution is the most appropriate for a legacy SQL Server database requiring basic disaster recovery with minimal configuration?

- **A.** Always On AG
- **B.** Log Shipping
- **C.** Always On FCI
- **D.** Geo-Replication

✅ **Answer:** B. Log Shipping
📝 *Explanation: Log shipping is simple, supports legacy environments, and requires minimal setup.*

---

### **Question 4**

Your application requires high availability with minimal downtime and the ability to read from secondary replicas. Which SQL Server HADR option meets the requirement?

- **A.** Log Shipping
- **B.** Always On AG with asynchronous mode
- **C.** Always On AG with synchronous mode and read-only replicas
- **D.** Always On FCI

✅ **Answer:** C. Always On AG with synchronous mode and read-only replicas
📝 *Explanation: Synchronous AG with read-only secondaries allows HA and load balancing.*

---

### **Question 5**

Which feature allows SQL Server HADR in Azure IaaS without requiring DNS or AD DS for a database-level failover?

- **A.** Always On AG with a listener
- **B.** Always On FCI with ILB
- **C.** SQL Server Log Shipping
- **D.** Azure SQL Managed Instance

✅ **Answer:** D. Azure SQL Managed Instance
📝 *Explanation: Azure SQL Managed Instance is a PaaS solution with built-in HADR and no DNS/AD requirements.*

