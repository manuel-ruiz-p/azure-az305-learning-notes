
# 📘 AZ-305 Study Guide: Design for Azure Monitor Logs (Log Analytics) Workspaces


## 🧠 Key Concepts

### 🔷 What is an Azure Monitor Logs (Log Analytics) Workspace?

An **Azure Monitor Logs workspace** is:

* A **resource container** used to collect and store monitoring log data.
* A **centralized location** to analyze log data with Kusto Query Language (KQL).
* Configurable for **pricing**, **data retention**, and **regional compliance**.
* Integrated with **Azure RBAC** for fine-grained access control.

---

## 🌐 Characteristics

* **Tables**: Log data is stored in structured tables specific to the resource type (e.g., `Heartbeat`, `Perf`, `AzureActivity`).
* **RBAC**: Access can be scoped to a **workspace**, **resource**, or **resource group**.
* **Deployment**: Workspaces are typically deployed using one of three models:

  * **Centralized (Hub-and-Spoke)**: Easier cross-resource correlation.
  * **Decentralized**: Greater isolation and security.
  * **Hybrid**: Mix of both; more complex and costly.
* **Access Contexts**:

  * **Workspace-context**: Access to all logs in a workspace.
  * **Resource-context**: Scoped access to logs from specific Azure resources.
* **Scalability**: Unlimited ingestion and storage; split workspaces only for organizational or access-control reasons—not scale.

---

## 🛠️ Design Considerations

### ✅ Access Control

* Use **Azure RBAC** to provide **least privilege access**.
* Combine **workspace-context** and **resource-context** access for flexibility.
* Enable **granular control** via resource-based scoping in centralized models.

### ✅ Deployment Model Selection

| Model         | Description                                                                |
| ------------- | -------------------------------------------------------------------------- |
| Centralized   | All logs in one workspace, easier correlation, more complex RBAC.          |
| Decentralized | Logs segmented by team/resource group, better isolation, less correlation. |
| Hybrid        | Combines both, but adds complexity and potential audit gaps.               |

### ✅ Compliance & Performance

* Place workspaces in regions aligned with **compliance or data sovereignty**.
* Avoid **egress charges** by placing workspace in same region as resources.
* For ingestion > **500 GB/day**, use **dedicated clusters**.

### ✅ Policy Enforcement

* Use **Azure Policy** to require VM diagnostics and resource logs to be sent to a designated workspace.
* Evaluate and **remediate non-compliance** using built-in or custom policies.

---

## 📝 Exam Tips

* Know when to **use one workspace vs multiple** (based on compliance, cost, and visibility).
* Understand how **RBAC scoping** impacts access to log data.
* Be able to **justify** a deployment model for different organizational needs.
* Be ready to **design policies** to ensure log data is forwarded correctly.
* Understand how to use **resource-context** logs to enforce least privilege access.

---

## 🧪 Practice Questions

### **Q1.** You are designing a monitoring solution for a multinational organization with data residency requirements. What is the BEST workspace deployment model?

- A. Centralized workspace in a single region
- B. Decentralized workspaces per region
- C. Hybrid model with cross-region central workspace
- D. A dedicated cluster with policy-based access

✅ **Answer:** B

> Decentralized workspaces per region ensure data sovereignty compliance.

---

### **Q2.** You want to give your developers access to logs from a specific app service without giving access to the full workspace. Which access model should you use?

- A. Workspace-context access
- B. Shared workspace with reader role
- C. Resource-context access
- D. Contributor role on workspace

✅ **Answer:** C

> Resource-context allows scoped access to specific resources.

---

### **Q3.** Which of the following is NOT a valid reason to split workspaces?

- A. To meet data sovereignty requirements
- B. To reduce ingestion latency
- C. To isolate logs by department
- D. To enforce resource-specific RBAC

✅ **Answer:** B

> Workspaces scale automatically. Latency is not a reason to split workspaces.

---

### **Q4.** Your organization ingests 700 GB/day of log data into Azure Monitor. What should you do?

- A. Use centralized workspace in default shared cluster
- B. Use multiple decentralized workspaces
- C. Configure a dedicated cluster for the workspace
- D. Reduce log data volume using diagnostic settings

✅ **Answer:** C

> Dedicated clusters are recommended when ingestion exceeds 500 GB/day.

---

### **Q5.** What is a downside of the hybrid workspace deployment model?

- A. Difficult to scale storage
- B. Complex RBAC setup and compliance auditing
- C. No ability to cross-correlate logs
- D. Inability to store logs in different geographies

✅ **Answer:** B

> Hybrid models increase complexity, cost, and may hinder compliance.

