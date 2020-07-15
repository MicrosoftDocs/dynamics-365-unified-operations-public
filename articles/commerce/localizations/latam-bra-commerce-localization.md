---
# required metadata

title: Commerce localization for Brazil
description: This topic provides an overview of the localization of Dynamics 365 Commerce for Brazil.
author: josaw
manager: annbe
ms.date: 05/26/2020
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

This topic describes **the scope for the Commerce functionality in Microsoft Dynamics 365 Commerce that are specific to Brazil**. This software includes features and functionality that is being designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that commonly affect retail businesses in Brazil (limited to the scope of Brazilian localization published [here](../../financials/localizations/latam-bra-scope.md)).

However, Microsoft Dynamics doesn't address all laws, regulations, or commercial requirements in Brazil, because laws and regulations vary in the way that they affect organizations. Additional details are available in the [Localization Availability Guide](https://aka.ms/ax-availabilityguide).

## The localization scope for Microsoft Dynamics 365 Commerce available in Brazil provides the following  capabilities:
- Retail product management and calculation of Brazil-specific taxes applicable to sales to final customers, incl. Estimated tax breakdown in printed fiscal receipts
- Generation of electronic fiscal documents NFC-e for retail sales, submission of the electronic fiscal documents via the government’s Sefaz web services, and printing of DANFE NFC-e fiscal receipts.  
- Cancellations of retail sales via the government’s Sefaz web services within the allowed time.
- Generation of electronic fiscal documents NF-e for retail returns, submission of the electronic fiscal documents via the government’s Sefaz web services, and printing of DANFE NF-e fiscal receipts.
- Generation of electronic fiscal documents CF-e (Cupom Fiscal eletrônico) for retail sales in São Paulo and registration of the electronic fiscal documents in the SAT fiscal device. 
- EFT integration for POS, including integration with popular local and global payment providers, support of debit and credit card payments.
- Management of Brazil-specific customer registration numbers from point of sale (POS), including entering, viewing, and modifying the registration numbers of CNPJ/CPF or Foreigner ID, and registration this numbers in NFC-e/NF-e/CF-e and printed receipts. 
- Postponed registration of fiscal documents in case of network failures (offline contingency mode)
- Control of fiscal documents in HQ, NFC-e discard, cancellation by substitution
- Issuing Linked NF-e over all types of registered fiscal documents 
- Support of fiscal documents for retail sales in tax and corporate reporting for legal entities operating in Brazil. 

## In Public Preview and General Availability the following POS-scenarios in brick-and-mortar stores are supported:

1. Cash-and-carry sales of goods
2. Cancellations and returns of cash-and-carry sales of goods
3. Cash-and-carry sales of goods in offline mode - contingency
4. Cancellation by substitution
5. Issuing gift cards, payments by gift cards
	 
## The following capabilities are currently not planned for Public Preview and will only be available upon General Availability of the Commerce localization for Brazil:
- Handling of fiscal customer information.
- Generation and submission of NF-e for returns and linked NF-e.
- Generation and submission of NFC-e/NF-e in contingency mode.
- Generation of CF-e and integration with the SAT device.
- EFT integrations.
 
## The following capabilities are currently planned for post-General Availability of the Commerce localization for Brazil: 
- N-1 support, enabling customers running Microsoft Dynamics AX 2012 R3 in their stores to work with Microsoft Dynamics 365 Commerce headquarters after an upgrade.
- Searching customers by registration numbers in POS.
- Support for Brazil-specific fields, such as tax registration numbers CNPJ/CPF, when merging customer master records in a call center.
- E-commerce capabilities for Brazil.

## Out of Scope :
- PAF-ECF fiscal printers
- ?
