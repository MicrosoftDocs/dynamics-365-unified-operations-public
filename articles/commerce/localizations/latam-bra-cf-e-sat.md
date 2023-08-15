---
title: CF-e fiscal documents and integration with SAT functionality in Commerce POS for Brazil
description: This article gives an overview of the generation of CF-e electronic fiscal documents for retail sales and their registration in the SAT fiscal device functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: EvgenyPopovMBS
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.20
ms.search.industry: Retail
---

# CF-e fiscal documents and integration with SAT functionality in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This article gives an overview of CF-e (Cupom Fiscal eletrônico) fiscal documents and their registration in the SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal device functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil. It also explains how to issue CF-e documents and print CF-e-SAT (Cupom Fiscal Eletrônico - SAT) fiscal receipts when retail sales of goods are completed in Commerce POS for Brazil.

A CF-e is an electronic fiscal document that is generated to register the sale of goods to a customer in São Paulo state. It enables tax and fiscal control by tax authorities. It also lets customers verify the validity and authenticity of fiscal documents that they receive. Sales of services aren't supported.

Commerce functionality for Brazil supports the CF-e model 59 format for Brazilian retailers. The CF-e model 59 format is a standard for retail electronic fiscal documents within the borders of São Paulo state, together with the national/regional standard NFC-e (Nota Fiscal do Consumidor eletrônica) model 65 format. For more information about the NCF-e format, see [NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md).

