---
# required metadata
title: NFC-e fiscal document functionality in Commerce POS for Brazil
description: This topic gives an overview of NFC-e fiscal document functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: akviklis
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
ms.author: akviklis
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.18

---

# NFC-e fiscal document functionality in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This topic gives an overview of NFC-e (Nota Fiscal do Consumidor eletrônica) fiscal document functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil. It also explains how to issue NFC-e documents and print DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) fiscal receipts when retail sales of goods are completed in Commerce POS for Brazil.

An NFC-e is an electronic fiscal document that is generated to register the sale of goods to a customer. It enables tax and fiscal control by tax authorities. It also lets customers verify the validity and authenticity of fiscal documents that they receive. Sales of services aren't supported.

Commerce functionality for Brazil supports the NFC-e model 65 format for Brazilian retailers. The NFC-e model 65 format is a national standard for electronic fiscal documents. It's designed for retail and is based on the same technical standards as the NF-e (Nota Fiscal eletrônica) model 55 format. For more information about the NF-e format and process, see [Brazil NF-e process overview](../../finance/localizations/latam-bra-nf-e-process.md).

## Supported scenarios

The following example scenarios show frequently performed Commerce actions that are associated with NFC-e documents.

### Scenario 1: Make a cash-and-carry sale of goods and print a DANFE receipt

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the QR code) on the printed DANFE receipt corresponds to the sale.

### Scenario 2: Make a cash-and-carry sale of goods to an identified customer

1. Sign in to POS.
1. Add products to the cart.
1. Add a named customer, or manually enter customer information. For more information, see [Manage customer information in POS for Brazil](latam-bra-customer-information.md).
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the information (including the QR code) on the printed DANFE receipt corresponds to the sale.

### Scenario 3: Make a cash-and-carry sale of goods in offline contingency mode

The NFC-e offline contingency mode must be used when a store's internet connection isn't available, or when the SEFAZ (Secretaria de Estado de Fazenda) authorization service is down. In offline contingency mode, POS locally generates NFC-e documents. Those documents are then transmitted to SEFAZ later.

1. Sign in to POS.
1. Add products to the cart.
1. Register payments for the transaction. You will receive an error when POS tries to communicate with SEFAZ.
1. Select **Postpone**, enter a justification for the postponement, and then finalize the transaction.
1. Verify that two copies of the detailed DANFE are printed: one for the consumer (via consumidor) and one for the establishment (via estabelecimento).
1. Verify that the information (including the QR code) on the printed DANFE receipts corresponds to the sale.
1. Verify that the DANFE receipts contain the following text: "EMITIDA EM CONTINGÊNCIA Pendente de autorização" ("ISSUED IN CONTINGENCY Authorization Pending").

### Scenario 4: Make a mixed sale that contains gift cards and other goods in the same transaction

The operations for issuing gift cards and adding value to gift cards aren't subject to taxations in Brazil. Therefore, they aren't written to the fiscal receipt.

1. Sign in to POS.
1. Add products to the cart.
1. Issue gift cards in the same transaction.
1. Register payments for the transaction.
1. Select the DANFE format (**Simplified** or **Detailed**), and then finalize the transaction.
1. Verify that the printed DANFE receipt doesn't include the gift cards together with the other goods that were sold.
1. Verify that separate receipts are printed for each gift card that was sold.

## Custom fields for DANFE fiscal receipts

DANFE fiscal receipts can implement and use the following custom fields to include additional information.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of the **Language text** page.

| Language ID | Text ID | Text                                      |
|-------------|---------|-------------------------------------------|
| en-US       | 900001  | Access key                                |
| en-US       | 900002  | Authorization protocol                    |
| en-US       | 900003  | Date of Authorization protocol            |
| en-US       | 900004  | Issuer's establishment name               |
| en-US       | 900005  | Issuer's establishment address            |
| en-US       | 900006  | Issuer's establishment state registration |
| en-US       | 900007  | Issuer's establishment CNPJ               |
| en-US       | 900008  | Date and time of issue                    |
| en-US       | 900009  | Type of operation (input or output)       |
| en-US       | 900010  | NFC-e / NF-e fiscal document number       |
| en-US       | 900011  | NFC-e / NF-e fiscal document series       |
| en-US       | 900012  | Not identified customer message           |
| en-US       | 900013  | Customer's name                           |
| en-US       | 900014  | Customer's address                        |
| en-US       | 900015  | Customer's CPF / CNPJ / Foreigner ID      |
| en-US       | 900016  | Item quantity                             |
| en-US       | 900017  | Item total amount                         |
| en-US       | 900018  | Total quantity                            |
| en-US       | 900019  | Total amount                              |
| en-US       | 900020  | QR code                                   |
| en-US       | 900021  | Taxpayer Interest Message                 |


On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                                    | Type    | Caption text ID |
|-----------------------------------------|---------|-----------------|
| EFDOCACCESSKEY\_BR                      | Receipt | 900001          |
| EFDAUTHORIZATIONPROTOCOL\_BR            | Receipt | 900002          |
| EFDAUTHORIZATIONPROTOCOLDATE\_BR        | Receipt | 900003          |
| FISCALDOCUMENTESTABLISHMENTNAME\_BR     | Receipt | 900004          |
| FISCALDOCUMENTESTABILISHMENTADDRESS\_BR | Receipt | 900005          |
| IENUMBER\_BR    						  | Receipt | 900006          |
| CNPJCPFNUM\_BR      					  | Receipt | 900007          |
| FISCALDOCUMENTDATE\_BR 				  | Receipt | 900008          |
| TYPEOFOPERATION\_BR                     | Receipt | 900009          |
| FISCALDOCUMENTNUMBER\_BR                | Receipt | 900010          |
| FISCALDOCUMENTSERIES\_BR                | Receipt | 900011          |
| EFDNOTIDENTIFIEDCUSTOMERMESSAGE\_BR     | Receipt | 900012          |
| FISCALDOCUMENTCUSTOMERNAME\_BR          | Receipt | 900013          |
| FISCALDOCUMENTCUSTOMERADDRESS\_BR       | Receipt | 900014          |
| FISCALDOCUMENTCUSTOMERDOCUMENT\_BR      | Receipt | 900015          |
| QTY\_BR               				  | Receipt | 900016          |
| TOTALAMOUNT\_BR    					  | Receipt | 900017          |
| EFDTOTALITEMQUANTITY\_BR      		  | Receipt | 900018          |
| TOTALAMOUNTWITHTAX\_BR 				  | Receipt | 900019          |
| EFDQRCODE\_BR                 		  | Receipt | 900020          |
| FISCALDOCUMENTCONSUMEROBSERVATION\_BR   | Receipt | 900021          |

### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the Receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

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

- **Lines:** Add the following fields:

    - **Item name** field
    - **Quantity (Qtd.)** – The quantity of items.
    - **Total value of the item (Valor total)** – The amount per item.
    - **Total quantity (Qtd. total de itens)** – The total quantity of items on the receipt.
    - **Total value (Valor total)** – The total amount of the receipt.

- **Footer:** Add the following fields:

    - **QR-code** – A receipt can include a QR code for DANFE model 65 for sales.
    - **Taxpayer Interest Message (Mensagem de Interesse do Contribuinte)** – An approximate breakdown of the tax burden in NFC-e fiscal documents.

For more information about how to work with receipt formats, see [Set up and design receipt formats](../receipt-templates-printing.md).

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

[Set up and design receipt formats](../receipt-templates-printing.md).
