---
title: Input controls and grid column sizes
description: This article describes how to create a consistent look and feel for forms by controlling the size of controls and grids.
author: jasongre
ms.date: 12/01/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6a7bb5b0-7350-46f1-a641-3f7a3187b687
---

# Input controls and grid column sizes

[!include [banner](../includes/banner.md)]

This article describes how to create a consistent look and feel for forms by controlling the size of controls and grids.

## Overview

Many frameworks offer complete freedom over the width of input controls. However, that level of freedom can lead to inconsistent presentation of data and a non-uniform layout for similar forms. For example, the customer name in one form might show 10 characters of information, whereas the customer name in another form might show 20 characters of information. To provide streamlined, easy-to-read interfaces, discrete sizing helps guarantee consistent presentation of data. The introduction of discrete sizing is a significant change to the basic input controls. The control framework attempts to provide a fresh, clean user experience that provides simplicity and consistency. As part of an attempt to provide consistent and uniform layout of forms, each input control is sized to one of four sizes: extra-small (XS), small (S), medium (M), or large (L). These sizes are determined by inspecting the explicitly specified width in the **DisplayLength** property of the control or the corresponding extended data type (EDT).

## Sizing grid columns
Column sizing in a grid control differs slightly from the legacy algorithm, which tried to provide an initial appealing presentation for each grid, based partly on the contents of the first page of data. The new approach disregards the contents of the first page of data. Instead, the end user decides which columns are most important to view and the ideal viewing width for each of those columns. By using personalization, each user can change the width of grid columns, and the client keeps track of that user's preference. In the new, simplified approach, the default column sizing is based on 75 percent of the base input control sizing. In most cases, we recommended that developers not override the default sizing. However, if you must resize the column width programmatically or in the model, see the next two sections of this article for guidance.

## Discrete sizing

| Size | Character range | Size in pixels (px) |
|------|-----------------|---------------------|
| XS   | 0–5             | 60  (25% of large)  |
| S    | 6–15            | 120 (50% of large)  |
| M    | 16–20           | 180 (75% of large)  |
| L    | >=30            | 240                 |

> [!NOTE]
> The explicit number of pixels will vary over time as the user interface evolves; however, the relative size of fields should remain constant. Developers should not rely on explicit pixel sizing.

## Forcing a desired discrete size
As the previous table shows, if you change the width of a grid-hosted control from 6 characters to 15 characters, you don't affect the width of the column. The layout engine gives the same width to all control widths that are in the 6-to-15-character range, because controls in this range are considered small (S). If you want to extend the control to medium (M) size, the width value must be set to a value that is more than 16 characters and less than 31 characters. For guidance about how to size input controls, see the following table. In some cases, the use of a form pattern will override or hide developer-defined sizing.

| Property          | Value        | Description                                                                                                                                            |
|-------------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| DisplayLengthMode | Auto         | Use the kernel’s default value.                                                                                                                        |
| DisplayLengthMode | Fixed        | Use the developer-defined **DisplayLength** value.                                                                                                     |
| WidthMode         | Auto         | Use the kernel’s default sizing behavior.                                                                                                              |
| WidthMode         | Fixed        | Use the developer-defined **Width** value.                                                                                                             |
| WidthMode         | Column Width | Use size-to-parent behavior.                                                                                                                           |
| DisplayLength     | N            | The developer-defined control width, which is specified in characters. (Values are mapped to the sizing groups that are listed in the previous table.) |
| Width             | N            | The developer-defined control width, which is specified in pixels.                                                                                     |







[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
