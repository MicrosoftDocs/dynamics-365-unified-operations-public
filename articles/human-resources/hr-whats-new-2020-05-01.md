---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (May 1, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for May 1, 2020.
author: andreabichsel
ms.date: 05/01/2020
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
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (May 1, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.3196. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## New Performance Management entities available in Data Management Framework (DMF)

The following entities are now available. If you don't see these entities listed in the entities list, use the **Refresh entities** option in **Framework Parameters > Entity settings > Refresh entity list**.

- **Discussion Competency**
- **Discussion Goals**
- **Discussion Measurement**
- **Discussion Topic**
- **Performance Journal**
- **Measurement**
- **Goal Measurement**

In addition, **Total score** and **Average score** were added to the **Discussion** entity.

## Increase length of leave request comments (275641)

Comments on leave requests now allow more than 100 characters.

## Final comments on reviews don't appear when the manager or employee is signed into a different company (431688)

All comments will now appear when viewing reviews.

## User-defined links aren't supported on new Worker form (390374)

User-defined links are now enabled on the streamlined **Worker** form.

## HcmRatingLevelEntity causes OData API crash (439476)

This change corrects the API crash. A duplicate name cased this error.

## In preview

## Leave suspension

You can suspend leave and absence in Human Resources for an employee. Suspending leave stops the leave accruals for selected leave types. If the suspension occurs after an accrual has been processed, suspending leave creates a prorated adjustment to the employee's leave balance. For more information, see [Suspend leave](hr-leave-and-absence-suspend-leave.md).

## Update user experience to indicate that accrual is suspended (429550)

The user experience now indicates that the accrual has been suspended for a plan.

## Suspend leave accrual for specified leave types (272447)

In this release, HR can create a rule to suspend leave accruals for employees with leave requests entered for unpaid leave. Unpaid leave can be a type, but doesn't have to be. You can suspend any leave based on another leave type.

## DMF entity available for accrual suspensions (429549)

A DMF entity is now available for accrual suspensions.

## Add reason code to accrual suspensions (429547)

Reason codes have been added to the accrual suspension.

## Begin transitioning from Human Resources parameters to leave and absence parameters

This release starts to combine Human Resources parameters with Leave and absence parameters.

## Carry forward rules

You can specify a carry forward leave type for carry forward balances where carry forward adjustments are transferred. For example, if an employee carries forward 10 days, you can pick a different leave type for those 10 days. For more information, see [Configure leave and absence types](hr-leave-and-absence-types.md).

## Known issues

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
