# AZ-305: Design for Conditional Access

---

## Overview

**Conditional Access (CA)** is a powerful **access control engine** in Microsoft Entra ID (formerly Azure AD) that evaluates **signals** (user identity, location, device state, etc.) and makes **real-time decisions** to allow, restrict, or block access to resources.

> 🔐 Conditional Access is essential for a **Zero Trust** strategy—verifying explicitly and using least privilege access.

---

## How Conditional Access Works

```

\[User Sign-In] --> \[Conditional Access Policy Evaluation]
↓
Allow | Require MFA | Block | Require Compliant Device | Other Controls

```

CA decisions are based on:

- Who the user is
- Where the user is (named locations/IPs)
- Device compliance
- Application being accessed
- Risk level (sign-in/user risk)
- Client app used

---

## Key Features

| Feature                                | Description                                                                 |
|----------------------------------------|-----------------------------------------------------------------------------|
| **Granular MFA**                       | Apply MFA only when needed (e.g., risky login, unknown location)            |
| **Named Locations**                    | Define IP ranges/countries for geo-based controls                          |
| **Device State Evaluation**            | Allow access only from compliant or hybrid-joined devices                  |
| **Approved Client Apps**              | Restrict access to Microsoft apps or approved apps                         |
| **Legacy Authentication Blocking**     | Protect against password spray attacks using older protocols               |
| **Report-only Mode**                   | Simulate and analyze CA policy effects before enforcement                  |
| **What If Tool**                       | Test policy scenarios for a given user and app                             |

> 💡 **License Requirement**: Microsoft Entra ID P1 or P2, or Microsoft 365 Business Premium

---

## Use Cases at Tailwind Traders

| Scenario                                           | Solution                                                                 |
|----------------------------------------------------|--------------------------------------------------------------------------|
| **Selective MFA**                                  | Apply MFA only to risky sign-ins or unknown locations                    |
| **Geo-blocking**                                   | Block access from countries or IP ranges where Tailwind Traders operates |
| **Managed Devices Only**                           | Require access from Intune-compliant or hybrid-joined devices            |
| **Approved Client Apps Only**                      | Restrict mobile access to managed or approved apps only                  |
| **Block Legacy Authentication**                    | Block protocols like POP/IMAP, SMTP, MAPI, etc.                          |
| **Compromised Accounts Protection**                | Enable user risk/sign-in risk policies and force password changes        |
| **Staged Rollouts with Report-only Mode**          | Evaluate the impact of policies before enforcement                      |
| **Policy Simulation using What If Tool**           | Predict how policies affect users/apps before applying                  |

---

## Example Conditional Access Policies

| Policy Name                     | Conditions                                         | Controls                          |
|----------------------------------|-----------------------------------------------------|------------------------------------|
| **Require MFA for Admins**       | Role = Global Admin                                 | Grant access, require MFA          |
| **Block Legacy Auth**            | Client app = Other clients (POP, IMAP, SMTP, etc.) | Block access                       |
| **Restrict Geo Access**          | Location = Not in Trusted List                      | Block access                       |
| **Compliant Devices Only**       | Device = Not compliant                              | Block or restrict access           |
| **High Sign-in Risk Users**      | Sign-in risk = High                                 | Require password change or MFA     |
| **Approved Apps Only**           | Client App ≠ Approved App                           | Block or restrict access           |

---

## Diagram: Conditional Access Evaluation Flow

```

\[User Sign-in Request]
|
\|-- Evaluate Conditions:
\- User Role
\- Location
\- Device State
\- Application
\- Risk Level
\- Client App
|
\`--> Apply Controls:
\- Allow Access
\- Require MFA
\- Require Compliant Device
\- Require Approved App
\- Block Access

```

---

## Best Practices

✅ Use **Report-only mode** before enforcing policies  
✅ Always **exclude break-glass admin accounts**  
✅ Block **legacy authentication protocols**  
✅ Apply **MFA selectively** to balance security and UX  
✅ Use **named locations** for geo-based decisions  
✅ Combine CA with **Intune/device compliance policies**

---

## Practice Exam Questions

**Q1.** Tailwind Traders wants to allow access to cloud apps only from managed devices. What should you configure?

A. Role-Based Access Control  
B. Conditional Access policy with device compliance  
C. Just-in-Time VM Access  
D. Application Proxy  

*Correct Answer: B*

---

**Q2.** How can an administrator preview the effect of a Conditional Access policy before enabling it?

A. Audit logs  
B. Diagnostic settings  
C. Report-only mode  
D. Entra Insights  

*Correct Answer: C*

---

**Q3.** Which protocol should be blocked using Conditional Access to prevent password spray attacks?

A. OAuth2  
B. POP and IMAP  
C. SAML  
D. OpenID Connect  

*Correct Answer: B*

---

**Q4.** What tool helps visualize how a Conditional Access policy will apply to a user?

A. Compliance Manager  
B. Risk Explorer  
C. What If tool  
D. Microsoft Defender for Cloud  

*Correct Answer: C*

---

**Q5.** What is the primary purpose of defining named locations in Conditional Access?

A. Restrict access to specific apps  
B. Apply risk-based Conditional Access  
C. Apply geo-based access decisions  
D. Assign roles based on IP location  

*Correct Answer: C*

---
