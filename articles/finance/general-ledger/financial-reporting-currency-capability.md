## Overview
Financial reporting has a wide variety of features in order to support complex currency reporting requirements. Financial reporting can report on any of the following currency amounts:
* Accounting currency amount 
* Reporting currency amount 
* Transaction currency amount 
* Translate to any currency setup within Dynamics 365 for Finance

## Filtering by currency




## Reporting on currency
By default, any amount appearing in a report will appear as the accounting currency amount. Any of the following actions will cause some level of translation to take place:
* Use of a reporting tree to summarize multiple legal entites with different accounting currencies
* Modifying the (?) currency field in the column definition
* Modifying the (?) currency in the row definition
* Using the (?) currency in the web viewer or the options pane of the web viewer

For amounts being translated, the following types of translation are available for use, as defined on each MainAccount. 

| Translation type  |  Description |  Example rate calculation |   
|---|---|---|
| Current | Uses the last rate on or before the period specified. Typically used for Balance Sheet accounts  |  (Rate) |   
| Weighted average  | Uses the weighted average rate for the period. Typically used for P&L accounts | ((Rate1 * Number of days in effect) + (Rate2 * Number of days in effect)) + …/ Number of days in the period  |   
|  Average | This is a simpler average rate for the period. Typically used for P&L accounts  | (Sum of rates)/(number of rates)  |   
| Transaction date (Historical)  | Uses the rate in effect on the posting date of the transaction. If no rate is available will use the closest previously entered rate.  Typically used for Retained Earnings, Equity accounts and longer term fixed assets (e.g. Land)  | (Rate)  |   

### Setup for Main Accounts
Two fields have been added to the Main Accounts and Main Account Templates in the Financial Reporter fast tab:
* Exchange rate type – choose the exchange rate type that contains the currencies and exchange rates you want to apply to this account. This table of currencies and exchange rates will be applied to actual data in Management Reporter.
* Currency translation type – select the method for how the exchange rate is calculated for this account. This currency method is used for both actual and budget data in Management Reporter.

If no field is defined at the account level, the calculation will instead check for the default rate type on the ledger form

### Setup for Retained Earnings
Retained earnings is special in that it is expecting a specific account category

### Setup to determine what translation currencies are available


### Example - Balance Sheet


### Example - Income Statement


Financial reporting attributes related to currency
* Acquisition date

Resources for more information
* https://blogs.msdn.microsoft.com/dynamics_financial_reporting/2014/01/23/acquisition-date-attribute-for-dynamics-ax-2012-cu7-feature/
* https://download.microsoft.com/download/2/0/D/20D27A5C-6AA5-4FA9-A6E9-AB6F244B38DA/Financial%20consolidations%20and%20currency%20translation.pdf
* https://blogs.msdn.microsoft.com/dynamics_financial_reporting/2013/10/24/currency-translation-for-microsoft-dynamics-ax-2012-part-3-report-designer-options-for-currency-translation-cu7-feature/
* https://blogs.msdn.microsoft.com/dynamics_financial_reporting/2013/10/23/currency-translation-for-microsoft-dynamics-ax-2012-part-2-changing-reporting-currencies-in-the-web-viewer-cu7-feature/
* https://blogs.msdn.microsoft.com/dynamics_financial_reporting/2013/10/23/currency-translation-for-microsoft-dynamics-ax-2012-part-1-setup-cu7-feature/
