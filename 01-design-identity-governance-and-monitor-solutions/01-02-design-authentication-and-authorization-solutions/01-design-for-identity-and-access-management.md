# AZ-305: Design for Identity and Access Management (IAM)

---

## Overview

Azure IAM (Identity and Access Management) helps control **who can access what**, under what conditions, and from which devices and locations. As an Azure architect, your IAM design should be **secure, unified, user-friendly, and adaptable** across all users, devices, and apps.

---

## Four Key Guidelines of a Strong IAM Solution

1. **Unified Identity Management**  
   - Centralized management of **all identities** and access to **cloud and on-prem** apps  
   - Improves **visibility, control, and compliance**

2. **Seamless User Experience**  
   - Fast, intuitive sign-ins  
   - Reduced password management overhead  
   - Boosts end-user **productivity**

3. **Secure Adaptive Access**  
   - Strong authentication (e.g., MFA)  
   - Risk-based adaptive policies  
   - Balances **security** with **usability**

4. **Simplified Identity Governance**  
   - Automated access management  
   - Ensures **least privilege**  
   - Applies to **users and admins**

---

## IAM Design Considerations for Tailwind Traders

| Scenario                              | Recommendation                                    |
|--------------------------------------|--------------------------------------------------|
| Internal workforce identity          | Use **Microsoft Entra ID** (formerly Azure AD)   |
| External partners & vendors          | Use **Microsoft Entra B2B**                      |
| Customer-facing apps & portals       | Use **Azure AD B2C (Microsoft Entra External ID)**|

---

### ✅ Consider Microsoft Entra ID

- Core **directory services**, **identity protection**, and **access management**
- Operates in **cloud**, **hybrid**, or **on-prem** environments
- Central IAM solution for **employees** and **apps**

### ✅ Consider B2B Collaboration

- Support **external business partners** (suppliers, vendors, contractors)
- Enable secure, policy-governed access for **guest users**
- Use **Microsoft Entra B2B**

### ✅ Consider B2C Identity

- Manage **customer identities** (signup, login, profile management)
- Use **Azure AD B2C** to enable secure, customizable **user experiences**
- Useful for **consumer-facing apps or portals**

---

## Summary Table

| IAM Feature               | Benefit                                             |
|---------------------------|------------------------------------------------------|
| Unified Identity          | Central visibility, reduced sprawl                   |
| Seamless UX               | Easier sign-ins, less helpdesk overhead              |
| Secure Adaptive Access    | Dynamic control based on risk                        |
| Identity Governance       | Enforced access policies, automated permissions      |
| Entra ID                  | Workforce IAM (internal apps, SSO, policies)         |
| Entra B2B                 | Partner/vendor access (guest user management)        |
| Entra B2C (Azure AD B2C)  | Customer identity with branded UX & self-service     |

---

## Practice Exam Questions

**Q1.** What is the primary benefit of unified identity management?

A. Reduces data storage cost  
B. Provides a single interface for building APIs  
C. Enables centralized visibility and control across all applications  
D. Prevents sign-ins from mobile devices  

*Correct Answer: C*

---

**Q2.** Which Microsoft Entra feature is best for enabling Tailwind Traders’ suppliers to securely collaborate?

A. Entra ID Governance  
B. Microsoft Entra B2B  
C. Azure AD B2C  
D. Azure Key Vault  

*Correct Answer: B*

---

**Q3.** What is the primary use case for Azure AD B2C?

A. Managing guest user access for vendors  
B. Managing admin access for internal apps  
C. Controlling sign-up and sign-in for customer-facing apps  
D. Monitoring Azure infrastructure resources  

*Correct Answer: C*

---

**Q4.** What is an example of secure adaptive access in IAM?

A. Automatically rotating passwords  
B. Multi-factor authentication based on sign-in risk  
C. Disabling inactive accounts  
D. Renaming user accounts regularly  

*Correct Answer: B*

---

**Q5.** Which of the following is NOT a characteristic of a strong IAM solution?

A. Risk-based access control  
B. Complex, multi-step user login  
C. Seamless user experience  
D. Centralized identity governance  

*Correct Answer: B*

---

Need visuals for IAM architecture or Entra B2B/B2C flows? Just ask!
