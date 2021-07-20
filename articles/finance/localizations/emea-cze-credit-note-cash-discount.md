---
# required metadata

title: Credit note on cash discount
description: This topic provides information that will help legal entities in the Czech Republic create, post, and print credit notes for cash discounts that are given to customers.
author: ShylaThompson
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustParameters, PrintMgmtSetupUIMain, Reasons
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 273063
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Credit note on cash discount

[!include [banner](../includes/banner.md)]

This topic provides information that will help legal entities in the Czech Republic create, post, and print credit notes for cash discounts that are given to customers.

Companies in the Czech Republic must issue credit notes for cash discounts that are given to customers. These credit notes must include the following information:

-   Invoice number
-   Value-added tax (VAT) base and amount from the original document
-   Reason for a correction

## Prerequisites

### Set up number sequences

Create a continuous number sequence for a legal entity. For more information, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md) On the **Accounts receivable parameters** page, select the number sequence that you created for **Sales credit note**. Additionally, set up a number sequencevfor **Sales credit note voucher**. You can use the same number sequence that you used for **Sales credit note**.

### Set up sales tax codes

For more information, see [Sales tax overview](../general-ledger/indirect-taxes-overview.md).

### Set up report formats for documents

1.  Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.

2.  On the **General** tab, under **Set up options for customer forms**,
    click **Print management**.

3.  In the tree, expand **Module - accounts
    receivable** \> **Documents** \> **Customer invoice**. In the **Report
    format** field, enter or select a value.

4.  In the tree, under the **Customer invoice** node, select **Original**. In
    the **Report format** field, enter or select a value.

5.  In the tree, expand **Module - accounts
    receivable** \> **Documents** \> **Free text invoice**. In the **Report
    format** field, enter or select a value.

6.  In the tree, under the **Free text invoice** node, select **Original**. In
    the **Report format** field, enter or select a value.

### Set up customer reason codes.

On the **Customer reason codes** page (**Accounts
receivable** \> **Setup** \> **Customer reason codes**), create or edit the
reason codes that are used for tax corrective documents.

### Set up Accounts receivable parameters

On the **Accounts receivable parameters** page (**Accounts
receivable** \> **Setup** \> **Accounts receivable parameters**),
on **Settlement** tab, on the **Options** FastTab, set up the following
parameters:

-   Select the **Require reason codes for credit notes** check box.

-   Select the **Post credit note for cash discount** check box.

In the **Reason code for cash discounts** field, select a default reason code to
use for tax corrective documents.

## Credit notes for cash discounts

Credit notes for cash discounts are posted automatically when open customer
transactions (customer invoice and customer payment) are settled. When credit
notes for cash discounts are posted, they include the reason codes that you set
up in Account receivable parameters, and a reference to the original invoice.
Credit notes for cash discounts are numbered by using the number sequence that
you set up for credit notes. The document printout is named **Tax corrective
document**. It includes the original invoice number, the VAT base and amount,
and the reason why a correction was printed.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]