# Azure RBAC & Governance Demo Project

##  Project Objective
This project demonstrates core Azure capabilities through subscription-level segmentation, role-based access control (RBAC), policy enforcement, and the deployment of a simple public-facing service (VM with NGINX).

It is designed as a practical scenario for beginners in Microsoft Azure and professionals exploring governance and multi-environment access models.

---

##  Azure Services Used
- Azure Active Directory (Azure AD)
- Azure Subscriptions
- Azure RBAC (IAM)
- Azure Policy
- Virtual Network (VNet)
- Network Security Group (NSG)
- Public IP
- Azure Virtual Machines (Ubuntu + NGINX)

---

##  Architecture Overview

###  Subscription Structure
- `DEV-Sub`
- `TEST-Sub`
- `PROD-Sub`

Each subscription is isolated and governed with its own policy scope.

###  User Groups and Access Rights (RBAC)

| Group              | DEV-Sub     | TEST-Sub    | PROD-Sub    |
|-------------------|-------------|-------------|-------------|
| Developers        | Contributor | Contributor | ❌ None     |
| QATesters         | ❌ None     | Contributor | ❌ None     |
| DevOpsEngineers   | Owner       | Owner       | Reader      |
| ProductManagers   | Reader      | Reader      | Reader      |

Each group consists of 2 individual users.

###  Azure Policy Assignments

| Subscription | Policy Type             | Example Policy                                     |
|--------------|--------------------------|---------------------------------------------------|
| DEV-Sub      | Allowed Locations        | Only `East US` is allowed for resource deployment |
| TEST-Sub     | Required Tags            | Enforce tags like `env=test`,                     |
| PROD-Sub     | Allowed Resource Types   | Only VM, NSG, and Public IP resources are allowed |

---

##  NGINX VM Deployment in Each Subscription

- Ubuntu 22.04 VM

```
  sudo apt update
  sudo apt install nginx -y
  sudo systemctl status nginx

```
- NSG rules for ports 22 (SSH) and 80 (HTTP)
- Accessed via browser using `http://<VM_Public_IP>`

---

##  Project Benefits
- Demonstrates Azure subscription governance
- Applies RBAC and policy enforcement in a real setup
- Ends with a working public service to verify setup

---

##  Suggested LinkedIn Hashtags
```
#Azure #CloudComputing #AzureRBAC #AzurePolicy #DevOps #MicrosoftAzure #CloudSecurity #NGINX #InfrastructureAsCode #Governance
```
