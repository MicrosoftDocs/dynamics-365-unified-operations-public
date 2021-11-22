---
title: Only one label is printed for multiple work headers on a single receipt
description: Only one label is printed for multiple work headers on a single receipt.
author: perlynne
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WHSLicensePlateLabel
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Only one label is printed for multiple work headers on a single receipt

KB number: 4614667

## Symptoms

Multiple work headers are created for the same target license plate as part of a single warehouse app receiving event. However, only one license plate label is printed when the product is received.

## Resolution

The system is behaving as designed.

In the current design, a single license plate label is always generated, regardless of the number of work header and work line combinations that exist. The generated label includes the information for only one combination.

To work around this issue, make sure that work header creation is always mapped to just one target license plate.
