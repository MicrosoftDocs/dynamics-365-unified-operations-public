---
# required metadata

title: Microsoft Dynamics 365 - Translation Service
description: The Microsoft Dynamics 365 - Translation Service (DTS) is designed to enhance the partners and ISVs translation experience of their solutions or when adding a new language for supported Dynamics products
author: kfend
manager: AnnBe
ms.date: 09/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 6154
ms.assetid: ejchoGIT
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Microsoft Dynamics 365 - Translaion Service Overview

[!include[banner](../includes/banner.md)]
Microsoft Dynamics 365 - Translation Service (DTS) is designed to enhance the partners and ISVs translation experience of their solutions or when adding a new language for supported Dynamics products.  

DTS uses custom trained machine translation(MT) system for Microsoft’s GA languages to maximize the quality of translation output.  DTS also supports recycling of the translation from the linguistic assets so that there is no need to translate the same string again.

Here is a high-level view of how the service works:
 
## Recycling of existing translation
The recycling is only enabled when a user uploads the XLIFF translation memory(TM) zip file.  Please refer to the XLIFF TM zip file section for more details.

## Custom trained MT system
DTS uses Microsoft Translator Hub(MT Hub) from Microsoft Research to customize the MT system for the Dynamics products.
The use of custom trained MT system is limited to the Microsoft’s GA languages unless the user upload the XLIFF TMs that contains more than 10,000 translation units (TUs).  In such case, DTS will create a custom trained MT specific to the request.

## Supported products
DTS currently supports the following product versions.  

Product Name |	Version |	File format |	Remark
--- | --- | --- | ---
Dynamics AX 2012	| All versions	| *.ktd, *.ald	|
Dynamics for Finance and Operations, Enterprise edition | All versions |	*.label.txt	|
Dynamics CRM	| 2011~2015 |	*.resx	|
Dynamics NAV | 2013~2017	| *.etx, *.stx, *.resx, *.txt, *.xml |	*.txt amd *xml are in NAV specific format

