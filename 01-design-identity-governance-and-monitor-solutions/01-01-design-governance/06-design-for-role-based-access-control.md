# AZ-305: Design for Role-Based Access Control (RBAC)

---

## What is Azure RBAC?

- Azure RBAC **grants access** to Azure resources you control.
- It evaluates each access request and **allows or denies** actions based on assigned roles.
- RBAC is an **allow model**: users are allowed only the actions explicitly permitted by their assigned roles.
- Example: To have write permission, the role assigned must explicitly include write access.

---

## Key Concepts of Azure RBAC

- Roles define **what actions** a user or service principal can perform.
- Role assignments tie **users, groups, or service principals** to roles.
- Role assignments are scoped to a **management group, subscription, resource group, or resource**.
- The **highest scope possible** should be used when assigning roles to simplify management.

---

## Use Case Scenarios for Tailwind Traders

- Allow one user to manage virtual machines in a subscription; another to manage virtual networks.
- Allow a database admin group to manage SQL databases across the subscription.
- Allow a user to manage all resources in a resource group.
- Allow an application to access all resources in a resource group.

---

## Best Practices for Azure RBAC

- **Grant least privilege** — give users only the permissions needed to perform their jobs.
- **Assign roles to groups, not individual users**, to simplify management.
- Carefully **scope roles** at the highest appropriate level.
- Use **custom roles** if built-in roles don’t fit your needs.
- Remember RBAC is **additive** — effective permissions are the sum of all role assignments.

---

## Azure Policy vs Azure RBAC Comparison

| Aspect            | Azure Policy                             | Azure RBAC                                    |
|-------------------|----------------------------------------|-----------------------------------------------|
| Purpose           | Ensures resources comply with rules    | Controls who can perform actions on resources |
| Focus             | Resource properties                    | User and service principal permissions         |
| Implementation    | Define policies                        | Assign roles with specific permissions         |
| Default Behavior  | Allow by default                      | Deny by default                                 |

- Use **both together** for comprehensive governance:
  - Azure Policy manages **resource configurations**.
  - Azure RBAC manages **user and app access**.

---

## Handling Overlapping Role Assignments

- Permissions from multiple role assignments are **combined** (additive).
- Example:  
  - User has **Contributor** role at subscription scope (broad permissions).  
  - Also has **Reader** role at resource group scope (limited permissions).  
  - Effective permission is Contributor (more permissive), so Reader role does not reduce access.

---

## Summary Table

| Concept                    | Description                                     |
|----------------------------|------------------------------------------------|
| Role Definition            | Set of permissions describing allowed actions  |
| Role Assignment            | Assigning a role to a user/group/service principal |
| Scopes                    | Management group, subscription, resource group, resource |
| Principle of Least Privilege | Assign minimum permissions needed               |
| Custom Roles               | Define granular permissions beyond built-in roles |
| Additive Permissions       | Effective permissions are sum of all assignments |

---

## Practice Exam Questions

**Q1.** What model does Azure RBAC follow for granting access?

A. Deny model  
B. Allow model  
C. Audit model  
D. Monitoring model  

*Correct Answer: B*

---

**Q2.** Which of the following is a best practice when assigning Azure RBAC roles?

A. Assign roles directly to users  
B. Assign roles to groups whenever possible  
C. Assign roles at the lowest possible scope  
D. Avoid using built-in roles  

*Correct Answer: B*

---

**Q3.** How does Azure RBAC handle multiple overlapping role assignments?

A. Denies access if any role denies permission  
B. Uses the most restrictive role  
C. Adds permissions together for effective access  
D. Uses the first assigned role only  

*Correct Answer: C*

---

**Q4.** When should you consider creating a custom Azure RBAC role?

A. When built-in roles grant more permissions than needed  
B. When you want to assign roles at the subscription level  
C. When you want to assign roles to groups  
D. When you want to audit resource compliance  

*Correct Answer: A*

---

**Q5.** Which of the following is true about the default access state in Azure RBAC?

A. All users have full access by default  
B. All access is denied by default until roles are assigned  
C. Users have read access by default  
D. Roles are assigned automatically  

*Correct Answer: B*

---

Need diagrams, flashcards, or a PDF version for Azure RBAC? Just let me know!
