# AZ-305: Design for Microsoft Entra ID

---

## Overview

**Microsoft Entra ID** (formerly Azure Active Directory) is a **multitenant, cloud-based directory and identity management service**. It unifies **directory services**, **access management**, and **identity protection**, and supports both **cloud-only** and **hybrid** environments.

> ✅ Core Features:  
> - Identity & access management  
> - Application access control  
> - Identity protection  
> - Hybrid directory integration

---

## Key Characteristics of Microsoft Entra ID

| Identity Strategy       | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Cloud-only             | All identities live and are managed directly in Microsoft Entra ID         |
| Hybrid Identity        | Extends on-premises Active Directory to the cloud                          |
| Directory Sync         | Use **Microsoft Entra Connect** or **Connect Cloud Sync** for integration  |

### Benefits of Microsoft Entra ID

- Centralized account management
- Integrated **RBAC**, **Conditional Access**, and **Access Reviews**
- Password hash sync and **SSO** (Single Sign-On)
- Support for **on-premises-to-cloud** identity extension

---

## Key Design Considerations for Tailwind Traders

| Consideration                                 | Design Guidance                                                                 |
|----------------------------------------------|----------------------------------------------------------------------------------|
| Centralized Identity Management              | Integrate cloud + on-prem directories for unified control                        |
| Single Entra Instance                        | Designate **one authoritative source** for all org accounts                      |
| Limit Privileged Sync                        | Do **not sync high-privileged cloud accounts** to on-prem AD                    |
| Password Hash Sync                           | Enables credential protection and reduces risk from **leaked passwords**        |
| Single Sign-On (SSO)                         | Simplifies user experience and improves security via one primary login          |
| Avoiding Identity Duplication                | Separate identities = higher **management overhead** and increased risk         |

---

## Hybrid Identity Strategy

- Use **Microsoft Entra Connect** for syncing on-prem AD to the cloud
- Enable **Password Hash Synchronization** for user credentials
- Filter out **high-privileged cloud accounts** from syncing
- Enable **SSO** to streamline login experience and auto-provision app access

---

## Visual Summary

```plaintext
[ On-Prem AD ]
      |
      | (Microsoft Entra Connect / Cloud Sync)
      v
[ Microsoft Entra ID ]
      |
   +--+--+
   |     |
[ SSO ] [ Identity Protection ]
```

## Summary Table

| Feature                       | Cloud-Only | Hybrid |
|-------------------------------|------------|--------|
| RBAC, Conditional Access      | ✅         | ✅     |
| Access Reviews                | ✅         | ✅     |
| Identity Protection           | ✅         | ✅     |
| Password Hash Sync            | ❌         | ✅     |
| SSO with On-Prem Accounts     | ❌         | ✅     |
| Integration with On-Prem AD   | ❌         | ✅     |

---

## Practice Exam Questions

**Q1.** What is the main benefit of using Microsoft Entra Connect?

A. It increases internet bandwidth for Azure  
B. It allows syncing of local group policies  
C. It synchronizes on-premises AD identities with Microsoft Entra ID  
D. It replaces the need for RBAC  

*Correct Answer: C*

---

**Q2.** Why should highly privileged Microsoft Entra accounts not be synced back to on-prem AD?

A. To improve SSO latency  
B. To reduce licensing costs  
C. To mitigate risk of cloud-to-on-prem pivot attacks  
D. To enable MFA  

*Correct Answer: C*

---

**Q3.** What is a key advantage of password hash synchronization?

A. It backs up user passwords to a recovery vault  
B. It enables seamless SSO in hybrid environments  
C. It allows access to SQL Server on-premises  
D. It disables conditional access policies  

*Correct Answer: B*

---

**Q4.** Tailwind Traders wants a single authoritative directory for clarity and consistency. What should they do?

A. Create multiple Entra tenants per business unit  
B. Use separate Entra directories for each environment  
C. Use a **single Microsoft Entra instance** as the source of truth  
D. Sync AD only with cloud-hosted SharePoint  

*Correct Answer: C*

---

**Q5.** What issue can arise from managing separate on-prem and cloud identities?

A. Reduced network throughput  
B. Extra management overhead and security risk  
C. Inability to provision applications  
D. Overuse of Azure Policy  

*Correct Answer: B*
