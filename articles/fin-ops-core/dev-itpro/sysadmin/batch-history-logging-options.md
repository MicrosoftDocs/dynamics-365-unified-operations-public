---
title: Batch history logging options
description: Learn how to configure batch history logging options to skip persisting INFO and PARAMETERS columns in the batch history table for improved database performance.
author: yogeshpatil
ms.author: yogeshpatil
ms.topic: how-to
ms.date: 03/18/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2026-03-18
ms.search.form:
ms.dyn365.ops.version: Platform update 65
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
---

# Batch history logging options

[!include [banner](../includes/banner.md)]

This article explains how to configure batch history logging options to optimize database storage and improve write performance by skipping the **INFO** and **PARAMETERS** columns when data is written to the batch history table.

## Overview

When batch jobs run, the system records history entries in the **BATCHHISTORY** table. By default, these entries include **INFO** and **PARAMETERS** column data for each batch job execution. Over time, these columns can consume significant database storage, especially in environments where batch jobs run frequently.

The **Batch history logging options** feature provides a configurable option to stop persisting the **INFO** and **PARAMETERS** columns when data is written to the batch history table. This optimization can significantly reduce database storage consumption and improve write performance.

## Prerequisites

Enable the **Batch history logging options** feature through a feature flight. Contact Microsoft Support to enable the flight for your environment.

## Configure batch history logging options

When you enable the feature flight, the **Batch history logging option** setting becomes available on the **Batch job** page. The recommended option is set by default when you enable the feature flight.

To configure batch history logging options, follow these steps:

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. In the **Batch history** section, locate the **Batch history logging option** setting.
1. Select the preferred logging option based on your requirements.

   - **Recommended** (default) - The **INFO** and **PARAMETERS** columns aren't persisted in the batch history table. This option provides the best database storage optimization and write performance.
   - **Legacy** - The **INFO** and **PARAMETERS** columns are persisted in the batch history table. Select this option if you require the historical info log and parameter data for troubleshooting or auditing purposes.

   > [!NOTE]
   > When you select the recommended option, the **INFO** and **PARAMETERS** values in the **BATCHHISTORY** table are stored as NULL. The current batch job's info log and parameters remain visible in the **Batch jobs** page. Only the historical records in the batch history table are affected.

## Behavior when the feature flight is disabled

When you disable the feature flight, the **Batch history logging option** setting is hidden from the user interface. In this state, the system persists the **INFO** and **PARAMETERS** columns in the batch history table as it does by default.

## Best practices

- Select the **Recommended** option to reduce database storage consumption and improve batch processing performance, especially in environments where batch jobs run frequently.
- If you need to retain historical info log and parameter data for regulatory or troubleshooting purposes, select the **Legacy** option.
- Combine this feature with regular [batch history cleanup](batch-history-cleanup.md) to maintain optimal database performance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
