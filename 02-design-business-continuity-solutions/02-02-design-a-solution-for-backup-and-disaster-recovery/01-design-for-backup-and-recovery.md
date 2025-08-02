
# Design for Backup and Recovery – AZ-305 Study Guide

## Overview

To ensure business continuity, mission-critical applications must be resilient and recoverable in the event of failure. While traditional on-premises infrastructure builds resiliency through hardware redundancy, cloud and hybrid applications require **strategic backup and recovery planning** to meet availability and recovery requirements.

This guide helps you understand how to define resiliency goals such as **SLAs**, **RTOs**, and **RPOs**, and how to choose appropriate backup and recovery technologies in Azure.

---

## 🔧 Key Concepts

### ✅ Resilient Applications

Resilient apps can:

* Handle **component failures** gracefully.
* Recover from **unexpected incidents** without significant downtime.
* Continue to function under **stress or disaster** scenarios.

---

## 📌 Define Your Backup and Recovery Requirements

### 1. **Identify Workloads and Their Usage**

* A **workload** is a logically separated unit (like a web app, database, or batch job).
* Each workload may have unique needs for:

  * Availability
  * Scalability
  * Data consistency
  * Disaster recovery

---

### 2. **Understand Usage Patterns**

* Identify critical and noncritical usage periods.
* **Critical workloads** might need **geo-redundancy** or **multi-region failover**.
* **Noncritical workloads** can optimize for cost (e.g., single-region deployment during off-peak hours).

---

### 3. **Availability Metrics**

| Metric                                | Description                                   |
| ------------------------------------- | --------------------------------------------- |
| **MTBF** (Mean Time Between Failures) | Average expected time between failures        |
| **MTTR** (Mean Time To Recovery)      | Average time to restore service after failure |

* Use these to evaluate infrastructure durability and design redundancy.

---

### 4. **Recovery Metrics**

| Metric                             | Description                                            |
| ---------------------------------- | ------------------------------------------------------ |
| **RTO** (Recovery Time Objective)  | Max time an app can be down after an incident          |
| **RPO** (Recovery Point Objective) | Max acceptable data loss in terms of time              |
| **RLO** (Recovery Level Objective) | Granularity of recovery (e.g., full system, app, file) |

* Run **risk assessments** to identify tolerances and business impact.

---

### 5. **Define Workload Availability Targets**

* Specify **target SLAs** per workload.
* Match availability targets with appropriate services and redundancy.
* Consider cost/complexity trade-offs when building high availability.

---

### 6. **Service-Level Agreements (SLAs)**

* Azure services provide defined **SLAs** (e.g., 99.9% uptime).
* Align your architecture to ensure no **single point of failure** undermines your workload SLA.

  > 🔍 Example: A workload with a 99.99% uptime target cannot rely on a service that offers only 99.9% SLA unless redundancy is added.

---

## ⚠️ Tip

> If **MTTR** for any critical component exceeds your **RTO**, your system **cannot recover within acceptable time**, potentially causing **business disruption**.

---

## ✅ After Requirements Are Defined

Select the appropriate **Azure backup, replication, and disaster recovery tools**:

* **Azure Backup**: For VM, SQL Server, file share backups.
* **Azure Site Recovery (ASR)**: For orchestrated DR of VMs and physical servers.
* **Geo-redundant storage (GRS)**: For cross-region data durability.
* **Snapshots & Vaults**: For granular or historical recovery.

---

## 📘 Summary Table

| Requirement                | Strategy in Azure                            |
| -------------------------- | -------------------------------------------- |
| Backup Granularity         | Use Recovery Services Vault, snapshots       |
| Long-term Retention        | Azure Backup with custom policies            |
| Multi-region Availability  | Azure Site Recovery + zone redundancy        |
| SLA Fulfillment            | Choose services with matching or higher SLAs |
| Data Consistency/Integrity | Use consistent snapshot or backup methods    |

---

## 📝 Practice Questions (Exam Style)

### **Question 1**

What does the **Recovery Level Objective (RLO)** define?

- **A.** The time needed to restore a backup
- **B.** The acceptable duration of data loss
- **C.** The component or scope that must be recovered
- **D.** The expected uptime percentage

✅ **Answer:** C
*RLO defines the **granularity of recovery**—e.g., server, app, or file.*

---

### **Question 2**

Which metric helps determine **how long a component will last before failing**?

- **A.** MTTR
- **B.** RPO
- **C.** MTBF
- **D.** SLA

✅ **Answer:** C
*MTBF (Mean Time Between Failures) helps predict system durability.*

---

### **Question 3**

Your application has a 99.99% uptime SLA, but one of its dependencies only guarantees 99.9%. What is the recommended action?

- **A.** Ignore it as the difference is small
- **B.** Accept the lower SLA
- **C.** Add redundancy for that service to eliminate the single point of failure
- **D.** Replace the dependency with a custom-built solution

✅ **Answer:** C
*You must eliminate single points of failure to meet strict SLA requirements.*

---

### **Question 4**

What should you do if a system's MTTR exceeds its RTO?

- **A.** Upgrade to premium storage
- **B.** Accept the business risk
- **C.** Re-architect to reduce MTTR or increase redundancy
- **D.** Increase the RPO value

✅ **Answer:** C
*You must ensure the system can recover **within the defined RTO**.*

---

### **Question 5**

Which of the following is **not typically part of defining a resiliency plan**?

- **A.** RTO/RPO requirements
- **B.** MTBF/MTTR measurements
- **C.** Selecting a database engine
- **D.** Business impact analysis

✅ **Answer:** C
*Selecting a database engine is a design detail, not part of defining resiliency goals.*

