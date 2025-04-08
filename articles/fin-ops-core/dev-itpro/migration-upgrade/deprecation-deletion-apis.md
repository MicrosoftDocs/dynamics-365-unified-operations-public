---
title: Deprecation of methods and metadata elements
description: Learn about the deprecation of methods and metadata elements that become obsolete as the code base evolves, including an overview on the cleanup of deprecated elements.
author: josaw
ms.author: josaw
ms.topic: article
ms.date: 02/19/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-01-31
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
