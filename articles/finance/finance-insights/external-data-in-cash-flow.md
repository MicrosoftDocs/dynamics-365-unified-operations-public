---
title: External data in cash flow forecasts
description: Learn about the setup steps that must be completed so that external data can be entered or imported into cash flow forecasts.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-06-08
ms.search.form: LedgerJournalSetup, LedgerJournalTable
ms.dyn365.ops.version: AX 10.0.12
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
---

# External data in cash flow forecasts

[!include [banner](../includes/banner.md)]

You can enter or import external data into cash flow forecasts. This article describes the setup steps that are specific to the use of external data and that enable the external data to be included in a cash flow forecast.

## External data setup

Use the **External source** tab on the **Cash flow forecast setup** page (**Cash and bank management \> Cash flow forecasting \> Cash flow forecast setup**) to enter settings that support the use of external data in cash flow forecasts.

You can enter or import external data into cash flow forecasts. Before you enter or import external data, set up external sources. On the **External source** tab, set up external cash flow categories. A category can be either **Outgoing** or **Incoming**. Select **Liquidity** as the posting type. In the **Legal entity settings** grid, select the legal entities and the corresponding main accounts that the external cash flow categories apply to.

For more information about how to set up cash flow forecasts, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md).

## Enter external data

To enter and modify external data for cash flow forecasts, use the **Open in Excel** experience. Select the **External data** button on the **Cash flow forecast** workspace page, and then select either **Add External Data** or **Edit existing external data**. When the Microsoft Excel file opens, enter information in the following fields:

- **Entry ID** (unique)
- **Description** (optional)
- **External Source name** – Select one of the values in the list that you defined when you set up Finance insights.
- **Legal Entity**
- **Date**
- **Amount in transaction currency**
- **Currency Code**
- **Default Dimension** (optional)
- **Document number** (optional)
- **Account number** (optional)
- **Account name** (optional)

## Import external data by using the Data Management framework

You can import external data for cash flow forecasts by using the **Data Management** workspace and the entity named **Cash flow forecast external source entry**.

To move setup data from one environment to another, use the following entities for the required setup tables:

- Cash flow forecast external source setup
- Cash flow forecast external source legal entity setup

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
