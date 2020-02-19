---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 18, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-02-18
ms.dyn365.ops.version: Human Resources

---
# What's new or changed in Dynamics 365 Human Resources (February 18, 2020)

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2903. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Platform update 32 

Platform update 32 is now available. For more information, see [What's new or changed in Platform update 32 for Finance and Operations (February 2020)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32).

## Search values are remembered when changing view options in streamlined employee form (383833)

The new **Worker** form now remembers  search values when you change the view options and apply changes.

## Compensation anagement summary tiles in preview feature redirect to wrong form (401861)

Fixed and variable compensation management tiles now disaplay the correct records when opening the new **Worker** form. Applies only when you've enabled the streamlined employee form preview feature in feature management.

## Empty Status field for some leave request records in Common Data Service (414915)

This change corrects an issue in Common Data Service when the **Status** field in a leave request is set to **Review**. Common Data Service now reflects the status.

## Skill gap analysis only possible for assigned job (411390)

You can now perform a skill gap analysis on any job defined in Human Resources.

## System currency is not syncing from Common Data Service to Human Resources in new environments (418011)

The system currency in Common Data Service can now sync to Human Resources.

## In preview

- [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features)

- [Benefits management preview features](hr-benefits-management-overview.md)

## Coming soon

### Updated Common Data Service solution

A new Common Data Service solution will soon be available with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** entity changes | <ul><li>**Compensation region** added</li><li>**Financial dimensions** added</li></ul> |
| **Worker** entity changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** entity changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** entity changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup entities | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calendar employment** entity | <ul><li>**Work calendar entity** added</li></ul> |
| New **Payroll position detail** entity | <ul><li>**Payroll position detail** added</li></ul> |
| New **Title** entity | <ul><li>**Title** added</li></ul> |
*The new "Title" entity will be included in the sync process between HR and CDS but will not initially be referenced from Job Position or Job entities.

## See also

[What's new or changed in Human Resources](hr-admin-whats-n32.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)
