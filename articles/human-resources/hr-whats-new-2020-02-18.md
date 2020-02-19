---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 18, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 02/07/2020
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

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2903. The numbers in parentheses in some headings refer to support numbers for reference.

## Platform update 32 

Platform update 32 is now available with this weeks release. [Find out more information about Platform update 32 here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32) .


## Streamlined employee form, search values remembered when changing view options - (383833)

With this change, the new worker form will now remember the search values when changing the view options and applying changes.

## Preview Features-Compensation Management Summary tiles redirect to wrong form  - (401861)

Fixed and variable compensation management tiles now open the new worker form with the correct records displayed. Only impacted when streamlined employee form is enabled in feature management.

## Status field empty for some Leave Request records in CDS - (414915)

This change corrects an issue in CDS when a leave request is in the review status. CDS will reflect the same in review status.

## Skill gap analysis only possible for assigned job - (411390)

In this release, skill gap analysis can be preformed on any job defined in Human Resources.

## System currency is not syncing from CDS to HR for new environments - (418011)

This change enables system currency with in CDS to sync between Talent and CDS.

## In preview

The following preview features were made available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## Coming soon

### Updated CDS Solution

A new Common Data Service solution will be available soon with the following changes:

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
