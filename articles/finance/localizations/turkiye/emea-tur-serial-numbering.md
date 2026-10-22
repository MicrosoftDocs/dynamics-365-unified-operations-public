---
title: Use continuous serial numbering of packing slips and invoices
description: Learn how to use continuous serial numbering for packing slips and invoices for the Republic of Türkiye in Microsoft Dynamics 365 Finance.
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: how-to
ms.date: 10/21/2026
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: SerialNumbering 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
ms.custom: 
  - bap-template
---

# Use continuous serial numbering of packing slips and invoices

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to use continuous serial numbering for packing slips and invoices for the Republic of Türkiye in Microsoft Dynamics 365 Finance.

In the Republic of Türkiye, specific number sequences are required for packing slips and invoices to ensure legal compliance and accurate tracking. To manage and track numbers in a system, you must follow a set of rules for number sequences. These rules ensure that each number is unique, in order, and easy to understand.

You can maintain organized records by using a specific format that includes prefixes, a year, and unique digits. To prevent confusion, you must ensure that the dates that are associated with these numbers are in the correct order.

Many types of documents benefit from this systematic approach to number sequencing. Examples include sales order packing slips, transfer order shipments, purchase return order product receipts, free text invoices, sales order invoices, purchase return order invoices, vendor invoice journals, customer invoices, and vendor return invoices in general journal entries.

When you use preprinted serial numbers, you must ensure that the posting date maintains chronological consistency. The posting date of each preprinted serial number must always follow the posting date of the previous preprinted serial number. In addition, to prevent the premature use of future dates, it must always precede the posting date of the next preprinted serial number. If there is a conflict with the posting date, a different number sequence should be used. This number sequence should be managed through number sequence groups.

Set up preprinted serial number configurations through common pages that you can open by using the following paths in Finance:

- **Accounts payable** \> **Setup** \> **Preprinted serial numbers**
- **Accounts receivable** \> **Setup** \> **Preprinted serial numbers**

> [!NOTE]
> As the preceding paths show, you can open the **Preprinted serial numbers** setup and parameter pages from both the **Accounts payable** module and the **Accounts receivable** module. Any changes that you make to the pages in one module are reflected on the pages in the other module.

## Serial numbering requirements

In Türkiye, preprinted serial numbers that are assigned to documents that you send to customers and vendors must use a serial prefix. Here are the general requirements for serial numbering in Türkiye:

- **Continuous values:** Numbers must be in order, without gaps.
- **Predefined format:** Set the format of the number sequence before you use it.
- **Prefix (three digits):** Numbers must include a three-digit code that identifies the sequence.
- **Year:** Numbers must include the current year in the sequence.
- **Number (nine digits):** Numbers must include a nine-digit number that uniquely identifies each entry.
- **Separators:** Use specific characters to separate the different parts of the sequence.

Set the **Serial prefix** field on the posting page for invoices and packing slips that you send to customers, for transfer order shipments, and for return product receipts and return invoices that you send to vendors. You can manually select the serial prefix when you post the relevant documents to the ledger. Alternatively, set the field automatically, based on a predefined parameter.

## Set up a serial number format

This section explains how to define serial number formats for various document types, such as e-archives, e-invoices, e-packing slips, and e-waybills. It provides information about preprinted serial numbers, including details about serial number formats and number sequences.

In Türkiye, you must generate serial numbers in a specific format that complies with regulations. The serial number must be 16 digits long (for example, *AAA2025000000001*), and it must include the following details:

- **Serial prefix:** Three digits (*AAA*)
- **Year:** Four digits (*2025*)
- **Serial number:** Nine digits (*000000001*)

You configure serial number formats on the **Serial number formats** tab of the **Preprinted serial numbers** parameter page (**Accounts payable** or **Accounts receivable** \> **Setup** \> **Preprinted serial numbers** \> **Parameters**).

The following table describes the fields that you can set on the **Serial number formats** tab.

