This article explains how to use this report to show and print information about ledger transactions for which sales tax is calculated.

## Tax Account and Non-Tax Account

This report will show tax transaction for both tax account and non-tax account. Definition of the two accounts is:

- Tax account: when tax transaction is posted, main account on "Sales Tax" journal line is tax account. e.g. sales tax payable, sales tax receivable
- Non-tax account: when tax transaction is posted, main account on original transaction is non-tax account. e.g. revenue account, expense account

In this report, report columns "Origin", "Sales tax receivable", "Sales tax payable" amount will show for non-tax account and will show 0 for tax account


## How to filter the data on this report

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report.

|Field|Description|
|-------|-----------------|
|Main accounts only|Tax transaction date range|
|From/To Main account|Main account range|
|From/To sales tax code|Sales tax code range|
|Grouping|Report is grouped by ledger account or sales tax code|
|Subtotal by sales tax code|Select this check box to show subtotal by sales tax code|
|Totals only|Select this check box to show totals only|
|Main accounts only|Select this check box to print only main accounts on the report|

