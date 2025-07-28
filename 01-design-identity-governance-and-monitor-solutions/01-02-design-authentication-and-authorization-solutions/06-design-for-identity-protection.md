
# 🌐 Design for Identity Protection (Enhanced for AZ-305)

---

## 🎯 Key Capabilities of Microsoft Entra Identity Protection

| Capability                    | Description                                                                                |
| ----------------------------- | ------------------------------------------------------------------------------------------ |
| 🔍 **Risk Detection**         | Identifies risky users and sign-ins using real-time and offline signals.                   |
| 🛡️ **Automated Response**    | Triggers Conditional Access to enforce policies (MFA, password reset, block).              |
| 📊 **Investigation & Export** | Risk events are available in Azure portal and exportable to tools like Microsoft Sentinel. |
| 🔗 **SIEM Integration**       | Enables correlation of identity risk data with broader security signals.                   |

---

## 🧠 Core Concepts You Must Know

### 🔐 Risk Types

| Risk Type        | Description                                                   | Examples                                         |
| ---------------- | ------------------------------------------------------------- | ------------------------------------------------ |
| **User Risk**    | Probability that the identity itself is compromised.          | Leaked credentials, unusual activity             |
| **Sign-in Risk** | Probability that the sign-in is not from the legitimate user. | Anonymous IP, atypical travel, malware-linked IP |

---

### 📘 Risk Detection Sources

* **Microsoft Threat Intelligence**
* **Behavioral analytics**
* **Leaked credential detection**
* **Impossible travel detection**
* **Sign-ins from risky IPs or TOR exit nodes**

---

### ⚙️ Risk Policies & Actions

| Policy Type             | Recommended Level                               | Actions                |
| ----------------------- | ----------------------------------------------- | ---------------------- |
| **User Risk Policy**    | `High`                                          | Require password reset |
| **Sign-in Risk Policy** | `Medium and above`                              | Require MFA            |
| **Compromised Users**   | Default policies can block or force remediation |                        |

---

### 🔄 Integration & Reporting

* 📤 **SIEM Integration:** Export to Microsoft Sentinel using Identity Protection connector.
* 📂 **Azure Portal Investigation:** Analyze and download risk events in `.CSV`.
* ⚙️ **Graph API:** Aggregate risk data with external sources or automate policy enforcement.

---

## 🔧 Best Practices for Tailwind Traders (Scenario-Based)

| Scenario                                          | Design Decision                     |
| ------------------------------------------------- | ----------------------------------- |
| Access from suspicious IPs or anonymous locations | Block or challenge with MFA         |
| Known leaked credentials for a user               | Automatically reset password        |
| Low sign-in risk                                  | Allow access without friction       |
| Investigating risks across platforms              | Export to Sentinel or use Graph API |
| Legacy authentication usage                       | Block using Conditional Access      |

---

## ✅ Summary

Identity Protection enables **automated detection, response, and investigation** of identity-related threats. Combined with Conditional Access and Sentinel, it forms a **layered defense** aligned with Zero Trust.

---

## 🧪 Exam-Level Questions (with Answers)

### **Question 1:**

You are designing a security solution for Tailwind Traders. You need to ensure that users with leaked credentials are prompted to reset their password automatically. What should you configure?

**A.** Sign-in risk policy
**B.** User risk policy
**C.** Named location policy
**D.** MFA registration policy

✅ **Answer:** **B. User risk policy**

> Explanation: Leaked credentials are evaluated under the **user risk** policy. This policy can trigger password reset.

---

### **Question 2:**

Which of the following best describes the sign-in risk policy?

**A.** Detects if a user has a weak password
**B.** Detects attempts from legacy authentication protocols
**C.** Evaluates the probability that a sign-in was not performed by the legitimate user
**D.** Evaluates whether an IP is geo-blocked

✅ **Answer:** **C.**

> Explanation: Sign-in risk is about determining the **likelihood that a specific sign-in attempt is malicious**.

---

### **Question 3:**

Tailwind Traders wants to detect and respond to sign-ins from anonymous IP addresses or TOR networks. What type of risk policy should be used?

**A.** Device compliance policy
**B.** User risk policy
**C.** Sign-in risk policy
**D.** Intune conditional access policy

✅ **Answer:** **C. Sign-in risk policy**

> Explanation: Anonymous IPs are evaluated during the sign-in attempt and are part of the sign-in risk detection set.

---

### **Question 4:**

Your client wants to correlate identity risk events with other Azure resources and generate alerts. Which integration is most appropriate?

**A.** Azure Monitor
**B.** Microsoft Sentinel
**C.** Microsoft Purview
**D.** Defender for Cloud

✅ **Answer:** **B. Microsoft Sentinel**

> Explanation: Microsoft Sentinel is the SIEM that can **ingest risk events** using the **Identity Protection data connector**.

---

### **Question 5:**

You’ve implemented Conditional Access and Identity Protection. You want to simulate the effects of a new policy without enforcing it yet. What should you use?

**A.** What If Tool
**B.** Audit Logs
**C.** Report-only mode
**D.** Azure Activity Logs

✅ **Answer:** **C. Report-only mode**

> Explanation: Report-only mode allows **testing the impact of a policy** before enforcing it on users.