| Field | Description |
| --- | --- |
| Format name | Specify the name of the serial format. |
| 1.field name | Select the value that appears in the first part of the serial number format. |
| 1.separator | Specify the characters or symbols that are used to divide the first and second parts of a preprinted serial number. |
| 2.field name | Select the value that appears in the second part of the serial number format. |
| 2.separator | Specify the characters or symbols that are used to divide the second and third parts of a preprinted serial number. |
| 3.field name | Select the value that appears in the third section of the serial number format. |
| 3.separator | Specify the characters or symbols that are used to divide the third and fourth parts of a preprinted serial number. |
| 4.field name | Select the value that appears in the fourth section of the serial number format. |
| 4.separator | Specify the characters or symbols that are used to divide the fourth and fifth parts of a preprinted serial number. |
| 5.field name | Select the value that appears in the fifth section of the serial number format. |
| Format | Specifies how the serial number format is structured based on the selections in each column. |

For the five ***x*.field name** fields (**1.field name**, **2.field name**, …**5.field name**), you can select the following options:

- **Serial prefix** – Select this option to specify that the serial prefix appears in the corresponding part of the serial number format.
- **Fiscal year** – Select this option to specify that the fiscal year appears in the corresponding part of the serial number format.
- **Number** – Select this option to specify that the unique serial number appears in the corresponding part of the serial number format.
- **None** – Select this option to specify that there is no value in the corresponding part of the serial number format.

The serial number format is then formed by sequentially combining the values of the ***x*.field name** and ***x*.separator** fields in the following way:

**1.field name** + **1.separator** + **2.field name** + **2.separator** + **3.field name** + **3.separator** + **4.field name** + **4.separator** + **5.field name**

For example, to generate a 16-digit preprinted serial number (such as *AAA2025000000001*) that complies with legal regulations, follow these steps:

1. In Finance, go to **Accounts payable** or **Accounts receivable** \> **Setup** \> **Preprinted serial numbers** \> **Parameters**.
1. On the **Serial number formats** tab, select **New**.
1. In the **Format name** field, enter a name.
1. In the **1.field name** field, select **Serial prefix**.
1. Leave the **1.separator** field blank.
1. In the **2.field name** field, select **Fiscal year**.
1. Leave the **2.separator** field blank.
1. In the **3.field name** field, select **Number**.
1. Leave the **3.separator** field blank.
1. In the **4.field name** field, select **None**.
1. Leave the **4.separator** field blank.
1. In the **5.field name** field, select **None**.
1. Select **Save**.

In this case, the serial number format is as follows:

*Serial prefix* + *Fiscal year* + *Number*

## Set up a serial prefix

This section explains how to set up a serial prefix for documents that you send to customers or vendors. You can define and manage serial prefixes for various document types. This setup is essential for maintaining accurate records and ensuring compliance with regulations, because it ensures that each document type uses a unique and traceable serial number format.

The following table describes the fields that you use to set up a serial prefix.

| Field | Description |
| --- | --- |
| Serial prefix | Enter a three-digit character set. |
| Number sequence group | Define a number sequence group for each serial prefix to maintain unique number sequences. |
| Serial type | Select the type of document. |
| Fiscal year | Enter the fiscal year. |
| Number of digits | Enter the length of the serial number. |
| Default prefix | Mark a serial prefix as the default. |

> [!NOTE]
> You must assign a separate number sequence group to each serial prefix. If more than one serial prefix uses the same number sequence group, the integrity of the number series is disrupted.

After you define a serial number format, set up a serial prefix for the document type.

For example, to set up a serial prefix for the document type for the serial number format that you created for a 16-digit preprinted serial number (such as *AAA2025000000001*), follow these steps:

1. In Finance, go to **Accounts payable** or **Accounts receivable** \> **Setup** \> **Preprinted serial numbers** \> **Preprinted serial numbers**.
1. In the **Document type** field, select the document type to create the serial prefix for.
1. Select **New**.
1. In the **Serial prefix** field, enter "AAA" as the three-digit prefix.
1. In the **Number sequence group** field, select the number sequence group that you created for the serial prefix.
1. Select **Save**.
1. In the **Reference** section, select the number sequence code that was created for the number sequence group. To create a number sequence, follow these steps:
    1. Go to **Organization administration** \> **Number sequences** \> **Number sequences**.
    1. In the **New** section, select **Number sequence**.
    1. In the **Number sequence code** field, enter a code for the new number sequence.
    1. In the **Name** field, enter a name for the number sequence.
    1. On the **Scope parameters** FastTab, in the **Scope** field, select *Company*. Then, in the **Company** field, select your company.
    1. On the **Segments** FastTab, define a single segment where the **Segment** field is set to **Alphanumeric**. In the **Value** field, enter 16 number signs ("\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#\#").
    1. Select **Save**.
