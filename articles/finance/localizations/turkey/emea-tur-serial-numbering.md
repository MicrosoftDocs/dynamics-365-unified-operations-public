---
title: Use serial numbering 
description: Learn about links to documentation resources for Türkiye, including links to resources about serial numbering. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: overview 
ms.date: 04/17/2025 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: SerialNumbering 
ms.dyn365.ops.version: 10.0.9 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Use serial numbering

[!INCLUDE[banner](../../includes/banner.md)]

In Türkiye, specific number sequences are needed for packing slips and invoices to ensure legal compliance and accurate tracking. To manage and track numbers in a system, it's important to follow a set of rules for number sequences. These rules ensure that each number is unique, in order, and easy to understand.

You can maintain organized records by using a specific format with prefixes, year, and unique digits. It's also important to make sure the dates associated with these numbers are in the correct order to avoid any confusion.

Documents, such as sales order packing slips, purchase return order product receipts, free text invoices, sales order invoices, purchase return order invoices, vendor invoice journals, customer invoices, and vendor return invoices in general journal entries, all benefit from this systematic approach to number sequencing.

When using a preprinted serial number, it's important to ensure that the posting date maintains chronological consistency. It should always follow the posting date of the previous preprinted serial number, preserving the correct order. Additionally, it must precede the posting date of the next preprinted serial number to prevent the premature use of future dates. If there's a conflict with the posting date, a different number sequence should be used, managed through number sequence groups.

Preprinted serial number configurations are set up through common pages accessed via the following menu items:

> [!NOTE]
> In Microsoft Dynamics 365 Finance, the **Preprinted serial numbers** setup and parameter pages can be accessed from both the **Accounts payable** and **Accounts receivable** modules. Any modifications made through one module is reflected consistently across both modules.

Navigate to these forms via the following menu paths:

- **Accounts payable > Setup > Preprinted serial numbers**
- **Accounts receivable > Setup > Preprinted serial numbers**

## Serial numbering requirements

In Türkiye, the use of serial prefix is mandatory for assigning preprinted serial numbers to documents sent to customers and vendors. The following are the general requirements for serial numbering in Türkiye:

- **Continuous values:** Numbers must be in order without gaps.
- **Predefined format:** Set the format of the number sequence before using it.
- **Prefix (3-digits):** A three-digit code that identifies the sequence.
- **Year:** Include the current year in the sequence.
- **Number (9-digits):** A nine-digit number that uniquely identifies each entry.
- **Separators:** Use specific characters to separate various parts of the sequence.

For invoices and packing slips sent to customers, the **Serial prefix** field in the posting form must be filled in. Similarly, for return product receipts and return invoices sent to vendors, the **Serial prefix** must be selected. This can be done either by manually selecting the serial prefix when posting the relevant documents to the ledger or by having it automatically populated based on a predefined parameter.

## Setup a serial number format

This article explains how to define serial number formats for various document types, such as e-archive, e-invoice, e-packing slip. It contains information about preprinted serial numbers, including details on serial number formats and number sequences. In Türkiye, serial numbers must be generated in a specific format in compliance with regulations. The serial number must be **16-digits** such as **AAA2025000000001** and include the following details:

- **Serial prefix**: 3-digits (AAA)
- **Year**: 4-digits (2025)
- **Serial number**: 9-digits (000000001)

Serial number format can be configured in the **Serial number formats** Tab on the **Accounts payable** or **Accounts receivable > Setup > Preprinted serial numbers > Parameters**. 
Each serial number format can be created by using options such as **Serial prefix**, **Fiscal year**, **Number**, or **None**.
The explanation for each option in serial number format are as below;

- **Serial prefix** - Specifies that the serial prefix displays in the corresponding part of the serial number format.
- **Fiscal year** - Specifies that the fiscal year displays in the corresponding part of the serial number format.
- **Number** - Specifies that the unique serial number displays in the corresponding part of the serial number format.
- **None** - Specifies that there isn't a value in the corresponding of the serial number format. 

The serial number format is generated by sequentially combining nine seperate fields, based on the selections in each column. In general, the resulting serial number format appears as follows:

_1.field name + 1.seperator + 2.field name + 2.seperator + 3.field name + 3.seperator + 4.field name + 4.seperator + 5.field name_


| **Field** | **Description** |
| --- | --- |
| **Format name** | Specifies the name of the serial format.|
| **1.field name** | Provides to select the value to be displayed in the first section of the serial number format.|
| **1.seperator** | Characters or symbols used to divide different sections of a preprinted serial number. |
| **2.field name** | Provides to select the value to be displayed in the second section of the serial number format.|
| **2.seperator** | Characters or symbols used to divide different sections of a preprinted serial number. |
| **3.field name** | Provides to select the value to be displayed in the third section of the serial number format.|
| **3.seperator** | Characters or symbols used to divide different sections of a preprinted serial number.|
| **4.field name** | Provides to select the value to be displayed in the fourth section of the serial number format.|
| **4.seperator** | Characters or symbols used to divide different sections of a preprinted serial number. |
| **5.field name** | Provides to select the value to be displayed in the fifth section of the serial number format.|
| **Format** | Specifies how the serial number format is structured based on the selections in each column.|

