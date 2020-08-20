---
# required metadata

title: Create a lease group
description: This topic describes the process of setting up lease groups, which are required for creating a new lease.
author: moaamer
manager: Ann Beebe
ms.date: 07/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: 10.0.13

---

# Create a lease group (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process of setting up lease groups, which are required for creating a new lease. The lease book determines the default books that must be created for each lease. Lease books are associated with a lease group. You can assign specific accounts to a lease group on the **Lease posting parameters** page.

1. To create a lease book, go to **Asset leasing > Setup > Lease groups**.
2. To add a lease group, click on the **New** button in the action pane. A new line will add to the lease group grid.
3. In the **Lease group** field, enter a value
4. In the **Description** field, enter a value

The information added in the preceding steps will be added to the **Lease group** drop-down list on the **Add lease** page.

## Associate a book to a lease group

After creating the lease groups, books can be assigned to each group. When you create a lease and assigns it to a lease group, the system will create a set of schedules for each book associated to that lease group.

1. To add books to a group, open the **Lease group** page (**Asset leasing > Setup > Lease group**).
2. Select a lease group, and then click the **Books** button.
3. Click **New**, and then select the book to assign to the lease group from the **Book type** drop-down menu. You can assign multiple books to a lease group if it's necessary to account for a lease in different ways. 

> [!Note] 
> Books must be set up first before they can be assigned to a lease group.
