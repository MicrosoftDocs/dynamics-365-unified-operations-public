---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (April 13, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for April 13, 2020.
author: andreabichsel
ms.date: 04/13/2020
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
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: Human Resources

---
# What's new or changed in Dynamics 365 Human Resources (April 13, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3136. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## New production release cadence

With this week's release, the release cadence for Human Resources shifts from a weekly update to a biweekly update. To ensure alignment with safe deployment practices, and maintain high standards of stability and reliability in the service, the process of deploying service updates to all regions is now a two-week rollout. Additional testing and monitors are in place to verify successful deployment at each stage of the process. For more information on the release cadence, see [Update process](hr-admin-setup-update-process.md).

## Rounding precision field isn't editable after specifying a Rounding type (435616)

With this change, the **Rounding precision** field is now available after you update the **Rounding type** field.

## Can't edit leave enrollment end date when the leave plan doesn't have accrual periods (413628)

You can now edit the enrollment end date without getting the error "Field Accrual date basis must be filled in."

## Employment entity doesn't sync to Dataverse (430834)

This change corrects an issue where the employment data wasn't syncing to Dataverse after adding financial dimensions. 

## Remove multi-parenting for Work Calendar Time Interval entity (431775)

This change removes multi-parenting for the **Work Calendar Time Interval** entity.

## Filter with CAST function doesn't work on OData call Position Worker Assignment entity (431699)

This update includes a change to allow  filter with CAST function within OData for the **Position Worker Assignment** entity.

## In Preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Known issues

## Employment Details entity

The **Employment Detail** entity has been updated with the following fields:

- **PayFrequency**
- **Employment Category ID**
- **Employment Type**
- **EmploymentType ID**
- **Benefit Employment Status**

The setup data for these fields rely on benefits management being enabled in the **Feature management** workspace. Don't populate or update these fields in the **Employment Detail** entity, because it will result in errors during import.

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