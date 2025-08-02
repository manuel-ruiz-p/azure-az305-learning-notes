

# 📘 Design for Azure Workbooks and Azure Insights

## ✅ Overview

**Azure Workbooks** are a component of **Azure Monitor** that enable data visualization and analysis across multiple sources. Combined with **Azure Insights**, which offer targeted monitoring experiences, Workbooks provide a powerful tool for centralized diagnostics, performance monitoring, and operational decision-making.

---

## 🧠 Key Concepts

### 📊 Azure Workbooks

* **Interactive Dashboards**: Workbooks are flexible canvases in the Azure Portal for data visualization, exploration, and diagnostics.
* **Multi-source Data**: Can combine data from Logs, Metrics, Azure Resource Graph, Alerts, Resource Health, and more.
* **Custom Visuals**: Grid views, charts, conditional formatting, and parameterized reports.
* **Authoring Power**: Authors can ingest, transform, and model data for insight into performance, health, availability, and usage.

### 🧩 Data Sources Supported

* Logs
* Metrics
* Azure Resource Graph
* Alerts
* Workload Health
* Azure Resource Health
* Azure Data Explorer

---

### 💡 Azure Insights

**Azure Insights** are pre-configured monitoring experiences focused on specific resources:

| Insight Type            | Description                                                         |
| ----------------------- | ------------------------------------------------------------------- |
| Application Insights    | Tracks performance, usage, and exceptions in web apps.              |
| Container Insights      | Monitors container workloads in AKS or ACI.                         |
| Network Insights        | Tracks network health and dependencies.                             |
| VM Insights             | Tracks OS performance, dependencies, and workloads on VMs.          |
| Resource Group Insights | Provides contextual monitoring across all resources in a group.     |
| Azure Cache for Redis   | Reports latency, failures, capacity, and health of Redis instances. |
| Cosmos DB Insights      | Offers performance and operational metrics for Cosmos DB.           |
| Key Vault Insights      | Monitors access performance and failures.                           |
| Azure Storage Insights  | Unified view of storage metrics and performance.                    |

---

## 🧭 Best Practices

* Use **Workbooks** for:

  * Building **operational playbooks**
  * Performing **root cause analysis**
  * Unifying telemetry across services
  * Creating **team-specific dashboards**
* Use **Insights** for:

  * A **focused view** into the health and performance of particular services
  * Enabling **predefined metrics and alerting**
  * Identifying performance degradation early

---

## 🔧 Design Considerations

| Area                      | Recommendation                                                       |
| ------------------------- | -------------------------------------------------------------------- |
| **Multi-Resource Views**  | Use Workbooks to visualize data across VMs, networks, and databases. |
| **Operational Playbooks** | Embed step-by-step diagnostic processes.                             |
| **Insights Integration**  | Leverage out-of-the-box dashboards for Cosmos DB, Redis, etc.        |
| **Access Control**        | Use Azure RBAC to control workbook visibility and access.            |


## 📌 Summary

* **Use Workbooks** for custom dashboards, operational playbooks, and diagnostics.
* **Use Azure Insights** for out-of-the-box monitoring tailored to specific Azure services.
* Combine both for a comprehensive and scalable monitoring solution across environments.

---

## 🧪 Exam-Level Questions

### ❓ Question 1

You need to analyze high CPU usage across multiple virtual machines in different resource groups. What should you use?

- A. Azure Metrics Explorer
- B. Azure Workbook
- C. Azure Resource Graph
- D. Azure Cost Management

**✅ Answer:** B
**Explanation:** Azure Workbooks allow cross-resource and cross-subscription analysis using logs and metrics, ideal for aggregating performance data like CPU usage.

---

### ❓ Question 2

Which Azure Monitor feature provides targeted monitoring and troubleshooting for Azure Key Vault?

- A. Application Insights
- B. Key Vault Insights
- C. Azure Policy
- D. Azure Workbook

**✅ Answer:** B
**Explanation:** Key Vault Insights is designed specifically to track the performance, availability, and failures of Azure Key Vault.

---

### ❓ Question 3

What data sources can **Azure Workbooks** natively connect to? *(Select two)*

- A. Azure Arc
- B. Azure Resource Graph
- C. Azure RBAC
- D. Azure Data Explorer

**✅ Answers:** B, D
**Explanation:** Azure Workbooks support Azure Resource Graph and Azure Data Explorer as data sources.

---

### ❓ Question 4

Tailwind Traders wants to allow different teams to create visual dashboards using logs and metrics from their services. Which solution is most appropriate?

- A. Azure Advisor
- B. Azure Workbook
- C. Azure Monitor Alerts
- D. Azure Sentinel

**✅ Answer:** B
**Explanation:** Azure Workbooks allow the creation of interactive dashboards using metrics, logs, and other sources.

---

### ❓ Question 5

Which capability makes Azure Workbooks suitable for a **composite resource view**?

- A. Support for ARM Templates
- B. Support for Azure Lighthouse
- C. Ability to join data across resources
- D. Centralized user authentication

**✅ Answer:** C
**Explanation:** Azure Workbooks support joining and combining data from multiple resources, enabling composite views.
