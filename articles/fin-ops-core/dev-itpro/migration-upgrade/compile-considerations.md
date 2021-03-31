---
# required metadata

title: Plan and prepare for compiling code against the latest update
description: This topic highlights potential issues that a developer might see when compiling partner code with the latest product updates.
author: dfroslie

ms.date: 10/15/2019

ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 102343
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
ms.search.region: Global
# ms.search.industry: 
ms.author: dfroslie
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Platform update 1

---

# Plan and prepare for compiling code against the latest update

[!include [banner](../includes/banner.md)]

With the rollout of the One Version servicing plan, Microsoft is committed to backward compatibility from a binary and functional perspective. For detailed information about One Version, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md). Even with backward compatibility as a priority, there are situations where development activities may result in required code changes. Some of those situations are described below. 

- When Microsoft makes an enumeration extensible, it is considered a binary compatible change. The compiler checks for unsafe extensible enumeration operations that depend on the integer value of a non-extensible enumeration. Any partner code that contains unsafe extensible enumeration operations will have compiler errors when re-compiled and will need to be modified. For more information, see [Add values to enums through extension](../extensibility/add-enum-value.md).

- To avoid possible unresolved references when compiling, a partner model should reference the top-level modules and sub-modules. If this is not done, a Microsoft change that adds new resources in an unreferenced sub-module may cause an unresolved reference. To resolve the compilation error, add the sub-module as a reference.

- Some methods will be attributed as obsolete to signal that they will be fully deprecated in the future. Any compiler warning that is generated due to the calling or wrapping of an obsolete method should be investigated to ensure that the expected code path still exists. In some cases, Microsoft code will directly call the new method in place of the obsolete method. When this happens, the code built around the obsolete method will not execute when expected.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]