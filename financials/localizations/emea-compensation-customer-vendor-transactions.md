---
# required metadata

title: Set up customer and vendor compensation | Microsoft Docs
description: 
author: mrolecki
manager: AnnBe
ms.date: 05-19-2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

keywords: CustTable, CustVendCompensation, VendTable, CustTrans, VendTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 1691503
ms.search.region: Hungary, Poland
# ms.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Set up customer and vendor compensation
This topic provides information about running the vendor and customer accounts compensation process for legal entities with a primary address in Hungary or Poland.

Users in Eastern Europe often need to settle receivables and payables amounts for the same company registered as a customer and a vendor in the system using legal procedure called compensation, also known as netting. 

## Enable compensation

### Set up compensation notes
You can set up notes to be printed in the compensation letter. You can open the Form notes page either from Accounts receivable, Accounts payable or Project management and accounting setup menu. When you create a new form note, you can select the part of the compensation letter from the following options to set up a note for:

 - **Compensation letter–Header** – top part of the compensation letter such as company name
 - **Compensation letter–Receivable** – body of the receivable compensation letter
 - **Compensation letter–Payable** – body for the payable compensation letter
 - **Compensation letter–Balance** – body of the balance compensation letter

You can enter a note for each corresponding combination of a form note and language.

The form note is based on the mathematical sign of the balance amount for the compensation report. If the balance amount is greater than zero, the receivable compensation note is printed. If the balance amount is less than zero, the payable compensation note is printed. If the balance amount is equal to the compensation letter, the balance note is printed.

### Set up a vendor and a customer
A legal entity or individual can be a customer or vendor of your company. The compensation option will be available only to the parties which are associated. The association can be done by opening a customer or vendor account details and selecting an associated party account in **Miscellaneous** details tab, field group **Remittance**, Customer account for a vendor master and Vendor account for a customer master.

### Create a compensation journal
You can create optionally a journal that will be used for presenting netting proposal, posting the proposal as well as printing a compensation report. You use **General journal** > **Journal entries** > **General journals** for this purpose.

## Record transactions
Typically, all the invoices recorded for the associated customer and vendor accounts are available and used for netting: 

 - **Sales invoices** (Accounts receivable > Orders > All sales orders)
 - **Free text invoices** (Accounts receivable > Invoices > All free text invoices)
 - **Vendor invoices** (Accounts payable > Purchase orders > All purchase orders)
 - **Project sales invoices** (Project management and accounting > Project invoices > Project invoice proposals)

You can also use any open vendor and customer transactions, like payments or invoices recorded through journals in the compensation process. 

## Process a compensation letter

If you have open customer and vendor transactions, you can start the process of compensation. You open All customers or All vendors page and then Transactions to review all party transactions. You can select one or multiple open transactions (with balance <> 0) and click Compensation button to open the page Compensation of customer/vendor transactions. In the page you have available two grids – one for customer, and the other one for vendor transactions. In one of those you will see the transactions selected in the previous step, in the other – transaction available for compensation. You can again use multi selection to mark transactions for compensation. Once you selected all the desired transactions, you can use Create compensation function. In the presented dialog you can select following options:

 - **Journal** – select a journal name to create a new journal
 - **Journal batch number** – select existing, previously created journal batch number
 - **Transaction date** – transaction date for journal entries
 - **Print compensation report** – to print a report the will be sent for acceptance by your cooperating party.

If you specify both Journal and Journal batch number, the number takes priority and transactions will be created in that journal not in a new one.

## Process compensation
Once you have a compensation proposal created in a journal, and your compensation proposal has been accepted by your cooperating party, you can go to the general journal and post transactions to record compensations in the general ledger. If needed a compensation report can be reprinted in a general journal lines page (**Print** > **Compensation Letter** function).


## FAQ
**Q: Can I compensate transactions for multiple vendor and customer accounts at once?**

**A**: You can have remittance relation between one vendor account and one customer account. Therefore, at once you can process compensations between single accounts.

**Q: Can I use foreign transactions for compensation?**

**A**: By default, compensation function is designed for transactions in domestic currency. You can also use foreign currency transactions but you must specify an exchange rate for the created compensation proposal transactions in a general journal.

**Q: Is the compensation function available for all countries?**

**A**: The compensation function is available only for legal entities with a primary address in Hungary or Poland.
