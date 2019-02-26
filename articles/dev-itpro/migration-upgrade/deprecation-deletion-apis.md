---
# required metadata

title: Deprecation of methods and metadata elements
description: Microsoft will keep evolving the code base, and as a result certain methods and meta data elements are no longer needed. 
author: robadawy
manager: AnnBe
ms.date: 02/11/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: robadawy
ms.search.validFrom: 2019-1-31 
ms.dyn365.ops.version: 8.1.3 
---

# Deprecation of methods and metadata elements
[!include[banner](../includes/banner.md)]

Microsoft will keep evolving the code base, and as a result, certain methods and meta data elements are no longer needed. When this happens Microsoft will mark the method or element for deprecation. 

* Methods are marked with the `SysObsolete` attribute typically explaining an alternative; and 
* Meta data elements have the `IsObsolete` property set to yes.

The deprecation is both binary and design time compatible. The referencing code will continue to work as expected; and no immediate action is required. When compiling any references to deprecated artifacts are reported as compile **warnings**. 

## Cleaning up deprecated elements
After a period of at least 12 months, Microsoft may delete obsoleted methods and meta data elements. 

To limit the risk of breaking any consumers, Microsoft will **not** delete any obsoleted methods or meta data elements, if telemetry shows they are still in use.

## Minimize the risk of being impacted
As a consumer of Microsoft's code base, here is a list of tips you can use to avoid being impacted:

1. Compile your code base at least every 12 months on top of the latest code base. If you discover any warnings due to usages of deprecated artifacts, please address these as soon as possible.
2. Avoid **new** dependencies on deprecated artifacts. If you do, Microsoft might just have deleted the artifact, as there is a time window between when releases and telemetry are available.

## List of deprecated methods and meta data elements
As a reference, please find an Excel file attached containing the artifacts that have been marked for deprecation in each of the major releases.

