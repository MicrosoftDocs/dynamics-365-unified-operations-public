---
title: Write extensible enums
description: Learn about how to write extensible enums, including an overview of using extensible enums in code and potential issues.
author: smithanataraj
ms.author: smnatara
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Write extensible enums

[!include [banner](../includes/banner.md)]

Make an enumeration (enum) extensible by setting the following enum properties:

- `Is Extensible` = `True`
- `UseEnumValue` = `No`

When you set these properties, downstream implementers can extend the enum with more elements. The values of the elements are determined at deployment time and aren't identical across systems. However, the following behavior is ensured:

- Data upgrade scripts aren't required. Enum values are persisted in the database, regardless of the enum that is extended. Therefore, when you make an enum extensible, the enum values that are used on any system prevail.
- The first element in the enum gets a value of 0 (zero). Therefore, you can still use an extensible enum with the **not** operator. The only exception is when the first element of the enum had a non-zero value before you made the enum extensible.

## Using extensible enums in code

Because developers no longer control enum values, you can't be certain about the enum values. When you use extensible enums in code, remember that you can't use extensible enums in comparisons. For example, **MyEnum::Value1 \> MyEnum::Value2** isn't supported.

Also, look for any conversions between integers and enums. For example, modeled ranges in views and queries, and queries that are created from code by using comparisons, such as **\<** and **\>**, or by using hardcoded integer values in comparisons.

When you compile the model and all dependent models, the compiler detects the comparisons and conversions to integers as errors.

Make sure you extract the logic where the enum values are used into **smaller methods**. By using this approach, an extension that uses Chain of Command (CoC) can handle the enum values that you add.

For **construct** methods where the instantiation is based on enum values, replace switch blocks with **SysExtension** wherever such a replacement is possible. In other cases, make sure that the default block is extensible. For an example, see the **PurchRFQCaseCopying** class.

If you use the enum in **switch blocks**, avoid having default blocks that either have or don't have throws that aren't extensible.
When there are **long switch case blocks** or **if...else blocks** for the enum values, consider creating a class hierarchy to handle specific logic that is related to the enum. For an example, see the **PriceGroupTypeTradeAgreementMapping** class hierarchy.

Use the **in** keyword for query ranges that use the enum values, and make the container that the **in** keyword uses extensible.

## Potential issues

Some enums require the elements to have a certain order or value, and you can't make them extensible. This restriction could apply to status enums, where the values represent a logical progressive sequence, like: Draft, Approved, Completed, or Archived. It could also apply to enums where the values must have a fixed integral value to match another artifact, like another enum or a tabpage control's number.

Some enums have many elements. Enums support up to 250 elements. If your enum has many elements, such as more than 100, consider redesigning the solution instead of making the enum extensible. If the enum is extensible, then adding more elements in the future might break customers' combined solution as the addition might exceed the limit.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
