---
title: System tracking fields show recent dates after upgrade
description: Learn why records may show recent created or modified dates after an upgrade to version 10.0 when system tracking fields are added to tables, and why this behavior is by design.
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

This article explains why records may display recent created or modified dates after an upgrade, even though the records existed before the upgrade.

## Overview

As part of ongoing improvements to auditing and data integrity, system tracking fields have been enabled on various tables across the application. These fields include:

- **CreatedBy**
- **CreatedDateTime**
- **ModifiedBy**
- **ModifiedDateTime**

When these fields are added to a table that didn't previously have them, existing records may appear to have been recently created or modified. This is expected behavior and is explained in the following sections.

## Why records show recent dates

When system tracking fields are enabled on a table, the database synchronization (dbSync) process that runs during an upgrade adds the new columns. Because the columns didn't previously exist, the system can't determine the actual date and time that existing records were originally created or modified. Instead, the current date and time of the upgrade are automatically populated as the initial values.

Any records that are created or modified after the upgrade report the correct date and time going forward.

## How to identify these fields

These fields aren't shown on standard user-facing form layouts. To view them, navigate to **Options** > **Record info** > **Show all fields** on the relevant form.

The fields can also be observed through direct SQL queries or the **SysTableBrowser** tool.

## Scope

This behavior applies to any table that has system tracking fields added during an upgrade. Examples include tables in the General Ledger and Financial Dimensions area, such as **MainAccount** and **DimensionAttributeValue**, but the same behavior occurs for any table across the application where these fields are newly enabled.

## Additional resources

[Database synchronization](../dev-tools/database-synchronization.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
