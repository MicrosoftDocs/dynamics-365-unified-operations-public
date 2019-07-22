---
# required metadata

title: Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operations platform update 29 (October 2019). 
author: tonyafehr
manager: AnnBe
ms.date: 07/09/2019
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
ms.dyn365.ops.version: Platform 29

---
# Preview features in Dynamics 365 for Finance and Operations platform update 29 (October 2019)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 29. This version has a build number of 7.0.XXXX. For more information about Platform update 29, see [Additional resources](whats-new-platform-update-28.md#additional-resources).


## Feature management
The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. In Platform update 29, additional features have been added, including:
- Enable all features that are not enabled
- Automatically enable all features after an update
- Do not allow a feature to be enabled based on a condition such as an existing config key is turned on
- Add a button called Check for updates that manually searches for new features and adds them to the list of features

## Data management job history clean up
The job history clean-up functionality in data management must be used to schedule a periodic cleanup of the execution history. This functionality is a step up to the existing staging table clean up functionality which is now deprecated.

## Business events catalog security
Role based security can be now applied to individual business events in the business event catalog. Once this security is enabled and configured, users will be able to only view and subscribe to business events to which thier role(s) have access. This security applies to integration scenarios like Microsoft Flow as well.

## Attachment recovery
An attachment recovery feature has been added that provides a recycle bin for record attachments. For a configured period of time after deletion, users and administrators can recover deleted attachments using the new deleted attachments forms. For more details, see [Configure document management](../../fin-and-ops/organization-administration/configure-document-management).

## Feature
A brief description of the feature, including a link to a topic where customers can read the details.

## Additional resources

### Platform update 29 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 29, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
