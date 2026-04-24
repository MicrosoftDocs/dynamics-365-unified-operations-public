---
title: Recreate missing consolidation transactions
description: Learn why some consolidation transactions may appear as duplicates or doubled and how to fix them. 
author: jchrist
ms.author: jchrist
ms.topic: article
ms.date: 03/10/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-5-31
ms.search.form: 
ms.dyn365.ops.version: 8.0.1
---

# Recreate missing consolidation transactions

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article explains why you might need to use the **Recreate missing consolidation transactions** option in Dynamics 365 Finance. In Dynamics 365 Finance version 10.0.48, the new **Recreate missing consolidation transactions** option helps resolve data inconsistencies that can occur when a consolidation process unexpectedly stops, such as due to a system interruption or manual termination.

## When do you need this option?

If a consolidation process stops while it's still running, the process might partially write some consolidation records to the database. These incomplete records can cause problems:

- The system can't automatically clean up these records when you run the consolidation again.
- They can cause duplicate or doubled balances to appear in the trial balance.
- They might result in missing or incomplete consolidation transaction headers or lines.

Over time, these problems can lead to incorrect financial results and reconciliation issues.

## What does this option do?

The **Recreate missing consolidation transactions** option scans the system to detect consolidation transactions that are missing or incomplete because of a failed or forcibly stopped consolidation process. You can run the detection first to scan for affected consolidation transactions. Then you can run it again to recreate the missing consolidation headers and lines. You can run both processes at the same time as well.

## How to use this option

Go to **Consolidations > Recreate missing consolidation transactions** to analyze the current data. Enter a **From date** and **To date** before running the process. The dates should match the dates of the last consolidation period but you can set them to a wider date range. If you use a large date range, it slows down the processing time. If the system finds missing consolidation transactions, it displays the results. To recreate the missing consolidation transactions, set **Recreate missing consolidation transactions** to **Yes**. Run the process again and the system automatically recreates the missing records.

When the process finishes, you can view any recreated consolidation transactions in **Consolidations > Consolidation transactions**.

This action repairs data inconsistencies caused by an interrupted consolidation process and doesn't replace a normal consolidation run.

### Key benefits

-   Reconstructs missing consolidation transaction headers and lines after an interrupted consolidation
-   Makes incomplete consolidation transactions visible in the **Consolidations transactions**
-   Enables users to review and remove consolidation transactions that couldn't be deleted previously
