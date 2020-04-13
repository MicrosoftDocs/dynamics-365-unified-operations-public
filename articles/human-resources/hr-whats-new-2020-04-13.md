---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (April 13, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 4/13/2020
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
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (April 7, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3136. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## New production release cadence

With this weeks release, the release cadence for Human Resources will shift from a weekly update to a bi-weekly update. To ensure alignment with safe deployment practices, and maintain high standards of stability and reliability in the service, the process of deploying service updates to all regions will be a two-week rollout. Additional testing and monitors will be in place to verify successful deployment at each stage of the process. For more information on the release cadence, see [Update process](hr-admin-setup-update-process.md).

## Rounding Precision field is not editable after specifying a Rounding Type - (435616)

With this change, the rounding precision field will now be available after updates are made to the rounding type field.

## Not able to edit the leave enrollment end date when the leave plan doesn't have accrual periods - (413628)

You will now be able to edit the enrollment end date without  error "Field Accrual date basis must be filled in".

## Employment entity not syncing to CDS  - (430834)

This change corrects an issue where the employment data was not syncing to CDS after financial dimensions were added. 

## Remove multi parenting for workcalendartimeinterval entity - (431775)

This change removes multi parenting for the workcalendartimeinterval entity.

## Filter with CAST function doesn't work on OData call “Position worker assignments” entity - (431699)

This update includes a change to allow use of the filter with CAST function within OData for entity "Position worker assignments"

## In Preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave will create a prorated adjustment to the employee's leave balance.  Documentation can be found [here](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-leave-and-absence-suspend-leave).

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred to. For example, if an employee carry's forward 10 days, you can pick a different leave type for those 10 days. Documentation can be found [here](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-leave-and-absence-types).

## Known issues

## Employment Details entity

The employment detail entity has been updated with the following fields:  PayFrequency, Employment Category ID, Employment Type, EmploymentType ID and Benefit Employment Status.  The setup data for these fields rely on benefits management being enabled in feature management.  Therefore, these fields should not be populated or updated in the employment detail entity, as it will result in errors during import.

## SharePoint preview doesn't work in some environments

If document preview for documents stored in SharePoint doesn't work, try the following procedure:

1. Verify the Admin user account has an email associated with the user record. You can view this information in the **User** page. If email isn't set up, you need to add the email and provider with the OData Excel add-in. By default, the email address isn't present in the Excel design. You'll need to edit the Excel design, add all fields, apply, and refresh. Once you've completed those steps, you can update the admin account.

2. After the Admin account has an associated email account, sign in to Human Resources with Admin credentials.

3. Access an attachment in SharePoint to start the document preview.

4. Sign in with another user account that has access to attachments and verify that the preview works as expected.
