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
ms.reviewer: josaw
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
# "What's new or changed in Dynamics 365 for Talent (August 27, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2447.

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is Production or Sandbox. Instances of the Sandbox type allow for early testing of new features. All existing Talent instances will be updated to the Production instance type. If you want one of your existing instances to be updated to the Sandbox instance type, contact Support to initiate the change request.

For more information about how changes are published, see [Provision Talent](./provisioning-talent.md).

### View extended information for performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews. In addition, direct managers and their employees can maintain and update performance journals to help ensure that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.

### Deleting legal entities is allowed if employees exist within the company (339849)

With this change, companies cannot be removed/deleted when employees and other related data exists for the legal entity.

### Compensation management BI analytics not matching on the compensation workspace (322493)

In this release, the compensation analytics has been adjusted to accurately reflect the plans assigned to employees.

### Workflow "placeholder" %company% displays DAT in when hiring employees through workflow (343905)

With this release, the company placeholder will display the legal entity that is associated with the employment of the new employee.

### CDSJobPositionEntity displays an error when valid to date is set (349387)

In this release, the Position Detail and the Position Duration data sources on the CDSJobPosition entity allow for edits from CDS to the date effective fields. 

### Employee Termination, last day worked is populated on the Assignment end date (332496)

This change will now default the position assignment end date to the employment end date. These defaults can be changed during the entry process.

### Legal entities not limited with hire (338871)
 
This change will restrict the hiring process to only show those legal entities the user has access to.  

## In preview

### Streamlined employee entry and navigation

This functionality is now available in sandbox and trial environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This will enable these changes for all users. You can turn this option off at any time.

For more information, see [Streamlined employee entry and navigation](./streamlined-employee-entry.md).

## Coming soon

### Platform update 29

For more details about Platform update 29, see [Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-29).
