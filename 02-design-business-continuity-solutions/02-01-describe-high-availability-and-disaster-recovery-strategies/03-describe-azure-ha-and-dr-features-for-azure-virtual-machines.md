
# Describe Azure High Availability and Disaster Recovery Features for Azure Virtual Machines

---

## 🔹 Key Azure Availability Options for VMs

Azure provides **three primary options** for enhancing availability in IaaS deployments:

1. **Availability Sets**
2. **Availability Zones**
3. **Azure Site Recovery**

All three options operate **outside the VM** and do **not interact with the internal workload** (OS, database engine, etc.).

---

## 1. ✅ Availability Sets

### ➤ Purpose:

Protect against **hardware failures** and **planned maintenance** within a single data center.

### ➤ Key Concepts:

* **Fault Domains (FDs):** Protect against hardware failures (e.g., power, network).
* **Update Domains (UDs):** Ensure not all VMs are rebooted simultaneously during Azure updates.

### ➤ Benefits:

* VMs in an availability set are distributed across multiple FDs and UDs.
* Ensures at least one VM remains available during maintenance or failures.

### ➤ Limitation:

* Only valid **within a single data center**.
* Doesn't protect against **OS-level failures** or **SQL Server crashes**.
* Can't be combined with Availability Zones.

### ➤ Best Practice:

* Use **separate availability sets per application tier** (e.g., web, database, AD DS).

---

## 2. ✅ Availability Zones

### ➤ Purpose:

Protect against **data center-level failures** within an Azure region.

### ➤ Structure:

* Each **zone** corresponds to a **separate data center**.
* Zones are logically numbered (**Zone 1, 2, 3**) and **physically isolated**.

### ➤ Benefits:

* Resilient to **entire data center outages**.
* Low latency between zones allows for **synchronous replication**.

### ➤ Notes:

* Zone numbering is **subscription-specific**; same zone number ≠ same physical data center.
* Introduces **minor latency**; ensure round-trip latency <1ms for synchronous operations (e.g., AGs).

---

## 3. ✅ Azure Site Recovery (ASR)

### ➤ Purpose:

Provide **disaster recovery** by replicating VMs across Azure regions.

### ➤ Key Points:

* Replicates VM state, including disk and configuration.
* **RTO:** Target is 2 hours monthly.
* **RPO:** May not meet aggressive RPO requirements due to lack of SQL Server transaction awareness.

### ➤ Use Case:

* Best suited when **VM-level recovery** is acceptable.
* Not ideal for **SQL Server data consistency**, unless used alongside native SQL Server HADR.

---

## 🧠 Summary Table

| Feature             | Scope              | Protects From          | Aware of SQL Server? | Best For                       |
| ------------------- | ------------------ | ---------------------- | -------------------- | ------------------------------ |
| Availability Sets   | Single Data Center | Hardware & maintenance | ❌                    | Basic HA within region         |
| Availability Zones  | Region-wide        | Data center outages    | ❌                    | HA across physical zones       |
| Azure Site Recovery | Cross-region       | Regional disaster      | ❌                    | DR replication between regions |

---

## 📝 5 Practice Questions (AZ-305 Style)

### **Q1.** Which Azure feature distributes VMs across fault and update domains within the same data center?

- A. Availability Zones
- B. Azure Load Balancer
- C. Availability Sets
- D. Azure Site Recovery

> **Answer:** ✅ C. Availability Sets

---

### **Q2.** What is the main limitation of using Availability Zones?

- A. They only support single-tier applications.
- B. They require shared storage.
- C. They can introduce slight latency.
- D. They are only available in one region.

> **Answer:** ✅ C. They can introduce slight latency.

---

### **Q3.** What is the purpose of Fault Domains in Azure?

- A. To prevent VM updates from occurring simultaneously
- B. To separate VMs across power and network infrastructure
- C. To replicate data between zones
- D. To monitor SQL Server transactions

> **Answer:** ✅ B. To separate VMs across power and network infrastructure

---

### **Q4.** Which statement is TRUE about Azure Site Recovery?

- A. It provides database-level failover for SQL Server.
- B. It replicates workloads between fault domains.
- C. It ensures transaction consistency for SQL Server.
- D. It replicates VMs to another Azure region.

> **Answer:** ✅ D. It replicates VMs to another Azure region.

---

### **Q5.** You are designing a multi-tier app with VMs in Azure. What is the best practice for HA using Availability Sets?

- A. Use a single availability set for all VMs.
- B. Group all VMs in Zone 1 for better performance.
- C. Create separate availability sets per tier.
- D. Combine Availability Sets with Availability Zones.

> **Answer:** ✅ C. Create separate availability sets per tier.

---
