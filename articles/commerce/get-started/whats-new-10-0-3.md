---
# required metadata

title: What's new or changed in Dynamics 365 for Retail version 10.0.3
description: This topic describes features that are in preview in Dynamics 365 Retail. 
author: josaw1
ms.date: 06/14/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-04-23
ms.dyn365.ops.version: Release 10

---
# What's new or changed in Dynamics 365 for Retail version 10.0.3

[!include [banner](../../includes/banner.md)]

This topic describes features that are new or changed in Dynamics 365 Retail. 

To learn about the features in Microsoft Dynamics 365 for Finance and Operations, see [What's new or changed in Finance and Operations version 10.0.3 (June 2019)](/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-3).

## New calculation logic for autocharges in call center for mixed delivery mode sales lines

This feature improves the existing autocharges functionality and support scenarios where retailers can apply different charges to sales lines based on mixed carts where different modes of delivery are being applied on different lines.

This feature adds additional capabilities to the new POS features for autocharges by allowing a more realistic calculation of charges based on the individual sales line characteristics.

## HQ extensions 

This release adds numerous extension points so that it's easier to customize Retail. The following extension points have been added to support custom extension scenarios.

- Retail headquarters: Refactored methods to support extensibility. These methods have been refactored to support extensibility through chain of command, delegates, or by providing access to members.
- Methods:

    - Order capture
 
        1. RetailTransactionTransformer.readTransactionSalesTrans
        1. RetailTransactionServiceOrders.createCustomerOrder
        1. Salesline.Insert
        1. Salesline.update

    - Merchandising

        1. RetailBarCodeManagement.CreateBarCodeNoDim
        1. EcoResProductRelationtable.validateWrite

## Additional resources

### Dynamics 365 April '19 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]