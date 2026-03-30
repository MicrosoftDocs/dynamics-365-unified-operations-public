---
title: Journal reports
description: Learn how to work with journal reports that are specific to legal entities with a primary address in Belgium in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Thailand
ms.search.validFrom: 2016-11-30
ms.search.form: TaxTable, VendParameters, CustParameters
ms.dyn365.ops.version: Version 1611
ms.assetid: 829a101f-e329-48b9-baf8-e36670ff43c8
---

# Journal reports (Posting journals)

[!include [banner](../../includes/banner.md)]

This article explains how to work with journal reports that are specific to legal entities with a primary address in Belgium in Microsoft Dynamics 365 Finance.

Periodically, Belgian companies must print a report for each journal. The report provides a chronological list of all the postings to the general ledger accounts for each journal. These reports prove the integrity of the accountancy and are used during financial audits to reconcile VAT settlement with the postings on the corresponding general ledger accounts.

There are five types of reports you can generate.
- **Purchase journal**: Provides an overview of all purchases.
- **Sales journal**: Provides an overview of all sales.
- **Financial journal**: Provides an overview of all financial entries.
- **Other journal**: Provides an overview of all diverse operations.
- **Overview journal**: Provides an overview of all the printed journals.

These reports are only available to legal entities whose primary address is in Belgium.

Each report consists of several sections and summaries including:
- A detailed overview of the postings to the general ledger accounts.
- A summary of the postings to the general ledger accounts.
- A detailed overview of tax posting.
- A summary of tax posting.
- A summary of the tax amount boxes used in the selected journal.

You can set the following parameters when you generate a report.

| **Field** | **Description** |
|-------------------------|-------------------------|
| Journal | Select the name of the sales journal to use to post transactions to the general ledger account. |
| From date | Select or enter the start date of the reporting period. |
| To date | Select or enter the end date of the reporting period. |
| Final print | Set to **Yes** to print the final version of the report.</br>When you select **Final print**, the following occurs:</br><ol></br><li>The **From date** you selected must belong to the period following the period of the last final printout end date. This validation depends on the value entered in the **Journal** field. If the field is empty, all of the posting journals that belong to this type (purchase, sales, financial, or other) are validated.</li></br><li>The page number of the report is sequential. The page number of the previous periods +1 is used as basis for the new numbering. Page numbering starts at zero for each new fiscal year.</li></br><li>A new line is added in the final print form for each posting journal.</li></br></ol> |
| Compress | Select this option to group amounts on the same ledger account in the same voucher into one line.</br><ul></br><li>When set to **No**, each transaction is shown on a separate line.</li></br><li>When set to **Yes**, transactions are grouped by account and shown as one summarized line.</li></br></ul> |

## Setup

The reports are linked to the posting journals in the general ledger by number sequences. For each posting journal, select the journal type, either purchase, sales, other, or financial, or you can leave the field empty.

To set up journal reports, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal setup** \> **Posting journals**.
1. On the Action Pane, select **Create** to generate posting journals automatically. The posting journals are created to correspond with the number sequence codes. To create a posting journal manually, select **New**.
1. Select a posting journal and in the **Belgian journal reports** section, in the **Journal type** field, select the journal type.
1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.
1. Select an item sales tax group, and in the **Reporting type** field, select where the item sales tax line amount will be included on the European Union (EU) sales list.
    - **Blank**: The sales tax line amount is included in the **Not assigned** column.
    - **Item**: The sales tax line amount is included in the **Items** column.
    - **Service**: The sales tax line amount is included in the **Services** column.
    - **Investment**: The sales tax line amount is included in the **Investment** column.

## Sales journals report

The sales journals report displays and prints a summary of sales transactions, such as sales invoices and credit memos that are posted to the general ledger. This report summarizes the following:
- The payment transactions per voucher and general ledger account.
- The overall debits and credits per general ledger account.
- The tax details per tax code and voucher number, including the tax base amount and tax amount distribution against goods, services, and investments.
- A list of the tax postings sorted by their corresponding tax reporting codes.

This report is typically used by collections agents, collections managers, chief financial officers, accounts receivable clerks, accounts receivable managers, and financial controllers to review the status of the invoices and the cash process.

To generate the sales journals report, go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Sales journals** and set the parameters.

## Purchase journals report

