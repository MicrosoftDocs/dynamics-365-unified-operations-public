---
# required metadata

title: Preview features in Dynamics 365 for Finance and Operations platform update 26 (May 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operation platform update 26 (May 2019). 
author: tonyafehr
manager: AnnBe
ms.date: 3/18/2019
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

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 26. This version has a build number of 7.0.XXXX. For more information about Platform update 26, see [Additional resources](whats-new-platform-update-26.md#additional-resources).

## Business Events Generally Available
Business events are now generally available. This means, business events are out of preview and is available by default without having to enable the flight.

## 1:N support for Microsoft Flow to subscribe to Business Events
Multiple Flow apps can subscribe to the same business event in the same legal entity.

## Business events are idempotent
Business events are idempotent. This means, the payload of a business event has a unique and ever increasing number called the ControlNumber. This control number can be used by consumers to apply duplicate detection logic and also out of order delivery detection logic to ensure robust processing of events.

## Feature
Feature description and link to topic with details.

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

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.

