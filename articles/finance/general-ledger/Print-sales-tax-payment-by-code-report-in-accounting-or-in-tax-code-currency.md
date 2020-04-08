---
title: Print Sales tax payment by code report in accounting or in tax code currency
---

You can print the **Sales tax payment by code** report in **Tax \> Inquiries and
reports \> Sales tax reports \> Sales tax payment by code.** By default, report
amounts are generated in the accounting currency of the legal entity for all
reporting codes which are set up on the **Sales tax reporting codes** page.

Starting from the Monthly update 10.0.11, you can also generate this report to
show amounts in the currencies of sales tax codes for all reporting codes which
are assigned to sales tax codes on **Sales tax codes** page.

Activate the feature
====================

On the **Feature management** workspace, activate the feature with name
**Generate the Sales tax payment by code report in the sales tax code currency**

Run the report
==============

Go to **Tax \> Inquiries and reports \> Sales tax reports \> Sales tax payment
by code.**

![A screenshot of a cell phone Description automatically generated](media/8c7416c86b2480de61afeede9552ce94.png)

In the field **Report currency** select:

-   **Accounting currency,** to print report amounts in the accounting currency

-   **Sales tax code currency**, to print report amounts in currencies of sales
    tax codes.

    You can see report example below:

![](media/15595f1ef641f7f443f8086036851967.png)

Report identifies that the Reporting code 101 has currency EUR if sales tax code
to which the reporting code is assigned, has **Sales tax currency** field set as
‘EUR’
