---
title: Tax Reform Overview
description: The article provides the high-level introduction to the Brazil tax reform since 2026
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/14/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Tax reform overview

[!include [banner](../../includes/banner.md)]

This article introduces the Brazil tax reform solution effective in 2026.

It explains how the Advanced Tax Calculation engine supports new tax types and functionality while legacy components stay unchanged during the transition period.

This solution aligns with the timeline and requirements defined by the Brazilian government, in line with Microsoft's current scope.

Starting in 2026, the Advanced Tax Calculation engine supports the new tax types and functionality, and legacy tax components stay unchanged during the transition period.

Learn more about advanced tax calculation in [Tax Calculation overview - Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/localizations/global/global-tax-calcuation-service-overview?context=%2Fdynamics365%2Fcontext%2Ffinance).

Learn more about legacy tax in [Brazil tax overview - Finance | Dynamics 365 | Microsoft Learn](/dynamics365/finance/localizations/brazil/latam-bra-calculate-taxes).


## New Brazilian tax types
- CBS—Contribution on goods and services. Federal: replaces PIS and COFINS (federal contributions).
- IBS—Goods and services tax. States and municipalities: replaces ICMS and ISS.
- IS—Selective tax (sometimes called excise tax or sin tax). Federal: applies to goods or services considered harmful to health or the environment (like alcoholic beverages and sugary drinks).

## Implementation timeline and transition

Complementary Law No. 214/2025 enables CBS, IBS, and Selective Tax (IS). 

The transition period runs from 2026 through 2033. During that time, legacy taxes (ICMS, ISS, PIS, Cofins, IPI) phase out gradually. 

In 2026, low pilot rates for CBS and IBS start along with preparatory obligations. 

By 2033, full implementation ends the legacy taxes and puts CBS and IBS fully in place.

## Versions
We recommend that you import and set up your Tax Calculation configuration with the version that matches your Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Supply Chain Management version.

Finance or Supply Chain Management version	Tax configuration version
10.0.46	Tax Calculation Configuration 47.73.265.46
10.0.45	Tax Calculation Configuration 47.73.265.46
10.0.44	Tax Calculation Configuration 47.73.265.46

## Supported transactions
The following lists the transactions supported in the Brazil tax reform in Advanced tax calculation engine.

* General journals
* Vendor invoice journal
* Free text invoice
* Project
  * Project invoice proposal
   
* Sales
  * Sales quotation
  * Sales order
  * Confirmation
  * Picking list
  * Packing slip
  * Sales invoice
  * Credit note
  * Return order
  * Header miscellaneous charge
  * Line miscellaneous charge
* Purchase
  * Purchase order
  * Confirmation
  * Receipts list
  * Product receipt
  * Purchase invoice
  * Header miscellaneous charge
  * Line miscellaneous charge
  * Credit note
  * Return order
  * Purchase requisition
  * Purchase requisition line miscellaneous charge
  * Request for quotation
  * Request for quotation header miscellaneous charge
  * Request for quotation line miscellaneous charge
* Inventory
  * Transfer order – ship
  * Transfer order – receive


