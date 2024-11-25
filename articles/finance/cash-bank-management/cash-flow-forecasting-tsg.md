---
title: Troubleshoot cash flow forecasting setup
description: Access answers to questions that you might have when you configure cash flow forecasting, including questions about setup and cash flow Power BI.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 03/23/2021
ms.custom:
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-12-30
ms.search.form: LedgerCovParameters
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot cash flow forecasting setup

[!include [banner](../includes/banner.md)]

This article provides answers to questions that you might have when you configure cash flow forecasting. It addresses frequently asked questions (FAQ) about the setup for cash flow, updates to cash flow, and cash flow Power BI.

## Why is cash flow shown for only one legal entity?

Cash flow forecasting is configured and calculated per legal entity. Power BI reports and the cash flow forecasts capability in Finance insights show the results.

Cash flow forecasting must be set up for each legal entity that you want to see a forecast for. Review the configuration of cash flow forecasting in all your legal entities. Alternatively, review the configuration of all the legal entities for cash flow forecasting, and make sure that they are set as you intended.

## Why doesn't Power BI show all the cash flow data?

Several steps must be completed before cash flow forecasts can appear in Power BI views. Review the following checklist, and make sure that every step has been completed:

- Set up cash flow for each legal entity.
- In General ledger parameters, set the system currency and the system exchange rate type.
- Set the ledger accounting currency and the exchange rate type.
- Enter exchange rates between the transaction currency and the accounting currency.
- Enter exchange rates between the accounting currency and the system currency.
- Enter exchange rates between the accounting currency and each bank currency.

## Why did cash flow Power BI work in previous versions but is now blank?

Verify that the "Cash flow measure V2" and "LedgerCovLiquidityMeasurement" measurements from Entity store have been configured. For more information about how to work with data in Entity store, see [Power BI integration with Entity store](../../fin-ops-core/dev-itpro/analytics/power-bi-integration-entity-store.md). Verify that all the steps that are required to view Power BI content have been completed. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md).

## Have the Entity store entities been refreshed?

You must periodically refresh your entities to ensure that the data is current and accurate. To manually refresh a specific entity, go to **System administration \> Setup \> Entity store**, select the entity, and then select **Refresh**. The data can also be updated automatically. On the **Entity store** page, set the **Automatic refresh enabled** option to **Yes**.

## Which calculation method should be used when calculating cash flow forecasts?

The Cash flow forecast calculation method has two important selection options. The **New** option will calculate cash flow forecasts for new documents and documents that have changed since the last batch job ran. This option tends to run faster because it processes a smaller subset of documents. The **Total** option will recalculate cash flow forecasts for every document in the system. This option takes more time because it has more work to complete.

### How do I improve the performance of the cash flow forecasting recurring batch job?

We recommend running your cash flow forecast once each day during the off-peak hours using the **New** calculation method. We recommend using this approach six days per week. Then run a cash flow forecast once each week using the **Total** calculation method on the day with the least amount of activity.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

