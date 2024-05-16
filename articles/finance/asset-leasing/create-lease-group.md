---
title: Create a lease group
description: Learn about how to set up lease groups, which are required to create new leases, including outlines on creating lease books and associating a book with a lease group.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseGroupTable
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Create a lease group

[!include [banner](../includes/banner.md)]

This article explains how to set up lease groups. Lease groups are required to create new leases. Lease books are associated with each lease group. Lease books determine the default books that must be created for each lease. You can assign specific accounts to a lease group on the **Lease posting parameters** page.

## Create a lease book and add a lease group

1. Go to **Asset leasing \> Setup \> Lease groups**.
2. On the Action Pane, select **New** to add a lease group. A line is added to the grid.
3. On the new line, in the **Lease group** field, enter a value.
4. In the **Description** field, enter a value.

The information that you just entered is added to the **Lease group** field on the **Add lease** page.

## Associate a book with a lease group

After you create lease groups, you can assign books to each group. When you create a lease and assign it to a lease group, the system creates a set of schedules for each book that is associated with that lease group.

> [!NOTE]
> Books must be set up before they can be assigned to a lease group.

1. Go to **Asset leasing \> Setup \> Lease group**.
2. Select a lease group, and then select **Books**.
3. Select **New**, and then, in the **Book type** field, select the book to assign to the lease group. You can assign multiple books to a lease group if a lease must be accounted for in different ways.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
