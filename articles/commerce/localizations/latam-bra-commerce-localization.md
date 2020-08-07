---
# required metadata

title: Commerce localization for Brazil
description: This topic provides an overview of the localization of Microsoft Dynamics 365 Commerce for Brazil.
author: josaw
manager: annbe
ms.date: 07/27/2020
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

This topic describes the scope of the Microsoft Dynamics 365 Commerce functionality that is specific to Brazil. It includes information about features and functionality that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that typically affect retail businesses in Brazil (within the scope of the [Brazilian localization](../../financials/localizations/latam-bra-scope.md#brazilian-localization-strategy)).

However, Commerce doesn't address all laws, regulations, or commercial requirements in Brazil, because laws and regulations vary in the way that they affect organizations. For more information, see the [Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck).

## Capabilities of the Commerce localization for Brazil

### Scope that is available in Brazil

The following features in Commerce headquarters and the point of sale (POS) are available to Commerce customers in Brazil:

- Retail product management and calculation of Brazil-specific taxes that are applicable to sales to final consumers. This feature includes an estimated tax breakdown in printed fiscal receipts.
- Generation of NFC-e (Nota Fiscal do Consumidor eletrônica) electronic fiscal documents for retail sales (model 65), submission of the electronic fiscal documents via the government's web services, and printing of DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) NFC-e receipts.
- Cancellation of retail sales via the government's web services within the allowed timeframe.
- Generation of NF-e (Nota Fiscal eletrônica) electronic fiscal documents for retail returns (model 55), submission of the electronic fiscal documents via the government's web services, and printing of DANFE receipts.
- Generation of CF-e (Cupom Fiscal eletrônico) electronic fiscal documents for retail sales in São Paulo (model 59) and registration of the electronic fiscal documents in the SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal device.
- Electronic funds transfer (EFT) integration for the POS. This feature includes integration with popular local and global payment providers, and support for debit and credit card payments.
- Management of Brazil-specific customer registration numbers. This feature includes capabilities for entering, viewing, and modifying CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas) tax registration numbers or Foreigner IDs, and for registering these numbers in NFC-e, NF-e, and CF-e, and printed receipts.
- Postponed registration of electronic fiscal documents in the event of network failures (offline contingency mode), and subsequent transmission of electronic fiscal documents in contingency from Commerce headquarters.
- Control of electronic fiscal documents in Commerce headquarters. This feature includes capabilities for discarding the documents and registering a cancellation by substitution.
- Generation and submission of electronic fiscal documents for customer orders.
- The ability to issue linked NF-e over all types of registered fiscal documents.
- N-1 support, so that customers who run Microsoft Dynamics AX 2012 R3 in their stores can work with Microsoft Dynamics 365 Commerce headquarters after an upgrade.
- Support for Brazil-specific fields, such as CNPJ/CPF tax registration numbers, when customer master records are merged in a call center.

### Supported scenarios

The following scenarios are supported by Commerce localization for Brazil:

- Cash-and-carry sales of goods
- Cancellations and returns of cash-and-carry sales of goods
- Cash-and-carry sales of goods in offline contingency mode
- Cancellation by substitution
- Issuing gift cards and payments by gift cards
- Registering and processing customer orders in the POS
- Posting fiscal documents in retail statements in Commerce headquarters
- Sales via e-Commerce storefronts
- Call center sales

### Fiscal registration for Brazil

Fiscal registration is the immediate registration of retail sales per local fiscal laws that are aimed at preventing tax fraud in the retail industry. The following main fiscal registration methods are available in Brazil:

- Generation of an NFC-e electronic fiscal document for a retail sale, and submission of the document to tax authorities (SEFAZ \[Secretaria de Fazenda\]) via a dedicated web service that is maintained by SEFAZ.
- Registration of a retail sale, in a SAT fiscal device that is connected to the POS, by using a CF-e electronic fiscal document.
- Registration of a retail sale in a fiscal printer that is connected to the POS.

Commerce supports fiscal registration via the [Fiscal integration framework](../localizations/fiscal-integration-for-retail-channel.md) and its extensions for specific countries or regions. Formats of electronic fiscal documents that meet the legal requirements in Brazil are configured by using the [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) functionality. Electronic fiscal documents are submitted via the [Electronic invoicing service](../../financials/localizations/e-invoicing-get-started.md). For more information about the submission process for electronic fiscal document and configuration for Brazil, see [Electronic invoicing add-on for Brazil](../../financials/localizations/e-invoicing-bra-get-started.md).

> [!NOTE]
> Integration with fiscal printers isn't available in Commerce. You can take advantage of the [N-1 capabilities](../dev-itpro/n-1-installation-configuration.md) to integrate Microsoft Dynamics AX 2012 R3 Retail Enterprise Point of Sale (EPOS), which supports the integration with fiscal printers for Brazil in Commerce headquarters.

## Availability of Commerce localization features for Brazil

| Feature                                                                  | Public preview | General availability (GA) | Post-GA | Not planned |
|--------------------------------------------------------------------------|----------------|---------------------------|---------|-------------|
| Retail product management, and tax setup and calculation                 | X              |                           |         |             |
| NFC-e (model 65) and DANFE for retail sales                              | X              |                           |         |             |
| Communication with SEFAZ via [Electronic invoicing service](../../financials/localizations/e-invoicing-get-started.md) | X              |                           |         |             |
| Retail statements in Commerce headquarters                               | X              |                           |         |             |
| Handling of fiscal customer information (for example, CPF/CNPJ)          |                | X                         |         |             |
| NF-e (model 55) and DANFE for sales returns                              |                | X                         |         |             |
| CF-e (model 59) for sales in São Paulo and integration with a SAT device |                | X                         |         |             |
| NFC-e/NF-e contingency in the POS (offline mode)                         |                | X                         |         |             |
| Transmission of NFC-e/NF-e in contingency from Commerce headquarters     |                | X                         |         |             |
| NFC-e cancellation, discard, cancellation by substitution                |                | X                         |         |             |
| EFT integration (Adyen and basic capabilities)                           |                | X                         |         |             |
| Searching for customers by registration numbers in the POS               |                |                           | X       |             |
| EFT integration (advanced capabilities and additional providers)         |                |                           | X       |             |
| Fiscal documents for customer orders from the POS                        |                |                           | X       |             |
| NF-e linked to NFC-e/CF-e and DANFE                                      |                |                           | X       |             |
| N-1 support for upgrade from AX 2012 R3                                  |                |                           | X       |             |
| E-Commerce capabilities for Brazil                                       |                |                           | X       |             |
| Merging CNPJ/CPF in customer master records in the call center           |                |                           | X       |             |
| Retail fiscal documents in fiscal book statements\*                      |                |                           |         | X           |
| Integration of the POS with fiscal printers                              |                |                           |         | X           |

\* *Fiscal book statements* are SPED (Sistema Público de Escrituração Digital) Fiscal, SPED Contributions, and ICMS-ST (Imposto sobre Circulação de Mercadorias e Serviços - Substituição Tributária) compensation and restitution statements for the supported states.
