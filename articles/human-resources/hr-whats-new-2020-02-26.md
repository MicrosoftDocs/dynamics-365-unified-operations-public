---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 25, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 2/25/2020
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
ms.search.validFrom: 2020-02-25
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (February 25, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2927. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Enable Case Management navigation and DMF Entity - (414754)

This preview feature enables additional navigation to case management cases. (Enabled in Feature Management) These menu items are surfaced in the compliance workspace of Dynamics 365 Human Resources. With this change, HR will now have access to: All cases, My cases, My open cases, My overdue cases and Cases assigned to me through workflow.

Along with the new views into cases, the "Case detail" data management framework entity is also available.

## Enable Relationship definitions in Global Address Book - (414762)

Relationships have now been enabled with in the Global Address Book. Prior to this week's release, the relationship fact box displayed any system defined relationships. Now, you can define those relationships within the Global Address Book page.

## A position can be removed when active compensation records exist for the position - (414568)

With this change, a new warning will appear when you attempt to delete a position and a worker has an active compensation record for that same position. In this scenario, you are required to update the employee fixed compensation record prior to removing the position.

## Performance review workflow occasionally adds sign-offs from people who are not part of the process - (414171)

This change, corrects an issue where additional sign-off participants are added to the performance review.

## Worker position assignment not created in CDS when selected on the New Worker Dialog  (413479)

This change corrects an issue when hiring a new worker and assigning the new hire to a position through the new worker dialog. In this scenario, the position assignment will now be reflected in CDS.

## Coming Soon

### Common Data Service solution will be available soon with the following changes:

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
*The new "Title" entity will be included in the CDS but will not initially be referenced from Job Position or Job entities.

Over the course of the next few weeks the above changes will be available in all environments. Once released, if you would like to manually install the latest HR CDS Solution, follow the steps below. 

1.	Navigate to https://admin.powerplatform.microsoft.com.
2.	Select Environments.
3.	Find the environment you would like to upgrade.  This should corresponded Environment name in the Common data service information section in the About form found in Dynamics 365 Human Resources.
4.	Click on the Name of the environment to go to the environment details.
5.	In the Action bar at the top, click Manage Solutions.  This will open a new browser window and navigate to Dynamics 365 Administration Center in the context of your environment.
6.	In the Solution list, find the Dynamics 365 Human Resources Anchor solution and click on it.
7.	Click the Upgrade button to apply the latest Solution version.

## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).