Registration of electronic fiscal documents for retail sales in an integrated SAT device is one of the fiscal registration methods that are available to retailers in São Paulo state. This feature includes the generation of CF-e electronic fiscal documents (CF-e model 59 format) for sales transactions in POS and registration of the electronic fiscal documents in a SAT fiscal device. For more information, see [About SAT](https://portal.fazenda.sp.gov.br/servicos/sat).

## Feature details

The feature for registration of electronic fiscal documents for retail sales in an integrated SAT device enables fiscal registration of retail sales in a SAT device that is connected to a hardware station. The feature takes advantage of the [fiscal integration framework](../localizations/fiscal-integration-for-retail-channel.md). Therefore, it supports all the built-in fiscal integration capabilities. The feature is included in the out-of-box solution but must be configured before it can be used.

The generation of CF-e electronic fiscal documents (CF-e model 59 format) is based on an [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) configuration and is done by the electronic reporting runtime engine that is part of the Commerce runtime.

The feature doesn't currently support customer orders that are picked up in POS. Support for the customer order pickup operation will be added later.

## Supported scenarios

The following example scenarios show frequently performed Commerce actions that are associated with CF-e-SAT documents.

### Scenario 1: Make a cash-and-carry sale of goods and print a CF-e-SAT receipt

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the bar code and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 2: Make a cash-and-carry sale of goods to an identified customer

1. Sign in to POS.
1. Add products to the cart.
1. Add a named customer, or manually enter customer information. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the bar code and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 3: Initiate a cancellation of sold goods

To cancel a sale, follow these steps.

1. Sign in to POS.
1. Open the **Show journal** page.
1. Find the sale that must be canceled.
1. Select **Cancel transaction**.
1. Register payment refunds for the transaction, and then finalize the transaction.
1. Verify that the information (including the bar code and QR code) on the printed CF-e-SAT cancellation receipt corresponds to the transaction.

> [!NOTE]
> Cancellation of approved CF-e documents that are issued by other stores isn't supported. Only CF-e documents that are issued by the same store can be canceled.

### Scenario 4: Make a cash-and-carry sale of goods by using SAT as contingency mode

If NFC-e is chosen as a main mode of a store establishment in São Paulo state, POS must generate CF-e documents via a SAT device when the store's internet connection isn't available, or when the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. This use of SAT is considered contingency mode.

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction. You will receive an error when POS tries to communicate with SEFAZ.
1. Select **Postpone**, and then finalize the transaction.
1. Verify that the information (including the bar code and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 5: Make a mixed sale that contains gift cards and other goods in the same transaction

The operations for issuing gift cards and adding value to gift cards aren't subject to taxation in Brazil. Therefore, they aren't written to the fiscal receipt.

1. Sign in to POS.
1. Add products to the cart.
1. Issue gift cards in the same transaction.
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the printed CF-e-SAT receipt doesn't include the gift cards together with the other goods that were sold.
1. Verify that separate receipts are printed for each gift card that was sold.

## Custom fields for CF-e-SAT fiscal receipts

In addition to the fields that are described in [Common list of custom fields for DANFE](latam-bra-nfce.md#custom-fields-for-danfe-fiscal-receipts) and [Simplified DANFE for model 55 fiscal receipt](latam-bra-nfce-cancel-return.md#simplified-danfe-for-model-55-fiscal-receipt), a CF-e-SAT for model 59 fiscal receipt can include the custom fields that are described in this section.

### Configure custom fields so that they can be used in receipt formats for sales receipts

Add the following POS labels to the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                                            |
|-------------|---------|-------------------------------------------------|
| en-US       | 900201  | Issuer's trade name                             |
| en-US       | 900202  | Testing environment                             |
| en-US       | 900203  | Testing environment (">" characters on 3 lines) |
| en-US       | 900204  | Cancellation Total value                        |
| en-US       | 900205  | Cancellation Access key                         |
| en-US       | 900206  | Cancellation QR-code                            |
| en-US       | 900207  | Cancellation Barcode (44 characters)            |
| en-US       | 900208  | Cancellation Barcode block 1 (22 characters)    |
| en-US       | 900209  | Cancellation Barcode block 2 (22 characters)    |
| en-US       | 900210  | Cancellation Date of issue                      |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                                                | Type    | Caption text ID |
|-----------------------------------------------------|---------|-----------------|
| FISCALDOCUMENTESTABLISHMENTTRADENAME\_BR            | Receipt | 900201          |
| EFDADDITIONALFISCALMESSAGETESTINGENVIRONMENT\_BR    | Receipt | 900202          |
| EFDADDITIONALFISCALMESSAGETESTINGENVIRONMENTROW\_BR | Receipt | 900203          |
| CANCELFISCALDOCUMENTTOTALAMOUNT\_BR                 | Receipt | 900204          |
| CANCELFISCALDOCUMENTACCESSKEY\_BR                   | Receipt | 900205          |
| CANCELFISCALDOCUMENTQRCODETEXT\_BR                  | Receipt | 900206          |
| CANCELBARCODE\_BR                                   | Receipt | 900207          |
| CANCELFISCALDOCUMENTBARCODEFIRST\_BR                | Receipt | 900208          |
| CANCELFISCALDOCUMENTBARCODESECOND\_BR               | Receipt | 900209          |
| CANCELFISCALDOCUMENTISSUEDATE\_BR                   | Receipt | 900210          |

### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language text values that you defined in the previous section.

- **Header:** Add the following fields:

    - **Trade name (Nome fantasia)** – The trade name of the fiscal establishment.
    - **Testing environment (SAT em condição de teste)** – The text "=&nbsp;TESTE&nbsp;=&nbsp;" and three lines of right angle brackets (\>), for cases where the SAT is in test condition.
    - **Cancellation Date of issue (Emissão / Data de recebimento)** – The date and time when the cancellation receipt is issued.
	
- **Lines:** Add the following fields:
	
    - **Cancellation Total value (Valor total)** – The total amount of the cancellation receipt.
    - **Cancellation Access key (Chave de acesso)** – The access key of the cancellation receipt.

- **Footer:** Add the following fields:

    - **Barcode (Código de barras)** – You can add a bar code field to CF-e-SAT for model 59 fiscal receipts for sales. This bar code is a graphical representation of the 44-digit **Access key (Chave de acesso)** value.
    - **Barcode block 1**, **Barcode block 2** – You can add 22-digit bar code fields to CF-e-SAT for model 59 fiscal receipts for sales that are printed on the till roll. This bar code is a graphical representation of the **Access key (Chave de acesso)** value that is divided into two parts, each of which has 22 digits.
    - **Cancellation QR-code** – A receipt can include a QR code for CF-e-SAT model 59 for cancellations, referring to the canceled sale.
    - **Cancellation Barcode** – A receipt can include a bar code for CF-e-SAT model 59 for sales cancellations. This barcode is a graphical representation of the 44-digit **Cancellation Access key (Chave de acesso)** value.
    - **Cancellation Barcode block 1**, **Cancellation Barcode block 2** – You can add 22-digit bar code fields to CF-e-SAT for model 59 fiscal receipts for sales cancellations that are printed on the till roll. This bar code is a graphical representation of the **Access key (Chave de acesso)** value that is divided into two parts, each of which has 22 digits.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

## Additional resources

[About SAT](https://portal.fazenda.sp.gov.br/servicos/sat)

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

[Set up and design receipt formats](../receipt-templates-printing.md)
