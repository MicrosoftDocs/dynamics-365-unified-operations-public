---
title: Serial numbering
description: Access links to documentation resources for Turkey, including links to resources about serial numbering.
author: RyanCCarlson2 
ms.author: rcarlson
ms.topic: overview
ms.date: 02/10/2024
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Turkey
ms.search.validFrom: 2020-02-03
ms.search.form: SerialNumbering
ms.dyn365.ops.version: 10.0.9
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Serial numbering

\[!include [banner](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/main/articles/finance/includes/banner.md)\]

In Turkey, specific number sequences are needed for packing slips and invoices to ensure legal compliance and accurate tracking. 
To manage and track numbers in a system, it is important to follow a set of rules for number sequences. 
These rules ensure that each number is unique, in order and easy to understand.

By using a specific format with prefixes, year and unique digits, you can maintain organized records. 
It is also important to make sure the dates associated with these numbers are in the correct order to avoid any confusion. 

Modules such as Accounts receivable, Accounts payable, General ledger, Sales orders, Packing slips, Invoices, Return orders and General ledger entries all benefit from this systematic approach to number sequencing. 


## General requirements

- **Continuous values:** Numbers must be in order without gaps.
- **Predefined format:** Set the format of the number sequence before using it.
- **Prefix (3 digits):** A three-digit code that identifies the sequence.
- **Year:** Include the current year in the sequence.
- **Number (9 digits):** A nine-digit number that uniquely identifies each entry.
- **Separators:** Use specific characters to separate various parts of the sequence.

When using a number sequence value, make sure the posting date:

- **Follows the previous number sequence value's posting date** - This keeps the numbers in chronological order.
- **Precedes the next number sequence value's posting date** - This prevents future dates from being used too soon.

If there is a conflict with the posting date, use a different number sequence, managed through number sequence groups.

Printed serial number configurations are set up through common forms accessed via the following menu items:

> [!NOTE]
> In Microsoft Dynamics 365 Finance, the **Printed Serial Numbers** setup and parameter forms can be accessed from both the **Accounts payable** and **Accounts receivable** modules. Any modifications made through one module will be reflected consistently across both modules.  
> You can navigate to these forms using the following menu paths:  
> - **Accounts payable** > **Setup** > **Printed serial numbers**  
> - **Accounts receivable** > **Setup** > **Printed serial numbers**  

## Accounts Receivable

### Sales orders

- **Packing slip:** Use a dedicated number sequence to identify each packing slip.
- **Invoice:** Use a dedicated number sequence for accurate tracking and legal compliance.
- **Packing slip return:** Customers must provide the packing slip number to match returns with original transactions.
- **Return invoice:** Customers must provide the invoice number to maintain proper financial records and audit trails.

### Free text invoice

- **Invoice:** Use a prefix to distinguish between different types of transactions for proper accounting.
- **Return invoice:** Customers must provide the invoice number to track returned goods correctly.


## General ledger (Customer – Vendor invoice)

If Account type is _Customer_ and; 

- For **Debit amount:** Use a prefix to ensure consistency and proper categorization of debit entries.
- For **Credit amount:** Customers must provide the invoice number to accurately reflect credit transactions in the ledger.

If Account type is _Vendor_ and; 

- For **Debit amount:** Use a prefix to differentiate between debit entries and ensure accurate record-keeping.
- For **Credit amount:** Vendors must provide the invoice number.


## Accounts Payable

### Purchase Orders

- **Packing slip return:** Use a dedicated number sequence to identify each return.
- **Packing slip:** Vendors must provide the invoice number.
- **Return invoice:** Use a dedicated number sequence for tracking returned items.
- **Invoice:** Vendors must provide the invoice number for accurate billing and accounting.


## Serial format

It contains information about preprinted serial numbers, including details on serial number formats and number sequences. 

The page also explains how to define serial number formats for various document types, such as e-archive, e-invoice, e-packing slip, invoice and packing slip. 
Each format includes fields like serial prefix, fiscal year and number.
Each document type has a specific serial number format that includes a serial prefix, fiscal year, unique number and optional separators to ensure consistency and organization.

| **Field** | **Description** |
| --- | --- |
| **Format name** | Defines the name of serial format |
| **Serial prefix** | The prefix to be used for documents generated for the selected document type is defined. |
| **Fiscal year** | Includes the fiscal year in which the document is issued. |
| **Number** | Unique sequential number assigned to each document. Ensures that each document can be uniquely identified. |
| **Separators** | Characters or symbols used to divide different sections of a serial number, such as the prefix, fiscal year and number. Common separators include hyphens, slashes, or spaces. |


### Set up a serial number format

Firstly, to create a 16-digit serial number format which is required by legislation, it is necessary to define the serial format. 

