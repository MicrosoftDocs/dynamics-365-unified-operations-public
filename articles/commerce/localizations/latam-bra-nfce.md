---
# required metadata
title: NFC-e - Electronic Fiscal Document for Consumers in Brazil
description: This topic gives an overview of the functionality for NFC-e for Brazil.
author: v-ankvik
manager: epopov
ms.date: 02/11/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 


# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.18

---

# NFC-e - Electronic Fiscal Document for Consumers in Brazil 

[!include[banner](../includes/banner.md)]

## Overview

The Commerce functionality for Brazil supports the Electronic Fiscal Document for Consumers (“Nota Fiscal do Consumidor eletrônica” - NFC-e) format for Brazilian retailers. The NFC-e format (model 65) is a national standard for electronic fiscal document, based on the same technical standards of the electronic fiscal document (NF-e) model 55, fitting to the particularities of retailing.

For more information about Electronic Fiscal Document (“Nota Fiscal Eletrônica” - NF-e), see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md). 

A NFC-e is an electronic fiscal document that is generated to register the sale of goods to a final consumer. It enables tax and fiscal control from tax authorities, and allows the consumers verifying the validity and authenticity of the received fiscal documents. Sales of services are not supported.

This topic explains how to issue NFC-es and print DANFE fiscal receipts when completing retail sales of goods on POS.

## Supported scenarios
The following scenarios are linked to NFC-e:

### Scenario 1: Make a cash-and-carry sale of goods and print DANFE receipt

1. Sign in to POS.
1. Add product(s) to the cart.
1. Register payments for the transaction.
1. Select DANFE format: Simplified or Detailed, and then finalize the transaction.
1. Verify that the information including QR-code on the printed DANFE receipt corresponds to the sale.

### Scenario 2: Make a cash-and-carry sale of goods to an identified customer

1. Sign in to POS.
1. Add product(s) to the cart.
1. [Add a named customer or specify customer information manually](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Select DANFE format: Simplified or Detailed, and then finalize the transaction.
1. Verify that the information including QR-code on the printed DANFE receipt corresponds to the sale.

### Scenario 3: Make a cash-and-carry sale of goods in offline contingency mode

The NFC-e offline contingency mode must be used when the store internet connection is not available or if the SEFAZ authorization service is down. In this case POS generates NFC-e documents locally, and then these documents are transmitted to SEFAZ in some time.

1. Sign in to POS.
1. Add product(s) to the cart.
1. Register payments for the transaction.
1. Get an error while communicating with SEFAZ.
1. Click on Postpone button, and specify a justification for the postponement, and finalize the transaction.
1. Verify that 2 copies of Detailed DANFE are printed: for the consumer (via consumidor) and for the establishment (via estabelecimento).
1. Verify that the information including QR-code on the printed DANFE receipts corresponds to the sale. 
1. Verify that the receipts contain the following text: "ISSUED IN CONTINGENCY Authorization Pending" ("EMITIDA EM CONTINGÊNCIA Pendente de autorização").

### Scenario 4: Make a mixed sale containing gift cards along with other goods in the same transaction 

The operations for issuing Gift cards or Add to gift card are not subject to taxations in Brazil, thus they are not written in the fiscal receipt.

1. Sign in to POS.
1. Add product(s) to the cart.
1. Issue gift card(s) within the same transaction.
1. Register payments for the transaction.
1. Select DANFE format: Simplified or Detailed, and then finalize the transaction.
1. Verify that the printed DANFE receipt does not include the gift card(s) along with the other goods sold.
1. Verify that separate receipt per each sold gift card is printed.

## DANFE Fiscal Receipts

**Fiscal receipts for Brazil** called "Documento Auxiliar da Nota Fiscal Eletrônica" (**DANFE**) can include additional information that was implemented by using custom fields:

- **Access key (Chave de acesso)** – Access key consisting of eleven blocks of four digits each.
- **Authorization protocol (Protocolo de Autorização)** – The number that is obtained from SEFAZ while issuing NFC-e / NF-e.
- **Fiscal data of the issuer (Emitente)**:
  - Name - Corporate name of the Fiscal establishment,
  - CNPJ - CNPJ of the Fiscal establishment,
  - IE - State registration ID of the Fiscal establishment,
  - Address - Address of the Fiscal establishment. 
- **Date of issue (Emissão / Data de  recebimento)** – Issue date and time of the receipt.
- **NFC-e / NF-e number (Número)** - Number of the electronic fiscal document.
- **Series(Série)** - Series of the electronic fiscal document.
- **Type of operation (Saída / Entrada )** - Input or output type of the operation.
- **Fiscal data of the customer (Destinatário)**:
  - Not identified customer message (),
  - Name - Name / Corporate name of the recepient,
  - CPF / CNPJ / Foreigner ID - CPF or CNPJ or Foreigner of the recepient, 
  - Address - Address of the recepient.
- **Quantity (Qtd.)** - Quantity per items.
- **Total value of the item (Valor total)** - Amount per item.
- **Total quantity (Qtd. total de itens)** - Total quantity of the receipt.
- **Total value (Valor total)** - Total amount of the receipt.
- **QR-code** – A receipt can include QR-code for DANFE for model 65 for sales.
- **Taxpayer Interest Message (Mensagem de Interesse do Contribuinte)** – Approximate breakdown of the tax burden in NFC-e.