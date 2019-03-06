---
# required metadata

title: Preview features in Dynamics 365 for Finance and Operations platform update 25 (Month 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operation platform update 25 (Month 2019). 
author: tonyafehr
manager: AnnBe
ms.date: 03/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2019-XX-XX
ms.dyn365.ops.version: Platform 25

---
# Preview features in Dynamics 365 for Finance and Operations platform update 25 (Month 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations platform update 25. This version has a build number of 7.0.XXXX. For more information about Platform update 25, see [Additional resources](whats-new-platform-25.md#additional-resources).

## Azure blob storage as an endpoint for business events
An Azure blob strorage account can be configured as an endpoint for business events. This adds to the existing set of Azure endpoint types that are supported thereby allowing for a wider choice for integration scenarios.

## Extensibility enhancements
The [second wave of platform extensibility enhancements](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/dynamics365-finance-operations/platform-extensibility2), included in Platform update 25, is documented in the April 2019 Release notes. There are fourteen enhancements detailed, with one of the highlights being that Chain of Command on an InternalUseOnlyAttribute method is now allowed with just a warning.

## Feature name
Brief description of the feature and how it helps customers.  Then provide a link to your topic that has details.

### PowerBI.com Report Pinning
Take advantage of improved flexibility in customization options available in the web client for power users. Use built-in tooling to replace standard analytical reports embedded in the application with custom solutions hosted on PowerBI.com. With the latest Platform Update release, power users are able to replace the standard reports in application workspaces with reports hosted on PowerBI.com.  These updates are immediately made available to other users of the workspace replacing the standard solution. Additional options include the ability to revert back to the analytical reports that were originally released with the application.

### Data Lake Integration

### Trickle feed support for Data Lake

### Edit Analytical Workspace
Empower users to author the reports they need right without relying on a developer. Using the latest Platform Update release, make non-disruptive enhancements to embedded application solutions. Power users are able to modify ready-made Analytical workspaces without leaving the client or using developer tools. Users who have specific security privileges can add or modify report visuals and add new pages to existing reports. The changes are applicable to all users viewing the report.

### System Printer Management
Use built-in system administration tools to manage network printers across legal entities with ease. Modify device properties and delete network printers with ease using a single view. These tools will drastically simplify the task of configuring network printer devices available within Microsoft Dynamics 365 for Finance & Operations applications.

### Client Alert Email Support
Stay on top of your business data with integrated change tracking tools. With the latest Platform Release, users are able to create Alert Rules that automatically dispatch email notifications to pre-defined groups of internal & external contacts when triggered by an event. With Dynamics 365 for Finance & Operations, users are able to define custom Alert Rules to monitor filtered views of their data. 
For more information, view article on [Client Alerts notifications by email](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/alert-email-notifications)

### Client Alert sub-table tracking
The latest Platform Update release includes the ability to create Alert Rules that monitor updates made to fields sourced from related tables. Previously, options were limited to fields sourced from the root data source. Now users are able to define alert rules for all fields on subtables which are visible to the user.

### Archive non-PDF files using Batch operation


## Additional resources

### Platform update 25 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 24, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.
