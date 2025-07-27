# AZ-305: Design for Subscriptions

---

## What Are Azure Subscriptions?

- **Azure Subscriptions** are logical containers that:
  - Serve as **units of management, scale, and billing**.
  - Define boundaries for **resource management, access control, cost tracking, and quotas**.
  - Provide **billing accounts** for Azure services and products.
- Types of subscriptions include **Enterprise Agreement**, **Pay-As-You-Go**, and others.

---

## Key Characteristics of Subscriptions

- Subscriptions provide **separate billing and cost tracking boundaries** — useful for separating environments like development, test, and production.
- They enable **policy application at individual subscription level**, supporting varying compliance needs.
- Subscriptions can be used to **scale workloads beyond single subscription limits**.
- They act as **management boundaries**, providing administrative separation and control.

---

## Design Considerations When Creating Subscriptions

1. **Align Subscriptions to Business Needs**
   - Treat subscriptions as **democratized management units**.
   - Assign subscriptions based on specific teams, workloads, or business priorities.

2. **Group Subscriptions Under Management Groups**
   - Group subscriptions sharing the same policies and role assignments under a common management group.
   - Example: West and East sales subscriptions inherit policies from the Sales management group.

3. **Create Dedicated Shared Services Subscriptions**
   - Isolate shared network resources (e.g., ExpressRoute, Virtual WAN) in a separate subscription.
   - Enables clear billing and administrative boundaries for common infrastructure.

4. **Consider Subscription Scale Limits**
   - Use multiple subscriptions to avoid hitting resource limits (e.g., maximum number of Azure Data Factory integrations per subscription).
   - Separate subscriptions suit large or specialized workloads like HPC, IoT, SAP.

5. **Administrative Management Boundaries**
   - Subscriptions provide clear boundaries for administrative roles.
   - Example: Corporate management group might have one subscription for both HR and Legal, sharing administrators.

6. **Azure Policy Assignment Scope**
   - Policies can be assigned at both management group and subscription levels.
   - For strict compliance workloads (e.g., PCI), consider using subscriptions for isolation instead of too many management groups.

7. **Network Topology Considerations**
   - Virtual networks (VNets) are **not shared across subscriptions**.
   - Inter-subscription communication requires technologies like **VNet peering** or **VPN gateways**.
   - Design subscriptions considering which workloads must communicate frequently.

8. **Subscription Owner Responsibilities**
   - Owners should be aware of their responsibilities.
   - Conduct **regular access reviews** via Microsoft Entra Privileged Identity Management to prevent privilege creep.

---

## Example: Tailwind Traders Subscription Design

- Sales Department:
  - West Sales Subscription  
  - East Sales Subscription  
- Corporate Department:
  - Single subscription for HR and Legal  
- IT Department:
  - Separate subscriptions for Research, Development, and Production  
- Shared Services:
  - Dedicated subscription for shared network infrastructure  

Subscriptions are grouped under respective management groups (Sales, Corporate, IT) to inherit common policies and role assignments.

---

## Important Tips

- Use subscriptions to **manage costs and enforce policies aligned with organizational units and workloads**.
- Avoid creating too many subscriptions unnecessarily — balance scale, governance, and management overhead.
- Consider network communication and compliance when assigning workloads to subscriptions.
- Regularly review access controls to maintain secure and compliant environments.

---

# Summary Table

| Concept                      | Description                                                                            |
|-----------------------------|----------------------------------------------------------------------------------------|
| Azure Subscription          | Logical container for billing, management, and scale boundaries of Azure resources.    |
| Billing & Cost Management    | Subscriptions separate billing and cost tracking for different environments or teams.  |
| Management Boundary          | Provides administrative separation for role assignments and access control.            |
| Policy Scope                 | Azure Policies can be assigned at subscription or management group levels.             |
| Shared Services Subscription | Isolate common network resources to a dedicated subscription for easier billing and management. |
| Scale Limitations            | Large workloads or those with resource limits should use separate subscriptions.       |
| Network Considerations       | VNets are isolated per subscription; cross-subscription communication requires peering or VPN. |
| Access Reviews              | Regular review of subscription owners' privileges to prevent excess permissions.       |

---

# Practice Exam Questions

**Q1.** You want to separate billing and administrative responsibilities for development, test, and production environments. What Azure feature is best suited for this?

A. Management Groups  
B. Azure Subscriptions  
C. Resource Groups  
D. Azure Policies  

*Correct Answer: B*

---

**Q2.** Your organization needs to isolate PCI-compliant workloads to ensure strict policy enforcement. What is the best way to isolate these workloads?

A. Use separate management groups for PCI workloads  
B. Use separate subscriptions for PCI workloads  
C. Assign all workloads under a single subscription and apply policies selectively  
D. Use resource groups within the same subscription  

*Correct Answer: B*

---

**Q3.** Which of the following is TRUE regarding Azure subscription limits and scale?

A. All workloads should be placed in a single subscription to simplify billing.  
B. Large or specialized workloads should be separated into multiple subscriptions to avoid hitting resource limits.  
C. Azure subscriptions have no limits and can scale infinitely.  
D. Resource groups are better suited for scaling than subscriptions.  

*Correct Answer: B*

---

**Q4.** Virtual networks are required to communicate between workloads in different subscriptions. How can this be achieved?

A. Using virtual network peering or VPN gateways  
B. By assigning the same IP address range in both subscriptions  
C. By deploying all workloads in the same subscription  
D. By using Azure Role-Based Access Control (RBAC)  

*Correct Answer: A*

---

**Q5.** What is an important governance practice for managing subscription owners?

A. Assign permanent owner roles without review  
B. Conduct regular access reviews with Microsoft Entra Privileged Identity Management  
C. Share subscription credentials among all team members  
D. Remove owners to avoid conflicts  

*Correct Answer: B*

---

Would you like a mind map or a cheat sheet for this topic as well?
