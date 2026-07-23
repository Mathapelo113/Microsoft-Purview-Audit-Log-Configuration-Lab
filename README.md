# Microsoft Purview Audit Log Configuration Lab

## Project Overview

This project demonstrates how to enable **Microsoft Purview Audit** logging within a Microsoft 365 environment. Microsoft Purview Audit provides centralized logging of user and administrator activities across Microsoft 365 services, enabling organizations to monitor activity, investigate security incidents, and meet compliance requirements.

This lab was completed as part of the **Microsoft Defender XDR Learning Path 3 – Lab 1 – Exercise 1**.

---

# Business Scenario

A healthcare organization is implementing **Microsoft Defender XDR** and **Microsoft Purview** to strengthen its security posture and comply with healthcare data protection regulations.

As a Security Operations Analyst, my responsibility was to enable Microsoft Purview Audit logging to ensure that user and administrator activities are captured for future investigations, compliance reporting, and forensic analysis.

---

# Objectives

- Access Microsoft Purview from Microsoft Defender XDR
- Navigate to the Audit solution
- Enable Unified Audit Logging
- Understand how audit logs support compliance and incident investigations
- Learn an alternative PowerShell method for enabling audit logging

---

# Technologies Used

- Microsoft Defender XDR
- Microsoft Purview
- Microsoft 365
- Exchange Online PowerShell
- Windows 11

---

# Skills Demonstrated

- Microsoft Purview Administration
- Microsoft 365 Security
- Compliance Monitoring
- Security Auditing
- Cloud Security
- Security Operations
- PowerShell Administration

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Platform | Microsoft Defender XDR |
| Compliance Platform | Microsoft Purview |
| Operating System | Windows 11 |
| PowerShell Module | ExchangeOnlineManagement |

---

# Implementation

## Step 1 – Open Microsoft Purview

From the Microsoft Defender XDR portal, I selected **More resources** and launched the Microsoft Purview portal.

### Screenshot

![More Resources](screenshots/01-more-resources.png)

---

## Step 2 – Microsoft Purview Portal

The legacy Microsoft Compliance Portal redirected to the new Microsoft Purview portal.

After accepting the privacy statement and data flow disclosure, the portal became available.

### Screenshot

![Microsoft Purview Portal](screenshots/02-microsoft-purview-portal-message.png)

---

## Step 3 – Navigate to Solutions

From the left navigation pane, I selected **Solutions**.

The Solutions page provides access to Microsoft Purview capabilities including:

- Audit
- eDiscovery
- Insider Risk Management
- Data Loss Prevention
- Information Protection

### Screenshot

![Solutions](screenshots/03-solutions.png)

---

## Step 4 – Open the Audit Solution

I selected **Audit** from the Solutions page.

The Audit solution allows administrators to search and investigate user and administrator activities occurring across Microsoft 365 services.

Examples include:

- User sign-ins
- File access
- Mailbox activity
- Permission changes
- Administrative actions

### Screenshot

![Audit](screenshots/04-audit.png)

---

## Step 5 – Enable Audit Logging

To begin collecting activity logs, I selected **Start recording user and admin activity**.

Enabling Unified Audit Logging allows Microsoft 365 to record security-relevant events across supported workloads.

These logs are commonly used during:

- Incident response
- Security investigations
- Compliance reporting
- Insider threat investigations
- Digital forensic investigations

### Screenshot

![Enable Audit Logging](screenshots/05-start-recording-user-and-admin-activity-bar.png)

---

# PowerShell Alternative

If the Audit button is unavailable or returns an error, Exchange Online PowerShell can be used.

## Install Exchange Online Module

```powershell
Install-Module ExchangeOnlineManagement
```

## Connect to Exchange Online

```powershell
Connect-ExchangeOnline
```

## Verify Audit Status

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

If the output returns:

```text
False
```

Audit logging is disabled.

## Enable Audit Logging

```powershell
Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
```

If prompted that organization customization has not been enabled:

```powershell
Enable-OrganizationCustomization
```

Run the enable command again:

```powershell
Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
```

## Confirm Audit Logging

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

Expected output:

```text
UnifiedAuditLogIngestionEnabled : True
```

## Disconnect

```powershell
Disconnect-ExchangeOnline
```

---

# Why Microsoft Purview Audit is Important

Microsoft Purview Audit provides organizations with centralized visibility into activities occurring across Microsoft 365 services.

Benefits include:

- Detecting suspicious activity
- Supporting security investigations
- Meeting compliance requirements
- Monitoring administrator actions
- Tracking user activity
- Providing forensic evidence during incident response

---

# Key Takeaways

- Successfully accessed Microsoft Purview through Microsoft Defender XDR.
- Navigated to the Audit solution.
- Enabled Unified Audit Logging.
- Learned how Microsoft 365 records user and administrator activities.
- Explored an alternative PowerShell method for enabling audit logging.
- Improved understanding of Microsoft Purview's role in compliance and security monitoring.

---

# Repository Structure

```
Microsoft-Purview-Audit-Logs-Lab/
│
├── README.md
│
├── screenshots/
│   ├── 01-more-resources.png
│   ├── 02-microsoft-purview-portal-message.png
│   ├── 03-solutions.png
│   ├── 04-audit.png
│   └── 05-start-recording-user-and-admin-activity-bar.png
│
└── LICENSE
```

---

# Learning Outcomes

Through this lab, I gained practical experience with Microsoft Purview Audit and learned how organizations enable audit logging to improve visibility into Microsoft 365 activity. I also explored the PowerShell method for configuring audit logging, reinforcing the importance of administrative automation and audit readiness in enterprise environments.

---

## Author

**Mathapelo Mlilo**

Aspiring SOC Analyst | IT Support Technician | Microsoft Security | CompTIA Security+ | Microsoft Sentinel | Microsoft Entra ID
