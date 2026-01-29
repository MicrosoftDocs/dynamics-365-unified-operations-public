---
title: Retail price reports
description: This article provides an overview of the price report feature that can be used to view upcoming price changes for assorted products in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/27/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: shajain
ms.search.validFrom: 2019-01-18
ms.assetid: b1b57734-1406-4ed6-8e28-21c705ee17e2
ms.custom: 
  - bap-template
---

# Retail price reports

[!include [banner](includes/banner.md)]

This article provides an overview of the price report feature that you can use to view upcoming price changes for assorted products in Microsoft Dynamics 365 Commerce.

To provide competitive prices to their customers, retailers often change prices of products. Store managers want the ability to easily access recent or upcoming price changes so that they can plan for the required resources to update the price labels displayed on the store shelves. With release 10.0 of Retail, a store manager can open the **Price** report by navigating to **All stores \> Store \> Price report** and view the updated prices for the products associated to the store. 

To enable the price report, turn on the **Enable price report for store** parameter. Find this parameter in Commerce headquarters at **Commerce parameters \> Discounts \> Miscellaneous**. When you open the **Price report** page, a dialog box appears with various configurations. The available configurations are listed in the following table.

| Configuration | Description |
|---|---|
| From date / To date| The date range for which the price report is generated. The duration is currently limited to seven days. |
| Channel| The store for which the price report is generated. |
| Display products with available inventory| Set this configuration to **Yes** to show only the prices for products that currently have physical inventory available in the store. |
| Display prices for variants | Set this configuration to **Yes** to display the prices of the variants along with the product masters. Turn on this configuration only if you have variant-specific prices, because the number of rows grows large. |
| Display products with price changes | Set this configuration to **Yes** to display the prices for only those dates on which the price changed. The price for *one day before* the selected **From date** always displays, so that the store manager can easily identify products that didn't change prices for the entire selected duration, and can also view the current price. |

After the report is generated, you can download the Excel file for any additional filtering needs. You can also use the price report to check the historical prices of products for past dates.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
