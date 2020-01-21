---
# required metadata

title: Preview features in Dynamics 365 Finance version 10.0.8 (February 2020)
description: This topic describes features that are either new or changed in Dynamics 365 Finance version 10.0.8.
author: roschlom
manager: AnnBe
ms.date: 11/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2019-11-20 
ms.dyn365.ops.version: 10.0.8

---
# Preview features in Dynamics 365 Finance version 10.0.8 (February 2020)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes preview features that are new or changed for Platform update 32 for Microsoft Dynamics 365 Finance, version 10.0.8. This version has a build number of 8.0.xxxx and is available as follows:

- Preview release: December 2019.
- General availability (self-update): January 2020.
- Auto-update: February 2020.

For more information about Platform update 32, see [Additional resources](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32.md#additional-resources).

## Expense receipt processing

[!NOTE]
> - This feature currently only supports the English language receipts.
> - This feature is currently only supported in the United States.
> - This feature does not use your data to build the learning. We have built a general machine learning model for receipt processing that is not based on the receipts you upload.
> - Dynamics 365 Finance will reach out to our Cognitive Services in order to extract the field data, the cognitive services will retain a copy of your receipt for up to 24 hours while processing completes. Once completed Cognitive Services will remove the receipt. Receipts are stored within Dynamics 365 Finance. Reference [Enable receipt understanding with Form Recognizer's new capability](https://azure.microsoft.com/en-us/blog/enable-receipt-understanding-with-form-recognizer-s-new-capability/)

Expense entry has been enhanced through the introduction of Receipt OCR processing, designed to improve the end user experience when creating expense reports.

Key features:
- Extracts Merchant name, Date and Total amount from a receipt
- Attempts to match the receipt to an expense transaction

This feature is supported using the **Expense reports re-imagined** feature. To turn on this feature, use the **Feature management** workspace and enable **Expense reports re-imagined** and **Auto-match and create expense from receipt** features.

For more information, see [Expense reports reimagined](ExpenseWorkspaceNew.md).



## Additional resources

### Platform update xx

Microsoft Dynamics 365 Supply Chain Management 10.0.8 includes Platform update 32. To learn more about Platform update xx, see [Preview features in Platform update 32](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-xx.md).


### Bug fixes 
For information about the bug fixes included in each of the updates that are part of 10.0.7, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=386529&dbType=3&qc=e03ced97fa18dc4439f36de17b00da7257dc15869a72e5b2435fec0acec0c493).


### Dynamics 365: 2019 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2019 release wave 2 plan](https://docs.microsoft.com/en-us/dynamics365-release-plan/2019wave2/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.
