# AZ-305: Design for Azure Policy

---

## What is Azure Policy?

- Azure Policy enables creation, assignment, and management of policies to **control or audit Azure resources**.
- Policies **enforce rules** to keep resource configurations compliant with corporate or organizational standards.
- Helps maintain governance by preventing or remediating noncompliant resources.

---

## Key Characteristics of Azure Policy

- Supports **individual policies** and **policy sets** called **initiatives** (groups of related policies).
- Comes with many **built-in policies and initiatives**.
- Policies are **inherited down the management hierarchy**.
- Can be scoped and enforced at different levels: subscription, resource groups, management groups, etc.
- Evaluates resources across Azure and **Arc-enabled resources** (resources outside Azure but managed by Azure).
- Identifies and highlights **noncompliant resources**.
- Supports **preventing creation of noncompliant resources** and **automatic remediation**.
- Integrates with **Azure Pipelines** for pre- and post-deployment policy enforcement.

---

## Applying Azure Policy

- Policies can be assigned at multiple levels; e.g.,  
  - **Production management group level**  
  - **Application resource group level**
- Use the **Azure Policy compliance dashboard** to:  
  - Get an aggregated compliance view  
  - Drill down to resource-level compliance  
  - Bulk remediate existing resources  
  - Automatically remediate new resources

---

## When Does Azure Policy Evaluate Resources?

Azure Policy evaluations are triggered by:

- Creation, deletion, or update of a resource within policy scope.
- New assignment of a policy or initiative to a scope.
- Update to an existing policy or initiative assignment.
- Standard compliance evaluation cycle (about every 24 hours).

---

## Handling Noncompliant Resources

Organizations can choose different actions on noncompliance:

- **Deny** changes that cause noncompliance.
- **Log** changes for audit purposes.
- **Modify** the resource before or after the change.
- **Deploy related resources** to achieve compliance.

---

## Automatic Remediation

- Useful for consistent tagging or fixing resource configurations.
- Azure Policy can **add or reapply tags** automatically.
- Example: Ensure all resources in a resource group have a specific `Location` tag.

---

## Azure Policy vs Azure RBAC

| Feature             | Azure Policy                                  | Azure RBAC                              |
|---------------------|----------------------------------------------|---------------------------------------|
| Purpose             | Ensures resource configurations are compliant with business rules | Controls who can perform actions on resources |
| Focus               | Resource state and compliance                 | User permissions and access control   |
| Enforcement         | Prevents or remediates noncompliant resources | Grants or restricts user actions      |
| Dependency          | Independent of who makes changes              | Controls who can make changes          |

- Use **both** together for full governance:  
  - RBAC controls **who can do what**  
  - Policy controls **what is allowed in resource configuration**

---

## Resource Access and Identity Management

- After defining identity management, control access with RBAC and monitor with:  
  - **Microsoft Entra Conditional Access** (enforce access conditions)  
  - **Microsoft Entra ID Protection** (monitor risky access)  
  - **Microsoft Entra Access Reviews** (periodic verification of access necessity)

---

## Summary Table

| Concept                     | Description                                      |
|-----------------------------|------------------------------------------------|
| Policy Types                | Individual policies and initiatives (policy sets)|
| Policy Scope                | Management groups, subscriptions, resource groups, resources |
| Compliance Evaluation       | Triggered on resource changes, policy assignments, or every 24 hours |
| Enforcement Options         | Deny, audit, modify, deploy related resources    |
| Remediation                 | Automatic fixing (e.g., tagging)                 |
| Policy vs RBAC              | Policy enforces configuration rules; RBAC controls access |
| Monitoring and Reporting    | Azure Policy compliance dashboard                |

---

## Practice Exam Questions

**Q1.** What is the primary purpose of Azure Policy?

A. To control user permissions to Azure resources  
B. To ensure Azure resources are compliant with organizational rules  
C. To monitor network traffic in Azure  
D. To manage billing and cost management  

*Correct Answer: B*

---

**Q2.** Which of the following triggers an Azure Policy evaluation? (Select all that apply)

A. A resource is created within a policy scope  
B. A policy is assigned to a scope  
C. A user logs into Azure Portal  
D. The standard compliance evaluation cycle runs  

*Correct Answers: A, B, D*

---

**Q3.** How does Azure Policy differ from Azure RBAC?

A. Azure Policy controls resource state compliance; RBAC controls user permissions  
B. Azure Policy controls user access; RBAC controls resource compliance  
C. Both perform the same function  
D. RBAC automatically remediates noncompliant resources  

*Correct Answer: A*

---

**Q4.** What feature of Azure Policy helps you quickly identify and fix noncompliant resources?

A. Azure Security Center  
B. Azure Policy compliance dashboard  
C. Azure Monitor alerts  
D. Azure Cost Management reports  

*Correct Answer: B*

---

**Q5.** You want to ensure that all resources in a resource group have a "Location" tag. How can you achieve this?

A. Use Azure RBAC to restrict resource creation  
B. Use Azure Policy with automatic remediation to enforce and apply the tag  
C. Use Azure Monitor to track tag changes  
D. Manually review and tag resources  

*Correct Answer: B*

---

Would you like me to prepare diagrams, flashcards, or a summary PDF for Azure Policy next?
