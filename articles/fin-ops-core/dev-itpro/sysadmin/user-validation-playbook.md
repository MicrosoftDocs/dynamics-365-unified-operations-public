---
title: User License Validation Playbook for Dynamics 365 Finance and Operations
description: Playbook for user license validation in Dynamics 365 Finance and Operations  
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

# Playbook for user license validation in Dynamics 365 Finance and Operations  

This playbook helps administrators prepare for **per-user license validation** for Dynamics 365 Finance and Operations (F&O) apps. It provides step-by-step guidance to align licensing with security roles, and prevent user access disruptions when per-user license validation goes into effect. Each step includes **Why**, **What**, and **How** explanations that are clear, actionable, and aligned to Microsoft licensing and security governance practices. Where appropriate, you’ll find tables that organize information such as license types, report paths, and validation outcomes. Use this playbook sequentially for best results, and repeat Steps 3–6 periodically as your security model and user base evolve.

---

## Before You Start

Confirm these prerequisites:

- ✅ **System Administrator access** in Dynamics 365 F&O  
- ✅ **Power Platform Admin or Global Admin permissions**  
- ✅ **Access to Microsoft 365 Admin Center**  
- ✅ **Upgrade to latest Quality Update** (see Step 1)  
- ✅ **Understand licensing agreements** (base vs. attach licenses)  
- ✅ **Enable User Security Governance reports** in Feature management