1. In the **Serial type** field, select the relevant serial type.
1. In the **Fiscal year** field, enter "2025".
1. In the **Number of digits** field, enter "9".
1. In the **Serial format** field, select the serial number format that you created.
1. Select the **Default prefix** option if the serial prefix is the default serial prefix.
1. Select **Save**.

Use the **Open**, **Closed**, and **Cancelled** tabs to manage and track the status of preprinted serial numbers for various documents. The following table describes these tabs.

| Tab | Description |
| --- | --- |
| Open | This tab lists all preprinted serial numbers that are currently active and available for use as needed. These serial numbers are generated, but they aren't yet assigned to any document. You can change the status of a preprinted serial number from *Open* to *Cancelled* by using the **Cancel** button. |
| Closed | This tab lists preprinted serial numbers that are assigned to specific documents. These serial numbers are no longer available for new assignments. However, the system retains them for record-keeping and tracking purposes. *Closed* status indicates that the preprinted serial number is associated with a document that is posted to a document. Therefore, you can't change the status of a serial number if it's *Closed*. |
| Cancelled | This tab lists preprinted serial numbers that are invalidated or voided. These serial numbers aren't available for use and are marked as canceled because of errors, duplicates, or other reasons. However, the system retains them for audit and compliance purposes. You can change the status of a preprinted serial number from *Cancelled* to *Open* by using the **Open** button. |

> [!NOTE]
>
> - If an error occurs during the posting process, the system creates the preprinted serial number and assigns *Free* status to it on the **Open** tab. After you fix the errors and complete posting, the system reuses the preprinted serial number and moves it to the **Closed** tab.
> - If the intended posting date is earlier than the date of the last posted document for the same serial prefix, the system prevents the posting and shows an error message. In this case, you must select a different serial prefix and then reattempt the posting.

## Use a serial prefix

This section explains how to use a serial prefix for relevant documents and configure the necessary settings to ensure correct serial numbering and tracking. Use a serial prefix for the following document types:

- Packing slip for a sales order
- Shipment for a transfer order
- Product receipt for a purchase order
- Free text invoice
- Sales order invoice
- Purchase order invoice
- Vendor invoice journal
- General journals

### Packing slip for a sales order

This section explains how to use a serial prefix in a packing slip for a sales order or a sales return order.

When you want to create a packing slip for a *sales order*, select the serial prefix on the **Packing slip posting** page.

To assign a serial prefix in a packing slip for a sales order, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select the sales order to create a packing slip for.
1. On the Action Pane, on the **Pick and pack** tab, in the **Generate** group, select **Packing slip**.
1. On the **Packing slip posting** page, on the **Overview** FastTab, in the **Serial prefix** field, select the serial prefix.
1. Select **OK** to post.

After the posting process, you can find the preprinted serial number that is assigned to the packing slip by looking in the **Packing slip** field on the **Packing slip journal** page.

> [!NOTE]
> In general, during packing slip posting processes where you must select a serial prefix, the following behavior applies:
>
> - If you select the **Default prefix** option on the **Preprinted serial numbers** page for a serial prefix for the *Packing slip* document type, the system automatically selects the serial prefix in the **Serial prefix** field.
> - If you don't select the **Default prefix** option, you must manually select the serial prefix in the **Serial prefix** field.

When you want to create a packing slip for a *sales return order*, you can't select the serial prefix on the **Packing slip posting** page. Instead, set the **Serial number** field to the packing slip number from the document that you received from the customer.

To create a packing slip for a sales return order, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select the sales order to create a packing slip for.
1. On the Action Pane, on the **Pick and pack** tab, in the **Generate** group, select **Packing slip**.
1. On the **Packing slip posting** page, in the **Serial number** field, enter the packing slip number from the document that you received from the customer.
1. Select **OK** to post.

### Shipment for a transfer order

This section explains how to use a serial prefix in a shipment for a transfer order.

When you want to ship a *transfer order*, you must select the serial prefix on the **Shipment** page.

> [!NOTE]
> You select the serial prefix in the same way, regardless of whether the warehouses on the transfer order use warehouse management processes (WMS). For both types of warehouses, the **Serial prefix** field is available on the **Shipment** page.

