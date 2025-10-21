---
title: User Validation Playbook
description: Playbook for User validation in Finance and Operations
author: ianceicys-msft
ms.author: ceian
ms.topic: how-to
ms.date: 10/21/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.dyn365.ops.version: AX 7.0
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# User Validation Playbook

[!include [banner](../includes/banner.md)]

# User License Validation Playbook for Dynamics 365 Finance and Operations

This playbook helps administrators prepare for **per-user license validation** for Dynamics 365 Finance and Operations (F&O) apps. Follow these steps to ensure compliance, align licensing with security roles, and prevent user access disruptions when license validation goes into affect.

---

## Before You Start

Before you begin, confirm the following prerequisites are in place:

- ✅ You have **System Administrator** access in Dynamics 365 Finance and Operations.  
- ✅ You have **Power Platform Administrator** or **Global Administrator** permissions in the **Power Platform admin center (Power Platform admin center)**.  
- ✅ You can access the **Microsoft 365 Admin Center** for license assignment.  
- ✅ You have upgraded to the **latest Quality Update** (see Step 0).  
- ✅ You understand your organization’s licensing agreement, including base and attach license structure.  
- ✅ You have the correct roles enabled to generate User Security Governance and Power Platform admin center reports.

For additional context, review the [Dynamics 365 Licensing Guide](https://www.microsoft.com/en-us/licensing/product-licensing/dynamics365?culture=en-us&country=us) before proceeding.

---

## Step 0: Upgrade to the Latest Proactive Quality Update

Upgrade your environments to ensure all licensing reports and validation logic are available.

> **Required minimum version:**  
> - **Application version:** 10.0.45 (10.0.2345.86 or later)  
> - **Platform update:** ProductUpdate69  
> - **Platform build:** 7.0.7690.75  
> - **Product build:** 10.0.2345.86  

Upgrading ensures the **User Security Governance (User Security Governance)** reports and license validation functionality are up to date.

---

## Step 1: Remove Inactive User Accounts

Remove inactive users who no longer require access to reduce license consumption.

### Identify Inactive Users
Use the **User Activity Aging Report** in the **User Security Governance (User Security Governance)** workspace.

> **Path:** `System Administration > Security > Security Governance > User Activity Aging Report`

### Why This Matters
Inactive users consume licenses unnecessarily and can trigger false compliance warnings. Removing them simplifies true-up and reservation planning.

---

## Step 2: Familiarize Yourself with the Licensing Model

Understand how roles, duties, and privileges map to licenses.

Review the most current [Dynamics 365 Licensing Guide](https://www.microsoft.com/en-us/licensing/product-licensing/dynamics365?culture=en-us&country=us).

Knowing license entitlements for each product (Finance, Supply Chain, Commerce, HR, Project Operations) ensures your compliance strategy aligns with Microsoft’s model.

---

## Step 3: Review User Role and License Mapping

### Where to Review
You can review and cross-check mappings through:
- **Power Platform admin center (Power Platform admin center)**
- **Lifecycle Services (Lifecycle Services)**
- **User Security Governance (User Security Governance)** reports within F&O

### Power Platform Admin Center
Go to:  
[Power Platform Admin Center – License Reporting](https://admin.powerplatform.microsoft.com/billing/licenses/financeAndOperations)

Each product card (Finance, Commerce, Supply Chain, HR, Project Operations) displays:

| Category | Description |
|-----------|--------------|
| **Total users requiring a license** | Users with roles that require a license |
| **Base and attach licenses** | Purchased vs. assigned licenses |
| **Commerce / Finance / SCM** | Roles mapped to these license types |
| **HR / Project Operations** | Roles tied to HR or project-related duties |

> ⚠️ **Important:**  
> - Users shown in **“Total users requiring a license”** will **lose access** when validation starts if they don’t have a license assigned.  
> - Unassigned licenses in your pool **do not automatically cover users**; each user must have a license explicitly assigned.

You can **export reports to CSV** for internal review and audit tracking.

---

## Step 4: Validate with User Security Governance Reporting

Cross-verify license assignments in F&O using the **User Security Governance (User Security Governance)** workspace.

> **Path:** `System Administration > Security > Security Governance > License Usage Summary Report`

### What You’ll See
The **License Usage Summary** report provides a breakdown by:
- User  
- User role license  
- Role, duty, and privilege  
- License type (Entitled / Not Entitled / Not Required)

### Why It Matters
This helps you:
- Detect unnecessary entitlements  
- Identify privileges that elevate users to higher-tier licenses  
- Optimize role assignments and ensure compliance  

### Related Reports

| Report | Path | Purpose |
|---------|------|---------|
| **Security Analysis** | `System Administration > Security > Security Governance > Security Analysis` | Identify privileges associated with a resource (AOT Name) and role |
| **Security Configuration** | `System Administration > Security > Security Configuration` | Revoke or modify privileges for a role |
| **License Usage Overview** | `System Administration > Security > Security Governance > License Usage Overview` | Identify which licenses grant each privilege |

---

## Step 5: Align License Assignments in Microsoft 365 Admin Center

All users must be assigned a valid Dynamics 365 license matching their role requirements.

### How to Assign
1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com/).  
2. Select **Users** > **Active users**.  
3. Choose a user and select **Licenses and Apps**.  
4. Assign the appropriate Dynamics 365 license (Finance, Commerce, SCM, HR, Project Ops, Team Member, or Attach).  

> **Tip:** If a user triggers multiple licenses, assign the **base** license first, then attach additional ones as required.

If you lack sufficient licenses, purchase or reserve additional seats before validation goes into affect.

---

## Step 6: Plan for Additional Licensing

### License Reservations and True-Ups
License Reservations help ensure capacity ahead of per-user license validation.

Reservations are commitments that take effect during your **True-Up** or annual order cycle.

#### Key Points
- Can be scheduled for **current or future usage** (up to 6 months ahead)  
- Cancellable within **72 hours** of start date  
- Must be made **at least 30 days** before agreement anniversary  

#### How to Reserve
1. In the **Microsoft 365 Admin Center**, go to **Billing > Your products > Volume licensing**.  
2. Select **Make reservations**.  
3. Choose your **Enterprise Agreement**.  
4. Pick a **Usage Date** and click **View services**.  
5. Select **Add services** and specify usage details (country, license quantity).  
6. Review and confirm to **Place Reservation**.

For more details, visit [License Reservations FAQ | Microsoft Learn](https://learn.microsoft.com/).

---

## Summary Checklist

| Step | Action | Tool |
|------|---------|------|
| 0 | Upgrade to latest Quality Update | Lifecycle Services |
| 1 | Remove inactive users | User Security Governance Activity Aging Report |
| 2 | Review licensing model | Dynamics 365 Licensing Guide |
| 3 | Review user-role mapping | Power Platform admin center / Lifecycle Services / User Security Governance |
| 4 | Validate license triggers | F&O User Security Governance Reports |
| 5 | Align license assignments | M365 Admin Center |
| 6 | Plan additional licenses | M365 Admin Center / Volume Licensing |

---

## Frequently Asked Questions (FAQ)

### Q1. Does this validation apply to ISV or third-party licenses?
No. Per-user license validation applies to **Dynamics 365 F&O licenses only**. ISV or custom module licenses are not currently part of the validation scope.

### Q2. How can I tell which roles trigger which licenses?
Use the **User Security Governance License Usage Summary Report** to view each privilege’s license requirement and entitlement.  
Alternatively, refer to the **Power Platform Admin Center** license reporting view for high-level summaries.

### Q3. Can I renew or purchase licenses in advance?
Yes. Depending on your **CSP or Enterprise Agreement**, licenses can be renewed or reserved in advance through the Microsoft 365 Admin Center or your licensing partner.

### Q4. Will sandbox environments be included?
Yes. Sandbox and production environments are both monitored, but license validation checks only apply on **production environments**.

---

## Additional resources

For information about how to buy and license finance and operations apps, see [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&amp;clcid=0x409).

For information about how to assign licenses to users in the Microsoft 365 admin center, see [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

More user licenses are required when multiple implementation projects exist for the same tenant. For more information, see [Multiple Lifecycle Services projects and production environments on one Microsoft Entra tenant](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md#licensing-requirements).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
