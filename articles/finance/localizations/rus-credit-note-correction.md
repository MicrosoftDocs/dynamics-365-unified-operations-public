---
# required metadata
title: Credit note corrections (Russia)
description: This topic provides information about creating credit note corrections in Accounts receivable and Accounts payable.
author: anasyash
ms.date: 08/09/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: 10.0.0

---

# Credit note corrections (Russia)

[!include [banner](../includes/banner.md)]

## Set up negative amount transactions as corrections

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Ledger** tab, on the **Accounting rules** FastTab, set the **Correction** option to **Yes**. Transactions that have negative amounts can now be posted as corrections in the general ledger.

## Set up credit notes as corrections

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Updates** tab, on the **Invoice** FastTab, set the **Credit note as correction** option to **Yes**.
3. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
4. On the **Invoice** tab, on the **Invoice** FastTab, set the **Credit note as correction** option to **Yes**.

## Set up the amount sign for a printed invoice

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.
–or–
Go to **Accounts payable** \> **Setup** \> **Forms** \> **Form setup**.
2. On the **Invoice** tab, in the **Credit notes print** field, select a value. This field controls the amount sign in the printable form of the invoice.

  - **Credit note**: On the **Printing** page, the document lines have the opposite amount sign that the invoice lines have. In other words, the printed amounts will be positive.
  - **Goods return**: On the **Printing** page, the document lines have the same amount sign as the invoice lines. In other words, the printed amounts will be negative.

## Create a credit note for correction in Accounts receivable

### Post free text invoices as credit corrections
You can create and post free text invoices as credit corrections for return item transactions. Use the following procedure to correct a free text invoice that has both positive and negative invoice amounts.

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Select an existing free text invoice for an item that was returned.
3. On the **Invoice lines** FastTab, add an invoice line that has either a positive invoice amount or a negative invoice amount, depending on the type of correction.
4. Select **Post** to open the **Post free text invoice** dialog box.
5. Set the **Credit correction** option to **Yes**, and then select **OK** to post the invoice. This invoice has either a positive amount sign or a negative amount sign, depending on the direction of the correction. If the invoice amount is positive, you receive a message that states that the parameter for credit correction is activated.

> [!NOTE]
> You can create a credit note by selecting **Create credit note** in the **Cancel** group on the **Invoice** tab of the Action Pane. Use the **Mark** check box to select the invoice and invoice lines, and then select **OK**. Lines are created that are identical to the invoice lines, but they have the opposite amount sign.

6. On the Action Pane, on the **Invoice** tab, in the **Related information** tab, select **Invoice journal** to open the **Invoice journal** page.
7. Select **Transactions** to open the **Customer transactions** page. Review the **Correction** column to verify that the transaction was generated as a correction for the return item transaction.

> [!TIP]
> If you don't see the **Correction** column, right-click anywhere in the heading row of the grid, and then select **Add columns**. In the dialog box, select the check box for the **Correction** column, and then select **Insert**.

8.Select **Voucher** to open the **Voucher transactions** page. Review the **Correction** column to verify that the transaction was posted as a correction.

### Create credit corrections for sales orders
Just as you can post free text invoices as credit corrections, you can create credit notes for sales orders. On the **Sales order** page, select **Credit note**. Select the sales order to issue a credit note for, select the sales order lines to correct, and then select **OK**. Then, on the **Posting invoice** page, set the **Credit correction** option to **Yes**, and post the invoice.

On the Invoice journal page, you can view the original invoice and the credit note. On the Customer transactions and Voucher transactions pages, you can verify that the transactions were posted as corrections.

## Create a credit note for correction in Accounts payable

### Post and print a reverse transaction for a purchase order credit note
You can use the **Credit note** button to post a purchase order credit note transaction as a reverse transaction. Select the purchase order for the credit note, select the purchase order lines, and then select **OK**. Then, on the **Vendor invoice** page, on the Action Pane, on the **Process** tab, in the **Set** group, select **Credit setup**. Set the **Credit correction** option to **Yes**, and post the invoice.

On the **Invoice journal** page, you can perform these actions:

- Select **Transactions** to open the **Vendor transactions** page, and review the **Correction** column to verify that the transaction was generated as a correction.
- Select **Voucher** to open the **Voucher transactions** page, and review the **Correction** column to verify that the transaction was generated as a correction.
- Select **Preview/Print** to print the report.

### Post vendor invoices as credit corrections
On the **Open vendor invoices** page, you can create and post vendor invoices as credit corrections for return item transactions. The procedure resembles the procedure for posting a reverse transaction for a purchase order credit note, earlier in the topic.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]