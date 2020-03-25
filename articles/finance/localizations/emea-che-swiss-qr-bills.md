---
# required metadata

title: Swiss QR-bills
description: This topic provides information about how to generate QR-bills and process incoming QR-slips.
author: neserovleo
manager: AnnBe
ms.date: 03/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Switzerland
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.9

---

# Swiss QR-bills

[!include [banner](../includes/banner.md)]


Beginning July 2020, processing and issuing QR-bills (QR-slips) in addition to the invoice will be required. This topic explains how to generate QR-bills and process the incoming QR-slips in Dynamics 365 Finance.

To enable the QR-bill functionality, enable the following features in the **Feature management** module:

- **Configurable payment ID**
- **(Switzerland) QR-bills**

> [!NOTE]
> When you enable the Swiss QR-bill functionality, it becomes available to additional countries. Depending on the address of the legal entity, these counties include, CH, DE, AT, FR, and IT.

## Electronic reporting configurations

The most recent versions of the following Electronic reporting configurations should be imported from LCS:

- Swiss QR-Bill text
- Swiss QR-Bill Structured information
- ISO20022 Credit transfer (CH)
- ISO20022 pain.002
- ISO20022 Camt.054

All required model and model mapping configurations will be imported automatically.

## Company bank account setup

On the **Bank account** page (**Cash and bank management** \> **Bank Accounts** \> **Bank accounts**), in the **QR-IBAN** field, specify the QR-IBAN number. This number can be used simultaneously with the ordinary IBAN number and has similar validations in the system.

### Cash discounts and tax codes descriptions 

Cash discounts and tax codes should all have the QR-bill description field populated. This description is used in QR-bill printing.

## Legal entity registration ID setup

To correctly populate the UID number on the generated QR slip, the UID value should be enterd in the **Registration ID** field on the Legal entity setup. Additionally, the informaiton in the **Registration category** field should correspond to the **VAT ID**.

## Accounts receivable setup

### Payment ID

On the **Payment ID** page, you can configure the Payment ID structure which is applied when outgoing QR slips are generated from the **Aaccounts receivable** module. The length of the Payment ID should be set up to be a length of 27 digits and generating the check digit using the **Modulo11** algorithm.
Non-digit symbols are excluded from the Payment ID when the algorithm is run, so the number sequences used for Customer accounts and Invoices should have digits only.

The Payment ID type applied on the invoice could default to the following level hierarchy:

- **Accounts receivable parameters** page > **Ledger and sales tax** tab
- **Customer groups** page
- **Customer account** page > **Payment defaults** tab
- **Method of payment** page > **Payment control** tab

### Methods of payment – customers

The method of payment should be set up on the customer accounts that use the QR-bills to define the details of the company bank account to which teh QR slip is issued. For processing the incoming payments in **camt.054** format, the Electronic reporting import configuration should be set up.

### Customer account

The default Method of payment must be selected, and the Payment ID type must be filled in if it's not already specified in the default setup for Customer groups on the **Account receivable parameters** page.

In the **Associated payment attachment** field group, the new type, **QR-bill** is added. When selected, the QR slip is printed when the document of the dedicated type is printed.


### Giro report processing group
The settings information provided in the Giro report processing groups determine how the **Billing information** section is filled on a QR slip. If necessary, you can configure and use different parts of this section on the QR bill in Electronic reporting. These include:

- **Account code**: The specific format dedicated for the specific customer account.
- **Customer relation**: The value of the specific customer account or customer group.
- **QR-Bill information**: The Electronic reporting format configuration responsible for filling the billing information.
- **Print scissors symbol**: The inclusion of the scissors symbol on the printed report. This could be important when choosing whether to send a printed or electronic version of the QR-slip.

## Accounts payable setup

### Methods of payment – vendors

For vendor methods of payment, you must specify the associated bank account, select the required Electronic reporting configurations for the export and import for payment file processing, and set up payment specification. A new payment specification parameter value, **Tp3.QR** is available For payments corresponding to the incoming QR-slips. In addition to payment specification setup, a specific option is also available on the vendor bank account for redefining the Specification parameter.

Payment ID should be activated on the **Payment attributes** tab to inherit the payment ID during the payment proposal with QR-bills.

