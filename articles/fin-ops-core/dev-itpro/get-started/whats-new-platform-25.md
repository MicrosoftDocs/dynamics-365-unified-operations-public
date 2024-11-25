---
title: What's new or changed in Dynamics 365 Finance platform update 25 (April 2019)
description: Learn about new or changed features in Dynamics 365 for Finance and Operation platform update 25. This version was released in April 2019.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-03-08
ms.dyn365.ops.version: Platform 25
---

# What's new or changed in Dynamics 365 Finance platform update 25 (April 2019)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 Finance platform update 25. This version has a build number of 7.0.5222. For more information about Platform update 25, see [Additional resources](#additional-resources).

## Extensibility enhancements
The [second wave of platform extensibility enhancements](/business-applications-release-notes/April19/dynamics365-finance-operations/platform-extensibility2) included in Platform update 25 is documented in the April 2019 Release notes. There are fourteen enhancements detailed, with one of the highlights being that Chain of Command on an InternalUseOnlyAttribute method is now allowed with just a warning.

## PowerBI.com report pinning
You can take advantage of improved flexibility in customization options available in the web client for power users by using built-in tooling to replace standard analytical reports embedded in the application with custom solutions hosted on PowerBI.com. With the latest Platform update, power users can replace the standard reports in application workspaces with reports hosted on PowerBI.com. These updates are immediately made available to other users of the workspace, replacing the standard solution. Additional options include the ability to revert back to the analytical reports that were originally released with the application.

## Entity store in Azure Data Lake (public preview)
Entity store is an Operational data warehouse that contains simplified transactional data for reporting with Power BI. Now you can stage entity store in your own Azure Data Lake Storage Gen2. You can use PowerBI.com in addition to other Azure and third-party tools to work with data. When this feature is enabled, entity store data isn't populated in the relational entity store database in the Microsoft subscription. Instead, it's populated in an Azure Data Lake Storage Gen2 account in your own subscription. You can use the full capabilities of PowerBI.com and other Azure tools to work with entity store.

To enable this feature, see [Entity store in your own Business Data Lake](/business-applications-release-notes/April19/dynamics365-finance-operations/erp-data-entity-store-byod-business-data-lake).

## Trickle feed support for entity store in Azure Data Lake (public preview)
When entity store is staged in Azure Data Lake, you have the option to enable trickle feed updates. If the trickle feed option is enabled, transactional data gets updated in your own Azure Data Lake as soon as they are committed in Dynamics 365 Finance. Use this option to enable real-time reporting with transactional data using PowerBI.com and other tools.

## Edit analytical workspace
You can now empower users to author the reports they need without relying on a developer. Using the latest Platform update, you can make non-disruptive enhancements to embedded application solutions. Power users are able to modify ready-made analytical workspaces without leaving the client or using developer tools. Users who have specific security privileges can add or modify report visuals and add new pages to existing reports. These changes are applicable to all users viewing the report.

## System printer management
Use built-in system administration tools to manage network printers across legal entities with ease. You can modify device properties and delete network printers by using a single view. These tools will drastically simplify the task of configuring network printer devices available within Dynamics 365 Finance applications.

## Client alert email support
Stay on top of your business data with integrated change tracking tools. With the latest Platform update, you can create alert rules that automatically dispatch email notifications to pre-defined groups of internal and external contacts when triggered by an event. With finance and operations, you can define custom alert rules to monitor filtered views of their data. For more information, see [Client Alerts notifications by email](../../fin-ops/get-started/alert-email-notifications.md).

## Client alert sub-table field tracking
The latest Platform update release includes the ability to create alert rules that monitor updates made to fields sourced from child tables. Previously, options were limited to fields sourced from the root data source. Now you can able define alert rules for all fields visible to the user including those from child tables.

## Azure blob storage as an endpoint for business events (private preview)
Azure blob storage account can be configured as an endpoint for business events. This adds to the existing set of Azure endpoint types that are supported, which allows for a wider choice of integration scenarios.

For more information about business events, see [Business events overview](../business-events/home-page.md). 

> [!Note]
> The business events feature is available as a private preview. For information about when the feature is scheduled for generally availability, see the [Release plans](/business-applications-release-notes/April19/dynamics365-finance-operations/planned-features). 

## Batch jobs single scheduler
Improvements are made in the batch framework to optimize the batch scheduling functionality. Only one batch scheduler will be active at a time, which will reduce contention on batch tables and may increase throughput. This is enabled by default in Platform update 25.

## Batch Jobs enhanced forms
The **Batch jobs** form has been enhanced to increase productivity and enhance the user experience. Users are able to switch between enhanced and legacy forms. For more information, see [Enhanced batch forms](../sysadmin/enhanced-forms.md).
Additionally, support has been added for saved views and will be released in a future Platform update. For information about saved views, see the [Release plans](/business-applications-release-notes/april19/dynamics365-finance-operations/saved-views).

## Batch jobs alerts and notifications
You can view batch job notifications in the action center. These notifications will keep you informed about batch events. You can enable alert rules for when a batch job ends, ends in error, or is canceled. You can choose whether the alerts are emailed to you or appear as a pop-up notification in the action center. For more information, see [Set up alerts](../sysadmin/alerts.md).

## Additional resources

### Platform update 25 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 25, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=299594&dbType=3&qc=cd4a0699eeae081b2b715d75b33ba6024dce2576563a84015bf60ed3509420a5).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

