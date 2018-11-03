---
# required metadata
title: Sales and purchase books for Russia 
description: This topic provides information about sales books and purchase books for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Sales and purchase books for Russia

[!include [banner](../includes/banner.md)]

## Create a purchase book 

A purchase book is a tax accounting document. In a purchase book, you can record vendor factures, factures on returns and credit notes to vendors, factures on advance reports from advance holders, factures on customer prepayments, and corrected tax transaction factures.


1.  Click **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.

2.  Click the **Statutory reporting** FastTab and, in the **Report Folder** field, specify the folder that contains the purchase book template.

3.  Close the page.

4.  Click **Accounts payable** \> **Setup** \> **Accounts payable parameters**.

5.  Click **Number sequences**, and in the **Number sequence code** field, select the number sequence for the reference type **Purchase book**.

6.  Close the page.

7.  Click **Accounts payable** \> **Periodic** \> **Purchase book** \> **Purchase books journal**.. A list of previously created purchase books is displayed in the form.

8.  Create a new purchase book.
    
    > [!NOTE]
    > The **New** button is available only if all books that are listed in the form are closed. The **Code** field is updated automatically based on the purchase book numbering sequence.
    
9.  In the **Name** field, enter a name for the book.

10. Click **Update** to open the **Purchase book** form.

    > [!NOTE]
    > You can only update an open book.

11. In the **To date** field, select the end date of the settlement period for which the purchase book is updated.
    
    > [!NOTE]
    > When you create the first book, you can set only the end date. The dates cannot be edited for later books. The **From date** and **To date** fields are determined by the tax settlement period.

12. Select the **Close the book** check box to close the book after the update.

13. Click **OK** to create a new purchase book. The lines of the purchase book are refreshed, and the closing date is saved in the **Closed date** field of the book in the **Purchase books journal** page.
    > [!NOTE]
    > Click **Delete** to delete a purchase book. Only the last book can be deleted regardless of whether it is closed or not.

14. Click **Print** \> **Purchase book** to print the purchase book in the internal report.
    
    > [!NOTE]
    > In the **Purchase books journal** page, click **Lines** to open the **Purchase book lines** form to verify purchase book line details.

## Create an additional page in a purchase book 

When you correct transactions for a closed tax period, an additional page is created in the closed purchase book to represent the tax period of the adjustment. Corrected factures are displayed in the new page in the purchase book.

The additional page contains information about purchase book totals at the end of the corrected period, including previous additional pages, corrected factures, and other registered changes.

1.  Click **General ledger** \> **Journals** \> **General journal**.

2.  Press CTRL+N to create a new line, and enter the required details.

3.  In the **Account type** field, select **Ledger**.

4.  In the **Account** field, select the ledger account number.
    
    > [!NOTE]
    > The ledger account must be specified with the **Sales tax** posting type.

5.  In the **Debit** field, enter the corrected debit amount.

6.  In the **Offset account type** field, select **Ledger**.

7.  In the **Offset account** field, select the ledger offset account number.

8.  Click the **General** tab. In the **Sales tax code** field, select the sales tax code for the transaction.
    
    > [!NOTE]
    > The ledger account specified in the **Account** field on the **Overview** tab must belong to the accounting posting group of the selected sales tax code.

9.  Click **Post** \> **Post** to post the journal voucher.

10. In the **Journal voucher** page, click **Functions** \> **Purchase book** to open the **Update facture** page.

11. In the **Counteragent** field, select the vendor.

12. In the **Date of the registration** field, select the registration date of the corrected facture.

13. In the **Facture** field, select the corrected facture from the vendor factures page, as specified in the **Counteragent** field.

14. In the **Facture date** field, view the facture creation date.
    
    > [!NOTE]
    > The corrected book code is determined by the date of the corrected period. Previous period modifications are registered in the book for the current period. These modifications are displayed on additional pages that are added to the books for previous periods.

15. In the lower section of the page, on the **Invoice** tab, use the **To facture** check box to select the invoice or invoices for the facture.
    
    > [!NOTE]
    > If you do not want to create a facture for a particular invoice line, clear the **To facture** check box on the **Invoice lines** tab.





