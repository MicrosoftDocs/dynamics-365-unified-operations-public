---
title: System tracking fields on financial tables
description: Learn about the system tracking fields that are enabled on tables across the application for auditing and data integrity purposes.
author: anaborges
ms.author: anaborges
ms.topic: article
ms.date: 04/03/2026
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-11-01
ms.dyn365.ops.version: Version 10.0
---

# System tracking fields on financial tables

[!include [banner](../includes/banner.md)]

This article describes the system tracking fields that are enabled on tables across the application and how they work.

## Overview

Various tables across the application have system tracking fields enabled on them. These fields automatically record who created or last modified a record. The fields include:

- **CreatedBy** – The user who created the record.
- **CreatedDateTime** – The date and time when the record was created.
- **ModifiedBy** – The user who last modified the record.
- **ModifiedDateTime** – The date and time when the record was last modified.

These fields support auditing capabilities and assist with data integrity investigations. The system maintains these fields automatically and doesn't require any user input.

## Where to view these fields

Standard form layouts don't show these fields. To view them, go to **Options** > **Record info** > **Show all fields** on the relevant form.

You can also see these fields through direct SQL queries or by using the **SysTableBrowser** tool.

## Tables with system tracking fields

The application enables system tracking fields on tables across multiple areas, including tables in the General Ledger and Financial Dimensions area such as **MainAccount** and **DimensionAttributeValue**.

> [!NOTE]
> If you recently upgraded to version 10.0, you might notice that existing records show the upgrade date in the **CreatedDateTime** and **ModifiedDateTime** fields. This date is expected. Because these columns didn't exist on the table before the upgrade, the database synchronization (dbSync) process adds the current date and time when it adds the columns. The system can't determine the original creation or modification dates for records that existed before tracking was enabled. All records created or modified after the upgrade reflect accurate dates.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
