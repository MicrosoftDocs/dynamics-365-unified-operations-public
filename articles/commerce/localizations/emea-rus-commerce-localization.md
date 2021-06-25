---
# required metadata

title: Commerce localization for Russia
description: This topic provides an overview of the localization of Microsoft Dynamics 365 Commerce for Russia.
author: akviklis
ms.date: 06/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: v-ankvik
ms.search.validFrom: 2021-6-23
ms.dyn365.ops.version: 10.0.21

---
# Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This topic describes the scope of the Microsoft Dynamics 365 Commerce functionality that is specific to Russia. It includes information about features and functionality that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that typically affect retail businesses in Russia (within the scope of the [Russian localization](../../finance/localizations/russia.md)).

However, Commerce doesn't address all laws, regulations, or commercial requirements in Russia, because laws and regulations vary in the way that they affect organizations. For more information, see the [Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck).

## Capabilities of the Commerce localization for Russia

### Scope that is available in Russia

The following features in Commerce headquarters and the point of sale (POS) are available to Commerce customers in Russia:

- Cash management
- Prepayments
- Simplified address format
- Gift cards
- Fiscal printer integration

### Supported scenarios

The following scenarios are supported by Commerce localization for Russia:

- Cash-and-carry sales of goods
- Returns of cash-and-carry sales of goods
- Cash-and-carry sales of goods in offline mode?
- Issuing gift cards and payments by gift cards
- Registering and processing customer orders in the POS
- Posting fiscal documents in retail statements in Commerce headquarters
- Sales via e-Commerce storefronts
- Call center sales

### Fiscal registration for Russia

Fiscal registration is the immediate registration of retail sales per local fiscal laws that are aimed at preventing tax fraud in the retail industry. The main fiscal registration method that is available in Russia is a registration of a retail sale in a special fiscal device named fiscal printer or online cash register that is connected to POS.

Commerce supports fiscal registration via the [Fiscal integration framework](../localizations/fiscal-integration-for-retail-channel.md) and its extensions for specific countries or regions.

## Availability of Commerce localization features for Russia

| Feature                                                                  | General availability (GA) | Post-GA | Not planned |
|--------------------------------------------------------------------------|---------------------------|---------|-------------|
| Cash payments: Process cash payment transactions in retail sales         | X                         |         |             |
| Cash payments: Changes in aggregation                                    | X                         |         |             |
| Prepayments: Customer account deposit and Customer order deposit         | X                         |         |             |
| Prepayments: Cancellation charges and testing of settlement              | X                         |         |             |
| Retail statements in Commerce headquarters                               | X                         |         |             |
| Simplified address format                                                | X                         |         |             |
| Gift cards: Issue gift card, add to gift card                            | X                         |         |             |
| Gift cards: Payment with gift card: settlement, different customers      | X                         |         |             |
| Loyalty program                                                          | X                         |         |             |
| Return controls                                                          | X                         |         |             |
| E-commerce capabilities for Russia?                                      |                           | X       |             |
| N-1 support for upgrade from AX 2012 R3                                  |                           |         | X           |

## Commerce functionality for Russia

Commerce functionality for Russia consists of the following parts:

- Common POS features that are available to customers in all countries or regions.
- Russian-specific features, such as Customer account deposit and Customer order deposit prepayments.

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see the [Commerce home page](../index.md).

### Russian-specific POS features

The following Russian-specific POS features are enabled after the Commerce localization for Russia has been set up and deployed:

- Electronic Fiscal Document for Consumers in Russia
- Customer account deposit and Customer order deposit prepayments
- Prepaymant cancellation charges
- Simplified address format
- Posting and control of electronic fiscal documents

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
