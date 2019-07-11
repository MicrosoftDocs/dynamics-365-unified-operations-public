---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (July 9, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 7/9/2019
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
ms.search.validFrom: 2019-07-09
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (July 9, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2374.

### Platform update 28

For more details about Platform update 28, see [Preview features in Dynamics 365 for Finance and Operations platform update 28 (July 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-28).

### The following entities now support custom fields in CDS: 

The following entities have been updated: Compensation fixed plan, Compensation reference point setup, Compensation reference point set up line, Payroll earning code, Pay period, Fixed compensation event and Compensation grid.
To view all updated entities in Talent go to: System administration->Links->Common data service configuration->CDS entity name drop down list. All entities listed are on the latest version. 

###  Add FullName to CDS Worker entity

Full name field has been added to the Worker entity.

### Full-time equivalent higher than 1.0

A warning will now be presented if a value greater than 1.0 is entered for the FTE on a position. 

### Future dated employment warning displays on worker form even when there is no future dated employment

With this release, you will no longer receive a message indicating that a future employment exists when navigating to the worker form from the exiting employees list on the Personnel Management workspace. 

### Unable to delete a business process in Talent

With this release an option has been added to delete business processes that have been created. Business processes can now be removed through the business process workspace.

### Leave balance is always shown as "zero" for plans with no accruals when using "Balance as of accrual period"

With this release, a change has been made to show the balance of the plans that are set up with no accruals. 

## In preview

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is **Production** or **Sandbox**. Instances of the **Sandbox** type allow for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

### Restrict leave types in time-off requests

Organizations can offer many different types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by HR instead. In this release, you can configure which leave types employees can submit time-off requests for. 

## Coming soon in Core HR

### View extended information for performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews, which their employees co-manage. In addition, direct managers and their employees can maintain and update performance journals to help guarantee that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports. 

### Entities supporting custom fields

The following entities will be enabled for Custom Fields in CDS: Leave type, Worker bank account, Work calendar
