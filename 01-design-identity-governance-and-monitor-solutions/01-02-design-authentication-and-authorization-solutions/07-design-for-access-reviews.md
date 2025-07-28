# 🔐 Design for Access Reviews (Enhanced for AZ-305)

**Topic:** Identity governance and access management
**Exam Domain:** Design identity, governance, and monitoring solutions
**Objective:** Design and implement access reviews to maintain least privilege and secure resource access

---

## 🔍 Overview: Why Access Reviews Matter

* Employees often change roles, requiring different access rights.
* Access must be provisioned at hire, adjusted on role change, and removed at departure.
* Access reviews help maintain **least privilege** and reduce risk from excessive or stale permissions.
* Microsoft Entra Access Reviews provide a **planned, repeatable, and auditable process** to review access to resources, apps, groups, and privileged roles.

---

## ⚙️ Core Capabilities of Microsoft Entra Access Reviews

| Capability             | Description                                                                                                 |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Access Validation**  | Reviewers verify that users still need access to assigned resources.                                        |
| **Targeted Resources** | SaaS apps, line-of-business apps, Microsoft 365 groups, Teams, access packages, and privileged roles (PIM). |
| **Reviewers**          | Resource owners, delegated reviewers, or self-attestation by end users.                                     |
| **Automated Actions**  | Remove users with no activity or who fail review.                                                           |
| **Notifications**      | Automated emails notify reviewers and users affected by access changes.                                     |

---

## 🧩 Access Review Roles

| Reviewer Type      | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| **Resource Owner** | Business owner responsible for the resource.                 |
| **Delegate**       | Designated group/person assigned by admin to conduct review. |
| **End User**       | Self-attestation where users confirm their own access needs. |

* **Note:** Reviewer assignments are fixed once the review is started.

---

## 📅 Planning Access Reviews: Example Scenario for Tailwind Traders

| Component           | Implementation Detail                                                                                                                       |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Resources to Review | Microsoft Dynamics resources                                                                                                                |
| Review Frequency    | Monthly                                                                                                                                     |
| Reviewers           | Dynamics program managers                                                                                                                   |
| Notification        | Email 24h before start with custom message for cooperation                                                                                  |
| Duration            | 24h review period (48h after notification)                                                                                                  |
| Automated Actions   | - Remove users inactive for 90 days<br>- Remove users not reviewed within timeframe<br>- Remove users from `dynamics-access` security group |
| Manual Actions      | Reviewers can pre-approve removals before automated enforcement                                                                             |
| User Notification   | Email users explaining removal and re-access process                                                                                        |

---

## 💡 Best Practices

* Define clear **policies and schedules** based on risk and compliance needs.
* Choose **qualified reviewers** who understand resource sensitivity.
* Combine access reviews with **Privileged Identity Management (PIM)** to govern admin roles.
* Leverage **automatic removal** for stale or unreviewed access to reduce risk.
* Communicate clearly to affected users on how to regain access if needed.
* Monitor review outcomes and adjust policies as needed for continuous improvement.

---

## ✅ Summary

Access reviews ensure ongoing compliance and enforce **least privilege access** by verifying user permissions to critical resources. They are a key part of an overall identity governance strategy and integrate tightly with Microsoft Entra ID, PIM, and Conditional Access.

---

# 🧪 Exam-Level Questions on Access Reviews

### Question 1

You need to design an access review process for the marketing SaaS app that requires business owners to approve access every quarter. What reviewer type should you assign?

**A.** Delegated reviewers
**B.** Resource owners
**C.** End users
**D.** Global administrators

✅ **Answer:** **B. Resource owners**

> Business owners are the resource owners responsible for approving access reviews on their resources.

---

### Question 2

Tailwind Traders wants to automatically remove access for users who have not signed in for 90 days as part of an access review. What feature supports this?

**A.** Access review automated removal for inactive users
**B.** Conditional Access policy
**C.** Privileged Identity Management access review
**D.** Microsoft Defender for Identity alerts

✅ **Answer:** **A. Access review automated removal for inactive users**

> Access reviews can be configured to automatically remove users with no interactive sign-in in a specified time frame.

---

### Question 3

Which of the following is **not** a valid reviewer type in Microsoft Entra access reviews?

**A.** Resource owner
**B.** Delegates
**C.** End users
**D.** Security administrator

✅ **Answer:** **D. Security administrator**

> Security administrator is a role but **not** a reviewer type in access reviews.

---

### Question 4

An access review has been created with delegated reviewers. After the review starts, you realize the reviewers are incorrect. What can you do?

**A.** Change the reviewers immediately
**B.** Delete and recreate the access review with correct reviewers
**C.** Assign additional reviewers mid-review
**D.** Pause the access review and reassign

✅ **Answer:** **B. Delete and recreate the access review with correct reviewers**

> Reviewer assignments cannot be changed after a review starts.

---

### Question 5

How can you ensure users who fail an access review can regain access if needed?

**A.** Allow reviewers to approve removals before enforcement
**B.** Use Conditional Access to automatically re-enable access
**C.** Send users email notifications with instructions to request access again
**D.** Use Microsoft Defender for Identity remediation

✅ **Answer:** **C. Send users email notifications with instructions to request access again**

> It is a best practice to notify users and provide a path for re-access if their access is removed.
