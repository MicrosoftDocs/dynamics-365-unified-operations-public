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

# Sales and purchase books. Invoice-factures journals.

[!include [banner](../includes/banner.md)]

  
# Generate Sales book, Purchase book and Additional sheets

Sales and purchase books are legacy documents which must be prepared and stored during the tax period. They should be submitted to Tax authorities periodically and at request. VAT books contain issued and received invoice-factures.

## Set up parameters

1.	In the **Accounts receivable parameters** page, define Number sequence for Sales book.
2.	In the **Accounts payable parameters** page, define Number sequence for Purchase book.
3.	In the **Tax > Indirect tax > Sales tax > Sales tax settlement periods** create tax period.
4.	In the **General ledger parameters** page, in the **Sales tax** tab, in the **Tax options** fast tab, in the field **Sale/purchase book date and number delimiter**, define the delimiter between date and number of invoice-facture in the printing format of sales/purchase book.
5.	In the **Accounts receivable parameters** page, in the **Ledger and sales tax** tab, in the **Sales book** fast tab, choose Electronic reporting formats for Sales book and Sales book additional sheet in xml.
6.	In the **Accounts payable parameters** page, in the **Ledger and sales tax** tab, in the **Purchase book** fast tab, choose Electronic reporting formats for Purchase book and Purchase book additional sheet in xml.


## Generate and print sales book

### Generate sales book

1.	Create a new sales book journal in **Accounts receivable > Periodic tasks > Sales book > Sales book journal**
[!NOTE] The **New** button is available only if all books that are listed in the form are closed. The **Code** field is updated automatically, based on the sales book numbering sequence.
2.	In the **Name** field, enter a name for the book.
3.	Click **Functions >Update** to generate lines in the sales book journal. In the opened dialog **Sales book** define the following parameters:
-	Review **From date** and **To date** fields which are determined automatically by the tax settlement period. 
-	Enable **Close the book** to close the book after the update. Upon closure, you cannot create new factures in a closed period. 
-	Click **OK**. The lines of the sales book are generated, and the closing date is saved in the **Closed date** field of the sales book journal.

### Functions available on the Sales books journals page
| **Function** | **Description** |
| ----- | ----- |
| **Lines** | Click to open the Sales book lines form to verify the sales book line details. |
| **Totals** | Click to review total VAT Base and VAT amounts for the Sales book. Totals are represented separately for Domestic VAT, Export VAT, VAT restoration |
| **Print > Sales book** | Click to print sales book report |
| **Print > Print additional list** | Click to print sales book additional sheet report |

### Print sales book
Choose the Sales book journal line in the **Sales book journals** page and click **Print > Sales book** 
Define the following parameters in the **Sales book to Microsoft office Excel** dialog:
2.	Review **From date** and **To date** - this is the sales book reporting period
3.	Enable **Group by factures** to group factures with the same Facture number into one line with total amount.
4.	Enable **Exclude storno** to exclude both original and storno transactions in specified period from the printing form report
5.	Enable **Create XML file** to create electronic report in legacy format in addition to Excel report.
6.	Click **OK**

### Print sales book additional sheet
Choose the Sales book journal line in the **Sales book journals** page and click **Print > Print additional list** 
Additional sheets for all tax settlement periods which were corrected in the chosen period of sales book will be generated and printed. Currently only corrective and revision factures which decrease VAT amount to be paid to tax authorities in the corrected period are considered for Additional sheet generation. Corrective and revision factures which increase the VAT amount are printed in the Sales book of current period. 

## Generate and print purchase book

### Generate purchase book
1.	Create a new purchase book journal in **Accounts payable > Periodic tasks > Purchase book > Purchase book journal**
[!NOTE] The **New** button is available only if all books that are listed in the form are closed. The **Code** field is updated automatically, based on the purchase book numbering sequence.
2.	In the **Name** field, enter a name for the book.
3.	Click **Update** to generate lines in the purchase book journal. In the opened dialog **Purchase book** define the following parameters:
-	Review **From date** and **To date** fields which are determined automatically by the tax settlement period. 
-	Enable **Close the book** to close the book after the update. Upon closure, you cannot create new factures in a closed period. 
-	Click **OK**. The lines of the purchase book are generated, and the closing date is saved in the **Closed date** field of the purchase book journal.

### Functions available on the Purchase books journals page
| **Function** | **Description** |
| ----- | ----- |
| **Lines** | Click to open the Purchase book lines form to verify the purchase book line details |
| **Totals** | Click to review total VAT Base and VAT amounts for the Purchase book |
| **Print > Purchase book** | Click to print purchase book report |
| **Print > Print additional list** | Click to print purchase book additional sheet report |

### Print purchase book
Choose the Purchase book journal line in the **Purchase book journals** page and click **Print > Purchase book** 
Define the following parameters in the **Purchase book to Microsoft office Excel** dialog:
1.	Review **From date** and **To date** - this is the sales book reporting period
2.	Enable **Group by factures** to group factures with the same Facture number into one line with total amount.
3.	Enable **Exclude storno** to exclude both original and storno transactions in specified period from the printing form report
4.	Enable **Create XML file** to create electronic report in legacy format in addition to Excel report.
5.	Click **OK**

### Print purchase book additional sheet
Choose the Sales book journal line in the **Sales book journals** page and click **Print > Print additional list** .
Additional sheets for all tax settlement periods which were corrected in the chosen period of purchase book will be generated and printed. Currently only corrective and revision factures which increase VAT amount to be deducted in the corrected period are considered for Additional sheet generation. Corrective and revision factures which decrease the VAT amount to be deducted in the corrected period, are printed in the Purchase book of current period. 


# Print issued and received factures journal
    
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

