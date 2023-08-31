---
title: Commerce localization for Russia
description: This article provides an overview of the localization of Microsoft Dynamics 365 Commerce for Russia.
author: EvgenyPopovMBS
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Russia
ms.author: josaw
ms.search.validFrom: 2021-06-23
ms.dyn365.ops.version: 10.0.21
ms.search.industry: Retail
---
# Commerce localization for Russia

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This article provides an overview of the localization of Microsoft Dynamics 365 Commerce for Russia and describes the scope of Commerce functionality that is specific to Russia. It includes information about features and functionality that are designed to address specific federal tax, retail, accounting, financial, or statutory reporting laws or regulations that typically affect retail businesses in Russia (within the scope of [Russian localization](../../finance/localizations/russia.md)).

Because laws and regulations vary in the way that they affect organizations, Commerce doesn't address all laws, regulations, or commercial requirements in Russia. For more information, see the [Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck).

To learn about point of sale (POS) features that are available to customers in all countries or regions, see the [Commerce home page](../welcome.md).

## Capabilities of Commerce localization for Russia

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
- Prepayments and posting of VAT for prepayments in Commerce headquarters.
- Prepayment cancellation charges.
- Simplified address format.

### Fiscal registration for Russia

Fiscal registration is the immediate registration of retail sales per local fiscal laws that are aimed at preventing tax fraud in the retail industry. The main fiscal registration method available in Russia entails using a specialized device called a fiscal printer or online cash register that is connected to POS.

Commerce functionality for Russia includes a [sample integration](./rus-fpi-sample.md) of the point of sale (POS) with a fiscal printer. This sample extends the [fiscal integration functionality](./fiscal-integration-for-retail-channel.md) and supports the application programming interface (API) of fiscal printers from [ATOL](http://integration.atol.ru/). It enables communication with a fiscal printer that is connected via a communication (COM) port by using a native software driver. The sample is provided in the form of source code and is part of the Retail software development kit (SDK).

## Availability of Commerce localization features for Russia

| Feature | Released | May be added in future releases | Not planned |
|-|:-:|:-:|:-:|
| A sample of the integration of the POS with a fiscal printer | X |  |  |
| Processing of cash payments using petty cash journals in Commerce headquarters | X |  |  |
| Customer account deposit and customer order deposit prepayments | X |  |  |
| Processing of prepayments and posting of VAT for prepayments in Commerce headquarters | X |  |  |
| Prepayment cancellation charges | X |  |  |
| Simplified Russian address format for retail customers | X |  |  |
| Processing of issued gift cards as prepayments, along with related fiscal printer functionality |  | X |  |
| Payment integration |  | X |  |
| E-commerce capabilities for Russia |  | X |  |
| Support of customer orders in fiscal printer integration |  | X |  |
| Cash collection |  | X |  |
| Processing of loyalty point redemptions as price discounts in retail transactions, along with related fiscal printer functionality |  | X |   |
| Restrictions on returns of items that belong to selected item groups |  | X |  |
| Aggregation of sales and returns that are registered within one shift |  | X |  |
| Gift card policies |  |  | X |
| Pricing enhancements |  |  | X |
| Labeling enhancements |  |  | X |
| N-1 support for upgrade from AX 2012 R3 |  |  | X |

## Additional resources

[Overview of fiscal integration for Commerce channels](fiscal-integration-for-retail-channel.md)

[Russian globalization overview](../../finance/localizations/russia.md)

[Product localization and translation availability guide](https://aka.ms/dynamics_365_international_availability_deck)

[ATOL documentation](http://integration.atol.ru/)

[Petty cash management for Commerce for Eastern Europe](emea-eeu-petty-cash-for-retail.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
