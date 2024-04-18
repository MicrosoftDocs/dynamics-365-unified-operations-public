---
title: VAT declaration for Lithuania
description: This article explains how to set up a VAT declaration for legal entities in Lithuania.
author: liza-golub
ms.date: 04/18/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Lithuania
ms.author: egolub
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
---

# VAT declaration for Lithuania

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Lithuania in the official XML format. It also describes how to preview the VAT declaration in Microsoft Excel.

The VAT declaration feature for Lithuania supports filing a VAT return for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a VAT group in the same system database. For each version of Finance that's listed in the following table, these capabilities are supported as of the specified build number.

## VAT declaration overview

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Lithuania. 
Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes 
(sales tax code, tax classifier) with the lookup result of the **Report field lookup** lookup field. 
In the following table, the "Lookup result" column shows the lookup result that's preconfigured for a specific VAT declaration field (tag) in the VAT declaration format. 
Use this information to correctly associate tax transaction attributes with the lookup result and then with the field (tag) of the VAT declaration.



## Set up sales tax authorities

To generate a VAT declaration in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. 
On the **Sales tax authorities** page, in the **Report layout** field, select **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for sales tax codes.