To generate a 16-digit preprinted serial number, you must first define the serial number format. To create a sample serial number such as **AAA2025000000001** in compliance with legal regulations, follow the steps below;

1. Navigate to **Accounts payable** or **Accounts receivable > Setup > Preprinted serial numbers > Parameters**.
2. Go to **Serial number formats** tab.
3. Select **New**.
4. In the **Format name** field, type a name.
5. In the **1.field name** field, select _Serial prefix_.
6. In the **2.field name** field, select _Fiscal year_.
7. In the **3.field name** field, select _Number_.
8. In the **4.field name** field, select _None_.
9. In the **5.field name** field, select _None_.
10. Select **Save**.

The serial number format is as follows;

_Serial prefix + Fiscal year + Number_


## Setup a serial prefix

This article explains how to set up a serial prefix for documents sent to customers or vendors. You can define and manage serial prefixes for various document types.

This setup ensures that each document type follows a unique and traceable serial number format, which is essential for maintaining accurate records and ensuring compliance with regulations. Here are the explanations for each field:

| **Field** | **Description** |
| --- | --- |
| **Serial prefix** | Type a 3-digits character set.|
| **Number sequence group** | Define a number sequence group for each serial prefix to maintain unique number sequences.|
| **Serial type** | Select type of document.|
| **Fiscal year** | Type fiscal year value. |
| **Number of digits** | Type the length of the serial number.|
| **Default prefix** | Mark a serial prefix to be used as the default. |

> [!NOTE]
> Each serial prefix must have a separate number sequence group assigned to it.
> Using the same number sequence group with different serial prefixes disrupts the integrity of the number series.

Once the serial number format is defined, a serial prefix should be set for the document type. The serial number format for the created sample preprinted serial number (AAA2025000000001) is defined as follows:

1. Navigate to **Accounts payable** or **Accounts receivable > Setup > Preprinted serial numbers > Preprinted serial numbers**.
2. In the **Document type** field, select the document type for which the serial prefix is to be created.
3. Select **New**.
4. In the **Serial prefix** field, type 3-digits prefix as "AAA".
5. In the **Number sequence group**, select a number sequence group created for the serial prefix.
6. Select **Save** and select number sequence code created for the number sequence group in the **Reference** section. To create a number sequence, follow these steps:

    1. Navigate to **Organization administration > Number sequences > Number sequences**.
    2. Select the **Number sequence** button in the **New** section.
    3. Give the number sequence a **Number sequence code** and a **Name**.
    4. Set the scope to **Company** and select your company.
    5. There must be only _Alphanumeric_ in **Segment** section and type 16-digits of the **#** character.
    6. Select **Save**.

8. In the **Serial type** field, select the relevant serial type.
9. In the **Fiscal year** field, type _2025_.
10. In the **Number of digits** field, type the value _9_.
11. In the **Serial format** field, select the created serial number format.
12. In the **Default prefix** field, mark the field if it's a default serial prefix.
13. Select **Save**.

**Open**, **Closed** and **Cancelled** tabs are used to manage and track the status of preprinted serial numbers for various documents. Here is the logic behind each tab:

| **Status** | **Description** |
| --- | --- |
| **Open** | This tab lists all serial numbers that are currently active and available for use. The preprinted serial numbers have been generated but not yet assigned to any document. They are ready to be used when needed. A preprinted serial number in **Open** status can be changed to **Cancelled** status by using the **Cancel** button. |
| **Closed** | This tab contains preprinted serial numbers that have already been used and assigned to specific documents. The preprinted serial numbers are no longer available for new assignments but are kept for record-keeping and tracking purposes. The status of a preprinted serial number in **Closed** status can't be changed, as the preprinted serial number is associated with a document that has been posted to a document. |
| **Cancelled** | This tab includes serial numbers that have been invalidated or voided. These serial numbers are not available for use and are marked as cancelled due to errors, duplicates or other reasons. They are retained in the system for audit and compliance purposes. A preprinted serial number in **Cancelled** status can be changed to **Open** status by using the **Open** button. |

> [!NOTE]
> If an error occurs during the posting process, the system creates the preprinted serial number and assign it a **Free** status in the **Open** tab.
>Once the errors are resolved and posting is completed, the system reuses the preprinted serial number and moves it to the **Closed** tab.
>
> If the posting date intended for posting is earlier than the date of the last posted document for the same serial prefix, the system prevents the posting and display an error message.
> In this case, a different serial prefix must be selected, and the posting must be reattempted.

