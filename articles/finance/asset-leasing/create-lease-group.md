---
title: Create a lease group
description: Learn about how to set up lease groups, which are required to create new leases, including outlines on creating lease books and associating a book with a lease group.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseGroupTable
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Create a lease group

[!include [banner](../includes/banner.md)]

This article explains how to set up lease groups. You need lease groups to create new leases. Each lease group associates with lease books. Lease books determine the default books that the system must create for each lease. You can assign specific accounts to a lease group on the **Lease posting parameters** page.

## Create a lease book and add a lease group

1. Go to **Asset leasing \> Setup \> Lease groups**.
1. On the Action Pane, select **New** to add a lease group. A line is added to the grid.
1. On the new line, in the **Lease group** field, enter a value.
1. In the **Description** field, enter a value.

The information that you enter is added to the **Lease group** field on the **Add lease** page.

## Associate a book with a lease group

After you create lease groups, assign books to each group. When you create a lease and assign it to a lease group, the system creates a set of schedules for each book that associates with that lease group.

> [!NOTE]
> Set up books before you assign them to a lease group.

1. Go to **Asset leasing \> Setup \> Lease group**.
1. Select a lease group, and then select **Books**.
1. Select **New**, and then, in the **Book type** field, select the book to assign to the lease group. You can assign multiple books to a lease group if a lease must be accounted for in different ways.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
