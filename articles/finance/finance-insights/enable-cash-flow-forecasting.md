---
# required metadata

title: Enable cash flow forecasting (preview)
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
# Enable cash flow forecasting (preview)

[!include [banner](../includes/banner.md)]

This topic explains how to turn on the Cash flow forecasts feature in Finance Insights.

> [!NOTE]
> To use payment predictions in the cash flow, you must set up the Customer payment predictions feature as described in [Enable customer payment predictions](enable-cust-paymnt-prediction.md).

1. Use information from the environment page in Microsoft Dynamics Lifecycle Services (LCS) to connect to the primary instance of Azure SQL for that environment. Run the following Transact-SQL (T-SQL) command to turn on flights for the sandbox environment. (You might have to turn on access for your IP address in LCS before you can connect remotely to Application Object Server \[AOS\].)

    `INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('CashflowInsightsFeature', 1)`

    > [!NOTE]
    > Skip this step if you're using version 10.0.20 or later, or if you're using a Service Fabric deployment. The Finance insights team should already have turned on the flight for you. If you don't see the feature in the **Feature management** workspace, or if you experience issues when you try to turn it on, contact <fiap@microsoft.com>.
  
2. Open the **Feature management** workspace, and follow these steps:

    1. Select **Check for updates**.
    2. Turn on the following features:

        - New grid control
        - Grouping in grids (preview) 
        - Customer payment predictions (preview)
        - Cash flow forecasts (preview)

3. Go to **Cash and bank management \> Cash flow forecast setup**, and add the liquidity accounts that should be included in the forecasts.

    > [!NOTE]
    > If liquidity accounts aren't set up, the cash flow can't be generated.

4. Go to **Cash and bank management \> Setup \> Finance Insights (preview) \> Cash flow forecasts (preview)**, and follow these steps:

    1. On the **Cash flow forecast** tab, select **Enable feature**.
    2. Select **Create prediction model**.

For more information about the cash flow forecasting capability, see [Cash flow forecasting](cash-flow-forecast-intro.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
