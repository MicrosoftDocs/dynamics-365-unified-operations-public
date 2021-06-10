---
# required metadata
title: NFC-e fiscal document functionality in Commerce POS for Brazil
description: This topic gives an overview of NFC-e fiscal document functionality in Microsoft Dynamics 365 Commerce POS for Brazil.
author: v-ankvik
manager: annbe
ms.date: 06/10/2021
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
ms.author: v-ankvik
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.18

---

# NFC-e fiscal document functionality in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic gives an overview of NFC-e (Nota Fiscal do Consumidor eletrônica) fiscal document functionality in Microsoft Dynamics 365 Commerce POS for Brazil, and explains how to issue NFC-es documents and print DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) fiscal receipts when completing retail sales of goods in Commerce POS for Brazil.

A NFC-e is an electronic fiscal document that is generated to register the sale of goods to a customer. It enables tax and fiscal control from tax authorities, and allows customers to verify the validity and authenticity of received fiscal documents. Sales of services are not supported.

Commerce functionality for Brazil supports the NFC-e electronic fiscal document model 65 format for Brazilian retailers. The NFC-e model 65 format is a national standard for electronic fiscal documents designed for retailing, and is based on the same technical standards as the NF-e (Nota Fiscal eletrônica) model 55 format. For more information about the NF-e format and process, see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md). 

## Supported scenarios

The following example scenarios show common Commerce actions associated with NFC-e documents.

### Scenario 1: Make a cash-and-carry sale of goods and print DANFE receipt

1. Sign in to POS.
1. Add product(s) to the cart.
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the QR code) on the printed DANFE receipt corresponds to the sale.

### Scenario 2: Make a cash-and-carry sale of goods to an identified customer

1. Sign in to POS.
1. Add product(s) to the cart.
1. Add a named customer, or specify customer information manually. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the QR code) on the printed DANFE receipt corresponds to the sale.

### Scenario 3: Make a cash-and-carry sale of goods in offline contingency mode

The NFC-e offline contingency mode must be used when the a store internet connection is not available or if the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. When in offline contingency mode, the POS generates NFC-e documents locally and these documents are then transmitted to SEFAZ at a later time.

1. Sign in to POS.
1. Add product(s) to the cart.
1. Register payments for the transaction. You will receive an error when POS attempts to communicate with SEFAZ.
1. Select **Postpone**, enter a justification for the postponement, and then finalize the transaction.
1. Verify that two copies of the detailed DANFE are printed: one for the consumer (via consumidor) and one for the establishment (via estabelecimento).
1. Verify that the information (including the QR code) on the printed DANFE receipts correspond to the sale. 
1. Verify that the DANFE receipts contain the following text: "EMITIDA EM CONTINGÊNCIA Pendente de autorização" ("ISSUED IN CONTINGENCY Authorization Pending").

### Scenario 4: Make a mixed sale containing gift cards along with other goods in the same transaction 

The operations for issuing Gift cards or Add to gift card are not subject to taxations in Brazil, thus they are not written in the fiscal receipt.

1. Sign in to POS.
1. Add product(s) to the cart.
1. Issue gift card(s) within the same transaction.
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the printed DANFE receipt does not include the gift card(s) along with the other goods sold.
1. Verify that separate receipts for each sold gift card are printed.

## DANFE fiscal receipt custom fields

DANFE fiscal receipts can include additional information by implementing and using the following custom fields.

- **Access key (Chave de acesso)** – Access key consisting of 11 blocks of four digits each.
- **Authorization protocol (Protocolo de Autorização)** – The number that is obtained from SEFAZ when issuing NFC-e or NF-e fiscal documents.
- **Fiscal data of the issuer (Emitente)**:
  - Name - Corporate name of the fiscal establishment.
  - CNPJ - CNPJ number of the fiscal establishment.
  - IE - State registration ID of the fiscal establishment.
  - Address - Address of the fiscal establishment. 
- **Date of issue (Emissão / Data de  recebimento)** – Issue date and time of the receipt.
- **NFC-e / NF-e number (Número)** - Number of the electronic fiscal document.
- **Series(Série)** - Series of the electronic fiscal document.
- **Type of operation (Saída / Entrada )** - Input or output type of the operation.
- **Fiscal data of the customer (Destinatário)**:
  - Name - Name of the recipient or corporation.
  - CPF/CNPJ/Foreigner ID - CPF/CNPJ number or foreigner ID of the recipient. 
  - Address - Address of the recipient.
- **Quantity (Qtd.)** - Quantity of items.
- **Total value of the item (Valor total)** - Amount per item.
- **Total quantity (Qtd. total de itens)** - Total quantity of items on the receipt.
- **Total value (Valor total)** - Total amount of the receipt.
- **QR-code** – A receipt can include a QR code for DANFE model 65 for sales.
- **Taxpayer Interest Message (Mensagem de Interesse do Contribuinte)** – Approximate breakdown of the tax burden in NFC-e.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md) 

[Commerce localization for Brazil](latam-bra-commerce-localization.md) 

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

