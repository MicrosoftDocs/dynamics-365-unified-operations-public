---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 3, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 3/3/2020
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
ms.search.validFrom: 2020-03-03
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (March 3, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2955. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Common Data Service solution is now available with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** entity changes | <ul><li>**Compensation region** added</li>|
| **Job position dimension** entity added | <ul><li>**Financial dimensions** added</li>
| **Worker** entity changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** entity changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** entity changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup entities | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calendar employment** entity | <ul><li>**Work calendar entity** added</li></ul> |
| New **Payroll position detail** entity | <ul><li>**Payroll position detail** added</li></ul> |
| New **Title** entity | <ul><li>**Title** added</li></ul> |
*The new "Title" entity is included in the CDS but will not initially be referenced from Job Position or Job entities.

Over the course of the next few weeks the above changes will be available in all environments. If you would like to manually install the latest HR CDS Solution, follow the steps below. 

1.	Navigate to https://admin.powerplatform.microsoft.com.
2.	Select Environments.
3.	Find the environment you would like to upgrade. This should correspond to the Environment name in the Common data service information section in the About form found in D365 for Human Resources.
4.	Click on the Name of the environment to go to the environment details.
5.	In the Action bar at the top of the page, click Manage Solutions.  This will open a new browser window and navigate to Dynamics 365 Administration Center in the context of your environment.
6.	In the Solution list, find the Dynamics 365 for Talent Anchor solution and click on it.
7.	Click the Upgrade button to apply the latest Solution version.


## Import Leave enrollment data entity issues - (406082)

With this change, an employee can be enrolled in a new leave plan with the same type as long as the new enrollment date is after the expired enrollment date of the previous plan.

## 401k PayrollWorkerEnrolledBenefitDetailEntity issue with contribution rates exporting in DMF - (420700)

With this change, the export for the PayrollWorkerEnrolledBenefitDetailEntity has been corrected to reflect the current values for employer contribution.

## Field "Person" must be filled in message after searching in the streamlined worker form - (402525)

In this week's release you will no longer receive a massage indicating the person must be filled in after searching for an employee.

## Note field value not rendering on add more skills form - (380134)

This change corrects an issue when personalizing the add more skills form in employee self-service.

## Multiple fixed compensation plans don't expire when transferring employees - (389466)

With this change, all active fixed compensation records for the "old" position will be expired as of the transition date.


## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).
