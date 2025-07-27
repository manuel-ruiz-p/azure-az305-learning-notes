# AZ-305: Design for Azure Landing Zones

---

## What is an Azure Landing Zone?

- An Azure landing zone is a **pre-configured infrastructure environment** designed to host your workloads.
- It ensures **foundational principles** like networking, identity, access management, policies, and monitoring are in place **before** deploying services.
- Analogy: Like city utilities (water, gas, electricity) ready before building homes, landing zones prepare the cloud “utilities” for workloads.

---

## Key Characteristics

- Composed of **management groups** and **subscriptions** designed to scale with business needs.
- Azure policies are **associated with landing zones** to maintain compliance.
- Landing zones are **provisioned through code** (Infrastructure as Code).
- Designed to support both **application migrations** and **development at scale** across the organization.
- The **Azure landing zone accelerator** is a portal-based tool to deploy a landing zone into an existing Microsoft Entra tenant.

---

## Planning and Best Practices

- **Include landing zones** in your Azure infrastructure design for governance and scaling.
- Use **subscriptions as management units** aligned with business priorities.
- **Apply Azure Policy** as guardrails for compliance across workloads.
- **Pre-provision landing zones with code**, using iterative approaches and central IT review to reduce refactoring.
- Use the **Azure landing zone accelerator** for a fully implemented conceptual architecture with opinionated configurations.
- **Focus on applications**, favoring application-centric migrations and development rather than just infrastructure lift-and-shift.
- Align your design with **Azure-native platform services** and the Azure roadmap.
- Scope landing zones for **both migrations and greenfield development**, enabling long-term scalability.
- Transition existing Azure architectures by deploying landing zones in parallel without disrupting current environments.

---

## Additional Notes

- Conduct an **Azure landing zone review** to assess readiness for cloud migration or new workload deployments.
- Recommended for customers with **2+ years Azure experience**.
- Helps identify **investment areas** for adoption strategy and optimize cloud readiness.

---

## Summary Table

| Aspect                  | Details                                         |
|-------------------------|------------------------------------------------|
| Purpose                 | Ready cloud infrastructure environment          |
| Components              | Management groups, subscriptions, policies      |
| Provisioning            | Infrastructure as Code, Azure landing zone accelerator |
| Governance              | Azure Policy guardrails                           |
| Focus                   | Application-centric migration and development    |
| Scalability             | Designed to scale with business needs           |
| Transition Approach     | Parallel deployment alongside existing setups    |

---

## Practice Exam Questions

**Q1.** What is the main purpose of an Azure landing zone?

A. To deploy virtual machines quickly  
B. To provide a pre-configured, scalable infrastructure environment  
C. To replace on-premises servers  
D. To create user accounts  

*Correct Answer: B*

---

**Q2.** Which tool can you use to deploy a full implementation of Azure landing zones with opinionated configurations?

A. Azure CLI  
B. Azure landing zone accelerator  
C. Azure Policy Builder  
D. Azure Monitor  

*Correct Answer: B*

---

**Q3.** What is a best practice when provisioning Azure landing zones?

A. Provision manually through the Azure portal  
B. Use Infrastructure as Code and an iterative approach  
C. Avoid using management groups  
D. Assign roles only at the subscription level  

*Correct Answer: B*

---

**Q4.** How should Azure landing zones be scoped for an organization?

A. Only for greenfield developments  
B. Only for lift-and-shift migrations  
C. To support both migrations and greenfield development at scale  
D. To support only small workloads  

*Correct Answer: C*

---

**Q5.** What is recommended for organizations with existing Azure environments wanting to adopt landing zones?

A. Completely replace existing management groups immediately  
B. Deploy landing zones in parallel with the current environment  
C. Stop all workloads before migrating to landing zones  
D. Use landing zones only for new subscriptions  

*Correct Answer: B*

---

Want diagrams or detailed flashcards on Azure landing zones? Just ask!
