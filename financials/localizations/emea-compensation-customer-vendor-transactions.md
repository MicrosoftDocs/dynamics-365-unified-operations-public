---
# required metadata

title: Set up customer and vendor compensation | Microsoft Docs
description: This topic provides information about how to run the vendor and customer account compensation process for legal entities that have their primary address in Hungary or Poland.
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
This topic provides information that will help you run the compensation process for vendor and customer accounts, for legal entities that have their primary address in Hungary or Poland.

Often, users in Eastern Europe must settle receivable and payable amounts for a company that is registered as both a customer and a vendor in the system. This settlement process uses a legal procedure that is known as *compensation* or *netting*. 

## Enabling compensation

### Set up compensation notes
You can set up notes so that they are printed in the compensation letter. You can open the **Form notes** page from **Setup** > **Forms** in Accounts receivable, Accounts payable, or Project management and accounting.

When you create a new form note, you can select the part of the compensation letter that you're setting up the note for:

 - **Compensation letter–Header** – The top part of the compensation letter, such as company name.
 - **Compensation letter–Receivable** – The body of the receivable compensation letter.
 - **Compensation letter–Payable** – The body of the payable compensation letter.
 - **Compensation letter–Balance** – The body of the balance compensation letter

You can enter a note for each corresponding combination of a form note and a language.

The form note is based on the mathematical sign of the balance amount for the compensation report:

- If the balance amount is more than 0 (zero), the receivable compensation note is printed.
- If the balance amount is less than 0 (zero), the payable compensation note is printed.
- If the balance amount is equal to the compensation letter, the balance note is printed.

### Set up a vendor and a customer
A legal entity or individual can be a customer or vendor of your company. The compensation option is available only to parties that are associated. To set up the association, open the account details for a customer or vendor account, and then, on the **Miscellaneous** tab, in the **Remittance** field group, select an associated party account: **Customer account** for a vendor master or **Vendor account** for a customer master.

### Create a compensation journal
You can optionally create a journal that will be used to present a compensation proposal. You can post the proposal and also print a compensation report. Go to **General journal** > **Journal entries** > **General journals**.

## Record transactions
Typically, all the invoices that are recorded for the associated customer and vendor accounts are available and are used for compensation: 

 - Sales invoices (**Accounts receivable** > **Orders** > **All sales orders**)
 - Free text invoices (**Accounts receivable** > **Invoices** > **All free text invoices**)
 - Vendor invoices (**Accounts payable** > **Purchase orders** > **All purchase orders**)
 - Project sales invoices (**Project management and accounting** > **Project invoices** > **Project invoice proposals**)

You can also use any open vendor and customer transactions in the compensation process. These transactions include payments or invoices that are recorded through journals. 

## Process a compensation letter
If you have open customer and vendor transactions, you can start the compensation process. Open the **All customers** or **All vendors** page, and then click **Transactions** to review all party transactions. Select one or multiple open transactions (transactions that have a balance that is more than or less than 0 [zero]). Then click **Compensation** to open the **Compensation of customer/vendor transactions** page. This page includes two grids, one for customer transactions and one for vendor transactions. One of the grids will show the transactions that you selected. The other grid will show the transactions that are available for compensation. You can select one or more transactions to mark for compensation. After you've finished selecting transactions, click **Create compensation**. In the dialog box that appears, you can set the following fields:

 - **Journal** – Select a journal name to create a new journal.
 - **Journal batch number** – Select an existing journal batch number.
 - **Transaction date** – The transaction date for journal entries.
 - **Print compensation report** – Select this option to print a report that will be sent to your cooperating party for acceptance.

If you set a value for both the **Journal** and **Journal batch number** fields, the number has priority. Therefore, transactions will be created in that journal, not in a new journal.

## Process compensation
After you've created a compensation proposal in a journal, and your compensation proposal has been accepted by your cooperating party, you can go to the general journal and post transactions to record compensations in the general ledger. If you must reprint a compensation report, you can click **Print** > **Compensation letter** on a general journal lines page.


## Frequently asked questions
**Q: Can I compensate transactions for multiple vendor and customer accounts at the same time?**

**A:** You can have a remittance relation between one vendor account and one customer account. Therefore, you can process compensation between single accounts at the same time.

**Q: Can I use foreign transactions for compensation?**

**A:** By default, the compensation function is designed for transactions in domestic currency. You can also use foreign currency transactions. However, in a general journal, you must specify an exchange rate for the compensation proposal transactions that are created.

**Q: Is the compensation function available for all countries or regions?**

**A:** The compensation function is available only for legal entities that have their primary address in Hungary or Poland.
