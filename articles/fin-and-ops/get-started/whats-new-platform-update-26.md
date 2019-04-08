---
# required metadata

title: Preview features in Dynamics 365 for Finance and Operations platform update 26 (May 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operations platform update 26 (May 2019). 
author: tonyafehr
manager: AnnBe
ms.date: 04/05/2019
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
ms.dyn365.ops.version: Platform 26

---
# Preview features in Dynamics 365 for Finance and Operations platform update 26 (May 2019)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 26. This version has a build number of 7.0.5257. For more information about Platform update 26, see [Additional resources](whats-new-platform-update-26.md#additional-resources).

## Business events generally available
Business events are now generally available. This means that business events are out of preview and are available by default, without having to enable the flight.

## 1:N support for Microsoft Flow to subscribe to business events
Multiple Flow apps can subscribe to the same business event in the same legal entity.

## Business events are idempotent
Business events are idempotent. This means that the payload of a business event has a unique and ever increasing number called the ControlNumber. This control number can be used by consumers to apply duplicate detection logic and out of order delivery detection logic to ensure robust processing of events.

## Azure Data Lake integration - CDM folder and model improvements 
Entity store in Azure Data Lake is available as public preview with Platform update 25. In Platform update 26, we have made improvements to the folder structure to enable multiple environments to use the same storage account. We have also included additional properties in the model, including relationships between entities. This will enable relationships in the model to appear in the Power BI dataset with the features introduced by PowerBI.com.

## Feature callouts
New features are regularly being developed for Finance and Operations. While documentation is helpful for explaining new features, raising awareness of these new capabilities to users directly in the product when they are encountered is powerful. To this end, [Feature callouts](../../dev-itpro/user-interface/feature-callouts.md) are available in Platform update 26 to point out a new capability to a user and optionally provide a hyperlink for the user to learn more about the feature.  

## Additional resources

### Platform update 26 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 26, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to be made to the compiler.
