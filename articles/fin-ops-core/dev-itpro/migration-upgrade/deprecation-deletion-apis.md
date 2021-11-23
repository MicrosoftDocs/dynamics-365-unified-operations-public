---
# required metadata

title: Deprecation of methods and metadata elements
description: This topic provides information about the deprecation of methods and metadata elements that become obsolete as the code base evolves. 
author: jorisdg
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: jorisde
ms.search.validFrom: 2019-1-31 
ms.dyn365.ops.version: 8.1.3 
---

# Deprecation of methods and metadata elements

[!include[banner](../includes/banner.md)]

As the Microsoft code base continues to evolve, some methods and metadata elements will no longer be required. Microsoft will mark these obsolete methods and metadata elements for deprecation.

- Methods are marked with the **SysObsolete** attribute. Typically, this attribute recommends an alternative to the method.
- For metadata elements, the **IsObsolete** property is set to **Yes**.

The deprecation is compatible with both binaries and design time. The referencing code will continue to work as expected, and no immediate action is required. During compilation, any references to deprecated artifacts are reported as compile **warnings**.

## Cleanup of deprecated elements

After a period of at least 12 months, Microsoft might delete obsolete methods and metadata elements.

However, if telemetry shows that any obsolete methods or metadata elements are still used, Microsoft will **not** delete them, to reduce the risk that consumers will be broken.

## Minimize your risk of being affected

Here are some tips that you, as a consumer of the Microsoft code base, can use to avoid being affected when methods and metadata elements are deprecated:

- Compile your code base at least every 12 months on top of the latest code base. If you receive any warnings because deprecated artifacts are used, address those warnings as soon as possible.
- Avoid **new** dependencies on deprecated artifacts. Microsoft might have just deleted the artifact, because there is a time window between when releases and telemetry are available.

## List of deprecated methods and metadata elements

For reference, download the Microsoft Excel file, [ObsoleteElementsPerVersion.xlsx](https://mbs2.microsoft.com/fileexchange/?fileID=d6b5589b-c2c7-4cdd-a6b9-87e080cb2f05), which shows the artifacts that have been marked for deprecation in each major release.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
