# VAT management and reporting by tax point date (Date of VAT register)

## Introduction

On 23rd of October 2018 in Italy the Law Decree 119 (L.D.119/2018) introduced a change in value-added tax (VAT) management in Italy that takes effect on July 1, 2019. Here is a summary of the change:

-	VAT payers can recover the input VAT in the VAT settlement for the month when the VAT point is triggered, even if the purchase invoice is received and recorded in the input VAT ledger before the fifteenth day of the next month. This rule doesn’t apply to transactions where the VAT point is triggered in a fiscal year that differs from the fiscal year in which the purchase invoice is received.

-	For supplies of services and supplies of goods, the invoice can be issued by the fifteenth day of the month after the month in which the VAT point was triggered. Invoices that are issued and booked before the fifteenth day of the month after the month in which the VAT point was triggered must be included in the VAT settlement of the previous month.

-	Starting on July 1, 2019, the invoice can be issued within 10 days of the VAT point. If the invoice isn’t issued at the VAT point, it should include, in addition to the invoice date, a reference to the VAT point date.

Invoices that are booked before the fifteenth day of the next month, but that have a reference to the previous VAT settlement, should not interrupt the sequential posting. Invoices with VAT point date in the previous month but invoice date in the current month should be booked in a chronological sequence with the invoices in the current month  with a reference to the fact that these invoices are related to the previous VAT settlement.

Companies that issue the sales invoice on the same day, without applying the change that is introduced by L.D.119/2018, remain compliant.

## Overview

This feature is delivered to support the changes introduced by the L.D.119/2018 on **Microsoft Dynamics 365 for Finance and Operations** starting from version **10.0.6**.

Before you start using this feature you must enable **Date of VAT register** feature in **Feature management** workspace, which introduces a new date-type field for VAT transactions – **Date of VAT register**. The additional date will serve as a VAT point determination criterion for including VAT transactions in the scope of the sales tax settlement period and, effectively, in VAT returns reporting.

**Note:**

1.	System doesn’t allow to post an invoice with value of **Date of VAT register** field in a closed interval of sales tax settlement period. 
2.	System doesn’t allow to update **Date of VAT register** field with a value in a closed interval of sales tax settlement period.

Learn more about **Date of VAT register** feature in [Tax point date (Date of VAT register)](../emea-tax-point-date.md).

## “Date of VAT register” impact on VAT settlement and reporting

When **Date of VAT register** feature is enabled in the **Feature management** workspace, user in legal entity with **primary address in Italy** will be able to activate **Date of VAT register** parameter on **General ledger parameters** page:

![date-of-vat-filling](./media/date-of-vat-gl-parameter.png)

When this parameter is switched on, **Settle and post sales tax** process and **Italian sales tax payment report** will consider sales tax transactions by **Date of VAT register** instead of date of transaction posting.

Note, that system will not allow:

-	to switch On **Date of VAT register** parameter on **General ledger parameters** page if there are tax transactions posted in open interval of sales tax settlement period with value of **Date of VAT register** field in a closed interval of sales tax settlement period.

-	to switch Off **Date of VAT register** parameter on **General ledger parameters** page if there are tax transactions with value of **Date of VAT register** field in a closed interval of sales tax settlement period but posted in open interval of sales tax settlement period.

-	to switch Off **Date of VAT register** feature in **Feature management** workspace if there is at least one legal entity where **Date of VAT register** parameter on **General ledger parameters** page is switched on.

## “Sales tax transactions extension” consistency check

**Date of VAT register** field is physically stored in a TaxTrans_W table which an extension of TaxTrans table. When a company switches on **Date of VAT register** parameter on **General ledger parameters** page, data source queries on some pages in the system starts working differently, joining the TaxTrans_W table. It is possible that user will not be able to see tax transactions posted in the past period. It is because there are no corresponding transactions in TaxTrans_W table because it was not used in the past.
To avoid this issue, we recommend running **Sales tax transactions extension** consistency check. Open **System administration** > **Periodical tasks** > **Database** > **Consistency check** page and mark **Program** > **General ledger** > **Sales tax** > **Sales tax transactions extension** check box (you don’t need to mark the parent checkboxes if you want to run only Sales tax transactions extension check):

![date-of-vat-consistency-check](./media/date-of-vat-consistency-check.png)

Run **Sales tax transactions extension** consistency check with:
-	**Check** option to find out if there are missing transactions in TaxTrans_W table in your system. As a result, system will inform you about how many transactions in TaxTrans table miss corresponding records in TaxTrans_W table.
-	**Fix** option if you want to compensate missing records in TaxTrans_W table. As a result, system will insert corresponding records to the TaxTrans_W table and Posted sales tax transaction in the past periods will be seen again everywhere in the system. 

Make sure that you have chosen the right date in **From date** on the dialogue . Leave **From date** field blank if you want to recover all the tax transactions in the system.

**Sales tax transactions extension** consistency check is available when **Date of VAT register** feature is enabled in **Feature management** workspace.

## Changes in the Italian sales tax payment report

You may run **Italian sales tax payment report** via the following menu items:

-	**Tax > Declarations > Sales tax > Sales tax (Italy)**

- **Tax > Declarations > Sales tax > Report sales tax for settlement period**

- **Tax > Inquires and reports > Sales tax payments, Sales tax (Italy) button**

-	**Tax > Inquires and reports > Sales tax payments**, **Print** report button (when Italian report layout is defined for the **Sales tax authority** specified for the **Sales tax settlement period** of the selected sales tax payment line)

**Date of VAT register** parameter on **General ledger parameters** page doesn’t impact on list of invoices represented on **Sales tax book section(s)** page(s), all the invoices posted in the related **Sales tax book sections** during the selected period will be included into the report. Nevertheless, resulting amounts of VAT will be calculated depending on **Date of VAT register** parameter on **General ledger parameters** page:

-	when **Date of VAT register** parameter on **General ledger parameters** page is switched On – by **Date of VAT register** of tax transactions in the period.

-	when **Date of VAT register** parameter on **General ledger parameters** page is switched Off – by posting date of tax transactions in the period.

When **Date of VAT register** parameter on **General ledger parameters** page is switched On, **Italian sales tax payment report** will additionally provide the following information:

1.	Pages of sales tax books sections: new **Date of VAT point (Date of VAT register)** (in Italian: “Momento di effettuazione dell’operazione”) column – represents the value of **Date of VAT register** of tax transaction.

2.	Totals by each sales tax book section is represented in three groups:

-	Operations in the actual period with competence date in the actual period

-	Operations in the actual period with competence date in the previous period

-	Operations in the next period with competence date in the actual period

3.	Totals by sales and purchase books are represented in three lines: 

-	Total operations in the actual period with competence date in the actual period

-	Total operations in the actual period with competence date in the previous period

-	Total operations in the next period with competence date in the actual period

4.	Summary section which represent total VAT amounts by sales tax books sections grouped by sales tax book sections, is represented separately in three parts:

-	Operations in the actual period with competence date in the actual period

-	Operations in the actual period with competence date in the previous period

-	Operations in the next period with competence date in the actual period

5.	Totals on summary section which represent total VAT amounts by sales tax books sections grouped by sales tax book sections, is represented separately in three lines:

-	Total operations in the actual period with competence date in the actual period

-	Total operations in the actual period with competence date in the previous period

-	Total operations in the next period with competence date in the actual period

Additionally, **Total calculated considering competence date** amount is provided in a separate line.

