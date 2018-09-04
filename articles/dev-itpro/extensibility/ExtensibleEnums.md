---
# required metadata

title: Writing extensible enums
description: This article how to write extensible enums.
author: Smitha Nataraj
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: Smitha Nataraj
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Extensible Enums

An enum is made extensible by setting the following properties on the enum:
+ Is Extensible = True
+ UseEnumValue = No.
	
> [!NOTE]
> After PU 21, the UseEnumValue is hidden and is implicitly set.

This will enable downstream implementors to extend the enum with more elements. The values of the elements are determined at deployment time, and will not be identical across systems.  However, the following is guaranteed:
	1. Data upgrade scripts are not required.Enum values are persisted in the data base - regardless of the enum being extensible.  This implies that enum values being used on any system, will prevail when making the enum extensible.
	2. The first element in the enum will get value zero
	The implies that an extensible enum can still be used with the 'not' operator; the only exception being that the first element of the enum had a non-zero value before being made extensible.
	
## Using extensible enums in code:

Since enum values are no longer controlled by the developer, there is no certainty on the enum values. Some of the things to look out for when using extensible enums in code are:

+ Extensible enums **cannot be used in comparisons**. Example MyEnum::Value1 > MyEnum::Value2
+ **Conversions between integer and enum**
  - Modeled ranges in views and queries, and queries created from code: 
      - Using comparisons, like <, >, .. 
      - Using hardcoded integer values in comparisons 
  - Compiling the model and all dependent models will flag the above.
	
+ Ensure that logic where the enum values are used are extracted out in **smaller methods**, allowing an extension using chain-of-command to handle the added enum values.
+ For **construct** methods where the instantiation is based on enum values, replace switch blocks with SysExtension where possible. In other cases, ensure that the default block is extensible.Example: see ```PurchRFQCaseCopying```
+ If the enum is used in **switch blocks**, avoid having default blocks with/without throws that are not extensible. 
+ When there are **long switch case blocks or if..else blocks** for the enum values, consider creating a class hierarchy to handle specific logic related to the enum. Example: See class hierarchy PriceGroupTypeTradeAgreementMapping
+ Use the **'in' keyword for query ranges using the enum values**, and make the container used by the 'in' keyword extensible.
