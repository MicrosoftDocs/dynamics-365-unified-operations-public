---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations platform update 27 (June 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operations platform update 27 (June 2019). 
author: tonyafehr
ms.date: 10/30/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2019-06-30
ms.dyn365.ops.version: Platform 27

---
# What's new or changed in Dynamics 365 for Finance and Operations platform update 27 (June 2019)

[!include [banner](../includes/banner.md)]

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 27. This version has a build number of 7.0.5286. For more information about Platform update 27, see [Additional resources](whats-new-platform-update-27.md#additional-resources).

## Feature Management
The **Feature management** experience provides a workspace where you can view, enable, disable, and schedule features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. 

For more information about Feature management, see [Feature management overview](feature-management/feature-management-overview.md).

## Dedicated capacity to process business events 
It will be no longer required to schedule the business event processing batch job to process business events. Dedicated threads are allocated to process business events by the system, which ensures faster processing of business events. The existing batch job is still available (but is not needed to run unless there are issues with dedicated capacity). If the batch job was already scheduled prior to this platform update, the batch will become ineffective and dedicated threads will take over after the update.

For more information, see [Business events overview](../../dev-itpro/business-events/home-page.md).

## Cancel a running batch job
It can take a long time to cancel a batch job if the job has tasks that are currently executing. The abort option provides a system administrator or batch job manager with the ability to cancel already executing tasks for jobs if the jobs are canceled. This provides a much faster mechanism to cancel a long running job that might impact system usage in other places. For more information, see [Abort an executing batch job](../../dev-itpro/sysadmin/batch-abort.md)

## Extensibility enhancements
The [fourth wave of platform extensibility enhancements](/business-applications-release-notes/April19/dynamics365-finance-operations/platform-extensibility4) included in Platform update 27 is documented in the April 2019 release notes. There are two enhancements detailed, with the highlight being that View extensions can now change label and help text values.

## Export data from all companies to BYOD can be enabled via parameters
The functionality to enable export from all companies to BYOD can now be enabled in framework parameters in data management. Until now, this required a flight to be enabled which is no longer needed.

## Additional resources

### Platform update 27 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 27, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=320391&dbType=3&qc=d5539716f56ccea45e2187c269570772af20e1f10a78371811220da6315a3c34).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]