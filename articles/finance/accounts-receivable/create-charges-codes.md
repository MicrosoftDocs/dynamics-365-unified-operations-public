---
# required metadata

title: Create charges codes
description: This article explains how to configure charges codes for both Accounts payable and Accounts receivable. 
author: rachel-profitt
ms.date: 03/23/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MarkupTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---

# Create charges codes

This article explains how to configure charges codes for both Accounts payable and Accounts receivable. If your organization requires that sales amounts or purchase amounts be tracked in addition to line items on a sales order or purchase order, you can use charges codes for this purpose. For example, you pay freight and insurance on a purchase order, and these amounts are itemized separately on the purchase order. In this case, you can specify whether the amounts are posted to expense accounts or added to the cost of the items.

## Set up charges codes for Accounts receivable

To create charges codes for Accounts receivable, follow these steps.

1. Go to **Accounts receivable** &gt; **Charges setup** &gt; **Charges code**.
2. Select **New**.
3. In the **Charges code** field, enter a code for the charge.
3. In the **Description** field, enter a description of the charge.
4. Optional: In the **Item sales tax group** field, select a sales tax group.
5. On the **Posting** FastTab, specify how the charge should be automatically debited and credited.
6. If you selected **Ledger account** as the debit type or credit type, specify a posting type in the **Posting** fields, and specify the main account in the **Account** fields.

### Example

Your customer pays the charge. Therefore, it's added to the sales order totals. You set up the following posting information:

- In the **Type** field in the **Debit** section, select **Customer/Vendor** to add the invoice charge to the customer's account.
- In the **Type** field in the **Credit** section, select **Ledger account**. Then, in the **Account** field, select the main account for revenue from invoice charges.

> [!NOTE]
> If the debit type or credit type for the selected code is either **Ledger account** or **Item**, you can enter a different currency for the charge transaction.

You can print the text for charges in the language that is assigned to the customer. To specify the text for the charges code in other languages, select **Translations**.

## Set up charges codes for Accounts payable

To create charges codes for Accounts payable, follow these steps.

1. Follow one of these steps:

    - Go to **Accounts payable** &gt; **Charges** **setup** &gt; **Charges code**.
    - Go to **Procurement and sourcing** &gt; **Setup** &gt; **Charges** &gt; **Charges code**.

2. Select **New**.
3. In the **Charges code** field, enter a code for the charge.
3. In the **Description** field, enter a description of the charge.
4. Optional: In the **Item sales tax group** field, select a sales tax group.
5. Optional: In the **Maximum amount** field, enter the maximum amount that is allowed for the charges code.

    This field is used to validate charges for vendor invoices. To enable the validation of charges, select the **Enable invoice matching validation** checkbox on the **Invoice validation** tab of the **Accounts payable parameters** page.

    > [!IMPORTANT]
    > To validate charges for invoices, you must also create an instance of a policy rule type that is based on charges for the specific vendor invoice policy.

6. On the **Posting** FastTab, specify how the charge should be automatically debited and credited.
7. If you selected **Ledger account** as the debit type or credit type, specify a posting type in the **Debit posting** and **Credit posting** fields, and specify the main account in the **Debit account** and **Credit account** fields.
8. To enable the comparison of charge values for an invoice that contains the charges from the corresponding purchase order header or lines, select the **Compare purchase order and invoice values** checkbox.

### Example

You can record the charge as an expense, as part of the total for the purchase order or vendor invoice. Follow these steps to set up posting information. 

- In the **Type** field in the **Credit** section, select **Customer/Vendor** to add the invoice charge to the vendor's account.
- In the **Type** field in the **Debit** section, select **Ledger account**. Then, in the **Account** field, select the main account for expenses from invoice charges.

Follow these steps to set up posting information so that the unit charge is added to the item cost.

- In the **Type** field in the **Credit** section, select **Customer/Vendor** to add the invoice charge to the vendor's account.
- In the **Type** field in the **Debit** section, select **Item** to add the charge to the item cost.

> [!NOTE]
> You might want to use a currency that differs from the currency that is specified on the purchase order or invoice. You can enter a different currency if the debit type or credit type for the selected code is either **Ledger account** or **Item**.

You can print the text for charges in the language that is assigned to the customer. To specify the text for the charges code in other languages, select **Translations**.
