---
title: Deprecation of methods and metadata elements
description: Learn about the deprecation of methods and metadata elements that become obsolete as the code base evolves, including an overview on the cleanup of deprecated elements.
author: josaw
ms.author: josaw
ms.topic: article
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3
---

# Deprecation of methods and metadata elements

[!include[banner](../includes/banner.md)]

As the Microsoft code base evolves, some methods and metadata elements become unnecessary. Microsoft marks these methods and metadata elements as deprecated.

- Methods are marked with the **SysObsolete** attribute. Typically, this attribute recommends an alternative to the method.
- For metadata elements, the **IsObsolete** property is set to **Yes**.

The deprecation works with both binaries and design time. The referencing code keeps working as expected, and no immediate action is required. During compilation, any references to deprecated artifacts are reported as compile **warnings**.

## Cleanup of deprecated elements

After a period of at least 12 months, Microsoft might remove obsolete methods and metadata elements.

However, if telemetry shows that you still use any obsolete methods or metadata elements, Microsoft **won't** remove them. This approach reduces the risk of breaking changes.

## Minimize your risk of being affected

To avoid being affected when Microsoft deprecates methods and metadata elements, follow these tips:

- Compile your code base at least every 12 months on top of the latest code base. If you receive any warnings because your code uses deprecated artifacts, address those warnings as soon as possible.
- Avoid **new** dependencies on deprecated artifacts. Microsoft might have removed the artifact because there's a time window between when releases and telemetry are available.

## List of deprecated methods and metadata elements

For reference, download the Microsoft Excel file [ObsoleteElementsPerVersion.xlsx](https://download.microsoft.com/download/4cde8eab-ab24-4101-b3c5-d5a5080e57bb/ObsoleteElementsPerVersion.xlsx) to see the artifacts that each major release marks for deprecation.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
