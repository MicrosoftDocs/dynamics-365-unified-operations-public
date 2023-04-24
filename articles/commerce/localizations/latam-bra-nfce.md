---
title: NFC-e fiscal document functionality in Commerce POS for Brazil
description: This article gives an overview of NFC-e fiscal document functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil.
author: EvgenyPopovMBS
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.18
ms.search.industry: Retail
---

# NFC-e fiscal document functionality in Commerce POS for Brazil

[!include[banner](../includes/banner.md)]

This article gives an overview of NFC-e (Nota Fiscal do Consumidor eletrônica) fiscal document functionality in Microsoft Dynamics 365 Commerce point of sale (POS) for Brazil. It also explains how to issue NFC-e documents and print DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) fiscal receipts when retail sales of goods are completed in Commerce POS for Brazil.

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

> [!NOTE]
> If NFC-e is chosen as a main mode of a store establishment in São Paulo state, POS must generate CF-e (Cupom Fiscal eletrônico) documents via a SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) device when the store's internet connection isn't available, or when the SEFAZ authorization service is down. This use of SAT is considered contingency mode. For more information, see the [Make a cash-and-carry sale of goods by using SAT as contingency mode](latam-bra-cf-e-sat.md#scenario-4-make-a-cash-and-carry-sale-of-goods-by-using-sat-as-contingency-mode) scenario for the integration of CF-e fiscal documents with SAT functionality.

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

DANFE fiscal receipts can implement and use custom fields to include additional information.

### Configure custom fields so that they can be used in receipt formats for sales receipts

You can configure the language text and custom fields that are used in the POS receipt formats. The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt layouts. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

Add the following POS labels to the **POS** section of the **Language text** page.

| Language ID | Text ID | Text |
|---|---|---|
| en-US | 900001 | Access key |
| en-US | 900002 | Authorization protocol |
| en-US | 900003 | Date of Authorization protocol |
| en-US | 900004 | Issuer's establishment name |
| en-US | 900005 | Issuer's establishment address |
| en-US | 900006 | Issuer's establishment IE (state) registration number |
| en-US | 900007 | Issuer's establishment CCM (city) registration number |
| en-US | 900008 | Issuer's establishment CNPJ registration number |
| en-US | 900009 | Date and time of issue |
| en-US | 900010 | Type of operation (input or output) |
| en-US | 900011 | NFC-e / NF-e fiscal document number |
| en-US | 900012 | NFC-e / NF-e fiscal document series |
| en-US | 900013 | Not identified customer message |
| en-US | 900014 | Customer's name |
| en-US | 900015 | Customer's address |
| en-US | 900016 | Customer's IE (state) registration number |
| en-US | 900017 | Customer's CCM (city) registration number |
| en-US | 900018 | Customer's CPF / CNPJ / Foreigner ID registration number |
| en-US | 900019 | Item quantity |
| en-US | 900020 | Item total amount |
| en-US | 900021 | Total quantity |
| en-US | 900022 | Total amount |
| en-US | 900023 | Item discount |
| en-US | 900024 | Subtotal discount |
| en-US | 900025 | Total discount |
| en-US | 900026 | Total discount message |
| en-US | 900027 | QR code |
| en-US | 900028 | Taxpayer Interest Message |

On the **Custom fields** page, add the following records for the custom fields for receipt layouts. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name | Type | Caption text ID |
|---|---|---|
| EFDOCACCESSKEY\_BR | Receipt | 900001 |
| EFDAUTHORIZATIONPROTOCOL\_BR | Receipt | 900002 |
| EFDAUTHORIZATIONPROTOCOLDATE\_BR | Receipt | 900003 |
| FISCALDOCUMENTESTABLISHMENTNAME\_BR | Receipt | 900004 |
| FISCALDOCUMENTESTABILISHMENTADDRESS\_BR | Receipt | 900005 |
| IENUMBER\_BR | Receipt | 900006 |
| CCMNUM\_BR | Receipt | 900007 |
| CNPJCPFNUM\_BR | Receipt | 900008 |
| FISCALDOCUMENTDATE\_BR | Receipt | 900009 |
| TYPEOFOPERATION\_BR | Receipt | 900010 |
| FISCALDOCUMENTNUMBER\_BR | Receipt | 900011 |
| FISCALDOCUMENTSERIES\_BR | Receipt | 900012 |
| EFDNOTIDENTIFIEDCUSTOMERMESSAGE\_BR | Receipt | 900013 |
| FISCALDOCUMENTCUSTOMERNAME\_BR | Receipt | 900014 |
| FISCALDOCUMENTCUSTOMERADDRESS\_BR | Receipt | 900015 |
| IETAXIDENTIFIER\_BR | Receipt | 900016 |
| CCMTAXIDENTIFIER_BR | Receipt | 900017 |
| CPFCNPJTAXIDENTIFIER_BR | Receipt | 900018 |
| QTY\_BR | Receipt | 900019 |
| TOTALAMOUNT\_BR | Receipt | 900020 |
| EFDTOTALITEMQUANTITY\_BR | Receipt | 900021 |
| TOTALAMOUNTWITHTAX\_BR | Receipt |900022 |
| FISCALDOCUMENTTOTALITEMSDISCOUNT\_BR | Receipt |900023 |
| FISCALDOCUMENTSUBTOTALDISCOUNT\_BR | Receipt |900024 |
| FISCALDOCUMENTDISCOUNTTOTAL\_BR | Receipt |900025 |
| FISCALDOCUMENTDISCOUNTTOTALMESSAGE\_BR | Receipt |900026 |
| EFDQRCODE\_BR | Receipt | 900027 |
| FISCALDOCUMENTCONSUMEROBSERVATION\_BR | Receipt | 900028 |

### Configure receipt formats

For every receipt format that is required, change the value of the **Print behavior** field to **Always print**.

In the receipt format designer, add the following custom fields to the appropriate receipt sections. Note that field names correspond to the language texts that you defined in the previous section.

- **Header:** Add the following fields:

    - **Access key (Chave de acesso)** – The access key that consists of 11 blocks, each of which has four digits.
    - **Authorization protocol (Protocolo de Autorização)** – The number that is obtained from SEFAZ when the NFC-e or NF-e fiscal document is issued.
    - **Date of Authorization protocol (Data de Autorização)** – The date and time when the NFC-e or NF-e fiscal document is registered in SEFAZ.
    - **Fiscal data of the issuer (Emitente)**:

        - **Name** – The corporate name of the fiscal establishment.
        - **CNPJ** – The CNPJ number of the fiscal establishment.
        - **IE** – The state registration ID of the fiscal establishment.
        - **CCM** – The city registration ID of the fiscal establishment.
        - **Address** – The address of the fiscal establishment.

    - **Date of issue (Emissão / Data de recebimento)** – The date and time when the receipt is issued.
    - **NFC-e / NF-e number (Número)** – The number of the electronic fiscal document.
    - **Series (Série)** – The series of the electronic fiscal document.
    - **Type of operation (Saída / Entrada )** – The input or output type of the operation.
    - **Fiscal data of the customer (Destinatário)**:

        - **Name** – The name or corporate name of the customer.
        - **CPF/CNPJ/Foreigner ID** – The CPF/CNPJ number or foreigner ID of the customer.
        - **IE** – The state registration ID of the customer.
        - **CCM** – The city registration ID of the customer.
        - **Address** – The address of the customer.

        Alternatively, there might be an unidentified customer message.

- **Lines:** Add the following fields:

    - **Item name** – The name of the item.
    - **Item quantity (Qtd.)** – The quantity of items.
    - **Item total amount (Valor total)** – The amount per item.
    - **Total quantity (Qtd. total de itens)** – The total quantity of items on the receipt.
    - **Total amount (Valor total)** – The total amount of the receipt.
    - **Item discount** – The discount per item.
    - **Subtotal discount** – The subtotal discount.
    - **Total discount** – The total discount of the receipt.
    - **Total discount message** – The total discount message. 

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
