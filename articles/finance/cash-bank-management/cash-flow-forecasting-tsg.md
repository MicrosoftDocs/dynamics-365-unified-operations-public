---
title: Troubleshoot cash flow forecasting 
description: Learn how to troubleshoot common issues with cash flow forecasting in Microsoft Dynamics 365 Finance.
author: mukumarm
ms.author: mukumarm
ms.topic: troubleshooting-general
ms.date: 07/13/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-12-30
ms.search.form: LedgerCovParameters
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot cash flow forecasting setup

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to troubleshoot common problems that can occur when you use **Cash flow forecasting** and the Cash overview Microsoft Power BI reports in Microsoft Dynamics 365 Finance.

Cash flow forecasting helps organizations analyze upcoming cash flow and currency requirements so that they can estimate future cash needs. Cash overview Power BI content provides visibility into cash flow and forecasts, and lets users analyze cash by legal entity, currency, and bank account.

## Why is cash flow shown for only one legal entity?

You configure and calculate cash flow forecasting per legal entity. Power BI reports and the cash flow forecasts capability in Finance insights show the results.

Cash flow forecasting must be set up for each legal entity that you want to see a forecast for. Review the configuration of cash flow forecasting in all your legal entities. Alternatively, review the configuration of all the legal entities for cash flow forecasting, and make sure that they're set as you intended.

## Why doesn't Power BI show all the cash flow data or the Cash flow Power BI report is empty

Before cash flow forecasts can appear in Power BI views, you must complete several steps. Review the following checklist, and make sure that every step is completed:

- Set up cash flow for each legal entity.
- In **General ledger parameters**, set the system currency and the system exchange rate type.
- Set the ledger accounting currency and the exchange rate type.
- Enter exchange rates between the transaction currency and the accounting currency.
- Enter exchange rates between the accounting currency and the system currency.
- Enter exchange rates between the accounting currency and each bank currency.
- Define the date dimension. Go to **Organization administration** > **Setup** > **Calendars** > **Date dimensions** and make sure that the date range has an **End date** that extends into the future.

## Why did cash flow Power BI work in previous versions but is now blank?

Verify that the "Cash flow measure V2" and "LedgerCovLiquidityMeasurement" measurements from Entity store are configured. For more information about how to work with data in Entity store, see [Power BI integration with Entity store](../../fin-ops-core/dev-itpro/analytics/power-bi-integration-entity-store.md). Verify that you completed all the steps that are required to view Power BI content. For more information, see [Cash overview Power BI content](Cash-Overview-Power-BI-content.md).

## Cash flow results appear incorrect

When multiple bank accounts use the same liquidity account, cash flow reporting aggregates data at the backing liquidity account level. Because of this aggregation, the report might not separate cash flow balances by individual bank account.

Use a separate liquidity account for each bank account when bank-level separation is required in cash flow reporting. This behavior is by design. A warning is shown during bank account setup when multiple bank accounts use the same liquidity account. Don't configure multiple bank accounts with the same liquidity account when separate cash flow reporting by bank account is required.

## Cash flow forecast is calculated by main account instead of bank account

Cash flow forecast reporting displays the balance of the main account that is linked to the bank account. The system doesn't separate bank account balances when multiple bank accounts are linked to the same main account.

Review the liquidity account setup for bank accounts. If separate cash flow forecast reporting is required by bank account, configure bank accounts so that each bank account uses a separate liquidity account.

## Error: An exchange rate can't be found when calculating cash flow forecast for purchase orders

When you calculate cash flow forecasts for purchase orders, you receive an error that resembles the following message:

Document: Purchase order, Number: 0008574771, Details: An exchange rate cannot be found for exchange rate type Default between currencies USD and NZD on exchange date.

In this error message, the exchange date is blank.

This issue can occur when the applicable **Sales tax settlement period** doesn't include the tax date of the purchase order. Because the settlement period interval isn't available for the purchase order tax date, the cash flow forecast calculation can't determine the exchange date that is required to find the exchange rate.

Configure the **Sales tax settlement period** so that the settlement period intervals include the tax dates of the affected purchase orders. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax settlement periods**.

## Are the Entity store entities refreshed?

You must periodically refresh your entities to ensure that the data is current and accurate. To manually refresh a specific entity, go to **System administration \> Setup \> Entity store**, select the entity, and then select **Refresh**. You can also update the data automatically. On the **Entity store** page, set the **Automatic refresh enabled** option to **Yes**.

## Which calculation method should be used when calculating cash flow forecasts?

The Cash flow forecast calculation method has two important selection options. The **New** option calculates cash flow forecasts for new documents and documents that changed since the last batch job ran. This option tends to run faster because it processes a smaller subset of documents. The **Total** option recalculates cash flow forecasts for every document in the system. This option takes more time because it has more work to complete.

### How can I improve the performance of the cash flow forecasting recurring batch job?

Run your cash flow forecast once each day during the off-peak hours by using the **New** calculation method. Use this approach six days per week. Then, run a cash flow forecast once each week by using the **Total** calculation method on the day with the least amount of activity.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
