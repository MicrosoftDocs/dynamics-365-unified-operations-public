---
title: Set up customer and vendor compensation
description: Learn about how to run the vendor and customer account compensation process for legal entities that have their primary address in Hungary or Poland.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Hungary, Poland
ms.search.validFrom: 2016-02-28
ms.search.form: CustTable, CustVendCompensation, VendTable, CustTrans, VendTrans
ms.dyn365.ops.version: AX 7.0.0
---

# Set up customer and vendor compensation

[!include [banner](../../includes/banner.md)]

This article helps you run the compensation process for vendor and customer accounts, for legal entities that have their primary address in Hungary or Poland.

Often, users in Eastern Europe must settle receivable and payable amounts for a company that the system registers as both a customer and a vendor. This settlement process uses a legal procedure that is known as *compensation* or *netting*.

## Enabling compensation

### Set up compensation notes

Set up notes so that they're printed in the compensation letter. You can open the **Form notes** page from **Setup** > **Forms** in Accounts receivable, Accounts payable, or Project management and accounting.

When you create a new form note, select the part of the compensation letter that you're setting up the note for:

- **Compensation letter–Header** – The top part of the compensation letter, such as company name.
- **Compensation letter–Receivable** – The body of the receivable compensation letter.
- **Compensation letter–Payable** – The body of the payable compensation letter.
- **Compensation letter–Balance** – The body of the balance compensation letter.

Enter a note for each corresponding combination of a form note and a language.

The form note is based on the mathematical sign of the balance amount for the compensation report:

- If the balance amount is more than 0 (zero), the receivable compensation note is printed.
- If the balance amount is less than 0 (zero), the payable compensation note is printed.
- If the balance amount is equal to the compensation letter, the balance note is printed.

### Set up a vendor and a customer

A legal entity or individual can be a customer or vendor of your company. The compensation option is available only to parties that are associated. To set up the association, open the account details for a customer or vendor account. On the **Miscellaneous** tab, in the **Remittance** field group, select an associated party account: **Customer account** for a vendor master or **Vendor account** for a customer master.

### Create a compensation journal

You can optionally create a journal that you use to present a compensation proposal. You can post the proposal and also print a compensation report. Go to **General journal** > **Journal entries** > **General journals**.

## Record transactions

Typically, all the invoices that you record for the associated customer and vendor accounts are available and used for compensation:

- Sales invoices (**Accounts receivable** > **Orders** > **All sales orders**)
- Free text invoices (**Accounts receivable** > **Invoices** > **All free text invoices**)
- Vendor invoices (**Accounts payable** > **Purchase orders** > **All purchase orders**)
- Project sales invoices (**Project management and accounting** > **Project invoices** > **Project invoice proposals**)

You can also use any open vendor and customer transactions in the compensation process. These transactions include payments or invoices that you record through journals.

## Process a compensation letter

If you have open customer and vendor transactions, you can start the compensation process. Open the **All customers** or **All vendors** page, and then select **Transactions** to review all party transactions. Select one or multiple open transactions (transactions that have a balance that's more than or less than 0 [zero]). Then select **Compensation** to open the **Compensation of customer/vendor transactions** page. This page includes two grids, one for customer transactions and one for vendor transactions. One of the grids shows the transactions that you selected. The other grid shows the transactions that are available for compensation. You can select one or more transactions to mark for compensation. After you finish selecting transactions, select **Create compensation**. In the dialog box that appears, you can set the following fields:

- **Journal** – Select a journal name to create a new journal.
- **Journal batch number** – Select an existing journal batch number.
- **Transaction date** – The transaction date for journal entries.
- **Print compensation report** – Select this option to print a report that you send to your cooperating party for acceptance.

If you set a value for both the **Journal** and **Journal batch number** fields, the number has priority. Therefore, transactions are created in that journal, not in a new journal.

## Process compensation

After you create a compensation proposal in a journal and your cooperating party accepts your compensation proposal, go to the general journal and post transactions to record compensations in the general ledger. If you need to reprint a compensation report, you can select **Print** > **Compensation letter** on a general journal lines page.

## Frequently asked questions

**Q: Can I compensate transactions for multiple vendor and customer accounts at the same time?**

**A:** You can create a remittance relation between one vendor account and one customer account. Therefore, you can process compensation between single accounts at the same time.

**Q: Can I use foreign transactions for compensation?**

**A:** By default, the compensation function is designed for transactions in domestic currency. You can also use foreign currency transactions. However, in a general journal, you must specify an exchange rate for the compensation proposal transactions that you create.

**Q: Is the compensation function available for all countries or regions?**

**A:** The compensation function is available only for legal entities that have their primary address in Hungary or Poland.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
