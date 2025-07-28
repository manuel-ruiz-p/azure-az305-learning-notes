# AZ-305: Design for Microsoft Entra B2C (Business-to-Customer)

---

## Overview

**Microsoft Entra B2C** (formerly Azure AD B2C) is a customer identity and access management (CIAM) solution that helps organizations manage how **consumers sign up, sign in, and manage profiles** when using apps. It's optimized for **scalable and secure identity experiences**, independent of your corporate directory.

> 🔐 B2C is ideal for customer-facing apps where users are **not part of your organization** (e.g., retail shoppers, service subscribers, etc.).

---

## Core Concepts

| Concept                           | Description                                                                |
| --------------------------------- | -------------------------------------------------------------------------- |
| **Entra Tenant vs B2C Tenant**    | Your org's Microsoft Entra tenant is **separate** from the B2C tenant      |
| **Customer Identity Management**  | You manage customer identities through user flows and policies             |
| **Flexible Identity Providers**   | Supports **local accounts**, **social logins**, and **federated identity** |
| **Customizable UX**               | Fully customizable UI using HTML/CSS templates                             |
| **Separation of Identity Stores** | Org users and customers are stored in **separate directories**             |

---

## B2C Architecture Diagram

```
[Customer Identity] ──> [Sign-In / Sign-Up Flow] ──> [Custom Policy / UI] ──> [Token Issued] ──> [App Access Granted]
```

---

## Key Features of Microsoft Entra B2C

| Feature                         | Description                                                         |
| ------------------------------- | ------------------------------------------------------------------- |
| **User Flows**                  | Predefined sign-up, sign-in, profile edit, and password reset flows |
| **Custom Policies**             | Advanced scenarios via Identity Experience Framework                |
| **Social Identity Integration** | Sign in via Facebook, Google, LinkedIn, Microsoft, GitHub, etc.     |
| **Custom Attributes**           | Up to 100 custom attributes per user                                |
| **API Connectors**              | Execute REST APIs at specific points in the user journey            |
| **External Identity Proofing**  | Integrate with third-party verification providers                   |
| **Brandable UI**                | Fully customize HTML/CSS for a consistent user experience           |
| **External Identity Stores**    | Delegate data management to CRMs or external databases              |

---

## Design Considerations for Tailwind Traders

| Design Recommendation                         | Justification                                                      |
| --------------------------------------------- | ------------------------------------------------------------------ |
| **Use reusable user flows**                   | ✅ Promotes consistency and reduces management overhead across apps |
| **Enable social identity sign-in**            | ✅ Increases sign-up rate and user convenience                      |
| **Customize UI for brand alignment**          | ✅ Ensures familiarity and trust among customers                    |
| **Store extended user data**                  | ✅ Capture preferences, demographics, and conversion data           |
| **Integrate with external systems**           | ✅ Use CRM or loyalty databases as the system of record             |
| **Verify identity with third-party services** | ✅ Strengthen onboarding for high-trust services                    |

---

## B2C vs. B2B Identity Design Comparison

| Criteria                 | Microsoft Entra B2B                              | Microsoft Entra B2C                              |
| ------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| **Target audience**      | Business partners, vendors, suppliers            | Consumers / customers of Tailwind Traders        |
| **User identity source** | External organizations, federated accounts       | Social accounts, local accounts, federated IDs   |
| **Identity separation**  | Guest users live in **same tenant** as employees | Customer users live in a **separate B2C tenant** |
| **Profile management**   | Managed by Tailwind Traders                      | Self-managed by customers                        |
| **Discovery & privacy**  | External users can discover others (optional)    | Users are isolated and private by default        |
| **UI customization**     | Limited branding (host org branding)             | Fully customizable UI per app or per journey     |
| **Identity proofing**    | Optional / via access policies                   | Integrate third-party verification during signup |

---

## Supported Identity Providers

* **Local accounts** (email/username + password)
* **Social identities**:

  * Microsoft
  * Facebook
  * Google
  * LinkedIn
  * GitHub
* **Enterprise identities via SAML/OpenID Connect**
* **Custom identity providers**

---

## Practice Exam Questions

**Q1.** What distinguishes Azure AD B2C from Microsoft Entra ID in the context of identity management?

A. B2C supports passwordless sign-in for employees
B. B2C is used for managing organizational users only
C. B2C separates customer identities into a distinct tenant
D. B2C requires a VPN connection for customers

*Correct Answer: C*

---

**Q2.** Which of the following is a benefit of using reusable user flows in Azure AD B2C?

A. Enforces MFA on all users
B. Allows multiple user flows in a single tenant
C. Enables consistent user experience across apps
D. Reduces the number of required tenants

*Correct Answer: C*

---

**Q3.** Tailwind Traders wants customers to sign in with existing accounts like Google or Facebook. What feature should they enable?

A. Azure Policy
B. API Management
C. Social identity providers in Azure AD B2C
D. B2B guest invitations

*Correct Answer: C*

---

**Q4.** How can Tailwind Traders maintain branding consistency during the user login journey?

A. Enable B2B theming
B. Customize HTML/CSS using page layout templates
C. Use default B2C forms without editing
D. Apply Azure Resource Manager templates

*Correct Answer: B*

---

**Q5.** Tailwind Traders wants to store additional user preferences and loyalty levels. What should they use?

A. Conditional Access
B. Application Insights
C. Custom user attributes in Azure AD B2C
D. Azure Policy with guest restrictions

*Correct Answer: C*

---

Would you like me to now generate a **single comprehensive Markdown file** with IAM, Entra B2B, and Entra B2C together? Or export them as a downloadable study guide (PDF/Word)?
