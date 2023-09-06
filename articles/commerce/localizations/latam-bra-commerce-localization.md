---
title: Commerce localization for Brazil
description: This article provides an overview of the localization of Microsoft Dynamics 365 Commerce for Brazil.
author: EvgenyPopovMBS
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 2020-08-03
ms.dyn365.ops.version: 10.0.13
ms.search.industry: Retail
---
# Commerce localization for Brazil

[!Include[banner](../includes/banner.md)]

This article describes the scope of the Microsoft Dynamics 365 Commerce functionality that is specific to Brazil. It includes information about features and functionality that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that typically affect retail businesses in Brazil within the scope of the [Brazilian localization](../../finance/localizations/latam-bra-scope.md#brazilian-localization-strategy).

Commerce doesn't address all laws, regulations, or commercial requirements in Brazil. Laws and regulations vary in the way that they affect organizations. For more information, see the [Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck).

To learn about point of sale (POS) features that are available to customers in all countries or regions, see the [Commerce home page](../welcome.md).

## Capabilities of the Commerce localization for Brazil

### Scope that is available in Brazil

The following features in Commerce headquarters and POS are available to Commerce customers in Brazil:

- Retail product management and calculation of Brazil-specific taxes that are applicable to sales to final consumers. This feature includes an estimated tax breakdown in printed fiscal receipts.
- Generation of NFC-e (Nota Fiscal do Consumidor eletrônica) electronic fiscal documents for retail sales (model 65), submission of the electronic fiscal documents via the government's web services, and printing of DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) NFC-e receipts.
- Cancellation of retail sales via the government's web services within the allowed timeframe.
- Generation of NF-e (Nota Fiscal eletrônica) electronic fiscal documents for retail returns (model 55), submission of the electronic fiscal documents via the government's web services, and printing of DANFE receipts.
- Generation of CF-e (Cupom Fiscal eletrônico) electronic fiscal documents for retail sales in São Paulo state (model 59) and registration of the electronic fiscal documents in the SAT (Sistema Autenticador e Transmissor de Cupons Fiscais Eletrônicos) fiscal device. For more information, see [About SAT](https://portal.fazenda.sp.gov.br/servicos/sat).
- Electronic funds transfer (EFT) integration for the POS. This feature includes integration with the Adyen payment provider that provides basic capabilities such as support for debit and credit card payments and saving payment-related data in sales transactions. For more information, see [Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil](latam-bra-adyen.md)
- Management of Brazil-specific customer registration numbers. This feature includes capabilities for entering, viewing, and modifying CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas) tax registration numbers or Foreigner IDs, and for registering these numbers in NFC-e, NF-e, and CF-e, and printed receipts.
- Postponed registration of electronic fiscal documents in the event of network failures (offline contingency mode), and subsequent transmission of electronic fiscal documents in contingency from Commerce headquarters.
- Control of electronic fiscal documents in Commerce headquarters. This feature includes capabilities for discarding the documents and registering a cancellation by substitution.
- Searching for customers by registration numbers in the POS.

### Fiscal registration for Brazil

Fiscal registration is the immediate registration of retail sales per local fiscal laws that are aimed at preventing tax fraud in the retail industry. The following fiscal registration methods are available in Brazil:

- Generation of an NFC-e electronic fiscal document for a retail sale, and submission of the document to tax authorities (SEFAZ \[Secretaria de Fazenda\]) via a dedicated web service that SEFAZ maintains.
- Registration of a retail sale, in a SAT fiscal device that is connected to the POS, by using a CF-e electronic fiscal document.
- Registration of a retail sale in a fiscal printer that is connected to the POS.

Commerce supports fiscal registration via the [Fiscal integration framework](../localizations/fiscal-integration-for-retail-channel.md) and its extensions for specific countries or regions. The [Electronic reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) functionality is used to configure formats of electronic fiscal documents that meet the legal requirements in Brazil.

> [!NOTE]
> Integration with fiscal printers isn't available in Commerce. You can take advantage of the [N-1 capabilities](../dev-itpro/n-1-installation-configuration.md) to integrate Microsoft Dynamics AX 2012 R3 Retail Enterprise Point of Sale (EPOS), which supports the integration with fiscal printers for Brazil in Commerce headquarters.

## Availability of Commerce localization features for Brazil

| Feature                                                                        | Released | May be added in future releases | Not planned |
|--------------------------------------------------------------------------------|:----------:|:---------------------------------:|:-------------:|
| Retail product management, and tax setup and calculation                       | X        |                                  |             |
| NFC-e (model 65) and DANFE for retail sales                                    | X        |                                  |             |
| Communication with SEFAZ                                                       | X        |                                  |             |
| Retail statements in Commerce headquarters                                     | X        |                                  |             |
| Handling of fiscal customer information (for example, CPF/CNPJ)                | X        |                                  |             |
| NF-e (model 55) and DANFE for sales returns                                    | X        |                                  |             |
| NFC-e/NF-e contingency in the POS (offline mode)                               | X        |                                  |             |
| Transmission of NFC-e/NF-e in contingency from Commerce headquarters           | X        |                                  |             |
| NFC-e cancellation                                                             | X        |                                  |             |
| NFC-e cancellation by substitution, discard                                    | Х        |                                  |             |
| EFT integration (Adyen and basic capabilities)                                 | Х        |                                  |             |
| CF-e (model 59) for sales in São Paulo state and integration with a SAT device | Х        |                                  |             |
| Searching for customers by registration numbers in the POS                     | X        |                                  |             |
| EFT integration (Adyen advanced capabilities and additional providers)         |          | X                                |             |
| Fiscal documents for customer orders from the POS                              |          | X                                |             |
| NF-e linked to NFC-e/CF-e and DANFE                                            |          | X                                |             |
| N-1 support for upgrade from AX 2012 R3                                        |          | X                                |             |
| E-commerce capabilities for Brazil                                             |          | X                                |             |
| Merging CNPJ/CPF in customer master records in the call center                 |          | X                                |             |
| Retail fiscal documents in fiscal book statements\*                            |          |                                  | X           |
| Integration of the POS with fiscal printers (PAF-ECF)\*\*                      |          |                                  | X           |

\* *Fiscal book statements* are SPED (Sistema Público de Escrituração Digital) Fiscal, SPED Contributions, and ICMS-ST (Imposto sobre Circulação de Mercadorias e Serviços - Substituição Tributária) compensation and restitution statements for the supported states.

\*\* *PAF-ECF* stands for Programa Aplicativo Fiscal – Emissor de Cupom Fiscal ou simplesmente.


## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md) 

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Manage customer information in POS for Brazil](latam-bra-customer-information.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)

[About SAT](https://portal.fazenda.sp.gov.br/servicos/sat)

[CF-e fiscal document functionality in Commerce POS for Brazil](latam-bra-cf-e-sat.md)

[Dynamics 365 Payment Connector for Adyen in Commerce POS for Brazil](latam-bra-adyen.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
