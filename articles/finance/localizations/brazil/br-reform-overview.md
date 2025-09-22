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

# Tax Reform Overview 

[!include [banner](../../includes/banner.md)]

The article provides a high-level introduction to the Brazil Tax Reform solution starting from 2026. 

It outlines the context of the reform and explains how the Advanced Tax Calculation engine supports new tax types and functionality, while legacy components remain unchanged during the transition period.

Our solution ensures compliance with the timeline and requirements defined by the Brazilian government , in line with Microsoft current scope.

From 2026 onward, the new tax types and functionality are supported by the Advanced Tax Calculation engine, while legacy tax components remain unchanged during the transition period. 

For more details for advanced tax calculation, see  [Tax Calculation overview - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/global-tax-calcuation-service-overview?context=%2Fdynamics365%2Fcontext%2Ffinance)
For more details for legacy tax, see [Brazil tax overview - Finance | Dynamics 365 | Microsoft Learn](https:Tax overview//learn.microsoft.com/en-us/dynamics365/finance/localizations/brazil/latam-bra-calculate-taxes)

## Brazilian new tax types
CBS--Contribution on Goods and Services
Federal , Replace PIS and CONFIS (Federal contributions)
IBS--Good and Services Tax
States & Municipalities, Replace ICMS and ISS
IS--Selective Tax (sometimes referred to as Excise tax /Sin tax)
Federal-Applies to goods or services deemed harmful to health or the enviornment (e.g. alcoholic beverages, sugary drinks, etc)

## Implementation Timeline & Transition

The law enabling CBS, IBS, and Selective Tax (IS) is Complementary Law No. 214/2025. 

Transition period is from 2026 to 2033. During that time, legacy taxes (ICMS, ISS, PIS, Cofins, IPI) will be gradually phased out. 

In 2026, pilot/initial rates will begin (very low) for CBS and IBS, plus preparatory obligations. 

By 2033, full implementation is expected: legacy taxes abolished; CBS/IBS fully in place.

## Versions
We recommend that you import and set up your Tax Calculation configuration with the version that matches your Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Supply Chain Management version.

Finance or Supply Chain Management version	Tax configuration version
10.0.46	Tax Calculation Configuration 47.73.265.46
10.0.45	Tax Calculation Configuration 47.73.265.46
10.0.44	Tax Calculation Configuration 47.73.265.46

## Supported transactions
The following lists the transactions supported in the Brazil tax reform in Advanced tax calculation engine.

 <p><ul><li>Invoice register<br><li>Invoice approval<br><li>Invoice pool 

 <li>Periodic journals

 <li>Vendor payment journal<br><li>Customer payment journal 
  
 <li>General journals<br><li>Vendor invoice journal
 <li>Free text invoice
  
 <p>Project<ul><li>Project invoice proposal<br> <li>Journals (Hour/Expense/Item/Fee)<br><li> Project quotations<br><li> Intercompany customer invoice<br> <li>Microsoft Dynamics 365 Project Operations integration journal 
 
 Sales</p><li>Sales quotation</li><li>Sales order</li><li>Confirmation</li><li>Picking list</li><li>Packing slip</li><li>Sales invoice</li><li>Credit note</li><li>Return order</li><li>Header miscellaneous charge</li><li>Line miscellaneous charge</li></ul><p>Purchase</p><ul><li>Purchase order</li><li>Confirmation</li><li>Receipts list</li><li>Product receipt</li><li>Purchase invoice</li><li>Header miscellaneous charge</li><li>Line miscellaneous charge</li><li>Credit note</li><li>Return order</li><li>Purchase requisition</li><li>Purchase requisition line miscellaneous charge</li><li>Request for quotation</li><li>Request for quotation header miscellaneous charge</li><li>Request for quotation line miscellaneous charge</li></ul><p>Inventory</p><ul><li>Transfer order – ship</li><li>Transfer order – receive</li></ul>|


