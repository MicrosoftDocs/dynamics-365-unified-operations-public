---
# required metadata

title: Create charges codes
description: This topic describes examples and how to configure charges codes for both accounts payable and accounts receivable. 
author: raprofit
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MarkupTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

---
# Create charges codes

If you must track sales amounts or purchase amounts in addition to line items on a sales or purchase order, you can use charges codes. For example, you might pay freight and insurance on a purchase order, and these amounts might be itemized separately on the purchase order. You can specify whether these amounts are posted to expense accounts, or whether they are added to the cost of the items.

You can create charges codes for Accounts receivable and Accounts payable.

**Set up charges codes for Accounts receivable**

1.  Click **Accounts receivable** &gt; **Charges setup** &gt; **Charges code**.

2.  Click **New**. In the **Charges code** field, type a code for the charge.

3.  In the **Description** field, type a description of the charge.

4.  Optional: In the **Item sales tax group** field, select a sales tax group.

5.  On the **Posting** FastTab, specify how the charge is automatically debited and credited.

6.  If you selected **Ledger account** as the debit type or credit type, specify a posting type in the **Posting** fields, and specify the main account in the **Account** fields.

**Example**

Your customer pays the charge. Therefore, the charge is added to the sales order totals. You set up the following posting information:

-   In the **Type** field in the **Debit** field group, select **Customer/Vendor** to add the invoice charge to the customer's account.

-   In the **Type** field in the **Credit** field group, select **Ledger account**. Then, in the **Account** field, select the main account for revenue from invoice charges.

** Note**

You can enter a different currency for the charge transaction if the debit type or credit type is either **Ledger account** or **Item** for the selected code.

You can print the text for charges in the language that is assigned to the customer. Click **Translations** to specify text for the charges code in other languages.

**Set up charges codes for Accounts payable**

1.  Click **Accounts payable** &gt; **Charges** **setup** &gt; **Charges code**.

–or–

Click **Procurement and sourcing** &gt; **Setup** &gt; **Charges** &gt; **Charges code**.

2.  Click **New**. In the **Charges code** field, type a code for the charge.

3.  In the **Description** field, type a description of the charge.

4.  Optional: In the **Item sales tax group** field, select a sales tax group.

5.  Optional: In the **Maximum amount** field, type the maximum amount that is allowed for this charges code.

This field is used to validate charges for vendor invoices. You can enable the validation of charges in the **Accounts payable parameters** form. In the **Invoice validation** area, select the **Enable invoice matching validation** check box.

** Important**

To validate charges for invoices, you must also create an instance of a policy rule type that is based on charges for the specific vendor invoice policy.

6.  On the **Posting** FastTab, specify how the charge is automatically debited and credited.

7.  If you selected **Ledger account** as the debit type or credit type, specify a posting type in the **Debit posting** and **Credit posting** fields, and specify the main account in the **Debit account** and **Credit account** fields.

8.  To enable the comparison of charges values for an invoice that contains the charges from the corresponding purchase order header or lines, select the **Compare purchase order and invoice values** check box.

**Example**

You can record the charge as an expense as part of the total for the purchase order or vendor invoice. You set up the following posting information:

-   In the **Type** field in the **Credit** field group, select **Customer/Vendor** to add the invoice charge to the vendor's account.

-   In the **Type** field in the **Debit** field group, select **Ledger account**. Then, in the **Account** field, select the main account for expenses from invoice charges.

To add the unit charge to the item cost, you set up the following posting information:

-   In the **Type** field in the **Credit** field group, select **Customer/Vendor** to add the invoice charge to the vendor's account.

-   In the **Type** field in the **Debit** field group, select **Item** to add the charge to the item cost.

** Note**

You might want to use a currency other than the currency that is specified on the purchase order or invoice. You can enter a different currency if the debit type or credit type is either **Ledger account** or **Item** for the selected code.

You can print the text for charges in the language that is assigned to the vendor. Click **Translations** to specify text for the charges code in other languages.
