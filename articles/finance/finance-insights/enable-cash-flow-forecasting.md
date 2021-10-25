---
# required metadata

title: Enable cash flow forecasting
description: This topic explains how to turn on the Cash flow forecasts feature in Finance Insights.
author: ShivamPandey-msft
ms.date: 07/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-24
ms.dyn365.ops.version: AX 10.0.13

---
# Enable cash flow forecasting

[!include [banner](../includes/banner.md)]

This topic explains how to turn on the Cash flow forecasts feature in Finance Insights.

> [!NOTE]
> To use payment predictions in the cash flow, you must set up the Customer payment predictions feature as described in [Enable customer payment predictions](enable-cust-paymnt-prediction.md).
  
1. Open the **Feature management** workspace, and follow these steps:

    1. Select **Check for updates**.
    2. Go to **All** tab.
    3. Search for **Cash flow forecasts**. If you do not find the feature, try searching for **(Preview) Cash flow forecasts**. 
    4. Turn on the feature.

3. Go to **Cash and bank management \> Cash flow forecast setup**, and add the liquidity accounts that should be included in the forecasts. Also setup **Liquidity account for payments** on **Accounts receivable** and **Accounts payable** tabs. Make sure to recalculate cash flow forecast.

    > [!NOTE]
    > If liquidity accounts aren't set up, the cash flow can't be generated.
    > For more information about the setup, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md).

4. Go to **Cash and bank management \> Setup \> Finance Insights (preview) \> Cash flow forecasts (preview)**, and follow these steps:

    1. On the **Cash flow forecast** tab, select **Enable feature**.
    2. Select **Create prediction model**.

For more information about the cash flow forecasting capability, see [Cash flow forecasting](cash-flow-forecast-intro.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
