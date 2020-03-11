---
# required metadata

title: Integrated tax
description: This topic describes the integration of tax data between Finance and Operations and Common Data Service.
author: robinarh
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: 
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Integrated tax

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

Tax setup data defines the setup for both indirect taxes (VAT, GST, Sales tax) and withholding tax. It describes the tax calculation rule, tax rate, tax accounting, settlement, and other concepts.

## Templates

Tax data includes a collection of entity maps that work together during data interaction, as shown in the following table.

| Finance and Operations apps | Model-driven apps in Dynamics 365 | Description |
-------------------------|---------------------------------
Tax codes                   | msdyn\_taxcodes.md | 
Tax groups                 | msdyn\_taxgroups.md | 
Tax item groups             | msdyn\_taxitemgroups.md | 
Tax Exemptions             | msdyn\_taxexemptcodes.md | 
Tax Authorities             | msdyn\_taxauthorities.md | 
Withholding tax codes       | msdyn\_withholdingtaxcodes.md | 
Withholding tax groups     | msdyn\_withholdingtaxgroups.md | 
Tax Ledger Account Group | msdyn\_taxpostinggroups     | 

[!include [banner](../../includes/dual-write-symbols.md)]

[!include [Tax groups](includes/TaxGroupEntity-msdyn-taxgroups.md)]

[!include [Tax item groups](includes/TaxItemGroupHeadings-msdyn-taxitemgroups.md)]

[!include [Tax Exemptions](includes/CdsTaxExemptCodes-msdyn-taxexemptcodes.md)]

[!include [Tax Authorities](includes/SalesTaxAuthorities-msdyn-taxauthorities.md)]

[!include [Withholding tax codes](includes/WithholdingCode-msdyn-withholdingtaxcodes.md)]

[!include [Withholding tax groups](includes/WithholdingGroups-msdyn-withholdingtaxgroups.md)]

[!include [Tax Ledger Account Group](includes/TaxPostingGroupsV2--msdyn-taxpostinggroups.md)]

