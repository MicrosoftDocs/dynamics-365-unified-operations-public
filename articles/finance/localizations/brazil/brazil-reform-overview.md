---
title: Tax Reform Overview
description: Learn how the Advanced Tax Calculation engine supports new tax types in the Brazil tax reform effective in 2026
author: yanansong
ms.author: yanansong
ms.topic: overview
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Tax reform overview

[!include [banner](../../includes/banner.md)]

This article provides and overview of the Brazil tax reform solution effective in 2026. It explains how the Advanced Tax Calculation engine supports new tax types and functionality while legacy components remain unchanged during the transition period.

This solution aligns with the timeline and requirements defined by the Brazilian government and aligns with Microsoft's current scope.

In 2026, the Advanced Tax Calculation engine supports new tax types and functionality, and legacy tax components remain unchanged during the transition period.

Learn more about advanced tax calculation in [Tax Calculation overview - Finance | Dynamics 365](/dynamics365/finance/localizations/global/global-tax-calcuation-service-overview?context=%2Fdynamics365%2Fcontext%2Ffinance).

Learn more about legacy tax in [Brazil tax overview - Finance | Dynamics 365](/dynamics365/finance/localizations/brazil/latam-bra-calculate-taxes).

## New Brazilian tax types

Brazil now has the following new tax types:

- CBS—contribution on goods and services. Federal: replaces PIS and COFINS (federal contributions).
- IBS—goods and services tax. States and municipalities: replaces ICMS and ISS.
- IS—selective tax (sometimes called excise tax or sin tax). Federal: applies to goods or services considered harmful to health or the environment, like alcoholic beverages, sugary drinks, and tobacco products.

## Implementation timeline and transition

Complementary Law No. 214/2025 enables CBS, IBS, and selective tax (IS). 

The transition period runs from 2026 through 2033. During that time, legacy taxes (ICMS, ISS, PIS, Cofins, and IPI) gradually phase out. 

In 2026, low pilot rates for CBS and IBS begin, along with preparatory obligations. 

By 2033, full implementation ends the legacy taxes and puts CBS and IBS fully in place.

## Versions

Import and set up your Tax Calculation configuration with the version that matches your Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Supply Chain Management version.

| Finance or Supply Chain Management version | Tax configuration version |
|--------------------------------------------|------------------------------------------|
| 10.0.46 <br> Build 10.0.2428.58             | - Tax Data Model: 50.                   <br>- Tax Calculation Data Model: 50.78  <br>- FNO Model Mapping: 50.78.48         <br>- Tax Calculation Configuration: 50.78.269. <br>- Tax Calculation Data Model (Brazil): 50.78.21. <br>- FNO Model Mapping (Brazil): 50.78.48.21. <br>- Tax Calculation Configuration (Brazil): 50.78.269.55. |
| 10.0.45 <br> Build 10.0.2345.124            | - Tax Data Model: 50                    <br>- Tax Calculation Data Model: 50.78  <br>- FNO Model Mapping: 50.78.48         <br>- Tax Calculation Configuration: 50.78.269 <br>- Tax Calculation Data Model (Brazil): 50.78.21 <br>- FNO Model Mapping (Brazil): 50.78.48.21 <br>- Tax Calculation Configuration (Brazil): 50.78.269.55 |
| 10.0.44 <br> Build 10.0.2263.182           | - Tax Data Model: 50                    <br>- Tax Calculation Data Model: 50.78  <br>- FNO Model Mapping: 50.78.48         <br>- Tax Calculation Configuration: 50.78.269 <br>- Tax Calculation Data Model (Brazil): 50.78.21 <br>- FNO Model Mapping (Brazil): 50.78.48.21 <br>- Tax Calculation Configuration (Brazil): 50.78.269.55 |

## Supported transactions

The following list shows the transactions that the advanced tax calculation engine supports for the Brazil tax reform.

1. General journals
1. Vendor invoice journal
1. Free text invoice
1. Project
   1. Project invoice proposal
1. Sales
   1. Sales quotation
   1. Sales order
   1. Confirmation
   1. Picking list
   1. Packing slip
   1. Sales invoice
   1. Credit note
   1. Return order
   1. Header miscellaneous charge
   1. Line miscellaneous charge
1. Purchase
   1. Purchase order
   1. Confirmation
   1. Receipts list
   1. Product receipt
   1. Purchase invoice
   1. Header miscellaneous charge
   1. Line miscellaneous charge
   1. Credit note
   1. Return order
   1. Purchase requisition
   1. Purchase requisition line miscellaneous charge
   1. Request for quotation
   1. Request for quotation header miscellaneous charge
   1. Request for quotation line miscellaneous charge
1. Inventory
   1. Transfer order—ship
   1. Transfer order—receive

## Synchronization

Because the new tax reform is part of the advanced tax calculation engine, synchronization between the advanced calculation and the legacy tax system remains consistent with the current behavior.

Learn more in [global-master-data-sync-tax-calculation](../global/global-master-data-sync-tax-calculation-service-finance.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