### Return format error codes and return format status mapping

If **pain.002** is will be used as a return file format, the Return format error codes and Return format status mapping must be set up. For more information, see [Import ISO20022 files](emea-iso20022-file-formats.md).

### Vendor account

Standard setup of the vendor account for ISO20022 payments is expected. For more information, see [Set up vendors and vendor bank accounts for ISO20022 credit transfers](tasks/set-up-vendor-iso20022-credit-transfers.md).

### Vendor bank account

Vendor bank accounts must have a QR-IBAN number assigned. Other fields are expected to be populated following the typical payment procedure for payment **Type 3** in Switzerland.

Additionally, there is an option to select a payment specification parameter directly on the vendor bank account. When a payment specification has been made, then during the time that a credit transfer file is generated, the value is given a higher priority than the method of payment specification.

## Accounts receivable process

### Generate the QR-slips

To generate the QR-slip for a document, such as a customer invoice), print the document and the QR-slip will automatically be generated as an additional report. After that, you can export the QR-bill to PDF and then print or sent it electronically.

The documents that support this functionality include:

- Sales order invoices
- Free text invoices
- Project invoices
- Interest notes
- Collection letters
- Account statement

### Import payments in camt.054 format
To the bank statement in camt.054 format from the bank, open the Customer payment journal line and run the Import payment function. The 27-digit long reference is expected in the Ref tag (in the RmtInf section) of the file. After the import, the payment transactions would be created and settled with customer transactions based on Payment Id value. For more information, see [Import ISO20022 files](emea-iso20022-file-formats.md).

## Accounts payable process

The scope of supported functionality covers the process of manual import of the QR code values into the input dialog which could be achieved by scanning devices transmitting the text value of the QR-code. The structure of the information from QR-code should follow the standards available at the SIX group website at the moment of the release. In case of any derivation from the structure in the information encrypted in QR code or any format changes required to follow the device-specific behavior, this could be configured using the Generic Electronic Reporting (GER) module without code modifications.

### Import QR bills

You can import the QR bills into the Invoice journal or the pending vendor invoice destinations.

To import QR-bills into the Invoice journal, run the **Import QR-Bill** function available on the **Invoice journal lines** page.

On the **Importing** dialog box, in the **QR bill** field, the name of the Electronic reporting format configuration is shown. You can update which Electronic reporting format should be used. Enter the QR code value in the plain text of the **QR-Bill** field, and then select **Ok**.

On the next page, the parsed values of the QR bill are shown on the **QR-Bill** tab. On the **General** tab, you can see the values of the recognized vendor, bank account, amount, and other details which will be imported into the system. After you select **OK**, the Invoice journal lines are created. If this QR slip was previously imported, you will be notified with a warning message. The information of the imported QR bill is stored and available for review on the **Imported QR bills** page.

For invoices associated with purchase orders, you can create pending vendor invoice headers that are based on QR bill information. To import the QR-bill, select **Import QR-bill** on the **Process** tab of the **Pending vendor invoices** page. Adding, reviewing and importing the QR code is similar to the description in the previous paragraph.

You can also import the QR bill when the vendor invoice is opened from the **Purchase order** page. The importing procedure is the same as the pending vendor invoice and if the invoice is associated with a purchase order, the import will happen automatically.

To process the QR bill without a predefined destination, or to a custom destination, a special option is available in the **Accounts payable** module under **Periodic tasks**. In this case, you must select the destination manually.

When the plain text of the QR bill is left blank, you can run the import from the text file which is located on the SharePoint folder based on the setup of the Electronic reporting source.

After the invoice is posted, the vendor transaction with the imported Payment ID is available for settlement in the payment journal.

## Payment files processing

Create vendor payment journal lines by using the Payment proposal functionality. For more information, see [Create and export vendor payments using ISO20022 payment format](tasks/create-export-vendor-payments-iso20022-payment-format.md).

For QR-bill related payments, the credit transfer file is generated based on the payment ID value, which is retrieved from the QR code.

You can import the **pain.002** and **camt.054** files from the **Payment transfers** page. For more details, see [Import ISO20022 files](emea-iso20022-file-formats.md).
