---
title: Tax reimbursement documents for Hungary
description: Learn how to set up and create tax reimbursement documents for Hungary, including outlines on setting up parameters and default exchange rates.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Austria
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Tax reimbursement documents for Hungary

[!include [banner](../../includes/banner.md)]

## Set up parameters for tax reimbursement documents

A customer might be a person who resides in a country or region that isn't a member of the European Union (EU). Customers of this type might request reimbursement of value-added tax (VAT) that they paid on purchases that they made in Hungary. These customers might also ask that you provide documentation of the amount of VAT that they paid to you. In this case, you can create a tax reimbursement document from the customer invoice.

### Set up a default exchange rate

Use this procedure to set up an exchange rate that is automatically selected in tax reimbursement documents.

1. Select **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Other** FastTab, in the **Tax reimbursement slip** field, select the type of exchange rate that should be used by default for tax reimbursement documents.

### Set up a number sequence

Use this procedure to set up a number sequence that is automatically assigned to tax reimbursement documents.

1. Select **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Number sequences** tab, in the **Reference** field, select **Tax reimbursement document**.
3. In the **Number sequence code** field, select a number sequence for tax reimbursement documents.
4. Complete the remaining optional fields.

## Create and print a tax reimbursement document

You can provide a tax reimbursement document to customers who have paid VAT to you. Customers can use the tax reimbursement document to claim a VAT reimbursement from the authorities.

The tax reimbursement document is available only if the customer is set up as a person on the **Customers** page. On the **Customers** page, on the **General** FastTab, confirm that the **Record type** field is set to **Person**.

### Set up print management for a tax reimbursement document

1. Select **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
2. On the **Form setup** page, on the **General** tab, select **Print management**.
3. On the **Print management setup** page, under **Module - accounts receivable**, select **Tax reimbursement slip**.
4. Under **Module - inventory management** &gt; **Picking list**, select either **Original** or **Copy**.
5. In the right pane, enter information about what should be printed.
6. Optional: In the **Footer text** field, enter text that should be printed at the bottom of the tax reimbursement document.

### Select invoice lines for a tax reimbursement document

1. Select **Accounts receivable** &gt; **Inquiries and reports** &gt; **Journals** &gt; **Invoice journal**.
2. On the **Invoice journal** page, on the **Overview** tab, select the customer invoice that the customer is requesting tax reimbursement for.
3. Select the **Tax reimbursement** check box for the selected invoice.
4. By default, on the **Lines** tab, in the **Tax reimbursement lines** field, all invoice lines are selected. Clear the check box for any invoice line that should be excluded from the tax reimbursement document.
5. On the **Overview** tab, select **Tax reimbursement** &gt; **Original preview** to view the document before you print it.
6. Optional: Select **Tax reimbursement** &gt; **Use print management** to modify the print settings, such as the number of copies to print.
7. On the **View original** page, review the information, and then print the tax reimbursement document.

When you print a tax reimbursement document, the document number that is assigned to the document appears in the **Tax reimbursement document** field on the **Invoice journal** page. The **Tax reimbursement** check box is unavailable for the lines that you included in the tax reimbursement document.

### Settle a tax reimbursement

When your organization reimburses a customer for VAT, you must indicate the reimbursement in the invoice journal. Otherwise, the customer could receive a duplicate reimbursement. Use the following procedure to settle invoice lines that a customer received a VAT reimbursement for.

1. Select **Accounts receivable** &gt; **Inquiries and reports** &gt; **Journals** &gt; **Invoice journal**.
2. On the **Invoice journal** page, on the **Overview** tab, select the customer invoice that the customer received a VAT reimbursement for.
3. Select **Tax reimbursement** &gt; **VAT settled**.

The **VAT settled** check box is selected for the invoice and the invoice lines.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