16. Click **Posting** \> **Update facture** to post the facture journal.
    
    > [!NOTE]
    > The created facture is updated in the Facture journal page. After VAT is processed and the purchase book lines are refreshed, the corrected facture is displayed in the **Purchase book lines** page. The **Correction** field group displays the details about the corrected facture.

17. Click **Accounts payable** \> **Periodic** \> **Purchase book** \> **Purchase books journal** to open the **Purchase books journal** form.

18. Select the additional page and click **Print** \> **Print additional list** to print the page.
    
    > [!NOTE]
    > Corrected purchase book lines are included in the additional pages. Other additional pages are created if other tax periods were corrected in the current reporting period.
    > The purchase book can be printed in a Microsoft Office Excel template.

## Create a sales book 

VAT debt accrual is generated according to sales book entries. All factures for sales of goods, services, and advance payments from customers are included in the sales book.

1.  Click **Organization administration** \> **Setup** \> **Organization** \> **Legal entities**.

2.  Click the **Statutory reporting** FastTab and, in the **Report Folder** field, specify the folder that contains the purchase book template.

3.  Close the page.

4.  Click **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.

5.  Click **Number sequences**, and in the **Number sequence code** field, select the number sequence for the reference type **Sales book**.

6.  Close the page.

7.  Click **Accounts receivable** \> **Periodic** \> **Sales book** \> **Sales books journal**. A list of previously created sales books is displayed in the form.

8.  Create a new sales book.
    
    > [!NOTE]
    > The **New** button is available only if all books that are listed in the form are closed. The **Code** field is updated automatically, based on the sales book numbering sequence.

9.  In the **Name** field, enter a name for the book.

10. Click **Update** to open the **Sales book** page.

11. In the **To date** field, select the end date of the settlement period for which the sales book is updated.
    
    > [!NOTE]
    > <P>When you create the first book, you can set only the end date. The dates cannot be edited for later books. The **From date** and **To date** fields are determined by the tax settlement period.

12. Select the **Close the book** check box to close the book after the update.
    
    > [!NOTE]
    > After you create and close the book, you cannot remove factures from the closed book. You cannot create new factures in a closed period.

13. Click **OK** to create a new sales book. The lines of the sales book are refreshed, and the closing date is saved in the **Closed date** field of the book in the **Sales books journal** page.
    
    > [!NOTE]
    > Click **Delete** to delete a sales book. Only the last book can be deleted regardless of whether it is closed or not.

14. Click **Print** \> **Sales book** to print the sales book in the internal report.
    
    > [!NOTE]
    > In the **Sales books journal** page, click **Lines** to open the **Sales book lines** form to verify the sales book line details.
    
    
    
    
    
# Print issued and received factures journal legacy format
    
Facture accounting journal contains list of issued and received invoice-factures related to activities for the benefit of another entity, like agent transactions or commission.

## Set up parameters for factures journal

In **General ledger parameters** page, on **Sales tax** tab, **Tax options** fast tab, fill the following fields:

- **Facture operation code delimiter** – delimiter to be used in case several operation types codes are assigned to a single facture
- **FACTURE ACCOUNTNG JOURNAL Format mapping** – Electronic reporting format for facture journal in xml.

## Print a facture accounting journal

1.	Run report through **General ledger > Inquiries and reports > Journal reports > Facture accounting journal**. In the opened dialog **Facture accounting journal** define the following parameters:

2.	Choose reporting period in the **Date interval code** field or define **From date** and **To date**

3.	In the field **Outgoing** choose the criteria for inclusion of intermediary deals factures into the facture journal: 

- **Date of the registration** - Issued factures journal contains all intermediary deals factures regardless confirmation to principal (intermediary deal information for such factures may be empty); 

- **Confirmation date** - Issued factures journal contains only confirmed intermediary deals factures (intermediary deal information for such factures is filled with received factures from principal)

4.	Enable **Date of reporting** to Filter factures by reporting date rather than facture date.

5.	Enable **Create XML file** to create electronic xml report in addition to Excel report.

6.	Click OK to print facture accounting journals for the selected period.

