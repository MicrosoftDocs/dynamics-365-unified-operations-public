---
# required metadata

title: Preview features in Dynamics 365 for Retail version 10.0.3
description: This topic describes features that are in preview in Dynamics 365 for Retail. 
author: josaw1
manager: AnnBe
ms.date: 05/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope:  Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-04-23
ms.dyn365.ops.version: Release 10

---
# Preview features in Dynamics 365 for Retail version 10.0.3

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

This topic describes features that are new or changed in Microsoft Dynamics 365 for Retail in 10.0.3. 

To learn about the features in Microsoft Dynamics 365 for Finance and Operations, see [Preview features in Finance and Operations version 10.0.3 (June 2019)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-3).

## New calculation logic for autocharges in call center for mixed delivery mode sales lines

This feature improves the existing autocharges functionality and support scenarios where retailers would like to apply different charges to sales lines based on mixed carts where different modes of delivery are being applied on different lines.

This new feature adds additional capabilities to the new POS features for autocharges by allowing a more realistic calculation of charges based on the individual sales line characteristics.

## HQ Extensions 

This release adds many extension points in our product so that it can be better customized by the customer. The extension points below have been added in this release to support custom extension scenarios.

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

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.