## Using of the serial prefix

This article provides information on how to use the **Serial prefix** for relevant documents and how to set up the necessary settings to ensure proper serial numbering and tracking. The serial prefix is used for the following document types:

- Packing slip in sales order
- Product receipt in purchase return order
- Free text invoice
- Sales order invoice
- Invoice in purchase return order
- Vendor invoice journal
- General journals

### Packing slip in sales order

This article explains how to use a serial prefix in **Packing slip** in **Sales order**.

When you want to create a packing slip for a sales order, the **Serial prefix** must be selected in **Packing slip posting** page.

To assign a serial prefix in a packing slip for a sales order, follow the steps below; 

1. Navigate to **Accounts receivable > Orders > All sales orders**.
2. Select the sales order that you want to create a packing slip.
3. Go to **Pick and pack** Tab.
4. Select **Packing slip** in **Generate** group.
5. In the **Packing slip posting** page, select a serial prefix in the **Serial prefix** field in Overview FastTab.
6. Select **OK** to post.

After the posting process, the preprinted serial number assigned to the packing slip can be viewed in the **Packing slip** field on the **Packing slip journal** page.

> [!NOTE]
> In general, during the packing slip posting processes where the **Serial prefix** needs to be selected;
> - If the **Default prefix** field is marked for a serial prefix in **Preprinted serial numbers** page for **Packing slip** document type, the **Serial prefix** is automatically selected in the **Serial prefix** field.
> - If the **Default prefix** isn't marked, the **Serial prefix** must be manually selected in the **Serial prefix** field.


When you want to create a packing slip for a sales return order, the **Serial prefix** can't be selected. The **Serial number** field must be filled with the packing slip number received from the document received from customer. 

To create a packing slip for a sales return order, follow the steps below; 

1. Navigate to **Accounts receivable > Orders > All sales orders**.
2. Select the sales order that you want to create packing slip.
3. Go to **Pick and pack** tab.
4. Select **Packing slip** in **Generate** group.
5. In the **Packing slip posting** page, the **Serial number** field must be filled with the packing slip number from the document received from customer.
6. Select **OK** to post.

### Product receipt in purchase return order

This article explains how to use a serial prefix in **Product receipt** in **Purchase order**.

When you want to create a product receipt for a purchase order, the **Serial prefix** can't be selected in **Product receipt posting** page.

To create a product receipt for a purchase order, follow the steps below; 

1. Navigate to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Select the purchase order that you want to create product receipt.
3. Go to **Receive** tab.
4. Select **Product receipt** in **Generate** group.
5. In the **Posting product receipt** page, the **Product receipt** field must be filled with the product receipt number from the document received from vendor.
6. Select **Post**.

When you want to create a product receipt for a purchase return order, the **Serial prefix** must be selected in **Product receipt posting** page;

To assign a serial prefix in a product receipt in purchase order, follow the steps below; 

1. Navigate to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Select the purchase order for which you want to create product receipt.
3. Go to the **Receive** tab.
4. Select **Product receipt** in **Generate** group.
5. In the **Product receipt posting** page, select a serial prefix in the **Serial prefix** field in Overview FastTab.
6. Select **Post**.

After the posting process, the preprinted serial number assigned to the product receipt can be viewed in the **Product receipt** field on the **Product receipt journal** page.

> [!NOTE]
> In general, during the product receipt posting processes where the **Serial prefix** needs to be selected;
> - If the **Default prefix** field is marked for a serial prefix in **Preprinted serial numbers** page for **Packing slip** document type, the **Serial prefix** is automatically selected in the **Serial prefix** field.
> - If the **Default prefix** isn't marked, the **Serial prefix** must be manually selected in the **Serial prefix** field.


### Free text invoice

This article explains how to use a serial prefix in **Free text invoice**. 

When you want to create a free text invoice with **positive** amount, the **Serial prefix** must be selected in the **Serial prefix** field. 

To assign a serial prefix in a free text invoice with **positive** amount, follow the steps below:

1. Navigate to **Accounts receivable > Invoices > All free text invoices**.
2. Select the free text invoice for which you want to post.
3. Select a serial prefix in the **Serial prefix** field in the **Free text invoice header** FastTab. 
4. Select **Post**

After the posting process, the preprinted serial number assigned to the invoice can be viewed in the **Invoice** field on the **Invoice journal** page.

When you want to create a free text invoice with **negative** amount, the **Preprinted invoice** field must be filled with the invoice number from the document received from customer.

> [!NOTE]
> When a free text invoice is created with **negative amount**, the **Serial prefix** field is unavailable and the **Preprinted invoice** field is displayed.
> The invoice number received from customer must be manually filled in the **Preprinted invoice** field.