The purchase journals report displays and prints a summary of the transactions in a purchase journal. This report is typically used by accounts payable coordinators and accountants.

To generate the purchase journals report, go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Purchase journals** and set the parameters.

## Financial journal report

The financial journals report displays and prints a summary of financial transactions, such as customer payments and vendor payments, that are posted to the general ledger account. This report summarizes the following:
- The payment transactions per voucher and general ledger account.
- The overall debits and credits per general ledger account.
- The tax details per tax code and voucher number, including the tax base amount and tax amount distribution against goods, services, and investments.
- A list of the tax postings sorted by their corresponding tax reporting codes.

The financial journals report is typically used by chief executive officers, chief financial officers, compliance managers, accounting managers, accounting supervisors, and financial controllers to review the status of the general ledger process.

To generate the financial journals report, go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Financial journals** and set the parameters.

## Other journal report

The other journal report displays and prints a summary of the posted transactions that aren't categorized under sales, purchases, or financials. This report is typically used by accountants, accounting managers, clerks, accounting supervisors, and compliance managers to inquire into journal transactions.

To generate the other journal report, go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Other journals** and set the parameters.

## Overview journal report

The overview journal report displays and prints a summary of the posted transactions that aren't categorized under sales, purchases, or financials.

This report is typically used by accountants, accounting managers, clerks, accounting supervisors, and compliance managers to inquire into journal transactions.

## Example

The following example procedure shows how you can set up posting journals and generate and print the posting journals reports. This example uses the FRRT legal entity.

