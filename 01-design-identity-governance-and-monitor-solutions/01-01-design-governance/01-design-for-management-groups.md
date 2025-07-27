# AZ-305: Design for Management Groups

---

## What Are Management Groups?

- **Management groups** are containers within Azure that organize subscriptions into a hierarchy to apply **governance policies, role-based access control (RBAC)**, and **compliance settings** consistently across multiple subscriptions.
- They enable **centralized management** of access, policies, and compliance across an entire Azure tenant.
- Policies or role assignments applied at a management group level **inherit down to all child management groups and subscriptions**.

---

## Key Features & Benefits of Management Groups

- **Policy Aggregation**: Assign Azure Policies and initiatives once at a management group level rather than per subscription.
- **Access Management**: Create RBAC role assignments at management group level and have them propagate to child subscriptions.
- **Compliance and Auditing**: Centralize monitoring and auditing of access and policy enforcement across subscriptions.
- **Scope Control**: Limit or enforce resources (e.g., restrict allowed VM regions) across subscriptions by using policy at the management group level.

---

## Characteristics of Management Groups

- **Hierarchy Limit**: Management groups can be nested up to **6 levels deep** (excluding the tenant root and subscription levels).
- **Tenant Root Group**: Every Azure AD tenant has a root management group. **All subscriptions are by default placed under this root**.
- **Authorization**: RBAC for management group operations is **not enabled by default** and requires explicit assignment.
- **Inheritance**: Policies and role assignments assigned at a management group propagate downward to all children.

---

## Design Considerations & Best Practices

When designing management groups, you want to balance flexibility, simplicity, and governance needs:

1. **Align Management Groups to Organizational Structure**
   - Use **departments, teams, or business units** to define management groups (e.g., Sales, Corporate, IT).
   - Helps assign policies and roles relevant to each group.

2. **Leverage Geographical Boundaries**
   - Create management groups per region (e.g., West US, East US) if different compliance or policies apply per geography.

3. **Implement a Top-Level Management Group**
   - Use a **platform-level management group** above department groups to assign common, global policies and roles for the entire organization.

4. **Keep the Hierarchy Flat and Manageable**
   - Limit the depth to 3-4 levels to reduce complexity.
   - Avoid very deep nesting that complicates troubleshooting and policy application.

5. **Separate Environments**
   - Create management groups for **Production**, **Development**, **Sandbox/Experimentation** to isolate environments.
   - Sandbox groups allow safe experimentation without affecting production policies.

6. **Isolate Sensitive Workloads**
   - Put highly sensitive data or workloads in dedicated management groups with stricter compliance and security policies.

---

## Example: Tailwind Traders Management Group Hierarchy

- **Root (Tenant Root)**
  - Tailwind Traders (Top-Level)
    - Sales
      - West Region
      - East Region
    - Corporate
      - HR
      - Legal
    - IT
      - Research
      - Development
      - Production
    - Sandbox

Each management group can have policies and RBAC tailored to its organizational or geographical needs.

---

## Important Tips

- Always **test policy impact** in sandbox groups before applying at production-level management groups.
- Use management groups to **enforce cost controls, resource restrictions, and compliance** uniformly.
- Audit role assignments and policy assignments regularly to ensure governance compliance.
- Remember RBAC on management groups must be explicitly assigned for users to manage them.

---

# Summary

| Concept                          | Description                                                                                   |
|---------------------------------|-----------------------------------------------------------------------------------------------|
| Management Groups               | Containers for grouping Azure subscriptions to apply policies and RBAC consistently.          |
| Hierarchy Depth Limit           | Up to 6 nested management group levels (excluding tenant root and subscriptions).             |
| Policy & RBAC Inheritance       | Assignments at management group level cascade down to child management groups and subscriptions.|
| Default Subscription Placement | All new subscriptions go under the tenant root management group by default.                    |
| Design Principle               | Align management groups to organizational/geographical structures, keep hierarchy flat, and isolate environments (Prod, Dev, Sandbox).|
| Top-Level Management Group     | For common policies and role assignments across entire organization.                           |
| Sensitive Data Isolation       | Use dedicated management groups for sensitive data with enhanced compliance policies.         |

---

# Practice Exam Questions

**Q1.** You need to restrict the regions where virtual machines can be created across multiple subscriptions in your Azure tenant. Which Azure feature allows you to enforce this restriction with a single policy assignment?

A. Role assignments at subscription level  
B. Azure Policy assignment at management group level  
C. Network Security Group rules at resource group level  
D. Azure Blueprints at resource level  

*Correct Answer: B*

---

**Q2.** Your company has 3 departments and wants to apply department-specific Azure policies. What is the recommended best practice when designing the management group hierarchy?

A. Create one management group per department directly under the tenant root and assign policies there.  
B. Place all subscriptions under a single management group and assign policies per subscription.  
C. Create multiple management groups nested 6 levels deep for each department.  
D. Assign policies directly to resource groups in each subscription.  

*Correct Answer: A*

---

**Q3.** Which statement about RBAC on management groups is TRUE?

A. RBAC on management groups is enabled by default.  
B. Role assignments on management groups only apply to that management group and not to subscriptions underneath.  
C. Role assignments at management group level are inherited by all child subscriptions and management groups.  
D. You cannot assign roles at management group level.  

*Correct Answer: C*

---

**Q4.** You want to create an isolated environment for users to experiment with new Azure features without impacting production resources or policies. What is the best approach?

A. Create a separate sandbox management group for experimental workloads.  
B. Use resource locks on production subscriptions to prevent changes.  
C. Assign users Reader role on production subscriptions.  
D. Create a resource group labeled "Sandbox" in the production subscription.  

*Correct Answer: A*

---

**Q5.** What is the maximum depth allowed for management group nesting within an Azure tenant (excluding tenant root and subscriptions)?

A. 3  
B. 4  
C. 6  
D. Unlimited  

*Correct Answer: C*

---

If you want, I can also create a mind map or cheat sheet for quick reference! Would you like that?
