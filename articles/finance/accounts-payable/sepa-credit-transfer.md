---
title: SEPA credit transfer overview
description: Learn about ISO 20022 credit transfers, which include Single Euro Payments Area (SEPA) credit transfers and any other electronic payments for vendors. 
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 07/28/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerJournalTransVendInvoice, LedgerJournalTransVendPaym, VendPaymMode
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 36b0f870-16d4-4bbb-8da5-e747e69b970d
---

# SEPA credit transfer overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

This article provides general information about ISO 20022 credit transfers, which include Single Euro Payments Area (SEPA) credit transfers and any other electronic payments for vendors. A SEPA credit transfer is a specific type of payment in euros from one company or individual to another company or individual. The article also explains how to set up and transmit a credit transfer payment file.

## What is a credit transfer message?

The credit transfer message is a request that an initiating party (your company) sends to move funds from its own account to a creditor. Many country/region-specific and bank-specific implementations of credit transfer messages exist. Some of these implementations are used within one country or region, and some are becoming standards. One well-established global standard is ISO 20022 and its initiation messages, such as Credit transfer. The following illustration shows the relations and coverage for selected credit transfer messages.
:::image type="content" source="./media/credit-transfer.jpg" alt-text="Screenshot of a diagram showing the relations and coverage for selected credit transfer messages."::: Credit transfer messages

## What are ISO 20022 and SEPA payments?

The European Commission set up the Single Euro Payments Area (SEPA) and dictates that all electronic payments are considered domestic, regardless of the country or region where the individual, business, or organization, and the bank are located. There's no difference between national or regional payments and cross-border payments. The SEPA includes the 28 member states of the European Union (EU), and also Iceland, Liechtenstein, Norway, Switzerland, Monaco, and San Marino. The SEPA helps form a single market for payment transactions within the European Economic Area (EEA). Ultimately, the SEPA is expected to reduce the number of payment formats that banks, businesses, and individuals must work with. The European Commission established the legal foundation for SEPA payments through the Payment Services Directive (PSD). The European Payments Council (EPC) supports the SEPA through the following activities:

- It sets the standards for SEPA electronic payments by using the ISO 20022 Universal financial industry message scheme XML format.
- It establishes rules and guidelines about the handling of euro payments.

The EPC, which consists of European banks, develops the commercial and technical frameworks for SEPA payment instruments. Three types of SEPA payments are used:

- Credit transfers
- Direct debits
- Cards

## What is a SEPA credit transfer?

A SEPA credit transfer is a payment from one company or individual to another company or individual. Payments must be in euros, and must include the International Bank Account Number (IBAN) and the Bank Identifier Code (BIC) for both parties. (The BIC is also known as the Society for Worldwide Interbank Financial Telecommunication \[SWIFT\] code.) Additionally, transaction costs must be shared between both parties. Credit transfers that occur between parties should use XML files that comply with ISO 20022 payment processing standards and the XML format, as specified by the EPC.

## How is a credit transfer implemented?

Implement the credit transfer payment format for European country/region by using the Electronic reporting (ER) and Methods of payment functionality in Microsoft Dynamics 365 Finance. Some credit transfer formats that are used in other regions still use the legacy payment framework. Among many other formats, twelve ISO 20022 credit transfer file formats are available. These export formats conform to the SEPA ISO 20022 XML standard. Use them to generate non-euro payment transfers for countries or regions where they're used and euro payments as specified in version 8.2 of the SEPA Credit Transfer Scheme Rulebook that the EPC releases. Before you can implement credit transfers, contact your bank to obtain the software that is required to upload electronic banking files. Use that software to transfer the XML files that contain payment orders to your bank.

## What credit transfer formats are currently supported?

Always go to the Shared asset library on Microsoft Dynamics Lifecycle services (LCS) and view the most up-to-date list of available files that have an asset type of **GER configuration**. The next section, "What do I have to set up?", provides a link to the article that explains how to create an LCS repository to review available configurations and import selected configurations.

## What do I have to set up?

- Before you can create credit transfer files, import at least one active credit transfer configuration into your ER configurations. For instructions, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).
- When you configure Accounts payable methods of payment, select the **Generic electronic reporting** check box, and select the appropriate credit transfer format (for example, **ISO 20022 Credit transfer (AT)**) as an export format configuration.
- Set up the legal entity and bank account information.
- Bank account numbers, IBANs, and sometimes SWIFT codes (BICs) or other IDs are required to create valid credit transfer payments. Therefore, set up them for the vendor bank account and the bank account for the organization that is requesting the transfer.
- Additional information might be required, such as value-added tax (VAT) numbers for the parties that are referred to in the credit transfer message. Set up this information for vendors and for the legal entity when it's requested.
- Some Accounts payable methods of payment, mostly ISO 20022–based methods of payment, might require additional setup for **Payment format code sets**, such as **Service type** = **SLEV**. Those codes are used as additional tagging for payment transactions during payment processing. Default values of Payment codes, like **Category purpose**, **Charge bearer**, **Local instrument**, and **Service level** can be set in two places. The first place is **Accounts payable payment journal header** and the second is **Accounts payable methods for payments**. Upon payment journal lines creation, Payment code values set on payment journal header are transferred to a journal line. If not set, the values from Methods of payment are used.

## What parameters can I use to generate credit transfer payments?

The list of specific parameters depends on the credit transfer format. The following table shows the parameters that are available when you generate an ISO 20022 credit transfer payment file for Germany in a vendor payment journal. By using the options that are available on the **Run in the background** tab, you can run payment generation in batch mode.

| Field | Description |
|---|---|
| Batch booking | Select this check box to include the batch booking tag in the XML file. |
| Processing date | Enter the date when the bank should process the payments. |
| Format | Select the format for remittance information, depending on the requirements of your country/region or bank:<ul><li>**Strd** – Select this option to use the structured format when one payment line settles against one invoice. This option isn't available for the country/region-specific export formats for France, Germany, or the Netherlands.</li><li>**Ustrd** – Select this option to use the unstructured format when the payment settles against multiple invoices. The invoice numbers for the settled invoices are concatenated and used as the remittance information. In compliance with ISO 20022 guidelines, unstructured remittance information is limited to 140 characters.</li></ul> |
| Number of invoices | Enter the number of invoices that the **Payment advice** report prints from. |
| Sequence number | Enter a sequence number to identify the file. The sequence number appears on the **Attending note** report. |
| Print attending note | Select this check box to print the **Attending note** report. |
| Print control report | Select this check box to print a report that contains the payment information. |
| Print covering letter | Select this check box to print the **Payment advice** report. |

## What are IBANs and BICs?

The International Bank Account Number (IBAN) and Bank Identifier Code (BIC) are used to identify any account in many countries/regions worldwide. These include the 34 SEPA countries/regions. Enter the BIC in the **SWIFT code** field and the IBAN in the **IBAN** field. For both the creditor’s bank account and the customer’s bank account, these fields are located on the **Additional identification** FastTab on the **Bank account** tab of the **Bank accounts** page. The use of BIC for SEPA payments is no longer enforced.

## How do I transmit a payment file to the bank?

When you generate payments, you also generate the payment file. You're prompted to save the file from your web browser to any available location. The next step is to send the XML file to your bank. This process varies from bank to bank. Follow the instructions from your bank to submit the files to the bank for processing.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
