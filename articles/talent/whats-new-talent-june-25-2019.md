---
# required metadata

title: What's new or changed in Dynamics 365 Talent (June 25, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 06/25/2019
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-06-25
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (June 25, 2019)

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Coming soon in Attract

### Job approvals appear on the home page

Approvals appear in an **Approvals** section on the dashboard. Approvers can review their approvals under **Assigned to you**, which shows the job ID, the job title, other approvers, and the date when the job was assigned. Users who submit a job for approval can review their jobs under **Requested by you**, which shows the approvers who must still approve the submitted job.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2357.

### Incorrect value displayed for Primary position (314266)

These changes will consistently display the **Primary position** setting on all pages.

### Can't edit after recalling the workflow in Review (318180)

Reviews that have been recalled via workflow can now be edited.

### Final comments field in Reviews isn't translated (325921)

The **Final comments** label will be translated in Talent.

### Preview features will be enabled only in sandbox environments

When you provision a new instance of Talent, you can indicate whether the instance type is **Production** or **Sandbox**. The **Sandbox** instance type allows for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

## In preview

### Restrict the leave types in time-off requests

Organizations can offer many types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by Human resources (HR) instead. In this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### Feature management area in Talent

**Feature management** will be removed from **System administration** because of issues with the feature. We'll re-introduce **Feature management** in a future release. 

### Common Data Service entity support for custom fields

The following entities will support custom fields: **Payroll earning code**, **Fixed compensation event**, **Compensation grid**, **Pay period**, and **Compensation reference point**. 

### New Common Data Service entities

The **Reason codes** entity will be added to Common Data Service.

### View performance information for direct and extended reports in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews. In addition, direct managers and their employees can maintain and update performance journals to help ensure that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.

### Print performance reviews

Employees, managers, and HR will be able to print an employee's performance review.
