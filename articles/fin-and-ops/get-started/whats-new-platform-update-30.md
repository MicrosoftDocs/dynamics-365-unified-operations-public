---
# required metadata

title: Preview features in Dynamics 365 for Finance and Operations platform update 30 (November 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operations platform update 30. 
author: tonyafehr
manager: AnnBe
ms.date: 08/13/2019
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
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Platform update 30

---
# Preview features in Dynamics 365 for Finance and Operations platform update 30 (November 2019)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 30. This version has a build number of 7.0.XXXX. While the general availability date is in November, the new features are available for early release in September. For more information about Platform update 30, see [Additional resources](whats-new-platform-update-28.md#additional-resources).

## Readable date time format for dateTime fields in business event payload
When a new business event is coded, a dateTime field can be enabled to output the value in a human readable format in the business event payload. Existing business event can also be modified to include a readable dateTime field in the payload thereby, preserving compatibility. The developer documentation for this is described in [Business events developer documentation](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/business-events/business-events-dev-doc).

## Hide fields much faster in personalization mode
Hiding fields in personalization mode is now **significantly** faster. Instead of waiting for confirmation from the system that a selected control can be hidden, this check is now being done asynchronously which allows users to hide controls as fast as they can click them. This same optimization has also been applied for skipping controls, locking fields, and adding fields as FastTab summary fields.   

## Feature name
Provide a brief description of the feature and link to the topic where they can read the details.

## Feature name
Provide a brief description of the feature and link to the topic where they can read the details.

## Feature name
Provide a brief description of the feature and link to the topic where they can read the details.

## Feature name
Provide a brief description of the feature and link to the topic where they can read the details.

## Additional resources

### Platform update 30 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 30, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
