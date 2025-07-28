
# Design Managed Identities 

Managing secrets, credentials, and authentication is a critical challenge in cloud-native applications. Azure Managed Identities solve this by providing automatically managed identities in Microsoft Entra ID that eliminate the need for developers to handle credentials directly.

## What Are Managed Identities?

Managed Identities are a feature of Microsoft Entra ID that create an identity for Azure services and applications, allowing them to authenticate securely to Azure resources without embedding credentials in code or configuration files. This identity can be used to acquire tokens from Microsoft Entra ID to access supported resources such as Azure Key Vault, Azure Storage, Azure SQL Database, and more.

* **Cost:** Managed identities are provided free of charge.
* **Availability:** Supported across all Microsoft Entra ID editions and widely supported Azure services.
* **Configuration:** Minimal setup required, especially with Azure App Service and Azure VMs.

## Types of Managed Identities

### 1. System-Assigned Managed Identity

* **Lifecycle tied to the Azure resource:** When the resource is deleted, the identity is deleted automatically.
* **Unique to a single resource:** Only that resource can use the identity to request tokens.
* **Ideal use cases:** Single-resource applications like a single VM, App Service, or Function needing to authenticate securely.

### 2. User-Assigned Managed Identity

* **Created as a standalone Azure resource:** Can be assigned to multiple Azure service instances.
* **Independent lifecycle:** Remains even if the resource is deleted, allowing reuse and consistent permissions.
* **Ideal use cases:** Multiple resources sharing the same identity, workloads with resource recycling, or preauthorized secure resource access scenarios.

## Benefits of Using Managed Identities

* **Eliminates credential management:** No need to store or rotate credentials manually.
* **Improves security:** Credentials are never exposed in code or config files.
* **Integrates seamlessly with Azure RBAC:** Access to resources is managed with Azure role-based access control.
* **Logging and auditing:** Authentication and activity logs are available via Azure Activity logs and Microsoft Entra sign-in logs.
* **Flexible enabling/disabling:** Can enable or disable managed identities at any time per resource.

## Common Azure Services Supporting Managed Identities

| Azure Service             | Supports Managed Identity?                      |
| ------------------------- | ----------------------------------------------- |
| Azure Virtual Machines    | Yes (System-assigned & User-assigned)           |
| Azure App Service         | Yes (System-assigned & User-assigned)           |
| Azure Functions           | Yes                                             |
| Azure Kubernetes Service  | Yes                                             |
| Azure Logic Apps          | Yes                                             |
| Azure Container Instances | Yes                                             |
| Azure Storage             | Yes (via Microsoft Entra authentication tokens) |
| Azure SQL Database        | Yes                                             |
| Azure Key Vault           | Yes (primary use case for secret access)        |

## Best Practices When Designing Managed Identities

* **Use system-assigned managed identities for simple, single-resource scenarios.** This reduces management overhead because identities are automatically created and cleaned up with the resource.
* **Use user-assigned managed identities for complex scenarios requiring identity sharing or pre-provisioning.** This allows multiple resources to authenticate as the same identity, simplifying permission management.
* **Leverage Azure Key Vault for secret storage.** Use managed identities to authenticate your apps to Key Vault, avoiding hard-coded secrets or credentials.
* **Apply least privilege access with RBAC.** Assign only the minimum roles necessary to the managed identities to reduce security risks.
* **Audit and monitor activity.** Use Azure Activity Logs and Microsoft Entra sign-in logs to monitor authentication activity and resource access.

## Real-World Scenario: Tailwind Traders

Tailwind Traders plans to migrate their stock-tracking apps to Azure VMs. By assigning system-assigned managed identities to these VMs, their apps can securely retrieve secrets from Azure Key Vault without embedding credentials in their source code. This enhances security, simplifies secret management, and reduces operational overhead.

---

# AZ-305 Style Exam Questions

```markdown
### Q1:  
**Which statement best describes a system-assigned managed identity?**

- A) It is created as a separate Azure resource and can be assigned to multiple Azure services.  
- B) It is tied to the lifecycle of a specific Azure resource and is deleted when that resource is deleted.  
- C) It requires manual credential rotation by the developer.  
- D) It allows any Azure resource to share the same identity.  

**Answer:** B) It is tied to the lifecycle of a specific Azure resource and is deleted when that resource is deleted.

---

### Q2:  
**What are the primary benefits of using managed identities for Azure resources?**

- A) Eliminates the need to manage credentials and integrates with Azure RBAC for access control.  
- B) Allows developers to hardcode credentials safely in code.  
- C) Requires manual key rotation for enhanced security.  
- D) Grants access to Azure resources without any authentication tokens.  

**Answer:** A) Eliminates the need to manage credentials and integrates with Azure RBAC for access control.

---

### Q3:  
**Which managed identity type should you use when multiple Azure resources require the same identity and consistent access permissions?**

- A) System-assigned managed identity  
- B) User-assigned managed identity  
- C) Legacy service principal  
- D) Application service principal  

**Answer:** B) User-assigned managed identity

---

### Q4:  
**How does Azure Key Vault authenticate an app using managed identities?**

- A) The app sends its username and password stored in configuration to Key Vault.  
- B) The app requests a Microsoft Entra ID token via its managed identity and presents it to Key Vault for access.  
- C) The app uses a certificate stored on the local machine to access Key Vault.  
- D) Azure Key Vault does not support managed identity authentication.  

**Answer:** B) The app requests a Microsoft Entra ID token via its managed identity and presents it to Key Vault for access.

---

### Q5:  
**What happens to a system-assigned managed identity when the associated Azure VM is deleted?**

- A) The managed identity continues to exist and can be assigned to other resources.  
- B) The managed identity is deleted automatically along with the VM.  
- C) The managed identity is disabled but remains in Microsoft Entra ID.  
- D) The managed identity is converted into a user-assigned identity.  

**Answer:** B) The managed identity is deleted automatically along with the VM.
```

