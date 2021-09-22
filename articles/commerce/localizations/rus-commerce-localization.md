---
# required metadata

title: Commerce localization for Russia
description: This topic provides an overview of the localization of Microsoft Dynamics 365 Commerce for Russia.
author: akviklis@microsoft.com
ms.date: 09/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 2021-6-23
ms.dyn365.ops.version: 10.0.21

---
# Commerce localization for Russia

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This topic provides an overview of the localization of Microsoft Dynamics 365 Commerce for Russia and describes the scope of Commerce functionality that is specific to Russia. It includes information about features and functionality that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that typically affect retail businesses in Russia (within the scope of [Russian localization](../../finance/localizations/russia.md)).

Because laws and regulations vary in the way that they affect organizations, Commerce doesn't address all laws, regulations, or commercial requirements in Russia. For more information, see the [Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck).

## Capabilities of Commerce localization for Russia

### Feature availability in Russia

Features in Commerce headquarters and the point of sale (POS) that are available to Commerce customers in Russia include:

- Cash management.
- Prepayments.
- Simplified address format.
- Gift cards.
- Fiscal printer integration.

### Supported scenarios

Scenarios that are supported by Commerce localization for Russia include:

- Cash-and-carry sales of goods.
- Returns of cash-and-carry sales of goods.
- Issuing gift cards and payments by gift cards.
- Registering and processing customer orders in the POS.
- Posting fiscal documents in retail statements in Commerce headquarters.
- Processing of prepayments and posting of value-added tax (VAT) for prepayments in Commerce headquarters.
- Sales via e-commerce storefronts.
- Call center sales.

### Fiscal registration for Russia

Fiscal registration is the immediate registration of retail sales per local fiscal laws that are aimed at preventing tax fraud in the retail industry. The main fiscal registration method available in Russia entails using a specialized device called a fiscal printer or online cash register that is connected to POS.

Commerce functionality for Russia includes a [sample integration](./rus-fpi-sample.md) of the point of sale (POS) with a fiscal printer. This sample extends the [fiscal integration functionality](./fiscal-integration-for-retail-channel.md) and supports the application programming interface (API) of fiscal printers from [ATOL](http://integration.atol.ru/). It enables communication with a fiscal printer that is connected via a communication (COM) port by using a native software driver. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

## Availability of Commerce localization features for Russia

| Feature | General availability (GA) | Post-GA | Not planned |
|-|-|-|-|
| Processing of cash payments using petty cash journals in Commerce headquarters | X |  |  |
| Processing of prepayments and posting of VAT for prepayments in Commerce headquarters | X |  |  |
| Handling of customer returns according to local requirements | X |  |  |
| A sample of the integration of the POS with a fiscal printer | X |  |  |
| Support of customer orders in fiscal printer integration |  | X |  |
| Processing of issued gift cards as prepayments, along with related fiscal printer functionality |  | X |  |
| Processing of loyalty point redemptions as price discounts in retail transactions, along with related fiscal printer functionality |  | X |  |
| Payment integration |  | X |  |
| E-commerce capabilities for Russia |  | X |  |
| Cash collection |  | X |  |
| Restrictions on returns of items that belong to selected item groups |  |  | X |
| Aggregation of sales and returns that are registered within one shift |  |  | X |
| Gift card policies |  |  | X |
| Pricing enhancements |  |  | X |
| Labeling enhancements |  |  | X |
| N-1 support for upgrade from AX 2012 R3 |  |  | X |

## Commerce functionality for Russia

Commerce functionality for Russia consists of the following:

- Common POS features that are available to customers in all countries or regions.
- Russia-specific features such as cash payments using petty cash journals, prepayments and posting of VAT for prepayments, and a sample integration of the POS with a fiscal printer.

### Common POS features

To learn about POS features that are available to customers in all countries or regions, see the [Commerce home page](../index.md).

### Eastern Europe-specific POS features


The following Eastern Europe–specific POS features are enabled after the Commerce localization for Russia has been set up:

- Customer cash payments according to the retail store cash management requirements.
- Cash payments that use petty cash journals in Commerce headquarters.
- Retail transactions that are aggregated according to specific criteria or posted separately.


For more information, see [Petty cash management for Commerce for Eastern Europe](emea-eeu-petty-cash-for-retail.md).

### Russia-specific POS features

The following Russia-specific POS features are enabled after the Commerce localization for Russia has been set up:

- A sample integration of the POS with a fiscal printer.
- Customer account deposit and customer order deposit prepayments.
- Support of customer orders in fiscal printer integration.
- Prepayments and posting of VAT for prepayments in Commerce headquarters.
- Prepayment cancellation charges.
- Payment integration.
- Simplified address format.
- Processing of issued gift cards as prepayments, along with related fiscal printer functionality.
- Processing of loyalty point redemptions as price discounts in retail transactions, along with related fiscal printer functionality.
- Posting and control of electronic fiscal documents in Commerce headquarters.

## Additional resources

[Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md)

[Russian globalization overview](../../finance/localizations/russia.md)

[Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck)

[ATOL documentation](http://integration.atol.ru/)

[Petty cash management for Commerce for Eastern Europe](emea-eeu-petty-cash-for-retail.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