To run through the example, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Organization**> **Legal entities**, and select the **FRRT** legal entity.
1. On the **Address** FastTab, select **Edit**.
1. In the **Country/region** field, select **BEL** (Belgium).
1. Go to **General ledger** \> **Journal Setup** \> **Posting journals**.
1. On the Action Pane, select **Create**.
1. Set the **Journal type** for the journals according to the following table.

    | **Journal** | **Journal type** |
    |-------------------------|-------------------------|
    | Acco_46 | Sales |
    | Acco_67 | Purchase |
    | JourNdF | Financial |
    | ODComptabl | Other |

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Item sales tax groups**.
1. Select the **NORMAL** item sales tax group.
1. In the **Reporting type** field, select **Item**.
1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
1. Select **TAXFRA**.
1. On the **General** FastTab, in the **Report layout** field, select **Belgium report layout**.
1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax reporting codes** and create the following reporting codes.

    | **Reporting layout** | **Reporting code** | **Report text** |
    |-------------------------|-------------------------|-------------------------|
    | Belgium reporting layout | 03 | Taxable supplies and services at a sales tax rate of 21 percent.</br>The delivery of a product or service transactions at a sales tax rate of 21 percent. |
    | Belgium reporting layout | 54 | VAT that is payable on the turnover that is included in codes **01**, **02**, and **03**. |
    | Belgium reporting layout | 81 | Amount of all purchases of goods, raw materials, and consumables, and related acquisition costs, excluding VAT deductible. |
    | Belgium reporting layout | 59 | Amount of deductible VAT. |


    Learn more in [Set up sales tax reporting codes](../belgium/emea-bel-intervat-tax-declaration.md#set-up-sales-tax-reporting-codes).

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. Select **TVA19.6**.
1. On the **Report setup** FastTab, in the **Sale** section, in the **Taxable sales** field, select **03**.
1. In the **Sales tax payable** field, select **54**.
1. In the **Purchase** section, in the **Tax purchases** field, select **81**.
1. In the **Sales tax receivable**, select **59**.

### Print the sales journal report

To print the sales journal report, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Select **New** and create a new free text invoice.
1. In the **Customer** **account** field, select **1001**.
1. In the **Date field,** select **4/15/2021**.
1. On the **Invoice lines** FastTab, in the **Main account** field, select **701000**.
1. In the **Sales tax group** field, select**VE-DOM**.
1. In the **Item sales tax group** field, select **NORMAL**.
1. In the **Quantity** field, enter "1".
1. In the **Unit price** field, enter "100".
1. Post the free text invoice.
1. Go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Sales journals**.
1. In the **Criteria** section, in the **Journal** field, select **Acco\_46**.
1. In the **From date** field, select **4/1/2021**.
1. In the **To date** field, select **4/30/2021**.
1. In the **Final print** field, select **Yes**.
1. Select **OK** to review the report.

![eSales journal report.](../media/emea-bel-journal-reports-sales-journal-report.png)

### Print the Purchase journal report

To print the purchase journal report, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select **New** and create a new purchase order.
1. In the **Vendor account** field, select **1001**.
1. In the **Item number** field, select **0001**.
1. In the **Quantity** field, enter "3".
1. On the **Line details** FastTab, on the **Setup** tab, in the **Sales tax** section, in the **Item sales tax group**, select **NORMAL**. In the **Sales tax group**, select **VE-DOM**.
1. Go to **Purchase** \> **Actions** \> **Confirm**.
1. Go to **Invoice** \> **Generate** \> **Invoice**.
1. In the **Invoice identification** section, in the **Number** field, enter "INVNUM\_001".
1. In the **Invoice dates** section, in the **Invoice date** field, select **4/12/2021**.
1. In the **Posting date** field, select **4/12/2021**.
1. Post the order.
1. Go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Purchase journals**.
1. In the **Criteria** section, in the **Journal** field, select **Acco\_67**.
1. In the **From date** field, select **4/1/2021**.
1. In the **To date** field, select **4/30/2021**.
1. In the **Final print** field, select **Yes**.
1. Select **OK** to view the report.

![Purchase journal report page 1.](../media/emea-bel-journal-reports-purchase-journal-report-1.png)
![Purchase journal report page 2.](../media/emea-bel-journal-reports-purchase-journal-report-2.png)
![Purchase journal report page 3.](../media/emea-bel-journal-reports-purchase-journal-report-3.png)
![Purchase journal report page 4.](../media/emea-bel-journal-reports-purchase-journal-report-4.png)

### Print the Financial journal report

To print the financial journal report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal entries** \> **General journals**.
1. Create a new journal.
1. In the **Name** field, select **JourNdF**.
1. Select **Lines**.
1. In the **Date** field, select **4/15/2021**.
1. In the **Account type** field, select **Customer**.
1. In the **Account** field, select **1001**.
1. In the **Credit** field, enter "100".
1. In the **Offset account type** field, select **Bank**.
1. In the **Offset account** field, select **FRRT OPER**.
1. In the **Item sales tax group** field, select **NORMAL**.
1. In the **Sales tax group** field, select **VE-DOM**.
1. Post the journal.
1. Go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Financial journals**.
1. In the **Criteria** section, in the **Journal** field, select **JourNdF**.
1. In the **From date** field, select **4/1/2021**.
1. In the **To date** field, select **4/30/2021**.
1. In the **Final print** field select **Yes**.
1. Select **OK** to review the report.

![Financial journal report page 1.](../media/emea-bel-journal-reports-financial-journal-report.png)

![Financial journal report page 2.](../media/emea-bel-journal-reports-financial-journal-report-2.png)

### Print the other journal report

To print the **Other journal** report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Journal entries** \> **General journals**.
1. Create a new journal.
1. In the **Name** field, select **ODComptabl**.
1. Go to **Lines**.
1. In the **Date** field, select **4/15/2021**.
1. In the **Account type** field, select **Customer**.
1. In the **Account** field, select **1001**.
1. In the **Debit** field, enter "100".
1. In the **Offset account type** field, select **Bank**.
1. In the **Offset account** field, select **FRRT OPER**.
1. In the **Item sales tax group** field, select **NORMAL**.
1. In the **Sales tax group** field, select **VE-DOM**.
1. Post the journal.
1. Go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Other journals**.
1. In the **Criteria** section, in the **Journal** field, select **ODComptabl**.
1. In the **From date** field, select **5/1/2021**.
1. In the **To date** field, select **5/31/2021**.
1. In the **Final print** field, select **Yes**.
1. Select **OK** and review the report result.

![Other journals report page 1.](../media/emea-bel-journal-reports-other-journal-report-1.png)
![Other journals report page 2.](../media/emea-bel-journal-reports-other-journal-report-2.png)

### Print the overview journal report

To print the overview journal report, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquiries and reports** \> **Journal reports** \> **Overview journals**.
1. In the **From date** field, select **4/1/2021**.
1. In the **To date** field, select **5/31/2021**.
1. Select **OK** and review the report result.

![Overview journal report.](../media/emea-bel-journal-reports-overview-journal-report.png)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
