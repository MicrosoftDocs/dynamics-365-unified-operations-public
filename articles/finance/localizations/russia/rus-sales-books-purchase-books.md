---
title: Sales books, purchase books, and invoice-factures journals
description: Learn how to work with sales books, purchase books, and invoice-factures journals for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 09/05/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Sales books, purchase books, and invoice-factures journals

[!include [banner](../../includes/banner.md)]

This article explains how to work with sales books, purchase books, and invoice-factures journals for Russia in Microsoft Dynamics 365 Finance.

## Generate a sales book, purchase book, and additional sheets

Sales books and purchase books are legacy documents that must be prepared and stored during the tax period. They should be submitted to the tax authorities periodically and at request. Value-added tax (VAT) books contain invoices-factures that are issued and received.

### Set up parameters for sales and purchase books

To set up parameters for sales and purchase books, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Accounts receivable parameters** page, on the **Number sequences** tab, define a number sequence for the **Sales book** reference.
1. On the **Accounts receivable parameters** page, on the **Ledger and sales tax** tab, on the **Sales book** FastTab, select Electronic reporting (ER) formats for Sales book and Sales book additional sheet in XML. 
1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**. 
1. On the **Accounts payable parameters** page, on the **Number sequences** tab, define a number sequence for the **Purchase book** reference.
1. On the **Accounts payable parameters** page, on the **Ledger and sales tax** tab, on the **Purchase book** FastTab, select ER formats for Purchase book and Purchase book additional sheet in XML.
1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
1. On the **Sales tax settlement periods** page, create a tax period.
1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **General ledger parameters** page, on the **Sales tax** tab, on the **Tax options** FastTab, in the **Sale/purchase book date and number delimiter** field, define the delimiter that is used between the date and number of invoices-factures in the printing format of sales books and purchase books.

### Generate and print a sales book

#### Generate a sales book

To generate a sales book, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Sales book \> Sales books journal**.
1. On the **Sales books journal** page, create a sales books journal. You can create a book only if all the books that are listed on the page are closed.
1. In the **Name** field, enter a name for the book.
1. On the Action Pane, select **Functions \> Update** to generate lines in the sales books journal.
1. In the **Sales book** dialog, set the **Close the book** option to **Yes** to close the book after the update. After a book is closed, you can't create new factures in a closed period.

    The **From date** and **To date** fields are set automatically, based on the tax settlement period.

1. Select **OK**. The lines of the sales book are generated, and the closing date is entered in the **Closed date** field of the sales books journal.

#### Commands on the Sales books journal page

The following commands are available on the Action Pane of the **Sales books journal** page.

| Command | Description |
|---------|-------------|
| Lines | Open the **Sales book lines** page, where you can verify the details of the sales book lines. |
| Totals | Open the **Totals** dialog, where you can review the total VAT base and VAT amounts for the sales book. Totals are shown separately for domestic VAT, export VAT, and VAT restoration. |
| Print > Sales book | Print the sales book report. |
| Print > Print additional list | Print the sales book additional sheet report. |
| Functions > Facture operation code | Change operation codes for factures. In the **Parameters** dialog, select the facture operation code that needs to be changed and enter a new facture operation code. In the **Type** field, select the purpose of the primary address of the counterparty for which the facture operation code needs to be changed. For example, you might select **Business**. In the **Counteragent type** field, select **Customer** or **Vendor** depending on the type of the party for which the facture operation code needs to be changed. Make sure that the **Kind of activity** field in the factures for which the operation code needs to be changed is set to **Basic**. |

#### Print a sales book

To print a sales book, follow these steps:

1. On the **Sales books journal** page, select the sales books journal line, and then select **Print \> Sales book**.
1. In the **Sales book to Microsoft Office Excel** dialog, define the following parameters:

    - **From date** and **To date** – Review the dates in these fields. These fields define the sales book reporting period.
    - **Group by factures** – Set this option to **Yes** to group factures that have the same facture number onto one line that has a total amount.
    - **Exclude storno** – Set this option to **Yes** to exclude original and storno transactions during the specified period from the report.
    - **Create XML file** – Set this option to **Yes** to create an electronic report in the legacy format, in addition to the Microsoft Excel report.

1. Select **OK** to print the sales book.

#### Print a sales book additional sheet

To print a sales book additional sheet, follow these steps:

1. In Dynamics 365 Finance, go to the **Sales books journal** page.
1. Select the sales books journal line, and then select **Print \> Print additional list**.

Additional sheets are generated and printed for all tax settlement periods that were corrected during the selected period for the sales book.

Currently, only corrective and revision factures that decrease the VAT amount that must be paid to the tax authorities during the corrected period are considered when additional sheets are generated. Corrective and revision factures that increase the VAT amount that must be paid are included in the sales book for the current period.

