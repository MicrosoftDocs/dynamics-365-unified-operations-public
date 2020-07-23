---
# required metadata

title: Commerce localization for Brazil
description: This topic provides an overview of the localization of Dynamics 365 Commerce for Brazil.
author: josaw
manager: annbe
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2020-8-03
ms.dyn365.ops.version: 10.0.13

---
# Commerce localization for Brazil

[!include[banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic describes **the scope of the Microsoft Dynamics 365 Commerce functionality that is specific to Brazil**. It includes features and functionalities that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that commonly affect retail businesses in Brazil (limited to the scope of the [Brazilian localization](../../financials/localizations/latam-bra-scope.md#brazilian-localization-strategy)).

However, Commerce doesn't address all laws, regulations, or commercial requirements in Brazil, because laws and regulations vary in the way that they affect organizations. Additional details are available in the [Product localization and translation availability Guide](https://aka.ms/dynamics_365_international_availability_deck).

## Capabilities of Commerce localization for Brazil 

### Scope available in Brazil

The following features are available to Commerce customers in Brazil in Commerce Headquarters (HQ) and point of sale (POS):

- Retail product management and calculation of Brazil-specific taxes applicable to sales to final consumers, including estimated tax breakdown in printed fiscal receipts.
- Generation of electronic fiscal documents NFC-e (Nota Fiscal do Consumidor eletrônica) for retail sales (model 65) and submission of the electronic fiscal documents via the government’s web services, and printing of DANFE NFC-e receipts.
- Cancellations of retail sales via the government’s web services within the allowed timeframe.
- Generation of electronic fiscal documents NF-e (Nota Fiscal eletrônica) for retail returns (model 55), submission of the electronic fiscal documents via the government’s web services, and printing of DANFE NF-e receipts.
- Generation of electronic fiscal documents CF-e (Cupom Fiscal eletrônico) for retail sales in São Paulo (model 59) and registration of the electronic fiscal documents in the SAT fiscal device. 
- EFT integration for POS, including integration with popular local and global payment providers and support of debit and credit card payments.
- Management of Brazil-specific customer registration numbers, including entering, viewing, and modifying CNPJ/CPF or Foreigner ID, and registration of these numbers in NFC-e/NF-e/CF-e and printed receipts. 
- Postponed registration of electronic fiscal documents in case of network failures (offline contingency mode) and subsequent transmission of electronic fiscal documents in contingency from HQ.
- Control of electronic fiscal documents in HQ, including the capabilities to discard the documents and to register a cancellation by substitution.
- Generation and submission of electronic fiscal documents for customer orders.
- Issuing Linked NF-e over all types of registered fiscal documents.
- N-1 support, enabling customers running Microsoft Dynamics AX 2012 R3 in their stores to work with Microsoft Dynamics 365 Commerce headquarters after an upgrade.
- Support for Brazil-specific fields, such as tax registration numbers CNPJ/CPF, when merging customer master records in a call center.

### Supported scenarios
1. Cash-and-carry sales of goods.
2. Cancellations and returns of cash-and-carry sales of goods.
3. Cash-and-carry sales of goods in offline mode - contingency.
4. Cancellation by substitution.
5. Issuing gift cards and payments by gift cards.
6. Registering and processing customer orders on POS.
7. Posting fiscal documents in Retail statements in HQ.
8. Sales via e-Commerce storefronts.
9. Call-center sales.

### Fiscal registration for Brazil
Fiscal registration stands for immediate registration of retail sales per local fiscal laws that are aimed to prevent tax fraud in the Retail industry. The following main fiscal registration methods are available in Brazil:
1. Generation of an electronic fiscal document NFC-e (Nota Fiscal do Consumidor eletrônica) for a retail sale and submission of the document to tax authorities (SEFAZ - Secretaria de Fazenda) via a dedicated web service maintained by SEFAZ.
2. Registration of a retail sale in a SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal device connected to POS using an electronic fiscal document CF-e (Cupom Fiscal eletrônico).
3. Registration of a retail sale in a fiscal printer connected to POS.

Commerce supports fiscal registration via the [Fiscal integration framework](../localizations/fiscal-integration-for-retail-channel.md) and its extensions for specific countries or regions. Formats of electronic fiscal documents in accordance with the legal requirements in Brazil are configured using the [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) functionality. Submission of electronic fiscal documents is done via the [Electronic invoicing service](../../financials/localizations/e-invoicing-get-started.md). You can find additional details on the electronic fiscal document submission process and configuration for Brazil on the following page: [Electronic invoicing add-on for Brazil](../../financials/localizations/e-invoicing-bra-get-started.md).

> [!NOTE]
> Integration with fiscal printers is not available in Commerce. You can leverage the N-1 capabilities to integrate Microsoft Dynamics AX 2012 R3 Retail Enterprise Point of Sale (EPOS), which supports the integration with fiscal printers for Brazil, with Commerce Headquarters.

## Availability of Commerce localization features for Brazil

| Feature                                                              | Public preview | General Availability - GA | Post GA | Not planned |
|----------------------------------------------------------------------|----------------|---------------------------|---------|-------------|
| Retail product management, tax setup and calculation                 |       +        |                           |         |             |
| NFC-e (model 65) and DANFE for retail sales                          |       +        |                           |         |             |
| Communication with Sefaz via [E-invoicing service](../../financials/localizations/e-invoicing-get-started.md)|+|  |         |             |
| Retail statements in HQ                                              |       +        |                           |         |             |
| Handling of fiscal customer information (CPF/CNPJ, etc.)             |                | +                         |         |             |
| NF-e (model 55) and DANFE for sales returns                          |                | +                         |         |             |
| CF-e (model 59) for sales in São Paulo & integration with S@T device |                | +                         |         |             |
| NFC-e/NF-e contingency in POS (offline mode)                         |                | +                         |         |             |
| Transmission of NFC-e/NF-e in contingency from HQ                    |                | +                         |         |             |
| NFC-e cancellation, discard, cancellation by substitution            |                | +                         |         |             |
| EFT integration (Adyen, basic capabilities)                          |                | +                         |         |             |
| Searching for customers by registration numbers in POS               |                |                           | +       |             |
| EFT integration (advanced capabilities, additional provider(s))      |                |                           | +       |             |
| Fiscal documents for customer orders from POS                        |                |                           | +       |             |
| NF-e linked to NFC-e / CF-e, DANFE                                   |                |                           | +       |             |
| N-1 support for upgrade from Microsoft Dynamics AX 2012 R3           |                |                           | +       |             |
| e-Commerce capabilities for Brazil                                   |                |                           | +       |             |
| Merging of CNPJ/CPF in customer master records in call center        |                |                           | +       |             |
| Retail fiscal documents in fiscal book statements\*                  |                |                           |         | +           |
| Integration of POS with fiscal printers                              |                |                           |         | +           |
    
\* *Fiscal book statements - SPED Fiscal, SPED Contributions and ICMS-ST compensation and restitution statements for the supported states.*