To assign a serial prefix in a shipment for a transfer order, follow these steps:

1. In Finance, go to **Inventory management** \> **Outbound orders** \> **Transfer order**.
1. Select the transfer order to ship.
1. On the Action Pane, on the **Ship** tab, in the **Operations** group, select **Ship transfer order**.
1. On the **Shipment** page, on the **Overview** tab, in the **Update** field, select **All**.
1. In the **Serial prefix** field, select the serial prefix.
1. In the **Invoice profile** field, select the scenario for the e-waybill. Learn more in [Export of electronic waybills for transfer order shipments](emea-turkiye-electronic-transfer-orders.md).
1. Select **OK** to post.

After the posting process, the **Transfer status** field of the transfer order is set to *Shipped*. You can find the preprinted serial number that is assigned to the shipment by looking in the **Voucher** field on the **Transfer order history** page. To open this page, on the Action Pane of the transfer order, on the **Transfer order** tab, in the **View** group, select **Transfer order history**.

> [!NOTE]
> In general, during transfer order shipment posting processes, the following behavior applies:
>
> - If you select the **Default prefix** option on the **Preprinted serial numbers** page for a serial prefix for the *Packing slip* document type, the system automatically selects the serial prefix in the **Serial prefix** field.
> - If the **Default prefix** option isn't selected, you must manually select the serial prefix in the **Serial prefix** field.

### Product receipt for a purchase order

This section explains how to use a serial prefix in a product receipt for a purchase order or a purchase return order.

When you want to create a product receipt for a *purchase order*, you can't select the serial prefix on the **Product receipt posting** page. Instead, set the **Product receipt** field to the product receipt number from the document that you received from the vendor.

To create a product receipt for a purchase order, follow these steps:

1. In Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order to create a product receipt for.
1. On the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
1. On the **Posting product receipt** page, in the **Product receipt** field, enter the product receipt number from the document that you received from the vendor.
1. Select **Post**.

When you want to create a product receipt for a *purchase return order*, select the serial prefix on the **Product receipt posting** page.

To assign a serial prefix in a product receipt for a purchase return order, follow these steps:

1. In Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order to create a product receipt for.
1. On the Action Pane, on the **Receive** tab, in the **Generate** group, select **Product receipt**.
1. On the **Product receipt posting** page, on the **Overview** FastTab, in the **Serial prefix** field, select the serial prefix.
1. Select **Post**.

After the posting process, you can find the preprinted serial number that is assigned to the product receipt by looking in the **Product receipt** field on the **Product receipt journal** page.

> [!NOTE]
> In general, during product receipt posting processes where you must select a serial prefix, the following behavior applies:
>
> - If the **Default prefix** option on the **Preprinted serial numbers** page is selected for a serial prefix for the *Packing slip* document type, the serial prefix is automatically selected in the **Serial prefix** field.
> - If the **Default prefix** option isn't selected, the serial prefix must be manually selected in the **Serial prefix** field.

### Free text invoice

This section explains how to use a serial prefix in a free text invoice.

When you want to create a free text invoice that has a *positive* amount, select the serial prefix in the **Serial prefix** field.

To assign a serial prefix in a free text invoice that has a positive amount, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Select the free text invoice to post.
1. On the **Free text invoice header** FastTab, in the **Serial prefix** field, select the serial prefix.
1. Select **Post**.

After the posting process, you can find the preprinted serial number that is assigned to the invoice by looking in the **Invoice** field on the **Invoice journal** page.

When you want to create a free text invoice that has a *negative* amount, you can't select the serial prefix because the **Serial prefix** field is unavailable. Instead, set the **Preprinted invoice** field to the invoice number from the document that you received from the customer.

To create a free text invoice that has a negative amount, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Select the free text invoice to post.
1. On the **Free text invoice header** FastTab, in the **Preprinted invoice** field, enter the invoice number that the customer provided.
1. Select **Post**.

### Sales order invoice

This section explains how to use a serial prefix in an invoice for a sales order or a sales return order.

When you want to create an invoice for a *sales order*, select the serial prefix in the **Serial prefix** field.

