---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (October 1, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Talent

---

# What's new or changed in Dynamics 365 Talent: Core HR (October 1, 2018)

**Build 8.1.1035.0**

This topic describes features that are either new or changed in Core HR.

## Turn off electronic payment validation

Electronic payment information validation occurs if you set up disbursements for
direct deposit either through **Employee self-service** workspace (ESS) or directly on the employee form. This option
gives you the flexibility to remove that validation if you do not require the
validation checks for amounts and remainder values. This feature is helpful if you're
integrating with an external payroll system that has different requirements.

## Manager self-service - Add goals for team members through the Team performance goals tile

Prior to this release, managers can add goals to their employees individually
through the performance goals associated to each employee. With this update,
managers can access the **Team performance goals** tile and create new goals by
selecting any of their direct reports.

## Manager self-service - Add reviews for team members through the Team performance reviews tile

Prior to this release, managers can add reviews to their employees individually
through the reviews associated to each employee. With this update, managers can
access the **Team performance reviews** tile and create new reviews by selecting
any of their direct reports.

## Configure proration options by leave plan

Organizations award time off differently based on when employees join and leave
the company. For some organizations, employees are awarded their full allocation
on their start date while others prorate the award. New options are provided in
this release to choose how to prorate the awards and accruals for joiners and
leavers in an organization. Options include: Prorated, Full accrual, and No accrual.

## Other changes

-   Employee entity updated - The **Personal** title can now be updated using the Excel
    add-in/data management.

-   Security change to allow removal of the **Delete** and **Deactivate** buttons in
    employee self-service for payment information.

## Known issue

-   **Issue:** When adding a new attachment to a worker, the **New** and
    **Edit** buttons are grayed out. **Workaround:** Before opening the
    attachment page, make sure that the FactBoxes on the **Worker** page are
    closed. If the FactBoxes are closed when the **Worker** page is loaded, the
    **Attachments** buttons will be enabled. (This issue will be fixed in the next
    platform update.)