Review [Dynamics 365 Licensing Guide](https://www.microsoft.com/en-us/licensing/product-licensing/dynamics365?culture=en-us&country=us)

## Step 1: Upgrade to the Latest Quality Update (10.0.45)

**Why**  
Upgrading ensures your environment has the **current license validation logic, telemetry, and reporting** needed to make accurate decisions. New governance capabilities, including **User Security Governance (User Security Governance)**, were introduced and improved in recent versions and may not be available in older builds. Running the latest **Proactive Quality Update** reduces the risk of encountering known issues or missing features that affect license calculations or report completeness. This step also standardizes the behavior across all environments, so your analysis in test/sandbox mirrors what you’ll see in production. Most importantly, it ensures your admins can rely on up-to-date **License Usage Summary** and related reports to plan assignments confidently.

**What**  
You will verify and, if necessary, upgrade the **Application** and **Platform** versions for all relevant F&O environments. The minimum recommended is **Application 10.0.45 (10.0.2345.86+)** with **ProductUpdate69** and **Platform build 7.0.7690.75**. You’ll also ensure that the **User Security Governance** features (including the license usage reports) are enabled in **Feature management**. Once upgraded, you’ll validate access to the **Security Governance** workspace and its reports. This creates the foundation for the data you’ll use in subsequent steps.



**How**  
Use **Lifecycle Services (Lifecycle services)** to apply the latest Quality Update across all environments, prioritizing production and any sandboxes you use for validation. After the update, sign in to F&O and go to **System administration → Feature management**, search for “User security governance” and “User security governance license usage summary report,” and enable them. Then open **System administration → Security → Security governance** to confirm the **License usage summary**, **Security analysis**, and **License usage overview** reports are available. Document version numbers and feature flags for audit and change control. If you rely on automations or ISV solutions, coordinate testing to ensure compatibility with the updated platform.

---

## Step 2: Remove Inactive User Accounts

**Why**  
Inactive users distort license demand by appearing in reports as if they still need access, which can lead to **over-purchasing** or **false compliance warnings**. Cleaning up unused accounts ensures your **license requirement baseline** reflects reality, improving both cost control and audit readiness. It also reduces your administrative burden when assigning licenses and mitigates the risk of stale accounts being inadvertently reactivated. By removing or disabling inactive users now, you avoid unnecessary noise in later steps and keep your focus on truly active, business-critical users. This cleanup step is a fast win that immediately improves data quality and compliance posture.

**What**  
You will identify and deactivate (or remove) users who haven’t logged in within your organization’s defined inactivity windows. The **User Activity Aging** report in the **User Security Governance** workspace provides a configurable view of users grouped by inactivity ranges (e.g., 30, 60, 90, 120+ days). You’ll use those groupings to determine which accounts should be disabled or deleted, based on HR and IT policies. After actioning those accounts, you’ll refresh your high‑level license reports so the numbers reflect the leaner, active user set. Maintain a record of actions for audit and rollback if needed.

**How**  
In F&O, go to **System administration → Security → Security governance → User activity aging** to review current activity levels. Configure your day ranges under **System administration → Security → Security governance setup → Parameters → User aging periods** to align with policy (for example, 30/60/90/120 days). For each user beyond your threshold, go to **System administration → Users → Users** and set the user to **Disabled** (or remove, per policy). Communicate changes to business owners and HR, especially for users on leave or in role transitions. Re-run your license reports (Power Platform admin center/Lifecycle services and User Security Governance) to confirm reductions in “users requiring a license.”

---

## Step 3: Familiarize Yourself with the Licensing Model

**Why**  
F&O uses a **named user** model that ties **roles, duties, and privileges** to license requirements, so misunderstanding the model can result in **under-license risk** or **unnecessary spending**. Users who span functionality across **Finance**, **Supply Chain Management**, **Commerce**, **Human Resources**, and **Project Operations** may need multiple licenses (Base + Attach) to remain compliant. The **Team Members** and **Operations – Activity** licenses are designed for light or read‑only usage, but a single “write” privilege can escalate a user into a higher license tier. Knowing these nuances ensures that your security design aligns with the lowest correct license level for each persona. It also helps you explain decisions to stakeholders and withstand audits with confidence.

**What**  
You will review the current **Dynamics 365 Licensing Guide** to understand **entitlements, Base vs. Attach rules, and product‑specific coverage**. Specifically, identify what each license type covers at a functional level (e.g., which processes in Finance vs. SCM) and where overlaps occur. Capture a simple mapping between your **key business personas** and their **intended license types** based on responsibilities. Pay special attention to custom roles that may aggregate privileges across product boundaries, as these commonly lead to attach license needs. Align your understanding with your partner/seller to ensure shared definitions.

**How**  
Read the latest [Dynamics 365 Licensing Guide](https://www.microsoft.com/en-us/licensing/product-licensing/dynamics365 to F&O. Create a one‑page internal reference mapping **standard roles** (and your top 10–15 custom personas) to intended license tiers. Mark any areas where your current roles appear to exceed intended scope (e.g., unexpected write privileges) and flag them for remediation in Step 4. Socialize this cheat sheet with security owners and functional leads to build consensus before you assign—or buy—licenses. Keep the reference current as Microsoft updates guidance or as your roles evolve.

---

## Step 4: Review User Role and License Mapping (Power Platform admin center/Lifecycle services)

**Why**  
A high‑level license view across environments highlights **where supply doesn’t meet demand**—for example, too few Finance seats for the number of users needing Finance. This step is the fastest way to quantify **how many** of each license type you need to assign or acquire, and to identify users who lack any assigned license. It provides a **cross‑tenant picture** that complements the granular privilege analysis you’ll do inside F&O. By spotting shortfalls early, you can avoid last‑minute purchases, approval bottlenecks, and user lockouts when validation begins. You’ll also discover misallocations (e.g., licenses assigned to users who no longer need them) that can be reallocated to close gaps.

**What**  
You will use the **Power Platform admin center (Power Platform admin center)** “User License Consumption” reports for Finance and Operations to compare **Required vs. Purchased vs. Assigned** seats by product. The report shows **Total users requiring a license**, **base licenses** assigned/available, and **attach licenses** assigned/available per product (Finance, SCM, Commerce, HR, Project Ops, Team Members, Operations – Activity). You’ll drill down into **“Users with unassigned licenses”** to see exactly who is missing seats and which license type they need. You may also use **Lifecycle services** to cross‑check production counts and export the same CSV data if Power Platform admin center access is not available for certain admins. Exporting to CSV supports deeper analysis, filtering, and sharing with stakeholders.

**How**  
Open **Power Platform admin center → Licensing → Finance and Operations** and review the **product‑level license summaries**. Click **View details/View all** to see user‑level requirements and the **“Users with unassigned licenses”** list; use filters to focus on specific license types with shortages. Export the CSV and annotate gaps (e.g., “Need +9 Finance base,” “Need +3 SCM attach”), then route the findings to procurement or your Microsoft partner. If you don’t have Power Platform admin center access, open **Lifecycle services → Project → Environment → License report** and download the CSV to achieve a similar view for production. Keep this gap analysis handy—you will resolve it via role cleanup (Step 4) and license assignment/ordering (Steps 5–6).

> **Product cards show:**  
> - Total users requiring a license  
> - Base licenses: assigned vs. available to assign  
> - Attach licenses: assigned vs. available to assign  
> - Supported products include Finance, SCM, Commerce, HR, Project Ops, Team Members, Operations – Activity

---

## Step 5: Validate with User Security Governance (User Security Governance) in F&O

**Why**  
User Security Governance gives a **telemetry‑driven, privilege‑level** view of why a user needs a license, so you can surgically remove **unnecessary entitlements** and minimize costs. It exposes which **roles/duties/privileges** cause a user to escalate from Team Member to a full app license (or to need multiple apps), enabling targeted remediation. This inside‑the‑app validation complements Power Platform admin center’s top‑down counts by confirming the **root causes** of license requirements. Without this step, you risk assigning or purchasing licenses you could have avoided by right‑sizing roles. It’s also invaluable for audit and documentation—showing exactly how your security design maps to licensing rules.

**What**  
You will use **License usage summary** in F&O to analyze users by **license status** and drill into the **Role → Duty → Privilege** chain. You’ll focus on items labeled **Entitled** (covered), **Not Entitled** (requires higher/different license), and **Not Required** (no license impact). You’ll also leverage **Security analysis** to find where specific privileged entry points are introduced into roles, and **Security configuration** to adjust or remove them. If a privilege is truly required, you’ll confirm the correct **attach license** need and plan assignments accordingly. The goal is to align each persona with the **lowest correct** license level without blocking legitimate work.

**How**  
In F&O, navigate to **System administration → Security → Security governance → License usage summary** and filter to users or roles of interest. For users with unexpected license needs, drill down to **privileges** marked **Not Entitled** to understand which entry points cause the escalation. Use **Security analysis** to locate all roles that include the problematic entry point, then open **Security configuration** to adjust/remediate the role (e.g., remove write or high‑impact privileges for read‑only personas). Recalculate/refresh the report and verify that the user now aligns to the intended license tier; if not feasible, plan to assign the appropriate attach license in Step 5. Document changes and rationale for audit traceability.

**License Tags User Security Governance (User Security Governance)**

| License Tag     | Meaning                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------|
| **Entitled**    | Action/privilege is covered by the current license and doesn’t trigger a higher license. |
| **Not Entitled**| Action/privilege isn’t covered and requires a higher or different license to be compliant. |
| **Not Required**| Action/privilege has no license requirement (often basic/read‑only).                      |

**Related Reports & Tools**

| Report / Tool         | Path                                                                              | Purpose                                                                                                  |
|-----------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Security Analysis** | System Administration → Security → Security governance → **Security analysis**    | Identify privileges/entry points and all roles that include them; locate root causes of license needs.  |
| **Security Configuration** | System Administration → Security → **Security configuration**               | Adjust roles/privileges (e.g., remove high‑impact privileges) to right‑size license requirements.       |
| **License Usage Overview** | System Administration → Security → Security governance → **License usage overview** | Review privileges/duties by required license to guide remediation and role design.                      |

---

## Step 6: Align License Assignments in Microsoft 365 Admin Center

**Why**  
When license validation begins, **users without required licenses will be blocked** from signing in to F&O production environments. Assigning the right **Base and Attach** licenses in advance prevents business disruption, especially in period‑end finance, warehousing, and order processing. Relying on “available seats” without explicit assignment is insufficient—licenses must be **assigned to each user** to be recognized. Timely assignments also reduce support load from end‑user warnings and avoid emergency escalations to procurement or IT. Completing assignments after Step 4 ensures you aren’t paying for licenses that better role hygiene could have avoided.

**What**  
You will assign the appropriate **Dynamics 365 Finance**, **Supply Chain Management**, **Commerce**, **Human Resources**, **Project Operations**, **Team Members**, or **Operations – Activity** licenses to each user per the Power Platform admin center and User Security Governance findings. For users spanning multiple apps, assign a **Base** license (highest‑value app) and then the necessary **Attach** licenses. If you find misassigned licenses (e.g., a full license on a read‑only user), reallocate them to users who actually need them. Create a **worklist** from Power Platform admin center’s “Users with unassigned licenses” and work through it systematically. Ensure alignment with HR and business owners for new joiners, leavers, and role changes.

**How**  
In the **Microsoft 365 Admin Center**, go to **Users → Active users → [Select user] → Licenses and apps**, then assign the required license(s). Follow Base‑then‑Attach sequencing: for example, give **Finance (Base)** first, then **SCM (Attach)** if the user needs both. Where supported, you can deep‑link from Power Platform admin center user records to the admin center to speed assignments. After assignment, re‑run Power Platform admin center/User Security Governance reports to confirm the user no longer appears in the “unassigned” or “Not Entitled” categories. Keep a change log (user, license, date) to support audits and renewal planning.

---

## Step 7: Plan for Additional Licensing (Reservations / Purchase)

**Why**  
If Power Platform admin center shows required seats exceeding purchased seats, you need to **acquire or reserve** additional licenses to prevent user lockouts. **License Reservations** (for Enterprise Agreement customers) allow you to **commit now** so seats are available immediately while billing flows through your next **True‑Up**. Planning ahead avoids last‑minute approvals, procurement delays, and operational risk as validation approaches. It also enables better budgeting by smoothing costs and documenting the business rationale for additional spend. Proactive planning is particularly important for large role changes, mergers, or new rollouts.

**What**  
You will determine the **delta** between required, assigned, and available seats for each product (e.g., +9 Finance Base, +3 SCM Attach). Based on your agreement type, you’ll either place **License Reservations** or **purchase additional licenses** via CSP/EA channels. You’ll document the **usage date** for reservations, acknowledging financial commitment at your next order cycle. You’ll also coordinate with your Microsoft seller/partner on any special pricing or prerequisites. Finally, you’ll build a small buffer for growth and onboarding to reduce repeated transactions.

**How**  
For EA customers, in **Microsoft 365 Admin Center** go to **Billing → Your products → Volume licensing → Make reservations**, select the appropriate **EA contract**, set a **Usage date** (up to 6 months ahead), and add the required services/quantities. Confirm and place the reservation (note the 72‑hour cancellation window). For CSP or non‑EA, work with your partner or purchase licenses directly so they appear in the Admin Center for assignment. After new seats are visible, complete the user assignments (Step 5) and validate in Power Platform admin center that shortages are resolved. Update your internal licensing tracker with reservations/purchases, quantities, and renewal/true‑up notes.

---

## Summary Checklist

| Step | Action | Tool / Report |
|------|--------|----------------|
| **0** | Upgrade to latest Quality Update | Lifecycle Services (Lifecycle services) |
| **1** | Remove inactive users | User Security Governance → User Activity Aging Report |
| **2** | Review licensing model | Dynamics 365 Licensing Guide |
| **3** | Review user‑role mapping | Power Platform admin center / Lifecycle services (User License Consumption) |
| **4** | Validate license triggers | F&O User Security Governance (License Usage Summary, Security Analysis) |
| **5** | Assign licenses | Microsoft 365 Admin Center |
| **6** | Plan additional licenses | Volume Licensing Reservations / CSP Purchase |

---

## FAQ
**Q1. Does per‑user license validation apply to ISV or third‑party solution licenses?**  
**A1.** No. Validation in this playbook applies to **Dynamics 365 F&O licenses** only. ISV or third‑party licenses are governed separately by those providers.

**Q2. How can I tell which roles trigger which licenses?**  
**A2.** Use the **User Security Governance License Usage Summary** to see roles, duties, and privileges with **Entitled/Not Entitled** status, and the **Role license matrix** in Power Platform admin center for a high‑level view. Drill down to privileges to identify exactly what escalates license needs.

**Q3. Can I renew or purchase licenses in advance?**  
**A3.** Yes. **EA License Reservations** let you commit seats ahead of your true‑up so they’re available to assign now. CSP and other channels also allow on‑demand purchases.

**Q4. Will sandbox environments be included?**  
**A4.**  **Per user license validation only applies to production** access. 

---

## Additional Resources

- [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409)  
 Admin Center)](https://learn.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)e tenant: licensing requirements](../../fin-ops/get-started/implement-multiple-projects-a