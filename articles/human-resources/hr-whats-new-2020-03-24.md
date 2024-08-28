---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (March 24, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for March 24, 2020.
author: andreabichsel
ms.date: 03/24/2020
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: evergreen
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-03-24
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (March 24, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3073. The numbers in parentheses in some headings refer to Lifecycle Services (LCS) support numbers for reference.

## Human Resources environment limits are now based on updated licensing (394595)

The limit on the number of environments per project in Lifecycle Services (LCS) has changed. The previous limit was two environments. The limit on the number of production and sandbox environments you can create for Human Resources in LCS is now based on updated licensing. You can now create as many environments as needed per LCS project, depending on the number of licenses purchased. The new licensing, updated on February 1, 2020, allows customers to purchase additional environments. For more information about licensing requirements for additional environments, see [Dynamics 365 Licensing Guide](https://dynamics.microsoft.com/pricing/#HumanResources).

## Platform changes

- Full page apps (Preview) - This preview feature, which requires you to enable the Saved views feature, allows Power Apps and third-party apps to be added as full-page experiences via the dashboard.

- Saved views (Preview) - This preview feature enables saved views, which provide a significant enhancement to the personalization subsystem. This feature allows users to have multiple named sets of personalizations per page. You can also publish views to security roles.

- Optimized "is one of" filtering experience - This feature enables an optimized "is one of" filtering experience that makes it easier to enter multiple filter values, has a simpler mechanism to remove individual or all filter values, and has a more compact and intuitive visualization of filter values.

- Recommended fields - Users often need to add fields to a grid or page. This can be difficult with so many available fields. Instead of having to search through a large list, this feature enables the system to surface a set of recommended fields based on what other users most often add in similar scenarios.

- Sticky default actions in grids - This feature ensures that the default action in a grid is linked to a specific column in a grid, regardless of whether that column is moved or hidden.

## Unable to adjust leave balance for a plan with no accruals that was created with "multiple leave type" feature on (419635)

With this change, you can adjust balances for leave plans that have been created with the Multiple leave type (Preview) feature enabled in feature management.

## In preview

The following preview features became available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

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

3.	Find the environment you want to upgrade. The environment should correspond to **Environment name** in the **Common Data Service information** section in the **About** form in Human Resources.

4.	Select the environment to view the environment details.

5.	In the action bar at the top, select **Manage Solutions**. A new browser window will open and navigate to **Dynamics 365 Administration Center** in the context of your environment.

6.	In the **Solution** list, select **Dynamics 365 Human Resources Anchor**.

7.	Select **Upgrade** to apply the latest solution.

## SharePoint preview doesn't work in some environments

If document preview for documents stored in SharePoint doesn't work, try the following procedure:

1. Verify the Admin user account has an email associated with the user record. You can view this information in the **User** page. If email isn't set up, you need to add the email and provider with the OData Excel add-in. By default, the email address isn't present in the Excel design. You'll need to edit the Excel design, add all fields, apply, and refresh. Once you've completed those steps, you can update the admin account.

2. After the Admin account has an associated email account, sign in to Human Resources with Admin credentials.

3. Access an attachment in SharePoint to start the document preview.

4. Sign in with another user account that has access to attachments and verify that the preview works as expected.

## Coming Soon

## New production release cadence

Beginning in April, the release cadence for Human Resources will shift from a weekly update to a bi-weekly update. To ensure alignment with safe deployment practices, and maintain high standards of stability and reliability in the service, the process of deploying service updates to all regions will be a two-week rollout. Additional testing and monitors will be in place to verify successful deployment at each stage of the process. For more information on the release cadence, see [Update process](hr-admin-setup-update-process.md).

## Known issues

## Employment Detail entity

The **Employment Detail** entity has been updated with the following fields: **PayFrequency**, **Employment Category ID**, **Employment Type**, **EmploymentType ID**, and **Benefit Employment Status**. The setup data for these fields rely on benefits management being enabled in Feature management. These fields shouldn't be populated or updated in the **Employment Detail** entity, because it will result in errors during import.

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
