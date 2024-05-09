---
title: Currency capabilities in financial reporting
description: Learn about financial reporting includes features that support complex currency reporting requirements, including an outline on filtering by currency.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 07/27/2021
ms.reviewer: kfend
audience: IT Pro, Developer 
ms.search.region: Global
ms.search.validFrom: 2020-01-09
ms.search.form: FinancialReports
ms.dyn365.ops.version: Version 10.0.8
---

# Currency capabilities in financial reporting

[!include [banner](../includes/banner.md)]

Financial reporting includes features that support complex currency reporting requirements. Financial reporting can generate reports using any of the following currency amounts:

- Accounting currency amount 
- Reporting currency amount 
- Transaction currency amount 
- Translated amount (currency translation is also known as conversion), translated to any currency that has been set up in the system

## Filtering by currency
By default, all report amounts are summarized and presented in the accounting currency of the relevant company. If you need to do additional analysis by the transactions and related currencies, you can do so by setting filters on the report. 

- In the column definition, you can use the **Currency** filter for any amount column. You can also  specify the ISO code of the currency you want to restrict the column to. When you set the column to a specific currency, only transactions entered for that currency will be displayed. 

- In the row definition, you can specify a **Row modifier** with the attribute set to **Transaction currency** with a currency code listed as the restriction. When you restrict the row to a specific currency, only transactions that are entered for the matching currency will be displayed. This is also the case when you restrict a column to a currency. 

> [!NOTE]
> When you use the **Transaction currency** attribute, if you don't specify a currency filter, the system will include transactions in all the currencies that you have transactions for. We recommend that you specify a currency filter to prevent the row from showing an aggregate amount that isn't meaningful when the report is generated.

## Reporting on currency
By default, any amount appearing on a report will appear as the accounting currency amount. Any of the following actions will cause some level of translation to take place:
- Modifying the **Currency display** field in the column definition to **Reporting currency from Ledger**, which will bring back translated amounts that are calculated in the Reporting currency
- Modifying the **Currency display** field in the column definition to **Transaction currency**, which will force the report to total different currencies together and display the entered amount in the column, regardless of currency
- Modifying the **Currency display** field in the column definition to any of the **Translate to...** options, which will perform the currency translation within Financial reporting

Additionally, the following actions will also cause translation:
- Use of a reporting tree to summarize multiple legal entities with different accounting currencies. Amounts will be translated to the accounting currency based on the legal entity specified in the report definition or the current company context if the @ANY company is used in the report definition. You will see the currency being used in Report Designer near the top of the page with text stating "Values will be displayed in USD" when US dollar is the accounting currency of the current company. 
- Using the **Currency** button in the web report viewer will cause one additional version of the report to be generated, overriding the accounting currency if it wasn't previously specified. 
Using the **Include all reporting currencies** button in Report Designer will cause additional versions of the report to be generated using translated data for each currency selected. 

> [!Note]
> This option should only be used if these versions are expected, since it takes additional resources to generate the additional reports. 

For amounts being translated within Financial reporting, the following types of translation are available for use, and are specified within each main account.

| Translation type  |  Description |  Example rate calculation |   
|---|---|---|
| Current | Uses the last rate on or before the period specified. Typically used for Balance Sheet accounts.  |  (Rate) |   
| Weighted average  | Uses the weighted average rate for the period. Typically used for P&L accounts. | ((Rate1 * Number of days in effect) + (Rate2 * Number of days in effect)) + …/ Number of days in the period  |   
|  Average | This is a simpler average rate for the period. Typically used for Profit and loss accounts.  | (Sum of rates)/(number of rates)  |   
| Transaction date (Historical)  | Uses the rate in effect on the posting date of the transaction. If no rate is available, the system will use the closest previously entered rate. Typically used for [Retained earnings](../general-ledger/retained-earnings-enhancements.md), Equity accounts and longer-term fixed assets (for example, Land).  | (Rate)  |   


### Setup for Exchange rate type
The exchange rate type defines the table of exchange rates and currencies to be used. The exchange rate type can be set in multiple locations. 

