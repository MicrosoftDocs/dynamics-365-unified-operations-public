---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 3, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 3, 2020.
author: andreabichsel
ms.date: 03/03/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-03-03
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (March 3, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2955. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Dataverse solution is now available with the following changes:

A new Dataverse solution will be available soon with the following changes:

| Description | Change |
| ----------------------------------------- | --- |
| **Job/Position** entity changes | **Compensation region** added</br>**Financial dimensions** added |
| **Worker** entity changes | **Name sequence** added</br>**Works from home** added</br>**Language** added</br>**Seniority date** added</br>**Anniversary date** added</br>**Original hire date** added |
| **Employment** entity changes | **Financial dimensions** added</br>**Termination reason** added</br>**Termination date** renamed from **Transition date**</br>**Probation date** added |
| **Worker address** entity changes | **Street address** added</br>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation |
| New variable compensation setup entities | **Compensation variable plan type**</br>**Compensation variable plan**</br>**Vesting rules**</br>**Compensation variable plan level** |
| New **Worker calendar employment** entity | **Work calendar entity** added |
| New **Payroll position detail** entity | **Payroll position detail** added |
| New **Title** entity | **Title** added. The new **Title** entity will be included in the sync process between Human Resources and Dataverse. It won't be initially referenced from **Job Position** or **Job** entities. |

Over the next few weeks, these entity changes will be available in all environments. To manually install the latest Dataverse solution for Human Resources:

1.	Go to the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).

2.	Select **Environments**.

3.	Find the environment you want to upgrade. The environment should correspond to **Environment name** in the **Common Data Service information** section in the **About** form in Human Resources.

4.	Select the environment to view the environment details.

5.	In the action bar at the top, select **Manage Solutions**. A new browser window will open and navigate to **Dynamics 365 Administration Center** in the context of your environment.

6.	In the **Solution** list, select **Dynamics 365 Human Resources Anchor**.

7.	Select **Upgrade** to apply the latest solution.

## Import issues with the Leave enrollment data entity (406082)

You can now enroll an employee in a new leave plan of the same type, as long as the new enrollment date is later than the expired enrollment date of the previous plan.

## Issue with exporting contribution rates in the 401k payrollWorkerEnrolledBenefitDetail entity in DMF (420700)

This change corrects the export functionality for the **payrollWorkerEnrolledBenefitDetail** entity to reflect the current values for employer contribution.

## Searching in the streamlined Worker form causes message saying Person field must be filled in (402525)

When you search for an employee, you'll no longer receive a message saying you must fill in the **Person** field.

## Note field value doesn't render on the Add more skills form (380134)

This change corrects an issue when you personalize the **Add more skills** form in Employee self service.

## Multiple fixed compensation plans don't expire when transferring employees (389466)

With this change, all active fixed compensation records for the old position will expire on the transition date.

## In preview

The following preview features became available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]