
# Describe High Availability and Disaster Recovery for PaaS Deployments

---

## 🔹 Overview

Platform as a Service (PaaS) offerings in Azure, such as **Azure SQL Database** and **Azure SQL Managed Instance (MI)**, are designed with **built-in high availability (HA)** and **disaster recovery (DR)**. You don’t manage the underlying infrastructure; instead, Azure provides mechanisms to ensure continuity, uptime, and data integrity, even during failures or disasters.

---

## ✅ Built-in High Availability for Azure SQL Services

### Azure SQL Database & SQL Managed Instance

* **Availability SLA:**
  Guaranteed **99.99% availability** via redundancy across compute and storage.

* **Automatic Failover:**

  * When a **node or hardware** fails, Azure detects the failure.
  * It spins up a **new node** and **reattaches the existing data** (stored separately).
  * All **committed transactions** are written synchronously to storage.
  * **Transient failures** may cause dropped connections — app-side **retry logic is required**.

> **Best Practice:** All cloud-native applications should be resilient to transient failures by implementing **exponential backoff retry logic**.

---

## ✅ Geo-Redundancy and Disaster Recovery Options

| **Feature**                | **Applies To**          | **Description**                                                                   |
| -------------------------- | ----------------------- | --------------------------------------------------------------------------------- |
| **Active Geo-Replication** | Azure SQL Database only | Manual failover between up to **4 readable secondaries** across regions.          |
| **Auto-Failover Groups**   | SQL DB & SQL MI         | Enables **automatic failover** across paired regions with **read/write routing**. |

* **Read Replicas**

  * Improve availability and **offload workloads** (e.g., reporting).
  * Deployed in **different Azure regions** for regional resilience.
  * Automatically **kept in sync** with the primary.

---

## ✅ Accelerated Database Recovery (ADR)

* **Always on, cannot be disabled.**
* Enables **instantaneous rollback** of **long-running transactions**.
* Uses **Persisted Version Store (PVS)** to isolate changes outside the main database pages.
* Helps Azure quickly recover databases during:

  * Failovers
  * Transaction aborts
  * Database restarts

> ADR **minimizes downtime** and significantly boosts **availability** of mission-critical applications.

---

## ✅ Fault Tolerance and Maintenance Behavior

* **Transparent Maintenance Events:**

  * Azure handles OS patches, hardware replacements, and upgrades.
  * **Failover is transparent** to end users — only uncommitted transactions are lost.
* **SQL DB/MI Limitations:**

  * `OFFLINE` and `EMERGENCY` modes are **not supported** (Azure controls state transitions).
  * `RESTRICTED_USER` and **Dedicated Admin Connection (DAC)** are supported.

> These restrictions protect the managed nature of the service while still offering diagnostic access.

---

## ✅ Database Integrity and Consistency

Azure ensures **data durability and integrity** through the following mechanisms:

* **Automatic Page Repair:**

  * Detects corrupted pages via **CHECKSUM** (enabled by default).
  * Automatically **repairs pages** using redundant copies.
  * If the repair is successful and has no user impact, it occurs silently.
  * Users are **notified proactively** only when necessary.

* **Backups and Integrity Checks:**

  * Frequent **full, differential, and transaction log backups**.
  * **Restore validations** run periodically.
  * **Lost write and stale read detection** built-in.

* **CHECKDB Command:**

  * You can run `DBCC CHECKDB`, but **repair options are not available**.
  * Ensures logical consistency within the data files.

---

## 🧠 Summary Table

| **Capability**                   | **Azure SQL DB** | **Managed Instance** | **Details**                                                |
| -------------------------------- | ---------------- | -------------------- | ---------------------------------------------------------- |
| SLA (99.99%)                     | ✅                | ✅                    | Built-in failover with automated node recovery             |
| ADR (Accelerated DB Recovery)    | ✅                | ✅                    | Enables near-instant rollback and faster database recovery |
| Auto-Failover Groups             | ✅                | ✅                    | Automatic region failover for high availability            |
| Active Geo-Replication           | ✅                | ❌                    | Manually failover to secondary regions (up to 4 replicas)  |
| Read Replicas                    | ✅                | ✅                    | For performance, not full DR unless combined with failover |
| DBCC CHECKDB (no repair)         | ✅                | ✅                    | Logical consistency check, no manual repairs               |
| CHECKSUM + Page Repair           | ✅                | ✅                    | Detect and auto-fix data page corruptions                  |
| OFFLINE/EMERGENCY Modes          | ❌                | ❌                    | Unsupported in PaaS                                        |
| Dedicated Admin Connection (DAC) | ✅                | ✅                    | Diagnostic access to recover from issues                   |

---

## 📝 Practice Questions (AZ-305 Level)

---

### **Q1.** What feature enables **automatic region-level failover** for both Azure SQL Database and SQL Managed Instance?

A. Availability Zones
B. Active Geo-Replication
C. Auto-Failover Groups
D. Azure Site Recovery

> **✅ Answer:** C. Auto-Failover Groups
> *Explanation:* Auto-Failover Groups offer built-in replication and automatic failover across paired Azure regions.

---

### **Q2.** During a node failure in Azure SQL Database, what happens to committed transactions?

A. They are lost
B. They are retried later
C. They are preserved due to synchronous storage write
D. They are logged and require manual re-entry

> **✅ Answer:** C. They are preserved due to synchronous storage write
> *Explanation:* All committed transactions are saved to Azure storage and are preserved during failover.

---

### **Q3.** Which of the following is **not supported** in Azure SQL Database?

A. RESTRICTED\_USER
B. EMERGENCY mode
C. DAC (Dedicated Admin Connection)
D. CHECKSUM

> **✅ Answer:** B. EMERGENCY mode
> *Explanation:* Azure manages database state transitions, so EMERGENCY mode is not available in PaaS.

---

### **Q4.** What is the main benefit of **Accelerated Database Recovery (ADR)**?

A. Full backup automation
B. Fast failover across zones
C. Instant rollback of long transactions
D. Automated database sharding

> **✅ Answer:** C. Instant rollback of long transactions
> *Explanation:* ADR uses persisted version store (PVS) to enable immediate transaction rollback and faster recovery.

---

### **Q5.** Why is it important to implement **retry logic** in applications using Azure SQL Database?

A. Azure requires custom error handling
B. To reconnect after intentional service reboots
C. To handle transient connection losses during failover
D. Because read replicas require polling

> **✅ Answer:** C. To handle transient connection losses during failover
> *Explanation:* During failover, connections are dropped, and retry logic ensures application resilience.

