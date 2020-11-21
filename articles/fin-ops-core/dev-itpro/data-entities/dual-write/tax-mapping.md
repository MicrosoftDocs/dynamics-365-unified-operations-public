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
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: rhaertle
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Integrated tax

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]



Tax setup data defines the setup for both indirect taxes (VAT, GST, Sales tax) and withholding tax. It describes the tax calculation rule, tax rate, tax accounting, settlement, and other concepts.

## Templates

Tax data includes a collection of entity maps that work together during data interaction, as shown in the following table.

Finance and Operations apps | Model-driven apps in Dynamics 365 | Description |
-------------------------|---------------------------------|----|
Item sales tax group | msdyn_taxitemgroups |
Sales tax authorities | msdyn_taxauthorities |
Sales tax exempt code entity CDS | msdyn_taxexemptcodes |
Sales tax groups | msdyn_taxgroups |
Sales tax ledger posting groups V2 | msdyn_taxpostinggroups |
Withholding tax codes | msdyn_withholdingtaxcodes |
Withholding tax groups | msdyn_withholdingtaxgroups | 


[!include [banner](../../includes/dual-write-symbols.md)]

[!include [Tax item groups](includes/TaxItemGroupHeadings-msdyn-taxitemgroups.md)]

[!include [Tax Authorities](includes/SalesTaxAuthorities-msdyn-taxauthorities.md)]

[!include [Tax Exemptions](includes/CdsTaxExemptCodes-msdyn-taxexemptcodes.md)]

[!include [Tax groups](includes/TaxGroupEntity-msdyn-taxgroups.md)]

[!include [Tax Ledger Account Group](includes/TaxPostingGroupsV2--msdyn-taxpostinggroups.md)]

[!include [Withholding tax codes](includes/WithholdingCode-msdyn-withholdingtaxcodes.md)]

[!include [Withholding tax groups](includes/WithholdingGroups-msdyn-withholdingtaxgroups.md)]

