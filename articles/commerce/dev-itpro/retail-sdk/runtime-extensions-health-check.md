---
title: Runtime extensions health check
description: This article explains how to use the runtime extensions health check feature.
author: aneesa
ms.date: 03/17/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2023-03-17
ms.dyn365.ops.version: AX 10.0.30
---

# Runtime extensions health check

Developers building Commerce runtime extensions can use the health check feature to quickly check if their extensions meet current requirements.

You can access the feature via this URL

```
https://[CommerceScaleUnitURL]/healthcheck?testname=extensions
```

The extensions health check validates runtime extensions for a range of requirements.

## Assembly tests

Extensions health check performs assembly tests for target framework and unsupported dependencies.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