To create a free text invoice with **negative** amount, follow the steps below:

1. Navigate to **Accounts receivable > Invoices > All free text invoices**.
2. Select the free text invoice that you want to post.
3. Type the invoice number provided by customer, in the **Preprinted invoice** field in **Free text invoice header** FastTab.
4. Select **Post**


### Sales order invoice

This article explains how to use a serial prefix in **Sales order invoice**.

When you want to create an invoice for a sales order, the **Serial prefix** must be selected in the **Serial prefix** field;

To assign a serial prefix in an invoice for a sales order, follow the steps below;

1. Navigate to **Accounts receivable > Orders > All sales orders**.
2. Select the sales order for which you want to create the invoice.
3. Go to the **Invoice** tab.
4. Select **Invoice** in **Generate** group.
5. In the **Posting invoice** page, select a serial prefix in the **Serial prefix** field in Overview FastTab.
6. Select **OK** to post.

After the posting process, the preprinted serial number assigned to the invoice can be viewed in the **Invoice** field on the **Invoice journal** page.

When you want to create an invoice for a sales return order, the **Serial prefix** can't be selected. The **Serial number** field must be filled with the invoice number from the document received from customer. 

To create an invoice for a sales return order, follow the steps below; 

1. Navigate to **Accounts receivable > Orders > All sales orders**.
2. Select the sales order for which you want to create the invoice.
3. Go to the **Invoice** tab.
4. Select **Invoice** in **Generate** group.
5. In the **Posting invoice** page, the **Serial number** field must be filled with the invoice number from the document received from customer.
6. Select **OK** to post.


### Purchase order invoice

This article explains how to use a serial prefix in **Purchase order invoice**.

When you want to create an invoice for a purchase order, the **Serial prefix** can't be selected. The **Product receipt** field must be filled with the invoice number from the document received from vendor.

To create an invoice for a purchase order, follow the steps below;

1. Navigate to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Select the purchase order that you want to create invoice.
3. Go to the **Invoice** tab.
4. Select on **Invoice** in **Generate** group.
5. In the **Vendor invoice** page, the **Number** field in the **Vendor invoice header** FastTab must be filled with the invoice number from the document received from vendor.
6. Select **Post**.

When you want to create an invoice for a purchase return order, the **Serial prefix** field must be selected in the **Serial prefix** field. 

To assign a serial prefix in an invoice for a purchase return order, follow the steps below; 

1. Navigate to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Select the purchase order for which you want to create invoice.
3. Go to the **Invoice** Tab.
4. Select on **Invoice** in **Generate** group.
5. In the **Vendor invoice** page, select a serial prefix in the **Serial prefix** field in **Vendor invoice header** FastTab.
6. Select **Post**.

After the posting process, the preprinted serial number assigned to the invoice can be viewed in the **Invoice** field on the **Invoice journal** page.

### Vendor invoice journal

This article explains how to use a serial prefix in **Vendor invoice journal**.

When you want to create a vendor invoice journal;

- If vendor account has debit amount, the **Serial prefix** must be selected in the **Serial prefix** field.
- If vendor account has credit amount, the **Serial prefix** can't be selected. The invoice number must be provided by the vendor and must be filled in the **Invoice** field.

After the posting process, the preprinted serial number assigned to the invoice can be viewed in the **Invoice** field on the **Invoice journal** page.

### General journals

This article explains how to use a serial prefix in **General journals**. The using of the serial prefix in general journal entries varies depending on whether the **Account type** is customer or vendor and whether the **amount** is debit or credit.

When you want to create a customer invoice in **General journals**;

- If the **Account type** is **Customer** and customer account has a credit amount, the **Serial prefix** can't be selected. The **Invoice** field must be filled with invoice number from the document received from customer. 
- If the **Account type** is **Customer** and customer account has a debit amount, the **Serial prefix** must be selected in the **Serial prefix** field.

- If the **Account type** is **Vendor** and vendor account has a credit amount, the **Serial prefix** can't be selected. The invoice number must be provided by the vendor and must be filled in the **Invoice** field. 
- If the **Account type** is **Vendor** and vendor account has a debit amount, the **Serial prefix** must be selected in the **Serial prefix** field.

After the posting process, the preprinted serial number assigned to the invoice can be viewed in the **Invoice** field on the **Invoice journal** page.

> [!NOTE]
> In general, during the invoice posting processes where the **Serial prefix** needs to be selected,
> - If the **Default prefix** field is marked for a serial prefix in **Preprinted serial numbers** page for **Invoice** document type, the **Serial prefix** is automatically selected in the **Serial prefix** field .
> - If the **Default prefix** isn't marked, the **Serial prefix** must be manually selected in the **Serial prefix** field.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
