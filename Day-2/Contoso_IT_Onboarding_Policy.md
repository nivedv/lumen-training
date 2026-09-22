# Contoso IT Onboarding Policy
## New Employee IT Setup & Access Guide

**Document Owner:** IT Operations Team  
**Version:** 3.2  
**Last Updated:** March 2025  
**Applicable To:** All new employees joining Contoso

---

## 1. Overview

This document outlines all IT-related policies, procedures, and setup requirements for new employees joining Contoso. All new hires in the IT department are required to complete the steps in this guide within their first five business days. Employees in other departments should work through Section 2 (Standard Onboarding) and contact the IT Help Desk for any additional support.

---

## 2. Standard IT Onboarding (All Employees)

Every new Contoso employee, regardless of department, must complete the following IT setup steps before they can access company systems.

### 2.1 Laptop Collection

- Laptops are available for collection from the **IT Help Desk, Floor 2, Building A**
- Collection hours: Monday–Friday, 8:30 AM – 5:30 PM
- Bring your **Contoso employee ID** and **signed equipment agreement form** (provided in your welcome pack)
- Laptops come pre-configured with standard applications including Microsoft 365, Teams, and the VPN client
- If you have a hardware preference (Mac vs. Windows), raise a request via the IT Self-Service Portal at least 5 business days before your start date

### 2.2 Corporate Email Setup

- Your Contoso email address follows the format: `firstname.lastname@contoso.com`
- Login credentials are sent to your personal email address 24 hours before your start date
- First-time login requires password reset — follow the instructions in the welcome email
- Multi-factor authentication (MFA) is mandatory and must be set up during first login
- Supported authenticator apps: Microsoft Authenticator (preferred), Google Authenticator

### 2.3 Microsoft 365 Account Activation

All employees receive access to the full Microsoft 365 suite:

| Application | Purpose |
|------------|---------|
| Outlook | Corporate email and calendar |
| Teams | Collaboration, messaging, video calls |
| SharePoint | Document storage and internal sites |
| OneDrive | Personal cloud storage (1 TB) |
| Word, Excel, PowerPoint | Productivity applications |
| Power BI | Reporting (IT and Finance teams — standard licence) |

