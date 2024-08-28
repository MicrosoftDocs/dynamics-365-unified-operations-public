---
title: What's new or changed in Platform update 30 for finance and operations apps (November 2019)
description: Learn about features that are new or changed in Platform update 30 for finance and operations apps in the update available as of November 2019.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: Platform update 30
---

# What's new or changed in Platform update 30 for finance and operations apps (November 2019)

[!include [banner](../includes/banner.md)]

This article describes features that are new or changed for Platform update 30 for finance and operations apps. This version has a build number of 7.0.5407. While the general availability date is in November, the new features are available for early release in September. For more information about Platform update 30, see [Additional resources](whats-new-platform-update-30.md#additional-resources).

## Readable date time format for dateTime fields in business event payload
When a new business event is coded, a dateTime field can be enabled to output the value in a human readable format in the business event payload. Existing business event can also be modified to include a readable dateTime field in the payload thereby, preserving compatibility. The developer documentation for this is described in [Business events developer documentation](../../dev-itpro/business-events/business-events-dev-doc.md).

## Hide fields faster in personalization mode
Hiding fields in personalization mode is now **significantly** faster. Instead of waiting for confirmation from the system that a selected control can be hidden, this check is now being done asynchronously, which allows users to hide controls as fast as they can click them. This same optimization has also been applied for skipping controls, locking fields, and adding fields as FastTab summary fields.   

## Extensibility enhancements
The following enhanced extensibility capabilities have been added in Platform update 30:

- Improve handling of form extension scenarios involving extension field groups that are extended again (Ref# 236593).
- Enable Default Action property on FormGridControl to use buttons added via Extension (Ref# 322756).
- Add post event handlers for delete events on form datasources into the transaction scope (Ref# 237952).
- Encourage customers/partners not to extend "internal" classes by adding a warning (Ref# 338010).
- Improve use of the SysPlugin pattern from X++ by adding better support for multiple key values and key values of different types (Ref# 330178).

## Feature Class property added into metamodel to support metadata association with features defined for Feature Management
A **Feature Class** property has been added into the metamodel and can be seen on multiple types in the Application Explorer in Visual Studio. This property is a lookup that points at features defined for Feature Management. This property currently has no effect. In the future, developers will use this property to ensure that pieces of metadata are only visible to users when the corresponding feature has been enabled in the Feature Management workspace. Currently, if the **Feature Class** property is set to a value, it results in a build warning so the developer is aware that it won't have any effect. The new property is visible on a few types including Menus and MenuItems, but will eventually be visible on Forms, Form Controls, and other types.
In the future, the first metadata types to get **Feature Class** property support will be Menus and MenuItems which will allow developers to only have those menu options available when the corresponding feature has been enabled. The runtime support for Menus and MenuItems is scheduled to be delivered in Platform Update 31.
Currently, the Feature Class property and the FeatureStateProvider API can be used to reference an existing feature in Feature Management, but additional features cannot be defined. That support is likely to be enabled once the **Feature Class** property work is complete. 

## New license types support associating users with a license
New license types are being made available to new customers. For customers on those new licenses, users need to be associated with a license. If a license is associated with a new user, the first time they sign in they are be added as a system user. If a license is not associated with a user, then they recieve a brief warning.


## Additional resources

### Platform update 30 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 30, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?kb=4520346&bugId=369591&dbType=3&qc=a1f7377056b8d98314a62c745da88565f03531d15de24c4a538132d68118059c).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
