
# 📂 Design for Azure Files Backup and Recovery (Enhanced for AZ-305)

## 📘 Overview

Azure Files is a fully managed cloud file share service that supports **SMB and NFS protocols**. For backup and recovery, Azure Files offers **share snapshots** and **Azure Backup integration** — enabling **point-in-time restore**, **instant file-level recovery**, and **centralized policy-based management**.

> ⚠️ Snapshots are NOT full backups. For long-term, policy-driven backup and BCDR (Business Continuity and Disaster Recovery), use **Azure Backup with Recovery Services Vault**.

---

## 🛠️ Key Backup Mechanisms

### 📸 1. Share Snapshots (Native)

* **Description**: A **read-only, point-in-time copy** of a file share.
* **Scope**: Applies to the **entire file share** (all files and folders).
* **Granularity**: Allows **individual file recovery** from the snapshot.
* **Characteristics**:

  * Incremental (stores only changes).
  * Created via portal, CLI, PowerShell, REST API.
  * Cannot be modified.
  * Cannot delete a file share with existing snapshots.

**Use Case**: Quick rollback after accidental file deletion or corruption in a shared drive.

---

### 🔁 2. Azure Backup Integration

* **Architecture**: Azure Backup **does not move data** to the Recovery Services Vault — it stores **only metadata** and manages snapshots internally.
* **Advantages**:

  * Centralized backup management.
  * Policy-based automation (daily, weekly, monthly, yearly retention).
  * Built-in **soft delete**, alerts, monitoring, and reporting.
  * Fast restores using snapshot pointers — no data transfer needed.

**Use Case**: Enterprise-grade protection with compliance, audit reporting, and automation needs.

---

## 🎛️ Backup Configuration Considerations

| Consideration                | Description                                                                                                |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Instant Restore**          | Restore specific files/folders instantly from snapshot without restoring the full share.                   |
| **Soft Delete Enabled**      | Automatically enabled when Azure Backup is turned on. Protects from accidental deletions.                  |
| **Self-Service Recovery**    | End-users (e.g., developers) can recover files via Windows VSS and server endpoint integration.            |
| **Backup Scheduling**        | Supports **once-per-day policy** only. For mission-critical shares, supplement with **on-demand backups**. |
| **Retention Granularity**    | Supports daily, weekly, monthly, yearly snapshot retention through backup policies.                        |
| **Organizational Strategy**  | Separate file shares by function (e.g., public vs. internal) to align backup frequency and restore goals.  |
| **Pre-deployment Snapshots** | Take a snapshot manually before deploying application changes to allow rollback if issues occur.           |

---

## ✅ Design Takeaways

* Azure Files snapshots are **fast, storage-native**, and **incremental**.
* Azure Backup extends snapshot capabilities with **policy automation**, **monitoring**, and **alerts**.
* For BCDR, combine **file organization**, **policy scheduling**, and **manual snapshots** before deployments.
* **Soft delete**, **instant restore**, and **self-service restore** enhance resilience and reduce support overhead.

---

## 📝 AZ-305 Practice Questions

---

### **Q1.** You need to protect an Azure File Share used for internal finance reports. The solution must allow daily backup, centralized monitoring, and soft delete. Which service should you use?

- A. Azure Site Recovery
- B. Azure Files Share Snapshots (manual)
- C. Azure Backup with Recovery Services Vault
- D. Azure Blob Backup

> ✅ **Correct Answer:** C. Azure Backup with Recovery Services Vault
> **Explanation**: Azure Backup enables automated daily backups, soft delete, monitoring, and centralized control via vault.

---

### **Q2.** A developer accidentally deletes a critical file in an Azure File Share. You need to restore **only that file** immediately with minimal effort. What feature should you use?

- A. Full share restore from vault
- B. Soft Delete
- C. Snapshot-based individual file restore
- D. Azure Site Recovery failover

> ✅ **Correct Answer:** C. Snapshot-based individual file restore
> **Explanation**: Snapshots allow file-level recovery without restoring the full share.

---

### **Q3.** Your policy allows backup only once per day. However, your application generates mission-critical reports throughout the day. What should you do?

- A. Use Azure File Sync to replicate data
- B. Enable Azure Site Recovery
- C. Implement on-demand snapshots via Azure CLI
- D. Increase the policy to backup every hour

> ✅ **Correct Answer:** C. Implement on-demand snapshots via Azure CLI
> **Explanation**: Azure Backup policies allow only daily backup. For frequent backup needs, take snapshots manually or via script.

---

### **Q4.** You plan to delete a file share but are blocked by an error. Which of the following is the MOST likely cause?

- A. The file share is in use
- B. The file share has soft delete enabled
- C. The file share is locked via RBAC
- D. The file share has existing snapshots

> ✅ **Correct Answer:** D. The file share has existing snapshots
> **Explanation**: You must delete all snapshots before deleting the share.

---

### **Q5.** What is stored in the Recovery Services vault when backing up Azure File Shares?

- A. Full data backup copies
- B. Binary replicas of file data
- C. Metadata about snapshots
- D. Azure Resource Manager templates

> ✅ **Correct Answer:** C. Metadata about snapshots
> **Explanation**: Azure Backup stores only metadata in the vault. Actual file data remains in the source share.

