---
# required metadata
title: CF-e fiscal document and integration with SAT functionality in Commerce POS for Brazil
description: This topic gives an overview of generation of electronic fiscal documents CF-e for retail sales and registration of the electronic fiscal documents in the SAT fiscal device functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
manager: annbe
ms.date: 09/09/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata
# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: 10.0.20

---

# CF-e fiscal document functionality in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic gives an overview of CF-e (Cupom Fiscal eletrônico) fiscal document and registration of the electronic fiscal documents in the SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal device functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil. It also explains how to issue CF-e documents and print CF-e-SAT (Cupom Fiscal Eletrônico - SAT) fiscal receipts when retail sales of goods are completed in Commerce POS for Brazil.

A CF-e is an electronic fiscal document that is generated to register the sale of goods to a customer in São Paulo. It enables tax and fiscal control by tax authorities. It also lets customers verify the validity and authenticity of fiscal documents that they receive. Sales of services aren't supported.

Commerce functionality for Brazil supports the CF-e model 59 format for Brazilian retailers. The CF-e model 59 format is a standard for retail electronic fiscal documents within the borders of São Paulo state along with the national standard - NFC-e model 65 format. For more information about the NCF-e format, see [NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md).

Registration of electronic fiscal documents for retail sales in an integrated SAT device (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) is one of the fiscal registration methods available to retailers in the São Paulo state of Brazil. The feature includes the generation of CF-e electronic fiscal documents (Cupom Fiscal eletrônico, model 59) for sales transactions in retail point of sale (POS) and registration of the electronic fiscal documents in the SAT fiscal device.

## Feature details
This feature enables fiscal registration of retail sales in a SAT device connected to a hardware station. It takes advantage of the [fiscal integration framework](https://docs.microsoft.com/en-us/dynamics365/retail/localizations/fiscal-integration-for-retail-channel), meaning it supports all of the built-in fiscal integration capabilities. It is included in the out-of-the-box solution but must be configured to be used.

The generation of the electronic fiscal document model 59 (CF-e) is based on an [Electronic reporting](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) configuration and is done by the electronic reporting runtime engine that is part of the Commerce runtime.

The feature currently does not support customer orders that are picked up in POS. Support for the customer order pickup operation will be added later.


## Supported scenarios

The following example scenarios show frequently performed Commerce actions that are associated with CF-e-SAT documents.

### Scenario 1: Make a cash-and-carry sale of goods and print a CF-e-SAT receipt

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the barcode and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 2: Make a cash-and-carry sale of goods to an identified customer

1. Sign in to POS.
1. Add products to the cart.
1. Add a named customer, or manually enter customer information. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the barcode and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 3: Initiate a cancellation of sold goods

To cancel a sale, follow these steps.

1. Sign in to POS.
1. Open **Show journal** page.
1. Find the sale that must be canceled.
1. Select **Cancel transaction**.
1. Register payment refunds for the transaction, and then finalize the transaction.
1. Verify that the information (including the barcode and QR code) on the printed CF-e-SAT cancellation receipt corresponds to the transaction.

> [!NOTE]
> Cancelling of approved CF-e issued by other stores is not supported. Only the CF-e issued by the same store can be cancelled. 

### Scenario 3: Make a cash-and-carry sale of goods in offline contingency mode

If the NFC-e is choosen as a main mode of a store establishment, POS must generate CF-e documents via SAT device when the store's internet connection isn't available, or when the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. This is considered as using SAT as contingency mode.

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction. You will receive an error when POS tries to communicate with SEFAZ.
1. Select **Postpone**, and then finalize the transaction.
1. Verify that the information (including the barcode and QR code) on the printed CF-e-SAT receipt corresponds to the sale.

### Scenario 4: Make a mixed sale that contains gift cards and other goods in the same transaction

The operations for issuing gift cards and adding value to gift cards aren't subject to taxations in Brazil. Therefore, they aren't written to the fiscal receipt.

1. Sign in to POS.
1. Add products to the cart.
1. Issue gift cards in the same transaction.
1. Register payments for the transaction.
1. Select the CF-e-SAT format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the printed CF-e-SAT receipt doesn't include the gift cards together with the other goods that were sold.
1. Verify that separate receipts are printed for each gift card that was sold.

## Custom fields for CF-e-SAT fiscal receipts

DANFE fiscal receipts can implement and use the following custom fields to include additional information:

- **Access key (Chave de acesso)** – The access key that consists of 11 blocks, each of which has four digits.
- **Authorization protocol (Protocolo de Autorização)** – The number that is obtained from SEFAZ when NFC-e or NF-e fiscal documents are issued.
- **Fiscal data of the issuer (Emitente)**:

    - **Name** – The corporate name of the fiscal establishment.
    - **CNPJ** – The CNPJ number of the fiscal establishment.
    - **IE** – The state registration ID of the fiscal establishment.
    - **Address** – The address of the fiscal establishment.

- **Date of issue (Emissão / Data de recebimento)** – The date and time when the receipt is issued.
- **NFC-e / NF-e number (Número)** – The number of the electronic fiscal document.
- **Series (Série)** – The series of the electronic fiscal document.
- **Type of operation (Saída / Entrada )** – The input or output type of the operation.
- **Fiscal data of the customer (Destinatário)**:

    - **Name** – The name of the recipient or corporation.
    - **CPF/CNPJ/Foreigner ID** – The CPF/CNPJ number or foreigner ID of the recipient.
    - **Address** – The address of the recipient.

- **Quantity (Qtd.)** – The quantity of items.
- **Total value of the item (Valor total)** – The amount per item.
- **Total quantity (Qtd. total de itens)** – The total quantity of items on the receipt.
- **Total value (Valor total)** – The total amount of the receipt.
- **QR-code** – A receipt can include a QR code for DANFE model 65 for sales.
- **Taxpayer Interest Message (Mensagem de Interesse do Contribuinte)** – An approximate breakdown of the tax burden in NFC-e fiscal documents.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
