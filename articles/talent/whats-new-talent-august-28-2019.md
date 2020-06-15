---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (August 27, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 8/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: andreabichsel
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-08-27
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 for Talent (August 27, 2019)

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2447. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is Production or Sandbox. Instances of the Sandbox type allow for early testing of new features. All existing Talent instances will be updated to the Production instance type. If you want one of your existing instances to be updated to the Sandbox instance type, contact Support to initiate the change request.

For more information about how changes are published, see [Provision Talent](./provisioning-talent.md).

### View extended information for performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews. In addition, direct managers and their employees can maintain and update performance journals to help ensure that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.

### Deleting legal entities isn't allowed if employees exist within the company (339849)

With this change, you can't remove or delete companies if employees and other related data exist for the legal entity.

### Compensation management business intelligence analytics don't match on the compensation workspace (322493)

In this release, compensation analytics have been adjusted to accurately reflect the plans assigned to employees.

### Workflow placeholder %company% displays DAT when hiring employees through workflow (343905)

With this release, the company placeholder displays the legal entity that is associated with the employment of the new employee.

### The CDSJobPosition entity displays an error when valid to date is set (349387)

In this release, the **Position detail** and the **Position duration** data sources on the **CDSJobPosition** entity allow for edits from Common Data Service to the **Date effective** fields. 

### For employee termination, the last day worked is populated on Assignment end date (332496)

This change now defaults the position **Assignment end date** to the **Employment end date**. You can change these defaults while entering data.

### Legal entities aren't limited with hire (338871)
 
This change restricts the hiring process to only show those legal entities the user has access to.  

## In preview

### Streamlined employee entry and navigation

This functionality is now available in sandbox and trial environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This enables these changes for all users. You can turn this option off at any time.

For more information, see [Streamlined employee entry and navigation](./streamlined-employee-entry.md).

## Coming soon

### Platform update 29

For more details about Platform update 29, see [Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-29).
