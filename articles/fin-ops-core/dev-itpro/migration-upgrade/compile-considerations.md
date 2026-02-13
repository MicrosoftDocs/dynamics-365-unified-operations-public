---
title: Plan and prepare for compiling code against the latest update
description: Learn about potential issues that a developer might see when compiling partner code with the latest product updates.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-10-01
ms.search.form: 
ms.dyn365.ops.version: Platform update 1
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
---

# Plan and prepare for compiling code against the latest update

[!include [banner](../includes/banner.md)]

With the rollout of the One Version servicing plan, Microsoft is committed to backward compatibility from a binary and functional perspective. For detailed information about One Version, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md). Even with backward compatibility as a priority, some development activities require code changes. Some of those situations are described in the following sections. 

- When Microsoft makes an enumeration extensible, it considers the change binary compatible. The compiler checks for unsafe extensible enumeration operations that depend on the integer value of a nonextensible enumeration. Any partner code that contains unsafe extensible enumeration operations has compiler errors when recompiled and needs to be modified. For more information, see [Add values to enums through extension](../extensibility/add-enum-value.md).

- To avoid possible unresolved references when compiling, a partner model should reference the top-level modules and submodules. If you don't add these references, a Microsoft change that adds new resources in an unreferenced submodule might cause an unresolved reference. To resolve the compilation error, add the submodule as a reference.

- Some methods are attributed as obsolete to signal that they're deprecated. Investigate any compiler warning that's generated due to the calling or wrapping of an obsolete method to ensure that the expected code path still exists. In some cases, Microsoft code directly calls the new method in place of the obsolete method. When this change happens, the code built around the obsolete method doesn't execute when expected.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]