- You can set the exchange rate type on the **Main accounts** page within General ledger; there is an option for **Exchange rate type** on the **Financial reporting** FastTab. 
- You can also specify an override of an exchange rate type for a legal entity, which will override the default behavior. 
- If no exchange rate type is specified for a main account, the exchange rate type will default from the ledger.

### Setup for Currency translation type
The Currency translation type will determine how each main account is translated. Currency translation rate type can also be set in multiple locations. 
- Within the **Main accounts** page in General ledger, there is an option for **Currency translation type** on the **Financial reporting** FastTab. 
- You can also specify an override of a currency translation rate type for a legal entity, which will override the default behavior. 


### Setup for Retained Earnings
Currency translation for retained earnings accounts is subject to some specific requirements:
- Any retained earnings account must be assigned to the Retained earnings main account category **Reference ID** of 29 on the **Main accounts** page if the account balance should be translated using the appropriate calculation.
- If the default category was renamed, financial reporting still expects the original with **Reference ID** of 29. 
   > [!NOTE]
   > You may have to personalize the form and add **Reference ID** as a column in order for this to display on the page.
- The retained earnings account only translates system-generated transactions initiated through the fiscal year-end close process. If any transactions are posted directly, they will not be accurately reflected through translation. 
- The retained earnings balance is translated at the rate that exists at the end of the most recently closed year. This means that it is a point-in time-calculation, not an accumulation of amounts and rates calculated from the beginning balance entered through today. 

Functionality that was introduced in preview for Dynamics 365 Finance version 10.0.7 enables functionality for enhanced flexibility for consolidation and dual currency. To enable this functionality in preview, create a support incident for financial reporting to be enabled in a sandbox or development environment. 

This feature improves the precision of calculations of retained earnings when earnings are calculated across multiple years using currency translation. When you enable this feature, any retained earnings account that has the **Currency translation type** field on the **Main accounts** page set to **Transaction date** will calculate the translated balance of the account using rates and balances from its entire history using the end-of-year rate X the balance for all years, rather than only using the most recent year and rate.

## Report design elements related to currency
The are additional report design elements that can be used when doing reporting on currencies.

### Autotext codes
Users can dynamically see the currency symbol, code, and description they have defined when the currency is changed. Three autotext options are available to Financial reporting to enable this functionality:
- Currency symbol (@CurrencySymbol)
- Currency code (@CurrencyCode)
- Currency description (@CurrencyDescription)

You can add the autotext both in the Column Definition and in the Report Definition headers. Additionally, anywhere in a report where a currency symbol is used will update with the appropriate symbol for the currency from Dynamics. Currency symbols are used in the following fields:

- **Display currency symbol on first row**, which is defined in the Report Definition
- **Use currency format in this row** (CS), which is defined in the Row Definition
- **Format Overrides** defined in the Row and Column Definition

### Financial reporting attributes related to currency
The following are additional report design attributes that can be used when reporting on currencies that will be included in the account or transaction drill-down lists in support of amount lines.

- Account currency
- Currency code
- Transaction currency
- Acquisition date

### Currency Translation Adjustment
The currency translation adjustment (CTA) is the difference between the rates used to calculate the balance sheet accounts and the rate used for the income statement accounts. This difference in rates will cause the balance sheet to be out of balance. 

You can use Financial reporting to calculate the CTA in two ways: 

1. Use the Rounding Adjustments dialog in the row definition

Financial reporting will calculate the amount of the difference from currency calculations using the rounding adjustments calculation. To use this calculation, edit the **Row Definition** and click **Edit > Rounding Adjustment**. Set the total assets row, total liabilities and equities row, and a threshold for maximum variance to silently accept. A line named **Rounding Adjustment** will be created for the rounding difference row and shown upon drill-down of the row you've selected.
 
2. Create a single line that includes all accounts and use it to calculate the CTA.

Put all of the accounts in a range, from assets to expenses. The difference will be the same amount as the rounding adjustment (CTA) and you can use the total to verify that the rounding adjustment dialog doesn't include any missing account balances. 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
