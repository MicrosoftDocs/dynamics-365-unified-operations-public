---
title: Performance and memory considerations for ER
description: Learn how Electronic reporting (ER) optimizes memory consumption during execution, with guidance for running reports that process large volumes of data.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/17/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: ERModelMappingDesigner, EROperationDesigner
ms.dyn365.ops.version: 10.0.29
ms.assetid: 
---

# Performance and memory considerations for ER

[!INCLUDE [banner](../includes/banner.md)]

This article describes how the Electronic reporting (ER) engine manages memory during report execution, and how that management affects reports that process large volumes of data.

## Overview

When you run an ER format, the ER engine loads data from the configured data sources, transforms it according to the format mapping, and produces the output document. For reports that process large volumes of data such as statutory declarations or high-volume transaction extracts, the amount of memory used during execution can become a limiting factor. High peak memory consumption can slow down execution and, in extreme cases, cause a report run to fail.

## Optimized memory consumption during ER execution

Starting in version 10.0.49, the ER reporting engine includes targeted optimizations that improve memory efficiency during execution. These optimizations reduce peak memory consumption by:

- **Minimizing unnecessary object creation** during data processing and document generation.
- **Avoiding redundant duplication of data in memory** so that the same data isn't held in multiple places at the same time.
- **Reusing existing data structures more effectively** instead of allocating new ones.

These improvements are broadly applicable across ER scenarios and are beneficial for reports that process large volumes of data.

> [!NOTE]
> These optimizations are built into the ER engine. You automatically benefit from them after you update to the applicable version. No configuration changes, parameter settings, or report redesign are required.

## What to expect

- **Reduced peak memory usage** during execution, which lowers the risk of out-of-memory failures for high-volume runs.
- **More consistent completion** of large reports, because the engine holds less data in memory at any one time.
- **No change to report output.** The optimizations affect only how the engine uses memory internally. The generated documents are identical to those produced by earlier versions.

## Recommendations for large reports

To get the most benefit when you run reports that process large volumes of data, consider the following practices:

- **Run high-volume reports in batch mode.** Batch execution offloads processing from interactive sessions. For more information, see [Electronic reporting (ER) destinations](electronic-reporting-destinations.md).
- **Filter the source data** to the records that the report actually requires, so that the engine processes only the data that you need.
- **Keep your ER configurations up to date** so that you receive the latest engine optimizations and fixes.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
