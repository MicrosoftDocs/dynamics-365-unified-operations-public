---
title: System tracking fields show recent dates after upgrade
description: Learn why financial dimension and general ledger records may show recent created or modified dates after an upgrade to version 10.0, and why this behavior is by design.
author: anaborges
ms.author: anaborges
ms.topic: article
ms.date: 03/06/2026
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-11-01
ms.dyn365.ops.version: Version 10.0
---

# System tracking fields show recent dates after upgrade

[!include [banner](../includes/banner.md)]

This article explains why some financial records may display recent created or modified dates after an upgrade, even though the records existed before the upgrade.

## Overview

Multiple tables in the General Ledger and Financial Dimensions area have had system tracking fields enabled on them. These fields include:

- **CreatedBy**
- **CreatedDateTime**
- **ModifiedBy**
- **ModifiedDateTime**

These fields were added to improve auditing capabilities and to assist with data corruption investigations.

## Why records show recent dates

Because these fields didn't previously exist on the tables, the database synchronization (dbSync) process that runs during an upgrade adds the new columns. When the columns are added, the current date and time are automatically populated for all existing records.

The system can't determine the actual date and time that a record was originally created, because that information wasn't tracked before the upgrade. Instead, the date and time that the column was added is used as the initial value. Any records that are created or modified after the upgrade report the correct date and time going forward.

## How to identify these fields

These fields aren't shown on standard user-facing form layouts. To view them, navigate to **Options** > **Record info** > **Show all fields** on the relevant form.

The fields can also be observed through direct SQL queries or the **SysTableBrowser** tool.

## Affected tables

The following tables are examples of tables that had system tracking fields added:

- **MainAccount**
- **DimensionAttributeValue**
- Other financial dimension-related tables

> [!NOTE]
> This behavior is not limited to financial dimension tables. Any table that has system tracking fields added during an upgrade will exhibit the same behavior.

## Additional resources

[Financial dimension activation](activate-financial-dimensions.md)

[Financial dimension configuration](financial-dimension-configuration-integration.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
