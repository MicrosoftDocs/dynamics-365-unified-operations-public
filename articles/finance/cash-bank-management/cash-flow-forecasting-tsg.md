---
# required metadata

title: Cash flow forecasting
description: This topic provides an overview of the cash flow forecasting process. It also explains how cash flow forecasting is integrated with other modules in the system.
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

# Troubleshoot Cash flow forecasting setup

[!include [banner](../includes/banner.md)]

This topic provides answers to questions that you might have when you configure cash flow forecasting[?]. It addresses frequently asked questions about how to setup cash flow, updates to cash flow, and cash flow Power BI. 

## Why does cash flow only show up for one legal entity?
Cash flow forecasting is configured and calculated per legal entity. The results are visualized in Power BI reports and in the Cash flow forecasts capability in Finance insights.  Cash flow forecasting must be set up for each legal entity that you’d like to see a forecast for. Review the configuration for cash flow forecasting in all your legal entities. alt: Review the configuration of all the legal entities for cash flow forecasting to ensure that they’re set as you intended.

## Why doesn’t the Power BI show all the cash flow data?
There are a number of steps to complete for cash flow forecasts to display in Power BI views. Review the following checklist to ensure that each step has been completed:

•	Cash flow is setup for each legal entity.
•	General ledger parameters for System currency and System exchange rate type have been set.
•	The ledger accounting currency and exchange rate type have been set.
•	Exchange rates between transaction currency and accounting currency have been entered.
•	Exchange rates between accounting currency and system currency have been entered.
•	Exchange rates between accounting currency and each bank currency have been entered.

## Why did cash flow PowerBI work on previous versions but is now blank?
Verify that the “Cash flow measure V2” and “LedgerCovLiquidityMeasurement” measurements from the entity store have been configured. Look for content on the entity store. For more information, see [Power BI integration with entity store](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/power-bi-integration-entity-store?toc=/dynamics365/finance/toc.json) 
Verify that the steps necessary for viewing Power BI content have been completed. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md). 

## Have the entity store entities been refreshed? 
It’s necessary to refresh your entities periodically to ensure that the data is current and accurate. Open System administration > Setup > Entity store to access the entity store. Select a specific entity to refresh and click the Refresh button. You can also set the Automatic refresh enabled option to Yes.
