---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 1, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources.
author: Darinkramer
manager: AnnBe
ms.date: 5/1/2020
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
ms.search.validFrom: 2020-05-1
ms.dyn365.ops.version: Human Resources

---
# "What's new or changed in Dynamics 365 Human Resources (May 1, 2020)"

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3196. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## New Performance Management entities available in Data Management Framework (DMF)

The following entities are now available. If you don't see these entities listed in the entities list, use the Refresh entities option in Framework Parameters > Entity settings > Refresh entity list.

- Discussion Competency
- Discussion Goals
- Discussion Measurement
- Discussion Topic
- Performance Journal
- Measurement
- Goal Measurement

In addition, Total score and Average score were added to the Discussion entity

## Increase length of leave request comments - (275641)

With this change the comments on leave requests will now allow more than 100 characters.

## Final comments on reviews don't appear when the manager or the employee is logged into a different company.  - (431688)

This change allows for all comments to appear when viewing reviews.

## User-defined links are not supported on new worker form - (390374)

User defined links have been enabled on the streamlined worker form.

## HcmRatingLevelEntity causing OData API crash. - (439476)

This change corrects the API crash. This error was caused because of a duplicate name.

## In preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Update user experience to indicate that accrual is suspended - (429550)

With this change, the user experience has been updated to indicate the accrual has been suspended for a plan.

## Suspend leave accrual for specified leave types - (272447)

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave may be a type, but doesn't have to be. Any leave can be suspended based on another leave type.

## Data Management Framework (DMF) entity available for accrual suspensions - (429549)

In this release, a DMF entity is now available for accrual suspensions.

## Add reason code to accrual suspensions - (429547)

Reason codes have been added to the accrual suspension.

## Begin transitioning from HR parameters to L&A parameters

In this release, parameters for leave and absence and the Human Resource Parameters will start to be combined. 

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Known issues

## SharePoint preview doesn't work in some environments

If document preview for documents stored in SharePoint doesn't work, try the following procedure:

1. Verify the Admin user account has an email associated with the user record. You can view this information in the **User** page. If email isn't set up, you need to add the email and provider with the OData Excel add-in. By default, the email address isn't present in the Excel design. You'll need to edit the Excel design, add all fields, apply, and refresh. Once you've completed those steps, you can update the admin account.

2. After the Admin account has an associated email account, sign in to Human Resources with Admin credentials.

3. Access an attachment in SharePoint to start the document preview.

4. Sign in with another user account that has access to attachments and verify that the preview works as expected.
