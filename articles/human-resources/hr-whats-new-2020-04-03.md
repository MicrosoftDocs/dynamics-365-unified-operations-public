---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (April 3, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for April 3, 2020.
author: andreabichsel
ms.date: 04/03/2020
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
ms.search.validFrom: 2020-04-03
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (April 3, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3111. The numbers in parentheses in some headings refer to Lifecycle Services (LCS) support numbers for reference.

## Features that are generally available the week of April 6

- **Leave and absence features** - For more information, see [Leave and absence overview](hr-leave-and-absence-overview.md).

- **Benefits management features** - For more information, see [Benefits management overview](hr-benefits-management-overview.md).

## Human Resources environment limits are now based on updated licensing (394595)

The limit on the number of environments per project in LCS has changed. The previous limit was two environments. The limit on the number of production and sandbox environments you can create for Human Resources in LCS is now based on updated licensing. You can now create as many environments as needed per LCS project, depending on the number of licenses purchased. The new licensing, updated on February 1, 2020, allows customers to purchase additional environments. For more information about licensing requirements for additional environments, see [Dynamics 365 Licensing Guide](https://dynamics.microsoft.com/pricing/#HumanResources).
 
## Error when trying to delete a questionnaire (428603)

This week's update corrects an issue where the following error displays when attempting to delete a questionnaire:

An unbalanced X++ TTSBEGIN/TTSCOMMIT pair has been detected.

## Performance journal and professional certificates security issue (428499)

This change limits the visibility of both performance journals and professional certificates based on the companies they have access to. 

## The abbreviation for Quebec and Manitoba (387510)

Starting data has been updated to reflect the correct abbreviation for Manitoba and Quebec.

## New entities available in Data Management Framework

The following entities are now available. If you don't see these entities listed in the entities list, use the **Refresh entities** option in **Framework Parameters > Entity settings > Refresh entity list**.

 - Leave and absence bank transaction V2
 - Leave and absence enrollment V2
 - Leave and absence plan tier V2
 - Leave and absence plan V2

## Dataverse solution is now available with the following changes:

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
| New **Title** entity | <ul><li>**Title** added</li></ul>The new **Title** entity is included in Dataverse but isn't referenced from the **Job Position** or **Job** entities at this time. |

> [!NOTE]
> Financial dimensions for both positions and employment provide one-direction integration for updates from Human Resources to Dataverse. Financial dimensions updates don't currently synchronize from Dataverse to Human Resources.

Over the next few weeks, these entity changes will be available in all environments. To manually install the latest Dataverse solution for Human Resources:

1.	Go to the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).

2.	Select **Environments**.

3.	Find the environment you want to upgrade. The environment should correspond to **Environment name** in the **Dataverse information** section in the **About** form in Human Resources.

4.	Select the environment to view the environment details.

5.	In the action bar at the top, select **Manage Solutions**. A new browser window will open and navigate to **Dynamics 365 Administration Center** in the context of your environment.

6.	In the **Solution** list, select **Dynamics 365 Human Resources Anchor**.

7.	Select **Upgrade** to apply the latest solution.

## In Preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave will create a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Coming Soon

## New production release cadence

Beginning in April, the release cadence for Human Resources will shift from a weekly update to a bi-weekly update. To ensure alignment with safe deployment practices, and maintain high standards of stability and reliability in the service, the process of deploying service updates to all regions will be a two-week rollout. Additional testing and monitors will be in place to verify successful deployment at each stage of the process. For more information on the release cadence, see [Update process](hr-admin-setup-update-process.md).

## Known issues

## Employment Detail entity

The **Employment Detail** entity has been updated with the following fields: **PayFrequency**, **Employment Category ID**, **Employment Type**, **EmploymentType ID**, and **Benefit Employment Status**. The setup data for these fields rely on benefits management being enabled in Feature management. These fields shouldn't be populated or updated in the **Employment Detail** entity, because it will result in errors during import.

## SharePoint preview doesn't work in some environments

If document preview for documents stored in SharePoint doesn't work, try the following procedure:

1. Verify the Admin user account has an email associated with the user record. You can view this information in the **User** page. If email isn't set up, you need to add the email and provider with the OData Excel add-in. By default, the email address isn't present in the Excel design. You'll need to edit the Excel design, add all fields, apply, and refresh. Once you've completed those steps, you can update the admin account.

2. After the Admin account has an associated email account, sign in to Human Resources with Admin credentials.

3. Access an attachment in SharePoint to start the document preview.

4. Sign in with another user account that has access to attachments and verify that the preview works as expected.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]