---
title: Extended data types
description: Learn about extended data types (EDTs), including overviews of label and help text, string size, the extends property, and the number of decimals.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Extended data types

[!include [banner](../includes/banner.md)]

Extended data types (EDTs) have a rich extension model that lets extenders change specific behaviors.

To provide an extensible solution, keep the following guidelines in mind when you work with EDTs.

## Label and help text

An extension can change the label and help text properties, but only one value can remain. If multiple solutions change the label of the same EDT, the various labels are, in functional terms, mutually exclusive. Therefore, you can't install those labels on the same system.

## String size

You can define the string size only on root EDTs. The system uses the largest value that is defined across the EDT and its extensions.

For derived EDTs, an extension can't change the string size, because that change breaks the IS-A relationship between the EDTs.

Assignments to string EDTs truncate the string to match the defined string size.

## Extends

An extension can't change the **extends** property. Any change that you make to this property after release causes a breaking change. Therefore, make sure that the property is set correctly before release.

If you set this property, neither you nor extenders can make changes to the string size later.

Avoid unnecessary dependencies. For example, don't extend generic EDTs such as Name and Description.

## Number of decimals

You can't change the **Number of decimals** property by using an extension.

If you set this property to **True**, extenders can change the number of decimal places.

If you set this property to **True**, make sure that the following conditions are met:

- All truncation logic honors the number of decimal places that you specify on the EDT, so no implicit or hardcoded rounding occurs.
- You don't assign the value to other incompatible EDTs that don't correctly handle rounding.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