### Generate and print a purchase book

#### Generate a purchase book

To generate a purchase book, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Periodic tasks \> Purchase book \> Purchase books journal**. 
1. On the **Purchase books journal** page, create a purchase books journal. You can create a book only if all the books that are listed on the page are closed.
1. In the **Name** field, enter a name for the book.
1. On the Action Pane, select **Update** to generate lines in the purchase books journal.
1. In the **Purchase book** dialog, set the **Close the book** option to **Yes** to close the book after the update. After a book is closed, you can't create new factures in a closed period.

    The **From date** and **To date** fields are set automatically, based on the tax settlement period.

1. Select **OK**. The lines of the purchase book are generated, and the closing date is entered in the **Closed date** field of the purchase books journal.

#### Commands on the Purchase books journal page

The following commands are available on the Action Pane of the **Purchase books journal** page.

| Command | Description |
|---------|-------------|
| Lines | Open the **Purchase book lines** page, where you can verify the details of the purchase book lines. |
| Totals | Open the **Totals** dialog, where you can review total VAT base and VAT amounts for the purchase book. |
| Print \> Purchase book | Print the purchase book report. |
| Print \> Print additional list | Print the purchase book additional sheet report. |
| Functions > Facture operation code | Change operation codes for factures. In the **Parameters** dialog, select the facture operation code that needs to be changed and enter new facture operation code. In the **Type** field, select the purpose of the primary address of the counterparty for which the facture operation code needs to be changed. For example, select **Business**. In the field **Counteragent type**, select **Customer** or **Vendor** depending on the type of the party for which the facture operation code needs to be changed. Make sure that **Kind of activity** in the factures for which the operation code needs to be changed is set to **Basic**. |

#### Print a purchase book

To print a purchase book, follow these steps:

1. In Dynamics 365 Finance, go to the **Purchase books journal** page.
1. Select the purchase books journal line, and then select **Print \> Purchase book**.
1. In the **Purchase book to Microsoft Office Excel** dialog, define the following parameters:
    - **From date** and **To date** – Review the dates in these fields. These fields define the purchase book reporting period.
    - **Group by factures** – Set this option to **Yes** to group factures that have the same facture number onto one line that has a total amount.
    - **Exclude storno** – Set this option to **Yes** to exclude original and storno transactions during the specified period from the report.
    - **Create XML file** – Set this option to **Yes** to create an electronic report in the legacy format, in addition to the Excel report.

1. Select **OK** to print the purchase book.

#### Print a purchase book additional sheet

To print a purchase book additional sheet, follow these steps:

1. In Dynamics 365 Finance, go to the **Purchase books journal** page.
1. Select the purchase books journal line, and then select **Print \> Print additional list**.

Additional sheets are generated and printed for all tax settlement periods that were corrected during the selected period for the purchase book.

Currently, only corrective and revision factures that increase the VAT amount that must be deducted during the corrected period are considered when additional sheets are generated. Corrective and revision factures which decrease the VAT amount that must be deducted during the corrected period are included in the purchase book for the current period.

## Print an issued and received factures journal

The facture accounting journal contains a list of issued and received invoice-factures that are related to activities for the benefit of another entity. Examples of these activities include agent transactions and commissions.

### Set up parameters for a factures journal

To set up parameters for a factures journal, follow these steps:

1. In Dynamics 365 Finance, go to the **General ledger parameters** page.
1. On the **Sales tax** tab, on the **Tax options** FastTab, define the following parameters:
   - **Facture operation code delimiter** – Define the delimiter that is used if several operation type codes are assigned to one facture.
   - **Facture accounting journal format mapping** – Select the ER format for facture journal in XML format.

### Print a facture accounting journal

To print a facture accounting journal, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger \> Inquiries and reports \> Journal reports \> Facture accounting journal**.
1. In the **Facture accounting journal** dialog, in the **Date interval code** field, select a reporting period. Alternatively, specify your own date range by using the **From date** and **To date** fields.
1. In the **Outgoing** field, select the criterion for including intermediary deals factures in the facture journal:

    - **Date of the registration** – The issued factures journal contains all intermediary deals factures, even if they haven't been confirmed with the principal. (The intermediary deal information for those factures might be empty.)
    - **Confirmation date** – The issued factures journal contains only confirmed intermediary deals factures. (The intermediary deal information for those factures is filled with the factures that have been received from the principal.)

1. Set the **Date of reporting** option to **Yes** to filter factures by reporting date instead of facture date.
1. Set the **Create XML file** option to **Yes** to create an electronic XML report in addition to the Excel report.
1. Select **OK** to print facture accounting journals for the selected period.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
