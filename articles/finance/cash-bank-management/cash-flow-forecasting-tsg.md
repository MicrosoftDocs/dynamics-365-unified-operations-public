---
# required metadata

title: Troubleshoot cash flow forecasting setup
description: This topic provides answers to questions that you might have when you configure cash flow forecasting. It addresses frequently asked questions about how to set up cash flow, updates to cash flow, and cash flow Power BI.
author: panolte
manager: AnnBe
ms.date: 12/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  LedgerCovParameters
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

This topic provides answers to questions that you might have when you configure cash flow forecasting. It addresses frequently asked questions about how to set up cash flow, updates to cash flow, and cash flow Power BI. 

## Why does cash flow only show up for one legal entity?
Cash flow forecasting is configured and calculated per legal entity. Power BI reports display the results, as does the Cash flow forecasts capability in Finance insights.  Cash flow forecasting must be set up for each legal entity that you’d like to see a forecast for. Review the configuration for cash flow forecasting in all your legal entities. alt: Review the configuration of all the legal entities for cash flow forecasting to ensure that they’re set as you intended.

## Why doesn’t the Power BI show all the cash flow data?
There are a number of steps to complete for cash flow forecasts to display in Power BI views. Review the following checklist to ensure that each step has been completed:

- Cash flow is set up for each legal entity.
- General ledger parameters for System currency and System exchange rate type have been set.
- The ledger accounting currency and exchange rate type have been set.
- Exchange rates between transaction currency and accounting currency have been entered.
- Exchange rates between accounting currency and system currency have been entered.
- Exchange rates between accounting currency and each bank currency have been entered.

## Why did cash flow Power BI work on previous versions but is now blank?
Verify that the “Cash flow measure V2” and “LedgerCovLiquidityMeasurement” measurements from the entity store have been configured. For more information working with data in the entity store, see [Power BI integration with entity store](../../fin-ops-core/dev-itpro/analytics/power-bi-integration-entity-store.md) Verify that the steps necessary for viewing Power BI content have been completed. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md). 

## Have the entity store entities been refreshed? 
It’s necessary to refresh your entities periodically to ensure that the data is current and accurate. Open Entity store page (**System administration > Setup > Entity store**) . Select a specific entity to refresh, and click the **Refresh** button. The data can also be refreshed automatically by setting the **Automatic refresh enabled** option to **Yes** on the **Entity store** page.
