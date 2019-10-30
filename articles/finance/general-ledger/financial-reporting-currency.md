Financial reporting has a wide variety of features in order to support complex currency reporting requirements. Financial reporting can report on any of the following amounts:
* Accounting currency amount 
* Reporting currency amount 
* Transaction currency amount 
* Translate to any currency set up within Dynamics 365 for Finance

For amounts being translated, the following types of translation are available, as defined on each MainAccount. 

|                  |                                                                             |                      |
| Translation type | Description                                                                 | Example calculation  | 
| Current          | Uses the last rate in the period. Typically used on Balance Sheet accounts  |                      |

| Average | Uses average rate for the period. Typically used on P&L accounts | (sum of rates)/(number of rates) |
| Weighted average  | Uses weighted average rate for the period. Typically used on P&L accounts. | ((Rate1 * Number of days in effect) + (Rate2 * Number of days in effect)) + …/ Number of days in the month  | 
| Transaction date (Historical) | Uses the rate in effect on the posting date of the transaction. Typically used on Retained Earnings, Equity accounts and longer term fixed assets (i.e. Land) | test | 

