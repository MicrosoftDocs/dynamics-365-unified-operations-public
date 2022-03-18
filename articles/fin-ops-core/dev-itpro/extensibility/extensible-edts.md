---
title: Extended data types
description: This topic provides information about extended data types (EDTs).
author: MichaelFruergaardPontoppidan
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Extended data types
[!include [banner](../includes/banner.md)]

Extended data types (EDTs) have a rich extension model that lets extenders change specific behaviors.

To provide an extensible solution, keep the following guidelines in mind when you work with EDTs.

## Label/Help text
Labels and Help text properties can be changed by an extension, but only one value can remain. If multiple solutions change the label of the same EDT, the various labels are, in functional terms, mutually exclusive. Therefore, those labels can't all be installed on the same system.

## String size
String size can be defined only on root EDTs. The system will use the largest value that is defined across the EDT and its extensions.

For derived EDTs, string size can't be changed by an extension, because the IS-A relationship between the EDTs will be broken.

Assignments to string EDTs will truncate the string to match the defined string size.

## Extends
The **extends** property can't be changed by an extension. Any change that is made to this property after release will cause a breaking change. Therefore, you must make sure that the property is set correctly before release.

If you set this property, neither you nor extenders will be able to make changes to the string size later. 

Avoid unnecessary dependencies. For example, don't extend generic EDTs such as Name and Description.

## Number of decimals
The **Number of decimals** property can't be changed by an extension.

If you set this property to **True**, extenders can change the number of decimal places. 

If you set this property to **True**, make sure that the following conditions are met:

+ All truncation logic honors the number of decimal places that is specified on the EDT, so that no implicit or hardcoded rounding will occur.
+ The value isn't assigned to other incompatible EDTs that don't correctly handle rounding.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]