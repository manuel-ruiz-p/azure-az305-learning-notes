# AZ-305: Design for Microsoft Entra B2B

---

## Overview

**Microsoft Entra Business-to-Business (B2B)** is a feature of Microsoft Entra ID that allows secure **collaboration with external partners, vendors, and guest users**. It enables organizations to **invite users as guests**, without managing their credentials or accounts, while retaining full control over access permissions and duration.

---

## How Microsoft Entra B2B Works

- External users are invited to the **Tailwind Traders tenant** as guest users.
- Users can authenticate with their **own identity providers** (corporate, social, or federated).
- Guest users access Tailwind Traders resources via an **email invitation link**.
- Users must **consent to permissions** and complete **MFA** if required.
- Guest users are shown the **Access Panel** with available apps and services.

[External User Identity] ──> [Invitation Email] ──> [Consent + MFA] ──> [Tailwind Traders Access Panel]


---

## Key Features of Microsoft Entra B2B

| Feature                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| Bring Your Own Identity (BYOI)  | External users use their **existing identity providers**                    |
| No account lifecycle management | Tailwind Traders **doesn't manage passwords or provisioning**              |
| Guest user model                | External users are invited and governed as **guest accounts**              |
| MFA Support                     | Optional but recommended for increased security                            |
| Conditional Access              | Enforce access policies based on **device, location, and MFA**             |
| App and service access          | Guest users can access both **cloud and on-prem apps** via the access panel|

---

## Microsoft Entra B2B Workflow

1. Admin or app owner invites user via **custom form or email**
2. Guest receives invite and clicks link
3. Guest **consents to required permissions**
4. If required, completes **Multi-Factor Authentication (MFA)**
5. Guest accesses the **Access Panel** with apps/services shared with them

---

## Design Considerations for Tailwind Traders

| Design Recommendation                          | Reason                                                                 |
|------------------------------------------------|------------------------------------------------------------------------|
| Delegate app-level guest user management       | ✅ App owners best know who should access their apps                   |
| Use Conditional Access                         | ✅ Enforce location, device, risk-based rules                          |
| Require MFA                                    | ✅ Add an extra security layer for all guest access                    |
| Integrate Identity Providers                   | ✅ Allow users to sign in with Google, Facebook, Microsoft, or SAML    |
| Implement Self-Service Sign-Up                 | ✅ Allow partners to register themselves with a **customized flow**    |

---

## Supported Identity Providers

- **Enterprise providers** (e.g., Microsoft Entra ID, Active Directory Federation Services)
- **Social identities** (e.g., Google, Facebook, Microsoft accounts)
- **SAML-based identity providers**

---

## Benefits of Microsoft Entra B2B

| Benefit                                | Description                                                             |
|----------------------------------------|-------------------------------------------------------------------------|
| Low admin overhead                     | Tailwind Traders doesn’t manage external passwords or lifecycles       |
| Enhanced security                      | Use Conditional Access + MFA                                           |
| Seamless external collaboration        | Users use their own accounts to access shared resources                |
| Granular access control                | Tailwind Traders stays in control of **who accesses what and when**    |
| Federated identity options             | Supports various identity providers to increase flexibility            |

---

## Practice Exam Questions

**Q1.** What is the primary benefit of Microsoft Entra B2B for Tailwind Traders?

A. Enables users to create local accounts in Entra ID  
B. Allows Tailwind Traders to fully manage guest user passwords  
C. Supports secure collaboration with external users using their own identity  
D. Provides internet-facing DNS services  

*Correct Answer: C*

---

**Q2.** Which security feature is recommended before a guest user accesses Tailwind Traders applications?

A. VPN connection  
B. Multi-Factor Authentication (MFA)  
C. Azure Key Vault  
D. Azure Monitor  

*Correct Answer: B*

---

**Q3.** How can Tailwind Traders reduce admin burden while maintaining app-specific access control?

A. Use SSO across all regions  
B. Disable conditional access  
C. Assign app owners to manage guest user access  
D. Sync external identities into their Entra directory  

*Correct Answer: C*

---

**Q4.** What is the purpose of integrating with external identity providers in B2B scenarios?

A. To reduce Azure costs  
B. To force users to create a new Tailwind Traders account  
C. To allow users to log in with existing credentials (e.g., Google, Facebook)  
D. To enable resource replication across tenants  

*Correct Answer: C*

---

**Q5.** What can be implemented to allow partners to self-register into the Tailwind Traders directory?

A. Application proxy  
B. Entra self-service sign-up flow  
C. Azure Kubernetes Service  
D. Azure Data Factory pipeline  

*Correct Answer: B*

---

Let me know if you'd like me to compile all identity-focused modules (IAM, Entra ID, Entra B2B) into one consolidated Markdown study guide or export them into a PDF.
