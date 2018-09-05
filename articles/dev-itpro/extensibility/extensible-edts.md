---
# required metadata

title: Extended data types
description: This article provides information about extended data types (EDTs).
author: mfp
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
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Extended data types

Extended data types (EDTs) have a rich extension model, which gives extenders control to change certain behaviors.  

To provide an extensible solution, keep the following in mind when workign with EDTs:

## Label/Help text
Labels and help text properties can be changed by an extension, but only one value can remain. If multiple solutions change the label of the same extended data type, then functionally, they would be mutually exclusive, meaning noone would install both on the same system.

## String size
String size can only be defined on root EDTs. The system will use the largest value defined across the EDT and its extensions.
String size can't be changed by an extension for derived EDTs because it would break the IS-A relationship between the EDTs.
Assignments to string EDTs will truncate the string to match the defined string size.

## Extends
This property can't be changed by an extension and results in a breaking change if it is changed after release. This means that you must ensure ensure it is set correctly prior to release. 
If you set this property, any future changes to the string size will not be allowed either by you or extenders. 
Additionally, avoid unnecessary dependencies like extending generic extended data types such as Name and Description.

## Extending the nunber of decimals
The property, **Number of decimals** can't be changed by an extension. Setting the property to **True** will allow extenders to change the number of decimals. 

If you set this property to **True**, ensure that:
+ All truncation logic would honor the number of decimals specified on the EDT meaning that no implicit or hard-coded rounding would occur.
+ The value is not assigned to other incompatible EDTs without proper handling of rounding.