The steps required to create the serial numbers are as follows:

- Go to **Serial number formats** tab in **Accounts payable** or **Accounts receivable > Setup > Preprinted serial numbers > Parameters**.
- Click **New**.
- In the **Format name** field, type a name.
- In the **1. field name** field, select _Serial prefix_.
- In the **2. field name** field, select _Fiscal year_.
- In the **3. field name** field, select _Number_.
- In the **4. field name** field, select _None_.
- In the **5. field name** field, select _None_.
- Click **Save**.

## Serial prefix

In this page is used to define and manage number sequences for various document types, such as invoices. Each number sequence includes a **Serial prefix**, **Number sequence group**, **Serial type**, **Fiscal year** and **Number of digits**. 
This setup ensures that each document type has a unique and traceable serial number format which is crucial for maintaining accurate records and compliance with financial regulations.

Here are explanations for each field:

| **Field** | **Description** |
| --- | --- |
| **Serial prefix** | A predefined set of characters appears at the beginning of each serial number. |
| **Number sequence group** | This field groups similar types of documents or transactions together. It ensures that each group has its own unique number sequence. |
| **Serial type** | Specify the type of document or transaction for which the serial number is being generated, such as e-packing slips or e-invoices. |
| **Fiscal year** | Indicates the fiscal year for which the serial number is valid. |
| **Number of digits** | Defines the length of the serial number. It ensures that all serial numbers within a sequence have a consistent format. |
| **Default prefix** | Determines the prefix to be used as the default for the relevant document type. |

These fields collectively ensure that each document type has a unique and traceable serial number format, which is crucial for maintaining accurate records and compliance with financial regulations.

**Open**, **Closed**, and **Cancelled** tabs are used to manage and track the status of serial numbers for various documents. 

Here is the logic behind each tab:

| **Status** | **Description** |
| --- | --- |
| **Open** | This tab lists all serial numbers that are currently active and available for use. These serial numbers have been generated but not yet assigned to any document or transaction. They are ready to be used when needed. |
| **Closed** | This tab contains serial numbers that have already been used and assigned to specific documents or transactions. These serial numbers are no longer available for new assignments but are kept for record-keeping and tracking purposes. |
| **Cancelled** | This tab includes serial numbers that have been invalidated or voided. These serial numbers are not available for use and are marked as cancelled due to errors, duplicates or other reasons. They are retained in the system for audit and compliance purposes. |


### Set up a serial prefix

Once the serial format is defined, a prefix should be set for the document type;

1. Go to **Accounts payable** or **Accounts receivable > Setup > Preprinted serial numbers > Preprinted serial numbers.**
2. In the **Document type** field, document type for which a prefix is to be created is selected.
3. Click **New**.
4. In the **Serial prefix** field, type 3-digit value.
5. In the **Number sequence group**, select a number sequence group created for the prefix and select number sequence.
6. Click **Save** and select number sequence code created for the prefix in the Reference section.
    To create a number sequence, follow these steps:
    - Navigate to **Organization administration > Number sequences > Number sequences**.
    - Click the **Number sequence** button in the **New** section.
    - Give the number sequence a **Number sequence code** and a **Name**.
    - Set the scope to **Company** and select your company.
    - There must be only _Alphanumeric_ in Segment section and type 16-digit #.
    - Save the number sequence.
7. In the **Serial type** field, select the serial type.
8. In the **Fiscal year** field, type year information.
9. In the **Number of digit** field, type the value _9._
10. In the **Serial format** field, select the relevant serial format.
11. In the **Default prefix** field, mark the field if it is default serial prefix.
12. Click **Save**.

## Usage of serial prefix

This article explains how to use serial prefixes in packing slips, product receipts and invoices.

### How to use a serial prefix in packing slips?

#### Packing slips for sales order
- When you want to create a sales order packing slip, Serial prefix must be selected in **Packing slip posting** form. Using serial prefix in a **Packing slip** involves the following steps;

1. Go to **Accounts receivable > Orders > All sales orders**.
2. Find and select the **Sales Order** for which you want to create a Packing Slip.
3. Click **Pick and pack** tab.
4. Select **Packing slip** > **Post packing slip**.
5. In the **Packing slip posting** form, there is **Serial prefix** field in Overview section.
6. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** would be filled automatically.
7. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
8. Click **OK** to post.

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number and permanently assign it to the **Closed** tab.

If the packing slip date intended for posting is earlier than the last posted packing slip date for the same serial prefix, the system will prevent the posting and display an error message. In this case, another serial prefix must be selected and must be posted.

#### Packing slips for sales return order
- When you want to create packing slip for sales return order, serial prefix cannot be selected. The packing slip number must be provided by the customer. The packing slip number must be entered in the **Serial number** field. Then the packing slip can be posted.


