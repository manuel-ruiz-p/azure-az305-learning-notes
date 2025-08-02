
# 📦 Design for Azure Blob Backup and Recovery (Enhanced for AZ-305)

## 📘 Overview

Azure Blob Storage is a cost-effective, massively scalable object storage solution. For backup and recovery of data stored in Azure blobs, Microsoft offers **operational backup**, **soft delete**, **versioning**, **point-in-time restore**, and **resource locks** — all designed to protect against **accidental deletion**, **data corruption**, and **unauthorized changes**, without moving data to a separate vault.

> **Key design principle**: Azure Blob Backup is operational and integrated — backup data stays **within the same storage account**, making it ideal for **high-frequency, low-latency recovery** scenarios.

---

## 🛠️ Core Features & Use Cases

### 🔁 1. Soft Delete (for Blobs & Containers)

* **Purpose**: Protects against **accidental or malicious deletions**.
* **Behavior**: Retains deleted blobs, snapshots, versions, or containers for a **configurable retention period (1–365 days)**.
* **Scope**:

  * **Blob soft delete** → Recovers a single blob or snapshot.
  * **Container soft delete** → Recovers an entire container and its contents.

**Use Case**: Recovering from accidental file deletions during development or manual admin operations.

> ⚠️ **Note**: Soft delete does **not** protect against deletion of the entire storage account.

---

### 🧬 2. Blob Versioning

* **Purpose**: Automatically retains previous versions of a blob.
* **Benefit**: Enables rollback to earlier versions in case of overwrites or incorrect updates.
* **Scenario**: When **multiple contributors** are modifying files, you can maintain a full history of changes.

**Use Case**: Restoring a legal document to its previous approved version after an incorrect update.

---

### 🕒 3. Point-in-Time Restore (PITR)

* **Purpose**: Allows granular restore of **block blobs** to a previous state across a container.
* **Functionality**:

  * Reverts write and delete operations made during a specified **retention period**.
  * Requires setting up a **management policy** on the storage account.

**Use Case**: Rolling back a data set to a known stable state after a corrupted batch update in a production app.

---

### 🔐 4. Resource Locks

* **Purpose**: Prevent accidental or unauthorized deletion or changes to blob storage resources.
* **Types**:

  * `CanNotDelete`: Resource can be read and modified but not deleted.
  * `ReadOnly`: Resource is accessible for read operations only.

**Use Case**: Preventing a mission-critical storage account from being accidentally deleted during infrastructure automation.

---

## ⚙️ Design Considerations

| Design Factor           | Best Practice                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Retention Planning**  | Choose a **retention window (1–365 days)** based on your organization’s RPO (Recovery Point Objective).                              |
| **Policy Automation**   | Automate PITR and versioning settings through ARM templates or Bicep for consistency across environments.                            |
| **Security & RBAC**     | Apply **resource locks** and configure **Azure RBAC roles** (e.g., Storage Blob Data Reader/Contributor) for least privilege access. |
| **Cost Implications**   | Soft delete, versioning, and PITR can **increase storage usage**; monitor and manage costs using Azure Cost Management.              |
| **Dev/Test Resilience** | Use PITR to revert stateful tests or data corruption quickly without requiring full backups or external vaults.                      |

---

## ✅ Summary: Key Design Takeaways

* Blob backup is **native, operational**, and **storage account-local**.
* **No additional infrastructure or agents required**.
* Enables rapid and granular recovery using **versioning**, **soft delete**, and **point-in-time** features.
* Resource locks ensure **non-technical or accidental changes** don't compromise storage availability or integrity.

---

## 📝 Exam Practice Questions (AZ-305 Level)

### **Q1.** You are designing a backup solution for a legal firm that stores critical documents in Azure Blob Storage. Each file is frequently updated by multiple authors. Which feature should you enable to track and restore previous versions?

A. Soft Delete
B. Point-in-Time Restore
C. Blob Versioning
D. Snapshots

> ✅ **Correct Answer:** C. Blob Versioning
> **Explanation**: Blob Versioning maintains previous versions and supports collaborative editing scenarios.

---

### **Q2.** You are designing a test environment where datasets need to be restored to a consistent state before each test run. Which Azure Blob feature supports this use case?

A. Blob Soft Delete
B. Resource Lock
C. Geo-Redundant Storage
D. Point-in-Time Restore

> ✅ **Correct Answer:** D. Point-in-Time Restore
> **Explanation**: PITR allows you to restore block blobs to a consistent prior state, ideal for test resets.

---

### **Q3.** A team accidentally deleted several blob containers in a storage account. Which feature would have allowed you to recover those containers?

A. Container-level Soft Delete
B. Point-in-Time Restore
C. Blob Versioning
D. Storage Account Lock

> ✅ **Correct Answer:** A. Container-level Soft Delete
> **Explanation**: Only container soft delete can recover deleted containers (not just blobs).

---

### **Q4.** You want to prevent accidental deletion of a production storage account. Which solution should you implement?

A. Blob Versioning
B. ReadOnly Lock
C. CanNotDelete Lock
D. Soft Delete

> ✅ **Correct Answer:** C. CanNotDelete Lock
> **Explanation**: CanNotDelete locks allow modification but block deletion unless the lock is first removed.

---

### **Q5.** Which statement is TRUE regarding Azure Blob operational backup?

A. It stores backups in an Azure Recovery Services vault.
B. It requires scheduling of backup jobs via Azure Automation.
C. It is a continuous backup stored in the same source storage account.
D. It only applies to premium storage accounts.

> ✅ **Correct Answer:** C. It is a continuous backup stored in the same source storage account.
> **Explanation**: Azure Blob operational backup stores backups within the same storage account and works continuously.

