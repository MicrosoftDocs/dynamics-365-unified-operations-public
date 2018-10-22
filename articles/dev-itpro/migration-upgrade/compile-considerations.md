---
# required metadata

title: Considerations when compiling
description: This topic highlights a few issues that a developer might see when compiling partner code with the latest update from Microsoft.
author: dfroslie
manager: AnnBe

ms.date: 10/19/2018

ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 102343
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Considerations when compiling against a new update

[!include [banner](../includes/banner.md)]

This topic highlights a few issues that a developer might see when compiling partner code with the latest update from Microsoft.

## Considerations

With the rollout of the ONE Version servicing plan, Microsoft is committed to be backward compatible from a binary and functional perspective (see https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/one-version for details).  However there are situations where development activities such as recompilation may result in required code changes.  Here are two examples:
 
1.	When Microsoft makes an enumeration extensible, it is a binary compatible change.  However, the compiler checks for unsafe extensible enumeration operations that depend on the integer value of a non-extensible enumeration (see https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/add-enum-value).  Any partner code with unsafe extensible enumeration operations will have compiler errors when re-compiled and will need to be modified.
 
2.	To avoid possible unresolved references when compiling, a partner model should reference the top level module(s) and all sub-modules for the top level modules.  If this is not done, it's possible that a Microsoft change that adds new resources in an unreferenced sub-module may cause an unresolved reference.  To resolve the compilation error, simply add the sub-module as a reference.

3.	Some methods will be attributed as obsolete to signal that they will be fully deprecated in the future.  Any compiler warning generated due to the calling or wrapping (via Chain of Command) of an obsolete method should be investigated to ensure the code path expected still exists.  In some cases, Microsoft code will directly call the new method in place of the obsolete method.  In this case, code built around the obsolete method will not execute when expected.

