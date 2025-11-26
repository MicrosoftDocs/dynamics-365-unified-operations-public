---
title: Demo data overview
description: Learn about demo data via an overview, including a table that defines various legal entities and an overview of embedded analytics.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 10/30/2025
ms.reviewer: johnmichalak
ms.collection: get-started
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: d876e8de-d547-43e5-9259-f095821dc758
---

# Demo data overview

[!include [banner](../../../finance/includes/banner.md)]

This article provides an overview of the available demo data.

Use demo data as the base data set for implementation support and demonstration purposes. The current demo data set supports the following verticals:

- Commerce
- Distribution
- Service Industries
- Public Sector
- Discrete & Process Manufacturing

The demo data set supports 40 languages across 16 countries or regions. It also supports various implementation scenarios. The following table lists the legal entities that are included in the demo data set.

| Legal entity | Description                          |
|--------------|--------------------------------------|
| BRMF         | Contoso Entertainment System Brazil  |
| CNMF         | Contoso Entertainment China          |
| DAT          | Default Company                      |
| DEMF         | Contoso Entertainment System Germany |
| FRRT         | Contoso Retail FR                    |
| FRSI         | Contoso Consulting FR                |
| GBSI         | Contoso Consulting GB                |
| GLCO         | Contoso Group                        |
| GLMF         | Contoso Entertainment System         |
| GLRT         | Contoso Retail                       |
| GLSI         | Contoso Consulting                   |
| INMF         | Contoso India                        |
| ITCO         | Contoso Italy                        |
| JPMF         | Contoso Entertainment Japan          |
| MXMF         | Contoso Entertainment System Mexico  |
| MYMF         | Contoso Entertainment System MYMF    |
| RUMF         | Contoso Entertainment System Russia  |
| RURT         | Contoso Retail RUS                   |
| US01         | Contoso US01                         |
| USMF         | Contoso Entertainment System USA     |
| USP2         | Contoso Orange Juice                 |
| USPI         | Contoso Process Industry             |
| USRT         | Contoso Retail USA                   |
| USSI         | Contoso Consulting USA               |
| USSW         | Contoso Shared Warehouse USA         |

## Embedded analytics

The demo data updates five companies to provide better reports on the new embedded analytics within workspace. Filter the embedded analytics to the following legal entities for the improved report data:

| Legal entity | Description                          |
|--------------|--------------------------------------|
| DEMF         | Contoso Entertainment System Germany |
| GLMF         | Contoso Entertainment                |
| USMF         | Contoso Entertainment System USA     |
| USRT         | Contoso Retail USA                   |
| USSI         | Contoso Consulting USA               |

Reports from the Cash overview Power BI content display in the **Cash overview** and **Bank management** workspaces.

To view the Cash flow forecasting reports with data, you must first run the forecast calculation process by using the **Calculate cash flow forecasts** function from the **Cash and bank management area**. You need to complete this process for each company included in the forecast. You then need to refresh the LedgerCovLiquidityMeasurement aggregate measure on the **Entity Store** page.

For demonstration purposes, you can add cash flow forecasting demo data by using the **Generate data** page from the **Demo data** module. This script inserts data into the cash flow forecasting tables to quickly populate information necessary for reports.

You can view the credit and collections analytics on the **Manage customer credit and collections** workspace. To view the analytics, you need to refresh the CustCollectionsBIMeasurements aggregate measure on the **Entity Store** page.

You can view the vendor payments analytics on the **Vendor payments** workspace. To view the analytics, you need to refresh the VendPaymentBIMeasure aggregate measure on the **Entity Store** page.

You can view the Purchase performance analytics on the **Purchase spend analysis** page from the Procurement and sourcing module. To view the analytics, you need to refresh the Purchase cube aggregate measure on the **Entity Store** page.

You can view the Sales and profitability analytics on the **Sales and profitability performance** page from the Sales and marketing module. To view the analytics, you need to refresh the sales cube aggregate measure on the **Entity Store** page.

You can view the production performance analytics on the **Production performance** page from the Production control module. To view the analytics, you need to refresh the Production cube aggregate measure on the **Entity Store** page.

For demonstration purposes, you can add production performance demo data by using the **Generate data** page from the Demo data module. This script generates production orders and associated feedback journals to populate the production performance reports with data.

You can view the warehouse performance analytics on the **Warehouse performance** page from the Warehouse management module. To view the analytics, you need to refresh the Warehouse aggregate measure on the **Entity Store** page.

For demonstration purposes, you can add warehouse performance demo data by using the **Generate data** page from the Demo data module. This script generates sales orders and warehouse work to populate the warehouse performance reports with data.

The demo data module is only available if you deploy the Demo data suite model on the environment.

## Vendor collaboration

In the USMF demo company, use three purchase orders for vendor US-104 for demonstration purposes. Sign in as user ErinH, a contact person who has access to vendor collaboration for US-104.

## Purchase order approval

In the USMF demo company, use two purchase orders for INGA to approve. Sign in as user INGA to see the purchase orders awaiting approval.

## Batch transfer rules for subledger journals

Change the batch transfer rules for subledger journal account entries to **Scheduled batch** to reflect a best practice. Configure the batches to run every 10 minutes. Accounting entries for all source documents don't appear in General ledger until the batch process runs. If you need to see the immediate effect in General ledger, set the **Transfer mode** to **Synchronous** on the **Batch transfer rules** page within **General ledger** parameters. While Synchronous works well for product demos and environments with low transaction volumes, it can cause performance issues in larger transaction volume environments.

:::image type="content" source="../../fin-ops/get-started/media/GL-parameters.PNG" alt-text="Screenshot of General ledger parameters.":::

## Cost accounting

Create three Cost accounting ledgers in demo data. The Cost accounting ledger USP2 provides an E2E demo experience based on data from legal entity USP2. The Cost control unit consists of two Cost object dimensions (Cost centers and Product groups). Actual cost, Budget cost, and Statistical measures are transferred for all 12 fiscal periods of year 2017. Overhead calculation is also performed for all fiscal periods of year 2017.

Configure but don't enable access level security. Enable this security in the **Cost accounting parameters** page.

:::image type="content" source="../../fin-ops/get-started/media/Cost-accounting-parameters.PNG" alt-text="Screenshot of Cost accounting parameters.":::

After you enable access level security, assign an employee to the role Cost object controller. Sign in as the employee and access the **Cost control** workspace. The employee can now see their Cost center performance and drill into details of how these values were calculated.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
