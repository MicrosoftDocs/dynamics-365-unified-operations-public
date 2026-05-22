---
title: AX 2009 migration - Import packages
description: Learn about how to import a migrated data package from Microsoft Dynamics AX 2009 into finance and operations.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Import packages

[!include [banner](../includes/banner.md)]

You can import data for a group of logically related entities that are sequenced in the correct order. You have three options for importing Microsoft Dynamics AX 2009 data that you want to migrate:

- AX 2009
- Finance and operations

## AX 2009

You can import data for migration directly from the source system. Follow these steps:

1. In AX 2009, in the navigation pane, select **Data migration**.
1. Go to **Common** > **Create migration group**.
1. In the **Migration group** form, select the migration group to export, and then select **Export now**.
1. In the **Export data** form, select the **Import package in target** check box, and then select **OK**.

## Finance and operations

You can import data for migration by using your finance and operations environment. Follow these steps:

1. Sign in to your environment by using an Administrator role.
1. On the dashboard, select the **Data Management** workspace.
1. Select **Import**.
1. Enter the name of the package, and then, in the **Source data format** field, select **Package**.
1. Select **Upload**, and then select the appropriate package file from the location for the data that you're importing. All the files from the package are imported.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
