---
title: Only one label prints for multiple work headers on a single receipt
description: Only one label prints for multiple work headers on a single receipt
author: SmithaNataraj
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

If multiple work headers are created for a single product, only one license plate label prints when receiving the product.

## Resolution

This is the expected behavior.
<!--KFM: The following sentence doesn't make sense. Please revise. -->
In the current design, a single license plate label is generated based on a single work header and not 'work labels' getting created based on target license plates.