To assign a serial prefix in an invoice for a sales order, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select the sales order to create an invoice for.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the **Posting invoice** page, on the **Overview** FastTab, in the **Serial prefix** field, select the serial prefix.
1. Select **OK** to post.

After the posting process, you can find the preprinted serial number that is assigned to the invoice by looking in the **Invoice** field on the **Invoice journal** page.

When you want to create an invoice for a *sales return order*, you can't select the serial prefix. Instead, set the **Serial number** field to the invoice number from the document that you received from the customer.

To create an invoice for a sales return order, follow these steps:

1. In Finance, go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Select the sales order to create an invoice for.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the **Posting invoice** page, in the **Serial number** field, enter the invoice number from the document that you received from the customer.
1. Select **OK** to post.

### Purchase order invoice

This section explains how to use a serial prefix in an invoice for a purchase order or a purchase return order.

When you want to create an invoice for a *purchase order*, you can't select the serial prefix. Instead, set the **Product receipt** field to the invoice number from the document that you received from the vendor.

To create an invoice for a purchase order, follow these steps:

1. In Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order to create an invoice for.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the **Vendor invoice** page, on the **Vendor invoice header** FastTab, in the **Number** field, enter the invoice number from the document that you received from the vendor.
1. Select **Post**.

When you want to create an invoice for a *purchase return order*, select the serial prefix in the **Serial prefix** field.

To assign a serial prefix in an invoice for a purchase return order, follow these steps:

1. In Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order to create an invoice for.
1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. On the **Vendor invoice** page, on the **Vendor invoice header** FastTab, in the **Serial prefix** field, select the serial prefix.
1. Select **Post**.

After the posting process, you can find the preprinted serial number that is assigned to the invoice by looking in the **Invoice** field on the **Invoice journal** page.

### Vendor invoice journal

This section explains how to use a serial prefix in a vendor invoice journal.

When you want to create a vendor invoice journal, use of the serial prefix depends on whether the amount of the vendor account is a debit or a credit.

- If the vendor account has a *debit* amount, select the serial prefix in the **Serial prefix** field.
- If the vendor account has a *credit* amount, don't select the serial prefix. Instead, set the **Invoice** field to the invoice number that the vendor provided.

After the posting process, you can find the preprinted serial number that is assigned to the invoice by looking in the **Invoice** field on the **Invoice journal** page.

### General journals

This section explains how to use a serial prefix in general journals.

When you want to create an invoice in general journals, use of the serial prefix depends on whether the account type is *Customer* or *Vendor*, and whether the amount of the account is a debit or a credit.

- If the account type is *Customer*:
  - If the customer account has a *credit* amount, you can't select the serial prefix. Instead, you must set the **Invoice** field to the invoice number from the document that you received from the customer.
  - If the customer account has a *debit* amount, you must select the serial prefix in the **Serial prefix** field.

- If the account type is *Vendor*:
  - If the vendor account has a *credit* amount, you can't select the serial prefix. Instead, you must set the **Invoice** field to the invoice number that the vendor provided.
  - If the vendor account has a *debit* amount, you must select the serial prefix in the **Serial prefix** field.

The **Use preprinted serial number in journal** parameter is available on the **Journal names** page.  
To access this setting, go to **General ledger** \> **Journal setup** \> **Journal names**, and then select the relevant journal name. On the **General** FastTab, you can find the **Use preprinted serial number in journal** parameter.  

Enabling this parameter means that the journal uses the preprinted serial numbering logic defined in the **Preprinted serial numbers** setup. This logic helps guarantee compliance with UBL-TR requirements for e-invoice documents, and ensures that each journal posting uses a valid, traceable serial prefix.  

> [!NOTE]  
> Enable this parameter only for journal types that are required to use preprinted serial numbers. For other journal types where continuous or system-generated numbering is sufficient, leave this option set to **No**.  

After the posting process, you can find the preprinted serial number that is assigned to the invoice by looking in the **Invoice** field on the **Invoice journal** page.

> [!NOTE]
> In general, during invoice posting processes where the serial prefix must be selected, the following behavior applies:
>
> - If the **Default prefix** option on the **Preprinted serial numbers** page is selected for a serial prefix for *Invoice* document type, the serial prefix is automatically selected in the **Serial prefix** field.
> - If the **Default prefix** option isn't selected, the serial prefix must be manually selected in the **Serial prefix** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
