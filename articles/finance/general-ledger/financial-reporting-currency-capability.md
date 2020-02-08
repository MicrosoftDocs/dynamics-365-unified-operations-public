---
# required metadata

title: Currency capabilities in financial reporting
description: Financial reporting includes features that support complex currency reporting requirements.
author: ryansandness
manager: AnnBe
ms.date: 01/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: ryansandness
ms.search.validFrom: 2020-01-09
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
By default, all report amounts are summarized and presented in the accounting currency of that company. If you need to do additional analysis by the transactions and related currencies, you can do so by setting filters on the report. 

- In the column definition, you can use the **Currency filter** for any amount column, and specify the ISO code of the currency you want to restrict the column to. When you set the column to a specific currency, only transactions entered for that currency will be displayed. 

- In the row definition, you can specify a **Row modifier** with the attribute set to **Transaction currency** with a currency code listed as the restriction. As is the case when you restrict a column to a currency, when you restrict the row to a specific currency,  only transactions entered for the matching currency will be displayed. 


## Reporting on currency
By default, any amount appearing on a report will appear as the accounting currency amount. Any of the following actions will cause some level of translation to take place:
- Modifying the **Currency display** field in the column definition to **Reporting currency from Ledger**, which will bring back translated amounts as calculated in the Reporting currency
- Modifying the **Currency display** field in the column definition to **Transaction currency**, which will force the report to total different currencies together and display the entered amount in the column, regardless of currency
- Modifying the **Currency display** field in the column definition to any of the **Translate to...** options, which will perform the currency translation within Financial reporting

Additionally, the following actions will also cause translation:
- Use of a reporting tree to summarize multiple legal entites with different accounting currencies. Amounts will be translated to the accounting currency based on the legal entity specified in the report definition or the current company context if the @ANY company is used in the report definition. You will see the currency being used in Report Designer near the top of the page with a text label saying "Values will be displayed in USD" when US dollar is the accounting currency of the current company. 
- Using the **Currency** button in the web report viewer will cause one additional version of the report to be generated, overriding the accounting currency if it wasn't previously specified. 
Using the **Include all reporting currencies** button in Report Designer will cause additional versions of the report to be generated using translated data for each currency selected. 
Note that this option should only be used if these versions are expected to be used, since it will take additional resources to generate the additional reports. 

For amounts being translated within Financial reporting, the following types of translation are available for use, as defined on each main account. 

| Translation type  |  Description |  Example rate calculation |   
|---|---|---|
| Current | Uses the last rate on or before the period specified. Typically used for Balance Sheet accounts.  |  (Rate) |   
| Weighted average  | Uses the weighted average rate for the period. Typically used for P&L accounts. | ((Rate1 * Number of days in effect) + (Rate2 * Number of days in effect)) + …/ Number of days in the period  |   
|  Average | This is a simpler average rate for the period. Typically used for Profit and loss accounts.  | (Sum of rates)/(number of rates)  |   
| Transaction date (Historical)  | Uses the rate in effect on the posting date of the transaction. If no rate is available will use the closest previously entered rate. Typically used for Retained Earnings, Equity accounts and longer term fixed assets (for example, Land).  | (Rate)  |   


### Setup for Exchange rate type
The exchange rate type defines the table of exchange rates and currencies to be used. The exchange rate type can be set in multiple locations. 

- You can set the exchange rate type on the **Main accounts** page within General ledger; there is an option for **Exchange rate type** on the **Financial reporting** FastTab. 
- You can also specify an override of an exchange rate type for a legal entity which will override the default behavior. 
- If no exchange rate type is specified for a main account, the exchange rate type will default from the ledger.

### Setup for Currency translation type
The Currency translation type will determine how each main account is translated. Currency translation rate type can also be set in multiple locations. 
- Within the **Main accounts** page within General ledger there is an option for **Currency translation type** on the **Financial reporting** FastTab. 
- You can also specify an override of a currency translation rate type for a legal entity which will overide the default behavior. 


### Setup for Retained Earnings
Currency translation for retained earnings accounts are subject to some specific requirements:
- Any retained earnings account must be assigned to the Retained earnings main account category on the **Main accounts** page to translate.
- If the default category was renamed, financial reporting is still expecting the original with the backing ID number of 29. 
- The retained earnings account only translates system-generated transactions initiated through the fiscal year-end close process. If any transactions are posted directly, they will not be accurately reflected through translation. 
- The retained earnings balance is translated at the rate that exists at the end of the most recently closed year. This means that it is a point-in time-calculation, not an accumulation of amounts and rates calculated from the beginning balance entered through today. 

Functionality that was introduced in preview for Dynamics 365 Finance version 10.0.7 enables functionality for enhanced flexibility for consolidation and dual currency. To enable this functionality in preview, create a support incident for financial reporting to be enabled in a sandbox or development environment. 

This feature improves the precision of calculations of retained earnings when earnings are calculated across multiple years using currency translation. When you enable this feature, any retained earnings account that has the **Currency translation type** field on the **Main accounts** page set to **Transaction date** will calculate the translated balance of the account using rates and balances from its entire history using the end-of-year rate X the balance for all years, rather than only using the most recent year and rate.

## Report design elements related to currency
The are additional report design elements that can be used when doing reporting on currencies.

### Auto-text codes
Users can dynamically see the currency symbol, code, and description they have defined when the currency is changed. Three auto-text options are available to Financial reporting to enable this functionality:
- Currency symbol (@CurrencySymbol)
- Currency code (@CurrencyCode)
- Currency description (@CurrencyDescription)

You can add the auto-text both in the Column Definition and in the Report Definition headers. Additionally, anywhere in a report where a currency symbol is used will update with the appropriate symbol for the currency from Dynamics. 

The places where currency symbols are used are:

- Display currency symbol on first row which is defined in the Report Definition
- Use currency format in this row (CS), which is defined in the Row Definition
- Format Overrides defined in the Row and Column Definition

### Financial reporting attributes related to currency
The following are additional report design attributes that can be used when reporting on currencies that will display on account or transaction drill down in support of amount lines.

- Account currency
- Currency code
- Transaction currency
- Acquisition date

### Currency Translation Adjustment
The currency translation adjustment (CTA) is the difference between the rates used to calculate the balance sheet accounts and the rate used for the income statement accounts. This difference in rates will cause the balance sheet to be out of balance. 

You can use Financial reporting to calculate the CTA in two ways: 

1. Use the Rounding Adjustments form in the row definition

Financial reporting will calculate the amount of the difference from currency calculations using the rounding adjustments calculation. To use this, edit the **Row Definition** and click **Edit > Rounding Adjustment**. Set the total assets row, total liabilities and equities row, and a threshold for maximum variance to silently accept. A line named **Rounding Adjustment** will be created for the rounding difference row and shown upon drill-down of the row you've selected.
 
2. Create a single line with all accounts to calculate the CTA 

Put all of the accounts in a range, from assets to expenses. This difference will be the same amount as the rounding adjustment (CTA) and can be used as a check total to make sure the rounding adjustment form is not including any missed account balance.

