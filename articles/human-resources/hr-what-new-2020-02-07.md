---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 7, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 2/4/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-02-07
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (February 7, 2020)"

This topic describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2835. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

## Learning Analytics doesn't show the course if the classroom is blank - (388289)

The learning analytics analytics page has been updated to display the course if the classroom is empty.

## Position lookup not taking timezone into account - (405344)

With this change the lookup for open positions will now take into account the timezone when validating if a position is open.

## Current balance analysis view not updated with the correct current leave balance after submitting time off requests - (409756)

The current balance has now been updated to include the submitted time off requests.

## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## Coming soon

### Platform update 32 

Platform update 32 will be available soon. [Find out more information about Platform update 32 here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32) .

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
