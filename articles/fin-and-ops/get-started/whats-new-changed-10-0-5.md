---
# required metadata

title: Preview features in Finance and Operations version 10.0.5 (August 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0.5. This version will be released in August.
author: tonyafehr
manager: AnnBe
ms.date: 05/29/2019
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
ms.dyn365.ops.version: Release 10.0.5

---
# Preview features in Finance and Operations version 10.0.5 (August 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0.5. This version will be released in August and has a build number of 10.0.xxx. For more information about version 10.0.5, see [Additional resources](whats-new-changed-10-0-5.md#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [Preview features in Dynamics 365 for Retail version 10.0.5](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/get-started/whats-new-10-0-5).

## Gender in currency declension for Eastern Europe 

You can now define the currency gender. 
On **Currecnies** page, click **Declension**. In the **Gender** field, select **Masculine**, **Feminine**, or **Neuter**. This parameter may have influence on declension of amount written in text in local language on Cash order. For example, amount 1,01 EUR is written in English text as *One euro 01 cent* on Cash order. When you set up **Gender** for EUR currency as **Neuter**, this amount will be translated to Czech language and written on Cash order as *Edno euro 01 cent*

For more information about existing functionality, see [Update how amounts are displayed on reports and documents](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/emea-amount-printing-forms).



## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.4, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=320385&dbType=3&qc=d5539716f56ccea45e2187c269570772af20e1f10a78371811220da6315a3c34).

### Platform update 28
Microsoft Dynamics 365 for Finance and Operations version 10.0.4 includes Platform update 28. To learn more about Platform update 28, see [Preview features in Finance and Operations platform update 28 (July 2019)](whats-new-platform-update-28.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
