---
# required metadata

title: Troubleshoot cash flow forecasting setup
description: This topic provides answers to questions that you might have when you configure cash flow forecasting. It addresses frequently asked questions (FAQ) about the setup for cash flow, updates to cash flow, and cash flow Power BI.
author: panolte
manager: AnnBe
ms.date: 12/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerCovParameters
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte 
ms.search.validFrom: 2020-12-30
ms.dyn365.ops.version: 10.0.15

---

# Troubleshoot cash flow forecasting setup

[!include [banner](../includes/banner.md)]

This topic provides answers to questions that you might have when you configure cash flow forecasting. It addresses frequently asked questions (FAQ) about the setup for cash flow, updates to cash flow, and cash flow Power BI.

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

Verify that the "Cash flow measure V2" and "LedgerCovLiquidityMeasurement" measurements from Entity store have been configured. For more information about how to work with data in Entity store, see [Power BI integration with Entity store](../../fin-ops-core/dev-itpro/analytics/power-bi-integration-entity-store.md) Verify that all the steps that are required to view Power BI content have been completed. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md).

## Have the Entity store entities been refreshed?

You must periodically refresh your entities to ensure that the data is current and accurate. To manually refresh a specific entity, go to **System administration \> Setup \> Entity store**, select the entity, and then select **Refresh**. The data can also be updated automatically. On the **Entity store** page, set the **Automatic refresh enabled** option to **Yes**.
