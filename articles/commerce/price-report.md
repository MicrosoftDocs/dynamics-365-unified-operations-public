---
title: Retail price reports
description: This article provides an overview of the price report feature that can be used to view upcoming price changes for assorted products in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/30/2023
ms.topic: overview
audience: Application user
ms.reviewer: josaw
ms.search.region: global
ms.author: shajain
ms.search.validFrom: 2019-01-18
ms.assetid: b1b57734-1406-4ed6-8e28-21c705ee17e2

---

# Retail price reports

[!include [banner](includes/banner.md)]

This article provides an overview of the price report feature that can be used to view upcoming price changes for assorted products in Microsoft Dynamics 365 Commerce.

In order to provide competitive prices to their customers, retailers often change prices of products. Store managers want the ability to easily access recent or upcoming price changes so that they can plan for the required resources to update the price labels displayed on the store shelves. With release 10.0 of Retail, a store manager can open the **Price** report by navigating to **All stores \> Store \> Price report** and viewing the updated prices for the products associated to the store. 

To enable the price report, the **Enable price report for store** parameter must be turned on. This parameter is located in Commerce headquarters at **Commerce parameters \> Discounts \> Miscellaneous**. Opening the **Price report** page displays a dialog box with various configurations. The available configurations are listed below.

> [!NOTE]
> The **Enable price report for store** parameter is deprecated in the 10.0.31 release and will be removed in October 2023. The price report is always accessible in the form as a standard function.

| Configuration | Description |
|---|---|
| From date / To date| The date range for which the price report should be generated. The duration is currently limited to seven days. |
| Channel| The store for which the price report should be generated. |
| Display products with available inventory| Setting this configuration to **Yes** will only show the prices for products that currently have physical inventory available in the store. |
| Display prices for variants | Setting this configuration to **Yes** will display the prices of the variants along with the product masters. This configuration should only be turned **On** if you have variant-specific prices, because the number of rows grows very large. In future releases, we'll enable the dimensions-based prices so that the store manager can choose the dimensions for which the prices should be displayed. |
| Display products with price changes | Setting this configuration to **Yes** will display the prices for only those dates on which the price has been changed. The price for *one day before* the selected **From date** will always be displayed, so that the store manager can easily identity products that haven't changed prices for the entire selected duration, and can also view the current price. |

After the report is generated, the Excel file can be downloaded for any additional filtering needs. The price report can also be used to check the historical prices of products for past dates.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
