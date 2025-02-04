---
title: What's new or changed in finance and operations apps version 10.0.6 (November 2019)
description: Learn about new or changed features in finance and operations apps version 10.0.6. This version was released in November 2019.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.dyn365.ops.version: Release 10.0.6 
---

# What's new or changed in finance and operations apps version 10.0.6 (November 2019)

[!include [banner](../../../finance/includes/banner.md)]


This article describes features that are either new or changed in finance and operations apps, including Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Supply Chain Management for version 10.0.6. This version has a build number of 10.0.234. While the general availability date is in November, the new features are available for early release in October. For more information about version 10.0.6, see [Additional resources](#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 Retail, see [What's new or changed in Dynamics 365 Retail version 10.0.6](../../../commerce/get-started/whats-new-10-0-6.md).

## Product configuration models V2 data entity

A second version for the “product configuration models” data entity is released (called “products configuration models V2”). The default template “418-product configuration models” is also needs to be so that it uses the new “product configuration models V2” data entity in the import/export framework templates. 
The template will not be auto-updated so that you will have to load the template from the default manually. The V2 entity exports one row as separate file in an attachment instead of inline, solving the size limitations of the V1 entity. 
 
What do you need to do to take this change?
-	As the V1 entity has been deprecated, you should start migrating from V1 to V2. If you are using the  “418-product configuration models” template, you can click on “load default templates” button and reload the template “418 – product configuration models”
-	If you need to keep compatibility with existing systems, you can for now continue using the existing template and the (deprecated) V1 entity until you move your integrations to the new template. 

## Feature management enhancements
Feature management now allows you to enable all new features by default, require confirmation to enable a feature, and enable all features that have not already been enabled. 

## Project contract committed detail
You can now drilldown into the details of the committed amount on the funding source of a project contract, allowing the user to easily see the activity that makes up the committed amount.

## Purchase agreement responsible party
You now have the ability to define primary and secondary responsible parties on the Purchase agreement classification form and resulting Purchase agreements.  This provides the user access to who oversees the agreements.

## RFQ link on the Purchase order line
You can add a reference link from the Purchase order lines back to the corresponding RFQ lines they originated from, allowing the user to easily be provided with the supporting request for quotation document.

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of version 10.0.6, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=369581&dbType=3&qc=ba058110be40fe16a39469298041b1a7baf82eb65bb9df4d864602d2c6bf93d7).

### Platform update 30
Version 10.0.6 includes Platform update 30. To learn more about Platform update 30, see [What's new or changed in Platform update 30 for finance and operations apps (November 2019)](../../fin-ops/get-started/whats-new-platform-update-30.md).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

