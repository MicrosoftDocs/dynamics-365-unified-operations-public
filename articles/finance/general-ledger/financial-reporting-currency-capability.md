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
* Modifying the currency display field in the column definition from blank or to something other than accounting currency
* Modifying the (?) currency in the row definition
* Using the (?) currency in the web viewer or the options pane of the web viewer

For amounts being translated, the following types of translation are available for use, as defined on each MainAccount. 

| Translation type  |  Description |  Example rate calculation |   
|---|---|---|
| Current | Uses the last rate on or before the period specified. Typically used for Balance Sheet accounts  |  (Rate) |   
| Weighted average  | Uses the weighted average rate for the period. Typically used for P&L accounts | ((Rate1 * Number of days in effect) + (Rate2 * Number of days in effect)) + …/ Number of days in the period  |   
|  Average | This is a simpler average rate for the period. Typically used for P&L accounts  | (Sum of rates)/(number of rates)  |   
| Transaction date (Historical)  | Uses the rate in effect on the posting date of the transaction. If no rate is available will use the closest previously entered rate.  Typically used for Retained Earnings, Equity accounts and longer term fixed assets (e.g. Land)  | (Rate)  |   


### Setup for Exchange rate type
The exchange rate type defines the table of exchange rates and currencies to be used. Exchange rate type can be configured in multiple locations. 

* Within the Main accounts form within General Ledger there is an option for Exchange rate type on the Financial reporting fast tab. 
* You can also specify an override of an exchange rate type for a legal entity which will override the default behavior. 
* If no exchange rate type is specified for a main account, the exchange rate type will default from the ledger.

## Setup for Currency translation type
The Currency translation type will determine how each main account is translated. Exchange rate type can also be configured in multiple locations. 
* Within the main accounts form within General ledger there is an option for Currency translation type on the Financial reporting fast tab. 
* You can also specify an override of an exchange rate type for a legal entity which will overide the default behavior. 


### Setup for Retained Earnings
Retained earnings is special in that it is expecting a specific account category

### Setup to determine what translation currencies are available

### Setup for Budget

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
