---
# required metadata

title: SEPA credit transfer overview | Microsoft Docs
description: This article provides general information about Single Euro Payments Area (SEPA) credit transfers, which are one of the three types of SEPA payments. A SEPA credit transfer is a payment (in euros) from one company or individual to another company or individual. The article also describes how to set up and transmit a SEPA credit transfer payment file.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-10-28 21:37:11
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: LedgerJournalTransVendInvoice, LedgerJournalTransVendPaym, VendPaymMode
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 11124
ms.assetid: 694a181c-b8db-47ef-979c-0fb9d66ee8c1
ms.region: Global
# ms.industry: 
ms.author: mrolecki

---

# SEPA credit transfer overview

This article provides general information about Single Euro Payments Area (SEPA) credit transfers, which are one of the three types of SEPA payments. A SEPA credit transfer is a payment (in euros) from one company or individual to another company or individual. The article also describes how to set up and transmit a SEPA credit transfer payment file.

What are SEPA payments?
-----------------------

The Single Euro Payments Area (SEPA) is set up by the European Commission and dictates that all electronic payments are considered domestic, regardless of the country/region where the individual, business, or organization, and the bank are located. There is no difference between national and cross-border payments. The SEPA includes the 28 European Union (EU) member states, and also Iceland, Liechtenstein, Norway, Switzerland, Monaco, and San Marino. The SEPA helps form a single market for payment transactions within the European Economic Area (EEA). Ultimately, the SEPA is expected to reduce the number of payment formats that banks, businesses, and individuals must work with. The European Commission established the legal foundation for SEPA payments through the Payment Services Directive (PSD). The European Payments Council (EPC) supports the SEPA through the following activities:

-   It sets the standards for SEPA electronic payments by using the ISO 20022 Universal financial industry message scheme XML format.
-   It establishes rules and guidelines about the handling of euro payments.

The EPC, which consists of European banks, develops the commercial and technical frameworks for SEPA payment instruments. Three types of SEPA payments are used:

-   Credit transfers
-   Direct debits
-   Cards

This article will focus on the first type, SEPA credit transfers.

## What is a SEPA credit transfer?
A SEPA credit transfer is a payment from one company or individual to another company or individual. Payments must be in euros, and must include the International Bank Account Number (IBAN) and the Bank Identifier Code (BIC) for both parties. (The BIC is also known as the Society for Worldwide Interbank Financial Telecommunication \[SWIFT\] code.) Additionally, transaction costs must be shared between both parties. Credit transfers that occur between parties should use XML files that comply with ISO 20022 payment processing standards and the XML format, as specified by the EPC.

## How is a SEPA credit transfer implemented?
The SEPA credit transfer payment format is implemented by using the Generic electronic reporting and Methods of payment functionality in Microsoft Dynamics AX. Nine SEPA export file formats are available. These export formats conform to the SEPA ISO 20022 XML standard that is specified in version 8.1 of the SEPA Credit Transfer Scheme Rulebook that the EPC releases. Before you can implement SEPA credit transfers, you must contact your bank to obtain the software that is required in order to upload electronic banking files. You will use that software to transfer the XML files that contain SEPA payments to your bank.

## What do I have to set up?
-   Before you can create SEPA export files, at least one active SEPA credit transfer configuration must be imported into your Generic electronic reporting configurations. You will select the **Generic electronic reporting** check box and select the SEPA credit transfer format as an export format configuration when you configure Accounts payable methods of payment.
-   You must also set up the legal entity and bank account information in Microsoft Dynamics AX.
-   IBANs and SWIFT codes (BICs) are required in order to make SEPA payments, so you must set up both the vendor bank account and the bank account for the organization that is requesting the transfer.

## What parameters are available for generating SEPA credit transfer payments?
The following table lists the parameters that you can use when you generate a SEPA credit transfer payment file in a vendor payment journal. By using the options that are available on the **Run in the background** tab, you can run payment generation in the batch mode.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Batch booking</td>
<td>Select this check box to include the batch booking tag in the XML file.</td>
</tr>
<tr class="even">
<td>Country</td>
<td>Enter the country/region code for the country/region-specific version of the credit transfer file to generate. The available options are <strong>AT</strong>, <strong>BE</strong>, <strong>FI</strong>, <strong>FR</strong>, <strong>DE</strong>, <strong>IT</strong>, <strong>ES</strong>, and <strong>NL</strong>. Leave this field blank to use the generic credit transfer file format.</td>
</tr>
<tr class="odd">
<td>Processing date</td>
<td>Enter the date when the bank should process the payments.</td>
</tr>
<tr class="even">
<td>Format</td>
<td>Select the format for remittance information, depending on the requirements of your country/region or bank:
<ul>
<li><strong>Strd</strong> –  Select this option to use the structured format when one payment line is settled against one invoice. This option is not available for the country/region-specific export formats for France, Germany, or the Netherlands.</li>
<li><strong>Ustrd</strong> – Select this option to use the unstructured format when the payment is settled against multiple invoices. The invoice numbers for the settled invoices are concatenated and used as the remittance information. In compliance with SEPA guidelines, unstructured remittance information is limited to 140 characters.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Variant (DE)</td>
<td>Enter <strong>002</strong> or <strong>003</strong> as the message variant.</td>
</tr>
<tr class="even">
<td>Number of invoices</td>
<td>Enter the number of invoices that the covering letter report is printed from.</td>
</tr>
<tr class="odd">
<td>Sequence number</td>
<td>Enter a sequence number to identify the file. The sequence number is displayed on the <strong>Attending note</strong> report.</td>
</tr>
<tr class="even">
<td>Print attending note</td>
<td>Select this check box to print the <strong>Attending note</strong> report.</td>
</tr>
<tr class="odd">
<td>Print control report</td>
<td>Select this check box to print a report that contains the payment information.</td>
</tr>
<tr class="even">
<td>Print covering letter</td>
<td>Select this check box to print the <strong>Payment advice</strong> report.</td>
</tr>
</tbody>
</table>

## What are IBANs and BICs?
The International Bank Account Number (IBAN) and Bank Identifier Code (BIC) are used to identify any account in the 32 SEPA countries/regions. Enter the BIC in the **SWIFT code** field and the IBAN in the **IBAN** field. For both the creditor’s bank account and the customer’s bank account, these fields are located on the **Additional identification** FastTab on the **Bank account** tab on the **Bank accounts** page.

## How do I transmit a payment file to the bank?
When you generate payments, the payment file is generated, and you're asked to save it from your web browser to any available location. The next step is to send the XML file to your bank. This process varies from bank to bank. Follow the instructions from your bank to submit the files to the bank for processing.

See also
--------

