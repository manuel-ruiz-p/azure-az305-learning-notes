
# Explore High Availability and Disaster Recovery Solution for IaaS (AZ-305)

## Key Architectures and Scenarios

### 1. **Single Region High Availability – Always On Availability Groups**

* Multiple SQL Server VMs with synchronous data replication.
* No shared storage required.
* Provides automatic failover and read replicas.
* Suitable for scenarios where high availability (HA) is needed within one region.

**Advantages:**

* Protection from VM/node failure.
* Minimal data loss if implemented correctly.
* Improved patching availability.
* Supports application connection redirection.

---

### 2. **Single Region High Availability – Always On Failover Cluster Instance (FCI)**

* Traditional HA method based on Windows Server Failover Clustering (WSFC).
* Requires shared storage (e.g., Azure Shared Disk or Storage Spaces Direct).
* More relevant in physical setups but still supported in Azure.

**Advantages:**

* Enhanced availability.
* Familiar setup for on-prem SQL admins.
* Works well with newer Azure shared storage features.

---

### 3. **Multi-Region / Hybrid Disaster Recovery – Always On Availability Groups**

* Cross-region AGs using WSFC to replicate data across regions.
* Requires Active Directory, DNS, and potentially on-prem integration.

**Advantages:**

* Combines HA and DR in a single feature.
* Data redundancy across regions.
* Works with Standard and Enterprise editions.

---

### 4. **Disaster Recovery – Distributed Availability Groups**

* "AG of AGs" setup, introduced in SQL Server 2016 (Enterprise only).
* Involves multiple WSFC clusters, each with its own quorum and witness.

**Advantages:**

* Reduces single point of failure.
* Easier to manage large-scale DR.
* Suitable for hybrid and multi-region scenarios.

---

### 5. **Disaster Recovery – Log Shipping**

* Backup, copy, and restore of transaction logs from primary to secondary server.
* Simple and robust solution with minimal configuration.

**Advantages:**

* Works over unreliable networks.
* Protects against data loss in FCIs.
* Cost-effective and easy to set up.

---

### 6. **Disaster Recovery – Azure Site Recovery**

* Platform-based DR solution replicating entire VMs.
* Not SQL-specific, but broad in support.

**Advantages:**

* Simple to configure in the Azure Portal.
* Good for organizations seeking VM-level DR rather than database-level.
* Useful for workloads beyond SQL Server.

---

## Summary

| Architecture                 | High Availability | Disaster Recovery | Shared Storage | Complexity | Suitable for |
| ---------------------------- | ----------------- | ----------------- | -------------- | ---------- | ------------ |
| Always On AG (single region) | ✅                 | ❌                 | ❌              | Moderate   | HA in region |
| FCI                          | ✅                 | ❌                 | ✅              | Moderate   | Legacy setup |
| Multi-region AG              | ✅                 | ✅                 | ❌              | High       | Full HADR    |
| Distributed AG               | ✅                 | ✅                 | ❌              | High       | Hybrid/large |
| Log Shipping                 | ❌                 | ✅                 | ❌              | Low        | Basic DR     |
| Azure Site Recovery          | ❌                 | ✅                 | ❌              | Low        | VM-based DR  |

---

## Practice Questions (Multiple Choice)

### **Question 1**

Which architecture uses multiple Always On Availability Groups to form a distributed topology across regions?

**A.** Log Shipping
**B.** Azure Site Recovery
**C.** Distributed Availability Groups
**D.** Failover Cluster Instance (FCI)

✅ **Answer:** C

---

### **Question 2**

Which of the following is TRUE about Failover Cluster Instances (FCIs) in Azure?

**A.** FCIs are only supported on physical servers, not virtual machines.
**B.** FCIs require shared storage and are ideal for scenarios without Azure Shared Disk.
**C.** FCIs provide HA without requiring shared storage.
**D.** FCIs are still viable in Azure with features like Azure Shared Disk.

✅ **Answer:** D

---

### **Question 3**

What is the PRIMARY benefit of using Azure Site Recovery for SQL Server disaster recovery?

**A.** Database-level failover with zero RPO
**B.** Fast transaction log shipping
**C.** VM-level replication that supports workloads beyond SQL Server
**D.** Requires minimal storage configuration like AGs

✅ **Answer:** C

---

### **Question 4**

Which HA/DR method is ideal for unreliable network environments?

**A.** Always On Availability Groups
**B.** Azure Site Recovery
**C.** Log Shipping
**D.** Distributed Availability Groups

✅ **Answer:** C

---

### **Question 5**

Why might you choose a multi-region Availability Group configuration?

**A.** You want the lowest cost option with manual backups.
**B.** You need a hybrid solution with HA and DR and region failover.
**C.** You want to avoid using Active Directory and WSFC.
**D.** You need support for SQL Server Express edition.

✅ **Answer:** B

