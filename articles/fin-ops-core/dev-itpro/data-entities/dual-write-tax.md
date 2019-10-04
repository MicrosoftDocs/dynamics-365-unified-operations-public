---
# required metadata

title: Integrated tax
description: This topic describes the integration of tax data between Finance and Operations and Common Data Service.
author:  
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

## Integrated tax

[!include [banner](../includes/banner.md)]

[!include [preview](../includes/preview-banner.md)]

When a business ecosystem is made up of Dynamics 365 applications including Dynamics 365 for Finance and Operations and Dynamics 365 for Customer Engagement, it's natural for customers to use a shared tax setup to enable the unified product experience. 
For example, customers manage their field service business with Dynamics 365 for Field Service, and process invoicing, payment, tax payment, tax return etc. in Dynamics 365 for Finance and Operations. With shared tax setup, a work order in Field Service can be synced with a sales order in Finance and Operations with tax. On the other hand, regardless of where the tax setup record originates, it's integrated behind the scenes across application boundaries and infrastructure differences. Integrated tax setup helps handle multi-mastering scenarios and provides a comprehensive view of the tax setup to the Dynamics 365 application suite.

## Data flow

Tax code is a well-defined concept in both Finance and Operations and Customer Engagement. In Finance and Operations, there are Sales tax group and Item Sales tax group which are attached to party and item, while in Customer Engagement, tax group is just a special tax code.

## Templates

Tax data includes ... A collection of entity maps works together during data interaction, as shown in the following table.

Finance and Operations   | Customer Engagement application
-------------------------|---------------------------------
Tax codes	               | msdyn\_taxcodes.md
Tax groups	             | msdyn\_taxgroups.md
Tax item groups	         | msdyn\_taxitemgroups.md
Tax Exemptions	         | msdyn\_taxexemptcodes.md
Tax Authorities	         | msdyn\_taxauthorities.md
Withholding tax codes	   | msdyn\_withholdingtaxcodes.md
Withholding tax groups	 | msdyn\_withholdingtaxgroups.md
Tax Ledger Account Group | msdyn\_taxpostinggroups	

[!include [banner](../includes/dual-write-symbols.md)]

[!include [Tax codes](dual-write/TaxCodes-msdyn-taxcodes.md)]

[!include [Tax groups](dual-write/TaxGroupEntity-msdyn-taxgroups.md)]

[!include [Tax item groups](dual-write/TaxItemGroupHeadings-msdyn-taxitemgroups.md)]

[!include [Tax Exemptions](dual-write/CdsTaxExemptCodes-msdyn-taxexemptcodes.md)]

[!include [Tax Authorities](dual-write/SalesTaxAuthorities-msdyn-taxauthorities.md)]

[!include [Withholding tax codes](dual-write/WithholdingCode-msdyn-withholdingtaxcodes.md)]

[!include [Withholding tax groups](dual-write/WithholdingGroups-msdyn-withholdingtaxgroups.md)]

[!include [Tax Ledger Account Group](dual-write/TaxPostingGroupsV2--msdyn-taxpostinggroups.md)]

