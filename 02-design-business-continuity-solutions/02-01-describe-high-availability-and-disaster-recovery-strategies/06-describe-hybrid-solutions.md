
# Describe Hybrid Solutions – AZ-305 Study Guide

## Overview

Hybrid solutions combine **on-premises infrastructure** with **cloud-based resources**, enabling flexibility, resilience, and support for both legacy and modern applications. In the context of SQL Server and Azure, hybrid architectures are primarily used for **high availability (HA)** and **disaster recovery (DR)**, especially during **cloud migration** or to **extend existing datacenters**.

---

## Key Concepts

### 🔄 Recovery Objectives

* **RTO (Recovery Time Objective):** Maximum acceptable time for restoring operations after a failure.
* **RPO (Recovery Point Objective):** Maximum acceptable data loss measured in time.

Understanding RTO and RPO helps determine the right architecture and technologies to meet business continuity goals.

---

## 🧩 Hybrid Architecture Scenarios

### 1. **Hybrid Architecture Definition**

A hybrid architecture spans on-premises and Azure (or even other clouds), allowing systems to continue functioning despite partial failures or outages.

---

### 2. **Use Cases for Hybrid HA/DR**

* DR extension for on-prem SQL Server using Azure.
* Migration step from on-prem to full cloud deployment.
* Cross-cloud HA (e.g., AWS → Azure).

---

### 3. **Limitations of PaaS in Hybrid**

* Azure SQL Database and SQL Managed Instance **do not support traditional hybrid AG or FCI scenarios**.
* PaaS is managed by Azure and abstracts most of the infrastructure, limiting integration with on-prem HADR technologies.

**⚠️ Exception:**
You can use **SQL Server transactional replication** from an **on-premises publisher** to an **Azure SQL Managed Instance subscriber**. However, replication **does not work in reverse**.

---

### 4. **Hybrid IaaS-based Solutions**

Most hybrid HADR solutions must use **SQL Server in IaaS (VMs)** to retain control over clustering, replication, and configuration.

**Example:**

* On-prem AG → Secondary replica in Azure.
* Requires configuration of:

  * **Active Directory Domain Services (AD DS)**
  * **DNS**
  * **Quorum voting**

---

### 5. **Networking Considerations**

Reliable, fast, and secure networking is essential to meet HADR objectives:

* **Azure ExpressRoute:** Private, dedicated high-throughput connection between on-prem and Azure.
* **Site-to-Site VPN:** Secure alternative if ExpressRoute is unavailable.
* **⚠️ Avoid exposing Azure VMs to the public internet.**

---

### 6. **Backup and Archival Storage**

* Azure can serve as:

  * Destination for **SQL Server backups**.
  * Cold storage/archive location using **Azure Blob Storage**.

Even if it's not a full hybrid architecture, **using Azure for backups** enhances disaster recovery posture.

---

## Summary Table

| Feature                           | PaaS Support | IaaS Support | Hybrid Ready | Notes                                     |
| --------------------------------- | ------------ | ------------ | ------------ | ----------------------------------------- |
| Transactional Replication         | ⚠️ Partial   | ✅            | ⚠️ One-way   | Only from on-prem to Azure SQL MI         |
| Availability Groups (AGs)         | ❌            | ✅            | ✅            | Requires AD, DNS, and reliable networking |
| Failover Cluster Instances (FCIs) | ❌            | ✅            | ✅            | Requires shared storage                   |
| Azure Site Recovery               | ❌            | ✅            | ✅            | Works at VM level, not SQL specific       |
| Backup to Azure Blob              | ✅            | ✅            | ✅            | Works with native SQL backup features     |

---

## 📘 Best Practices

* Always define and test your RTO and RPO targets.
* Use ExpressRoute for enterprise-grade hybrid networking.
* Do not expose IaaS SQL Server VMs to the public internet.
* Leverage Azure storage for cost-effective, secure backup storage.

---

## 📝 Practice Questions (Exam Style)

### **Question 1**

Which of the following hybrid solutions is supported when using SQL Server transactional replication?

**A.** Azure SQL Managed Instance as a publisher to on-prem subscriber
**B.** Azure SQL Database to on-prem SQL Server
**C.** On-prem SQL Server as publisher to Azure SQL Managed Instance
**D.** SQL Server IaaS to PaaS back replication

✅ **Answer:** C

---

### **Question 2**

Why is PaaS typically not used for hybrid HADR solutions?

**A.** PaaS supports shared disks
**B.** PaaS doesn't allow control over infrastructure like AD or clustering
**C.** PaaS offers built-in hybrid failover
**D.** PaaS is only available in private networks

✅ **Answer:** B

---

### **Question 3**

Which network configuration is recommended to support a hybrid availability group spanning on-premises and Azure?

**A.** Expose SQL Server VMs to the internet
**B.** Use site-to-site VPN or ExpressRoute
**C.** Use public DNS with failover routing
**D.** Configure peering with public IPs

✅ **Answer:** B

---

### **Question 4**

Which Azure service can be used as a cold storage target for SQL Server database backups in a hybrid scenario?

**A.** Azure SQL Database
**B.** Azure ExpressRoute
**C.** Azure Blob Storage
**D.** Azure Key Vault

✅ **Answer:** C

---

### **Question 5**

What is a key requirement when extending an on-premises availability group to Azure?

**A.** Using Azure SQL PaaS
**B.** No need for Active Directory
**C.** Shared storage across regions
**D.** Setting up AD DS and DNS in Azure

✅ **Answer:** D

