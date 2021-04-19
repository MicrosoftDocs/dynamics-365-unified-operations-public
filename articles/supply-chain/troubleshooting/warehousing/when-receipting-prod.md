---
title: Only one label prints for multiple work headers on a single receipt
description: Only one label prints for multiple work headers on a single receipt
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

# Only one label prints for multiple work headers on a single receipt

KB Number: 4614667

## Issue description

If multiple work headers are created for the same target license plate as part of a single warehouse app receiving event, only one license plate label prints when receiving the product.

## Resolution

This is the expected behavior.

In the current design, a single license plate label is generated, regardless of how many work header and work line combinations exist. The generated label will only include the information for one of these combinations.

To work around this issue, make sure your work header creation always maps to just one target license plate.
