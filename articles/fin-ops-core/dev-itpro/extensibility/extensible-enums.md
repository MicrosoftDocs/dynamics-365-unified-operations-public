---
title: Write extensible enums
description: This topic provides information about how to write extensible enums.
author: smithanataraj
ms.date: 09/26/2018
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
ms.author: smnatara
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible enums

[!include [banner](../includes/banner.md)]

An enumeration (enum) is made extensible by setting the following enum properties:

- Is Extensible = True
- UseEnumValue = No

If you set these properties, downstream implementors can extend the enum with more elements. The values of the elements are determined at deployment time and won't be identical across systems. However, the following behavior is ensured:

+ Data upgrade scripts aren't required. Enum values are persisted in the database, regardless of the enum that is extended. Therefore, when an enum is made extensible, the enum values that are used on any system will prevail.
+ The first element in the enum gets a value of 0 (zero). Therefore, an extensible enum can still be used with the **not** operator. The only exception is when the first element of the enum had a non-zero value before the enum was made extensible.
	
## Using extensible enums in code
Because enum values are no longer controlled by the developer, there is no certainty about the enum values. When you use extensible enums in code, remember that extensible enums can't be used in comparisons. For example, **MyEnum::Value1 \> MyEnum::Value2**.

Also, look for any conversions between integers and enums. For example, modeled ranges in views and queries, and queries that are created from code by using comparisons, such as **\<** and **\>** or by using hardcoded integer values in comparisons.

When the model and all dependent models are compiled, the comparisons and conversions to integers will be detected by the compiler as errors.
	
Make sure that logic where the enum values are used is extracted in **smaller methods**. In that way, an extension that uses Chain of Command (CoC) can handle the enum values that are added.

For **construct** methods where the instantiation is based on enum values, replace switch blocks with **SysExtension** wherever such a replacement is possible. In other cases, make sure that the default block is extensible. For an example, see the **PurchRFQCaseCopying** class.

If the enum is used in **switch blocks**, avoid having default blocks that either have or don't have throws that aren't extensible. 
When there are **long switch case blocks** or **if...else blocks** for the enum values, consider creating a class hierarchy to handle specific logic that is related to the enum. For an example, see the **PriceGroupTypeTradeAgreementMapping** class hierarchy.

Use the **in** keyword for query ranges that use the enum values, and make the container that the **in** keyword uses extensible.

## Potential issues
Some enums require the elements to have a certain order or value, and cannot be made extensible. This could be status enums, where the values represent a logical progressive sequence, like: Draft, Approved, Completed, or Archived. It could also be enums where the values must have a fixed integral value to match another artifact, like another enum or a tabpage control's number.   

Some enums have many elements. Enums support up to 250 elements. If your enum has many elements, such as more than 100, consider redesigning the solution instead of making the enum extensible. If the enum is extensible, then adding more elements in the future might break customers's combined solution as the addition might exceed the limit.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]