### How to use a serial prefix in product receipt?

#### Product receipt for purchase order

- When you want to create product receipt for a purchase order, **Serial prefix** cannot be selected in **Product receipt posting** form. Using serial prefix in a **Product receipt** involves the following steps;

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Find and select the purchase order for which you want to create a product receipt.
3. In the **Purchase order** form, go to the **Receive** tab.
4. Click on **Product receipt**.
5. In the **Product receipt** field, enter a product receipt number (e.g. from the vendor’s product receipt).
6. Click **Post**.

#### Product receipt for purchase return order

- When you want to create a **Product receipt** for a purchase return order, the Serial prefix must be selected in **Product receipt posting** form;

1. In the **Product receipt posting** form, there is **Serial prefix** field in Overview section.
2. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
3. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
4. Click **OK** to post.

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the product receipt date intended for posting is earlier than the last posted product receipt date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and must be posted.

### How to use a serial prefix in invoicing?

#### Free text invoice
- When you want to create a customer invoice using a **Free text invoice;**

-   If the free text invoice amount is **positive**;
    
1. If the **Default prefix** is marked in **Preprinted serial numbers** form for **Invoice** document type, **Serial prefix** will be filled automatically.
2. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, user must select the serial prefix manually.

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and invoice must be posted.

- If the free text invoice amount is **negative**;
1. The **Serial prefix** field will be hidden and cannot be selected. The **Preprinted invoice** field will appear. The invoice number must be provided by the customer. Then the invoice number is filled and the invoice is posted.

#### Invoice for sales order
- When you want to create a **Sales order invoice**; **Serial prefix** must be selected;

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. Find and select the **Sales Order** for which you want to create the invoice.
3. Click the **Invoice** tab.
4. Select **Generate > Invoice**.
5. In the **Posting invoice** form, there is **Serial prefix** field in Overview section.
6. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
7. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
8. Click **OK** to post.

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected by checking last posted invoice date and invoice must be posted.

#### Invoice for sales return order
- When you want to create an invoice for **Sales return order**, serial prefix cannot be selected. The invoice number must be provided by the customer. Invoice number must be filled in the **Serial number** field. Then invoice can be posted.

- When you want to create a purchase order invoice, **Serial prefix** cannot be selected in **Vendor invoice posting** form. Invoice number must be provided by vendor;

1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
2. Find and select the **Purchase order** for which you want to create invoice.
3. In the **Purchase order** form, go to the **Invoice** tab.
4. Click on **Invoice**.
5. In the **Number** field, enter an invoice number (e.g., from the vendor’s invoice number).
6. Click to **Post**.

#### Invoice for Purchase return order
- When you want to create a **Purchase return order invoice**; Serial prefix must be selected.

1. In **Vendor invoice posting** form, there is **Serial prefix** field in **Overview** section.
2. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
3. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
4. Click **OK** to post.

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and invoice must be posted.

#### Invoice for Vendor invoice journal
- When you want to create a vendor invoice by using **Vendor invoice journal**;

- If vendor account has credit amount, **Serial prefix** cannot be selected. Invoice number must be provided by the vendor and must be filled in the **Invoice** field.
- If vendor account has debit amount, the **Serial prefix** field will appear;

1. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
2. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
3. Click **Post.**

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and invoice must be posted.

#### General journal entries for customer invoice
- When you want to create a customer invoice by using **General journal**;

- If customer account has a credit amount, **Serial prefix** cannot be selected. Invoice number must be provided by the customer and must be filled in the **Invoice** field.
- If customer account has debit amount, **Serial prefix** field will appear;

1. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
2. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
3. Click **Post.**

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and invoice must be posted.

#### General journal entries for vendor invoice
- When you want to create a vendor invoice by using **General journal**;

- If vendor account has credit amount, **Serial prefix** cannot be selected. Invoice number must be provided by the vendor and must be filled in the **Invoice** field.
- If vendor account has debit amount, **Serial prefix** field will appear;

1. If the **Default prefix** field is marked in **Preprinted serial numbers** form, **Serial prefix** will be filled automatically.
2. If the **Default prefix** is not selected, **Serial prefix** will be empty. In this case, the user must select the serial prefix manually.
3. Click **Post.**

If user gets any error during the posting process, the system will create the serial number and will keep it in **Open** tab as **Free** status.

After resolving the errors, when the posting is completed, the system will reuse the serial number in the **Open** tab and permanently assign the serial number to the **Closed** tab.

If the invoice date intended for posting is earlier than the last posted invoice date for the same serial prefix, the system will prevent the posting and display a warning message. In this case, another serial prefix must be selected and invoice must be posted.


\[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/main/articles/includes/footer-banner.md)\]
