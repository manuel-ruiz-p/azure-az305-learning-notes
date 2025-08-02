
# Design for Azure Monitor Data Sources — Enhanced Overview

**Azure Monitor** is a comprehensive monitoring platform that helps you collect, analyze, and act on telemetry data from your applications, infrastructure, and services. It enables observability across your entire Azure and on-premises environments.

Azure Monitor supports two **primary components**:

* **Logs**: Used for complex queries, analysis, and diagnostic data.
* **Metrics**: Lightweight numerical data for near-real-time monitoring.

---

## 🔍 Key Components

| Component   | Description                                                                                                                                        |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Logs**    | Stores structured and unstructured data that can be queried with Kusto Query Language (KQL). Useful for deep analysis, diagnostics, and reporting. |
| **Metrics** | Numeric values collected at regular intervals. Optimized for near-real-time monitoring and alerting on performance issues.                         |

---

## 📦 Common Monitoring Data Sources

Azure Monitor collects data from **multiple layers** of your application and infrastructure:

### 🔼 Tiers of Monitoring Data

| Tier                    | Examples                                | Description                                                |
| ----------------------- | --------------------------------------- | ---------------------------------------------------------- |
| Application Tier        | App Insights, Custom Events, Exceptions | Highest-level insights into code performance and behavior  |
| Operating System Tier   | Performance Counters, Syslog, IIS Logs  | Metrics and logs from OS-level components                  |
| Azure Resource Tier     | Azure Diagnostics, Activity Logs        | Platform logs about resource operations and configurations |
| Azure Subscription Tier | Azure Resource Health, Alerts, Policy   | Subscription-wide events, compliance, and state            |

---

## 🛠️ Key Features to Consider

### 1. **Unified Data Platform**

* Combine logs and metrics from multiple resources.
* Analyze and correlate events across services.

### 2. **Log Queries**

* Use **KQL** to write complex queries for troubleshooting, diagnostics, and reporting.
* Store queries for reuse in workbooks or dashboards.

### 3. **Near-Real-Time Metrics**

* Supports performance thresholds, alerts, and anomaly detection.
* Use **Metrics Explorer** to visualize trends interactively.

### 4. **Data Destinations**

* Export monitoring data to:

  * **Log Analytics Workspace**
  * **Event Hubs** (for SIEM integration)
  * **Storage Accounts** (for long-term retention)

### 5. **Alerts**

* Create alert rules on both logs and metrics.
* Integrate alerts with:

  * **Azure Monitor Action Groups**
  * **ITSM tools** or **Logic Apps**

---

## 🧠 Monitoring Data Types to Configure

| Data Type                | Source            | Description                    |
| ------------------------ | ----------------- | ------------------------------ |
| **Windows Events**       | Windows Event Log | Security, system, and app logs |
| **Performance Counters** | Windows OS        | CPU, memory, disk usage, etc.  |
| **Syslog**               | Linux Systems     | Kernel and daemon logs         |
| **Text Logs**            | Apps              | Custom local disk logging      |
| **JSON Logs**            | Apps              | Structured data logs           |
| **IIS Logs**             | Web Servers       | HTTP request and error logging |

---

## 🧭 Best Practices for Implementation

* Define **what resources** you need to monitor (VMs, apps, databases).
* Use **Log Analytics Workspaces** to store and query logs.
* Use **Metrics Explorer** for real-time metric visualization.
* **Create alerts** based on thresholds or specific log patterns.
* Segment **access and visibility** based on environment (e.g., Dev, Test, Prod).
* Use **Diagnostic Settings** to route platform metrics and logs to different destinations.

---

## ✅ AZ-305 Style Practice Questions (Markdown)

```markdown
### Q1:  
**Which Azure Monitor feature should you use to perform deep analysis on large volumes of structured and unstructured telemetry data using Kusto Query Language (KQL)?**

- A) Azure Monitor Metrics  
- B) Azure Activity Log  
- C) Azure Monitor Logs  
- D) Azure Application Insights  

**Answer:** C) Azure Monitor Logs

---

### Q2:  
**Which tool in Azure Monitor allows you to interactively explore metric trends and investigate performance anomalies?**

- A) Log Analytics  
- B) Azure Dashboards  
- C) Metrics Explorer  
- D) Alerts Manager  

**Answer:** C) Metrics Explorer

---

### Q3:  
**What is the correct hierarchy of monitoring data tiers from top to bottom in Azure Monitor?**

- A) OS tier → App tier → Azure Resource tier  
- B) App tier → OS tier → Azure platform tier  
- C) Azure platform tier → App tier → OS tier  
- D) OS tier → Azure Resource tier → App tier  

**Answer:** B) App tier → OS tier → Azure platform tier

---

### Q4:  
**Which type of monitoring data is best suited for alerting on performance thresholds in near-real-time?**

- A) Azure Monitor Logs  
- B) Diagnostic Logs  
- C) Azure Monitor Metrics  
- D) Application Insights Traces  

**Answer:** C) Azure Monitor Metrics

---

### Q5:  
**You need to collect custom application logs in JSON format from local disk for analysis in Azure Monitor. Which method should you use?**

- A) Performance Counters  
- B) Syslog  
- C) JSON Log Configuration  
- D) IIS Diagnostics  

**Answer:** C) JSON Log Configuration
```
