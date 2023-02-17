--- 
# required metadata 
 
title: Set up sales tax codes
description: This article explains how to set up sales tax codes in Dynamics 365 Finance. 
author: twheeloc
ms.date: 09/27/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxTable, TaxData   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up sales tax codes

[!include [banner](../../includes/banner.md)]

This article explains how to set up sales tax codes. Sales tax codes are created for every indirect tax or duty that the legal entity is obligated to calculate, collect, and pay to sales tax authorities.

This task uses the USMF demo company.

1. Go to **Navigation pane > Tax > Indirect taxes > Sales tax > Sales tax codes**.
2. Select **New**.
3. In the **Sales tax code** field, type a value.
4. In the **Name** field, type a value.
5. Select a **Settlement period** by opening the pull-down list to specify which Sales tax authority and in which intervals this sales tax needs to be reported and paid.
6. Select a **Ledger posting group** to specify the main accounts to post sales tax to the general ledger.
7. Expand the **Calculation** FastTab. This includes multiple fields that control how sales tax amounts will be calculated. Fill these fields out as needed.  
8. On the **Action Pane** at the top of the interface, select **Sales tax code**.
9. Select **Values**.
10. Enter the value for this tax code in the **value** column.

    On the **Calculation** FastTab, in the **Origin** field, if **Amount per unit** is selected, the value will be multiplied by the quantity on the transaction to calculate the sales tax amount.  If the tax code is not a unit-based tax, the value is a percentage that is applied on the Origin for this tax code to calculate the sales tax amount.     

11. Select **Save**.
12. Close the page.
13. Select **Save**.

As of Microsoft Dynamics 365 Finance version 10.0.22, if you're using the [Tax service](../../localizations/global-tax-calcuation-service-overview.md), and the [**Support multiple VAT registration numbers**](../../localizations/emea-multiple-vat-registration-numbers.md) feature is enabled in the **Feature management** workspace, you can use **Type of tax** field to specify type of the tax code. The following values are available:

- Standard VAT
- Reduced VAT
- VAT 0%
- Excise
- Other

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
