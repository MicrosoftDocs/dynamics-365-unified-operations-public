---
title: Deprecation of methods and metadata elements
description: Learn about the deprecation of methods and metadata elements that become obsolete as the code base evolves, including an overview on the cleanup of deprecated elements.
author: josaw
ms.author: josaw
ms.topic: article
ms.date: 05/06/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3
---

# Deprecation of methods and metadata elements

[!include[banner](../includes/banner.md)]

As the Microsoft code base continues to evolve, some methods and metadata elements are no longer required. Microsoft marks these obsolete methods and metadata elements for deprecation.

- Methods are marked with the **SysObsolete** attribute. Typically, this attribute recommends an alternative to the method.
- For metadata elements, the **IsObsolete** property is set to **Yes**.

The deprecation is compatible with both binaries and design time. The referencing code continues to work as expected, and no immediate action is required. During compilation, any references to deprecated artifacts are reported as compile **warnings**.

## Cleanup of deprecated elements

After a period of at least 12 months, Microsoft might delete obsolete methods and metadata elements.

However, if telemetry shows that any obsolete methods or metadata elements are still used, Microsoft **won't** delete them, to reduce the risk that consumers will be broken.

## Minimize your risk of being affected

Here are some tips that you, as a consumer of the Microsoft code base, can use to avoid being affected when methods and metadata elements are deprecated:

- Compile your code base at least every 12 months on top of the latest code base. If you receive any warnings because deprecated artifacts are used, address those warnings as soon as possible.
- Avoid **new** dependencies on deprecated artifacts. Microsoft might have deleted the artifact, because there's a time window between when releases and telemetry are available.

## List of deprecated methods and metadata elements

For reference, download the Microsoft Excel file, [ObsoleteElementsPerVersion.xlsx](https://download.microsoft.com/download/4cde8eab-ab24-4101-b3c5-d5a5080e57bb/ObsoleteElementsPerVersion.xlsx), which shows the artifacts that are marked for deprecation in each major release.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