To activate your M365 account, visit [office.com](https://office.com) and sign in with your Contoso email credentials.

### 2.4 VPN Setup

Contoso uses **Cisco AnyConnect VPN** for secure remote access.

**Setup Instructions:**
1. The VPN client is pre-installed on your Contoso laptop
2. Open Cisco AnyConnect from your applications
3. Enter the server address: `vpn.contoso.com`
4. Sign in with your Contoso email and password
5. Complete the MFA challenge on your authenticator app
6. You are now connected — you will see the Contoso network icon in your taskbar

**VPN Policy:**
- VPN connection is mandatory when accessing any internal system from outside the office
- VPN sessions timeout after 8 hours of inactivity — you will need to reconnect
- Personal devices may connect to VPN only with prior approval from the IT Security team
- Split tunnelling is disabled — all traffic routes through the VPN when connected

**Troubleshooting Common VPN Issues:**
- *Error: Authentication failed* — Ensure MFA is fully set up. Reset via the IT Self-Service Portal
- *Error: Server unreachable* — Check your internet connection. Contact IT Help Desk if issue persists
- *Slow connection on VPN* — Raise a ticket via the IT Self-Service Portal with your location and time of issue

---

## 3. System Access Requests

### 3.1 Standard Access

Standard system access is provisioned automatically for all new employees based on their role and department within **2 business days** of their start date. Standard access includes:

- Corporate email and M365
- Contoso intranet and SharePoint
- HR self-service portal (Workday)
- Learning management system (Contoso Academy)
- IT Help Desk ticketing system (ServiceNow)

### 3.2 Additional Access Requests

For access to systems not included in standard provisioning:

1. Log into the **IT Self-Service Portal**: `itsupport.contoso.com`
2. Click **"Request Access"**
3. Select the system from the catalogue
4. Provide business justification
5. Your manager will receive an approval request via email
6. Access is provisioned within **3 business days** of manager approval

**High-Privilege Access** (admin rights, production systems, security tools) requires additional approval from the department head and CISO team. Processing time: up to 5 business days.

### 3.3 Access Review Policy

- All system access is reviewed every **90 days** for IT department employees
- All other employees: access reviewed every **180 days**
- Access is automatically revoked upon employee offboarding
- Unused access rights inactive for more than 60 days are suspended pending review

---

## 4. IT Department Specific Onboarding

The following section applies specifically to employees joining the **IT department**.

### 4.1 IT Team Structure

The IT department at Contoso is organised into the following teams:

| Team | Function |
|------|----------|
| IT Operations | Infrastructure, servers, networks, and data centres |
| IT Security | Cybersecurity, compliance, SIEM, vulnerability management |
| Application Engineering | Application development, APIs, integrations |
| Service Desk | L1/L2 support, ITSM, ticket management |
| Data & Analytics | Data engineering, BI, AI platforms |
| IT Architecture | Enterprise architecture, cloud strategy |

### 4.2 Development Environment Setup

Employees joining development or engineering roles will receive:

- **Admin rights** on their local device (requires CISO sign-off)
- Access to **GitHub Enterprise** (raised separately via IT Self-Service Portal)
- Development VM provisioned within 3 business days (spec based on role)
- Azure DevOps access for CI/CD pipelines
- Docker and Kubernetes tooling pre-installed on dev VMs

**Approved IDEs:**
- Visual Studio Code (standard)
- Visual Studio 2022 (on request)
- JetBrains IntelliJ / Rider (on request, licence required)
- PyCharm Professional (on request, licence required)

To request an IDE licence, raise a ticket in ServiceNow under **"Software Request"**.

### 4.3 Security Tools Access

IT Security team members will be onboarded to the following platforms:

| Tool | Purpose | Access Request |
|------|---------|----------------|
| Microsoft Sentinel | SIEM and SOAR | Via IT Self-Service Portal + CISO approval |
| Defender for Endpoint | Endpoint protection | Standard provision for IT Security team |
| Qualys | Vulnerability scanning | Via IT Self-Service Portal |
| Splunk | Log analysis | Via IT Self-Service Portal + Team Lead approval |
| CrowdStrike | Threat detection | Via IT Self-Service Portal + CISO approval |

### 4.4 First Week Schedule — IT Department

| Day | Activity |
|-----|----------|
| Day 1 | Laptop collection, credentials setup, MFA, team meeting |
| Day 2 | Systems access provisioning, IT tools walkthrough, meet IT buddy |
| Day 3 | Shadow your team lead — attend standups and key meetings |
| Day 4 | Complete mandatory security awareness training (2 hours, in LMS) |
| Day 5 | 1:1 with your manager — discuss 30/60/90 day plan |

---

## 5. IT Policies — Quick Reference

### 5.1 Acceptable Use Policy

- Company devices are for business use. Reasonable personal use is permitted but monitored.
- You must not install unlicensed software on company devices
- Access to prohibited websites (adult content, gambling, piracy) is blocked and logged
- Saving company data to personal cloud storage (personal Google Drive, Dropbox) is **prohibited**
- Sensitive data must be stored only in approved Contoso systems (SharePoint, OneDrive for Business)

### 5.2 Password Policy

| Requirement | Standard |
|-------------|---------|
| Minimum length | 14 characters |
| Complexity | Upper, lower, number, and special character |
| Expiry | 90 days (IT staff), 180 days (all other staff) |
| Password reuse | Last 12 passwords cannot be reused |
| Failed attempts | Account locked after 10 failed attempts |

Password resets can be performed via the self-service portal at `account.contoso.com` or by contacting the IT Help Desk.

### 5.3 Data Classification Policy

All data handled by employees must be classified and handled accordingly:

| Classification | Examples | Handling |
|---------------|---------|---------|
| **Public** | Press releases, public website | No restrictions |
| **Internal** | Internal communications, project docs | Store in SharePoint, do not share externally without approval |
| **Confidential** | HR data, financial data, customer data | Encrypt, share on need-to-know basis only |
| **Restricted** | Security keys, credentials, trade secrets | Encrypted storage only, strict access controls, logged access |

### 5.4 Incident Reporting

Security incidents must be reported **immediately** (within 30 minutes of detection):

1. Call the **IT Security Hotline: 0800-CONTOSO-SEC** (available 24/7)
2. Raise a P1 ticket in ServiceNow under **"Security Incident"**
3. Do not attempt to remediate the incident yourself before reporting
4. Preserve all evidence — do not restart or wipe affected systems
5. Inform your direct manager

Examples of reportable incidents: phishing emails clicked, malware detected, unauthorised access attempt, lost/stolen device, accidental data exposure.

---

## 6. IT Help Desk Contact

| Channel | Details | Hours |
|---------|---------|-------|
| **Phone** | 0800-CONTOSO-IT | Mon–Fri 7:00 AM – 9:00 PM |
| **Teams** | @ITHelpDesk (company Teams) | Mon–Fri 8:00 AM – 6:00 PM |
| **Portal** | itsupport.contoso.com | 24/7 (P1/P2 alerts monitored out of hours) |
| **Walk-in** | Floor 2, Building A | Mon–Fri 9:00 AM – 5:00 PM |
| **Emergency** | Security Hotline: 0800-CONTOSO-SEC | 24/7 |

**SLA Targets:**

| Priority | Description | Response Time | Resolution Target |
|---------|-------------|--------------|------------------|
| P1 — Critical | Production outage, security incident | 15 minutes | 4 hours |
| P2 — High | Key system degraded, multiple users impacted | 1 hour | 8 hours |
| P3 — Medium | Single user issue, workaround exists | 4 hours | 2 business days |
| P4 — Low | General enquiry, new access request | 1 business day | 5 business days |

---

## 7. Frequently Asked Questions

**Q: How long does it take to get my laptop ready?**  
A: Laptops are pre-configured and available for collection from Day 1. If you have a specific hardware request, submit it at least 5 business days in advance.

**Q: I forgot my password and can't log in. What do I do?**  
A: Use the self-service password reset at `account.contoso.com`. If MFA is also inaccessible, call the IT Help Desk on 0800-CONTOSO-IT with your employee ID ready.

**Q: Can I use my personal phone for MFA?**  
A: Yes. Download Microsoft Authenticator on your personal device and enrol it via the account settings portal.

**Q: Can I install my own development tools?**  
A: Approved tools only. Use the IT Self-Service Portal under "Software Request" to request any tools not pre-installed. Unlicensed or unapproved software is a policy violation.

**Q: How do I request admin rights on my device?**  
A: Raise a request via IT Self-Service Portal. Admin rights require CISO approval and are typically reserved for IT staff with a documented business need.

**Q: What happens to my access when I leave the company?**  
A: All access is automatically revoked on your last day. You will receive a deprovisioning notification from IT 5 days before your last day.

**Q: Is there a test or sandbox environment for learning?**  
A: Yes — the Contoso Dev Sandbox is available for all IT staff. Request access via the IT Self-Service Portal under "Dev Environment Access."

---

*Contoso IT Onboarding Policy | Version 3.2 | IT Operations Team*  
*For questions: itops@contoso.com | itsupport.contoso.com*
