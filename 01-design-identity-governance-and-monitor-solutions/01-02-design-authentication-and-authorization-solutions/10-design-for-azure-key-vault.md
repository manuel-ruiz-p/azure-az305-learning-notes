
# Design for Azure Key Vault 

Storing and managing secrets, encryption keys, and certificates directly in application code or configuration is risky and increases the chance of accidental exposure. **Azure Key Vault** is a cloud service designed to securely store and control access to sensitive information such as tokens, passwords, encryption keys, and certificates.

## What Is Azure Key Vault?

Azure Key Vault helps organizations protect cryptographic keys and secrets used by cloud applications and services. It enables centralized management of sensitive data, reduces risks, and enhances security posture by integrating tightly with Azure security controls.

### Key Vault Capabilities:

* **Secret Management:** Secure storage and fine-grained access control for application secrets like passwords, API keys, connection strings, and tokens.
* **Key Management:** Create, import, rotate, and control encryption keys used to encrypt data. Supports both software-protected keys and hardware security module (HSM)-protected keys.
* **Certificate Management:** Simplifies enrollment, management, and deployment of TLS/SSL certificates for both Azure and on-premises resources.

## Key Vault Service Tiers

| Tier     | Features                                      | Use Cases                                        |
| -------- | --------------------------------------------- | ------------------------------------------------ |
| Standard | Software-based encryption keys                | Typical app secrets and keys                     |
| Premium  | Hardware Security Module (HSM)-protected keys | High security scenarios, compliance requirements |

## Benefits of Azure Key Vault

* **Centralized Secrets Storage:** Secrets are stored securely and managed in a central location, reducing the risk of accidental leaks.
* **Separation of Duties:** Customers control their keys and secrets without embedding them in apps, reducing liability.
* **Access Policies and RBAC:** Control access tightly by defining who or what can access specific secrets, keys, and certificates.
* **Logging and Monitoring:** Audit access through Azure Activity Logs and Azure Monitor to track usage and detect anomalies.
* **Built-in Integration:** Easily integrate with Azure services and your own applications without writing extensive custom security code.

## Best Practices When Using Azure Key Vault

### 1. Separate Key Vaults by Application or Environment

* Define security boundaries to reduce the blast radius in case of compromise.
* Segregate secrets based on app sensitivity, environment (dev/test/prod), or team ownership.

### 2. Use Access Policies and Least Privilege

* Grant only necessary permissions to applications and users.
* Use managed identities for Azure services to simplify secure access without credentials.

### 3. Secure Network Access

* Enable firewall rules and Virtual Network Service Endpoints to restrict Key Vault access to authorized networks.

### 4. Enable Soft Delete and Purge Protection

* **Soft Delete:** Prevents accidental deletion by retaining deleted vaults and objects for a configurable retention period, like a recycle bin.
* **Purge Protection:** Prevents malicious or accidental permanent deletion, enforcing a retention lock on deleted vaults and secrets.

### 5. Integrate with Azure Managed Identities

* Use managed identities for seamless and secure access to Key Vault from Azure resources without managing credentials.

---

# AZ-305 Style Exam Questions

```markdown
### Q1:  
**Which Azure Key Vault service tier provides hardware security module (HSM) protected keys?**

- A) Basic  
- B) Standard  
- C) Premium  
- D) Enterprise  

**Answer:** C) Premium

---

### Q2:  
**What is the primary benefit of enabling soft delete on an Azure Key Vault?**

- A) It enables encryption of keys using software-based keys.  
- B) It prevents accidental deletion by retaining deleted vaults and objects for a retention period.  
- C) It restricts Key Vault access to specific virtual networks.  
- D) It automatically rotates secrets on a scheduled basis.  

**Answer:** B) It prevents accidental deletion by retaining deleted vaults and objects for a retention period.

---

### Q3:  
**Which method is recommended to provide secure access for an Azure App Service to retrieve secrets from Azure Key Vault?**

- A) Store the Key Vault credentials in app settings.  
- B) Use a managed identity assigned to the App Service.  
- C) Use a shared access signature (SAS) token.  
- D) Embed the vault access keys in the application code.  

**Answer:** B) Use a managed identity assigned to the App Service.

---

### Q4:  
**How can you reduce the blast radius in case of a Key Vault security breach?**

- A) Store all secrets for all applications in a single Key Vault.  
- B) Separate Key Vaults by application or environment to define security boundaries.  
- C) Disable firewall and virtual network service endpoints.  
- D) Share user-assigned managed identities across all applications.  

**Answer:** B) Separate Key Vaults by application or environment to define security boundaries.

---

### Q5:  
**What does purge protection in Azure Key Vault do?**

- A) Automatically encrypts all stored secrets with HSM.  
- B) Prevents the permanent deletion of vaults and objects, even after soft delete.  
- C) Allows immediate recovery of deleted vaults without retention periods.  
- D) Enables logging of all secret retrievals from the vault.  

**Answer:** B) Prevents the permanent deletion of vaults and objects, even after soft delete.
