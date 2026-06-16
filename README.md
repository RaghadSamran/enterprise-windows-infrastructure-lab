# Enterprise Windows Infrastructure Lab (Azure)

A hands-on enterprise IT infrastructure lab deployed on Microsoft Azure, simulating a real-world corporate environment with Windows Server 2022, Active Directory Domain Services, DNS, DHCP, Group Policy, and identity lifecycle management.

---

## Architecture

```text
Azure Resource Group (IT-Infrastructure-Lab)
                |
       Windows Server 2022
           (DC-Server)
                |
    -------------------------
    |            |          |
   AD DS        DNS        DHCP
                |
       OUs / Users / Groups
                |
    Shared Folders + GPOs
```

---

## Lab Environment

| Component | Details |
|---|---|
| Platform | Microsoft Azure |
| Server OS | Windows Server 2022 Datacenter (Azure Edition) |
| VM Size | Standard D2s v7 (2 vCPUs, 8 GB RAM) |
| Domain | company.local |
| Domain Controller | DC-Server |

---

## What Was Built

### Phase 1 — Azure VM Deployment
- Deployed Windows Server 2022 on Microsoft Azure
- Configured RDP access, Standard SSD storage, and networking
- Created resource group: IT-Infrastructure-Lab

### Phase 2 & 3 — Server Roles Installation
- Installed Active Directory Domain Services (AD DS)
- Installed DNS Server and DHCP Server
- Promoted DC-Server to Domain Controller for a new forest (company.local)

### Phase 4 — Organizational Structure
- Created 3 Organizational Units: IT, HR, Operations
- Created 6 domain users across departments
- Created 3 security groups: IT-Group, HR-Group, Operations-Group
- Assigned users to their respective department groups

### Phase 5 — Group Policy Configuration
Created a domain-wide Security-Policy GPO enforcing:
- Minimum password length: 8 characters
- Password complexity: Enabled
- Account lockout threshold: 3 failed attempts
- Account lockout duration: 10 minutes
- Screen lock timeout: 3 minutes with password protection

### Phase 6 — Identity Lifecycle Management
Demonstrated full user provisioning workflow:
- Created new user (Nora Salem) in HR department
- Added user to HR-Group (access granted)
- Removed user from HR-Group (access revoked)
- Disabled user account (offboarding complete)

### Phase 7 — Shared Folder Permissions
- Created department shared folders: IT, HR, Operations
- Configured share permissions restricted to respective security groups
- Demonstrated role-based access control (RBAC) in practice

### Phase 8 — Troubleshooting: Account Lockout Investigation
- Investigated repeated failed logon attempts using Windows Event Viewer (Event ID 4625)
- Identified the locked account in Active Directory Users and Computers
- Restored access through account management and documented remediation steps

---

## Technologies Used

- Microsoft Azure (Cloud Infrastructure)
- Windows Server 2022
- Active Directory Domain Services (AD DS)
- DNS Server
- DHCP Server
- Group Policy Management (GPMC)
- Windows Event Viewer
- Remote Desktop Protocol (RDP)

---

## Key Skills Demonstrated

- Cloud infrastructure deployment (Azure)
- Windows Server administration
- Active Directory design and management
- Group Policy configuration and enforcement
- Role-Based Access Control (RBAC)
- Identity and Access Management (IAM)
- User lifecycle management
- File share permissions management
- Security event investigation and troubleshooting

---

## Screenshots

Screenshots are organized by phase in the `/screenshots` folder.

---

## Limitations

Due to Windows 11 Home ARM edition limitations on Apple Silicon, a domain-joined client workstation was not implemented. Core Active Directory services, Group Policy configuration, user management, authentication workflows, and account administration were successfully deployed and validated on the domain controller.
