---
# required metadata

title: Preview features in Finance and Operations version 10.0.6 (November 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0.6. This version will be released in October.
author: tonyafehr
manager: AnnBe
ms.date: 08/15/2019
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
ms.search.validFrom:  
ms.dyn365.ops.version: Release 10.0.6

---
# Preview features in Finance and Operations version 10.0.6 (November 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0.6. This version has a build number of 10.0.XXX. While the general availability date is in November, the new features are available for early release in October. For more information about version 10.0.6, see [Additional resources](whats-new-changed-10-0-5.md#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [Preview features in Dynamics 365 for Retail version 10.0.6](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new-10-0-6).

## title

description of feature

## Product configuration models V2 data entity

A second version for the “product configuration models” data entity is released (called “products configuration models V2”). The default template “418-product configuration models” is also needs to be so that it uses the new “product configuration models V2” data entity in the import/export framework templates. 
The template will not be auto-updated so that you will have to load the template from the default manually. The V2 entity exports one row as separate file in an attachment instead of inline, solving the size limitations of the V1 entity. 
 
What do you need to do to take this change?
-	As the V1 entity has been deprecated, you should start migrating from V1 to V2. If you are using the  “418-product configuration models” template, you can click on “load default templates” button and reload the template “418 – product configuration models”
-	If you need to keep compatibility with existing systems, you can for now continue using the existing template and the (deprecated) V1 entity until you move your integrations to the new template. 

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.6, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=348248&dbType=3&qc=71f7c009fafc56f21399d05a7062454208256c806b7f5c706a89f4452964c26e).

### Platform update 30
Microsoft Dynamics 365 for Finance and Operations version 10.0.6 includes Platform update 30. To learn more about Platform update 30, see [Preview features in Finance and Operations platform update 30 (November 2019)](whats-new-platform-update-30.md).

### Dynamics 365: 2019 release wave 2 plan
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
