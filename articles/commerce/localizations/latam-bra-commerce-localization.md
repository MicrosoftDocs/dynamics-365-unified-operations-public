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

## Prerequisites
1. [Set up legal entity parameters](../../financials/localizations/latam-bra-legal-entity-parameters.md).
2. [Set up fiscal document source text](../../financials/localizations/tasks/br-00001-2-set-up-fiscal-document-source-text.md) for Commerce.
3. Submission of Brazilian business documents (listed below) is done through [Electronic invoicing service](../../financials/localizations/e-invoicing-get-started.md). The configuration steps and the process of submitting an NFC-e fiscal document is similar to the one described in the following article: [Electronic invoicing add-on for Brazil](../../financials/localizations/e-invoicing-bra-get-started.md).
4. Formats for electronic documents in accordance with the legal requirements in Brazil are configured using the [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) functionality.

## Capabilities of Commerce localization for Brazil 

### Scope available in Brazil

The following features are available to Commerce customers in Brazil in Commerce Headquarters (HQ) and point of sale (POS):

- Retail product management and calculation of Brazil-specific taxes applicable to sales to final consumers, including estimated tax breakdown in printed fiscal receipts.
- Generation of electronic fiscal documents NFC-e (Nota Fiscal do Consumidor eletrônica) for retail sales (model 65) and submission of the electronic fiscal documents via the government’s web services, and printing of DANFE NFC-e receipts.
- Cancellations of retail sales via the government’s web services within the allowed timeframe.
- Generation of electronic fiscal documents NF-e (Nota Fiscal eletrônica) for retail returns (model 55), submission of the electronic fiscal documents via the government’s web services, and printing of DANFE NF-e receipts.
- Generation of electronic fiscal documents CF-e (Cupom Fiscal eletrônico) for retail sales in São Paulo (model 59) and registration of the electronic fiscal documents in the SAT fiscal device. 
- EFT integration for POS, including integration with popular local and global payment providers amd support of debit and credit card payments.
- Management of Brazil-specific customer registration numbers, including entering, viewing, and modifying CNPJ/CPF or Foreigner ID, and registration of these numbers in NFC-e/NF-e/CF-e and printed receipts. 
- Postponed registration of electronic fiscal documents in case of network failures (offline contingency mode) and subsequent transmission of electronic fiscal documents in contingency from HQ.
- Control of electronic fiscal documents in HQ, including the capabilities to discard the documents and to register a cancellation by substitution.
- Generation and submission of electronic fiscal documents for customer orders.
- Issuing Linked NF-e over all types of registered fiscal documents.
- N-1 support, enabling customers running Microsoft Dynamics AX 2012 R3 in their stores to work with Microsoft Dynamics 365 Commerce headquarters after an upgrade.
- Support for Brazil-specific fields, such as tax registration numbers CNPJ/CPF, when merging customer master records in a call center.

### Supported scenarios:
1. Cash-and-carry sales of goods.
2. Cancellations and returns of cash-and-carry sales of goods.
3. Cash-and-carry sales of goods in offline mode - contingency.
4. Cancellation by substitution.
5. Issuing gift cards, payments by gift cards.
6. Working with customer orders on POS.
7. Posting fiscal documents in Retail statements in HQ.
8. Sales via e-Commerce storefronts
9. Call-center sales

## Brazilian Commerce localization features
| Feature                                                              | Public preview | General Availability - GA | Post GA | Is not currently planned |
|----------------------------------------------------------------------|----------------|---------------------------|---------|--------------------------|
| Retail product management, tax setup and calculation                 |       +        |                           |         |                          |
| NFC-e (model 65) and DANFE for retail sales                          |       +        |                           |         |                          |
| Communication with Sefaz via [E-invoicing service](../../financials/localizations/e-invoicing-get-started.md)|+|  |         |                          |
| Retail statements in HQ                                              |       +        |                           |         |                          |
| Handling of fiscal customer information (CPF/CNPJ, etc.)             |                | +                         |         |                          |
| NF-e (model 55) and DANFE for sales returns                          |                | +                         |         |                          |
| CF-e (model 59) for sales in São Paulo & integration with S@T device |                | +                         |         |                          |
| NFC-e/NF-e contingency in POS (offline mode)                         |                | +                         |         |                          |
| Transmission of NFC-e/NF-e in contingency from HQ                    |                | +                         |         |                          |
| NFC-e cancellation, discard, cancellation by substitution            |                | +                         |         |                          |
| EFT integration (Adyen, basic capabilities)                          |                | +                         |         |                          |
| Searching of customers by registration numbers in POS                |                |                           | +       |                          |
| EFT integration (advanced capabilities, additional provider(s))      |                |                           | +       |                          |
| Fiscal documents for POS customer orders                             |                |                           | +       |                          |
| NF-e linked to NFC-e / CF-e, DANFE                                   |                |                           | +       |                          |
| N-1 support for upgrade from Microsoft Dynamics AX 2012 R3           |                |                           | +       |                          |
| e-Commerce capabilities for Brazil                                   |                |                           | +       |                          |
| CNPJ/CPF in customer master records merge in a call center           |                |                           | +       |                          |
| Retail fiscal documents in *fiscal book statements**                 |                |                           |         | +                        |
| PAF-ECF fiscal printers                                              |                |                           |         | +                        |
    
\* *Fiscal book statements - SPED Fiscal, SPED Contributions and ICMS-ST compensation and restitution statements for the supported states.*
