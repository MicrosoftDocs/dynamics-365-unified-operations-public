--- 
title: Set up short picking item reallocation
description: Learn how to enable warehouse workers to quickly find alternative locations if there isn't sufficient inventory at the location they've been directed to.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 5/29/2026
ms.custom: bap-template 
ms.reviewer: kamaybac   
ms.search.form: WHSWorkException, WHSWorker, WHSLocationWithWorkException  
---

# Set up short picking item reallocation

[!include [banner](../../includes/banner.md)]

This procedure shows how to enable warehouse workers to quickly find alternative locations isn’t sufficient inventory at the location they’re directed to.  

A **Work exception** controls the reallocation process, and the warehouse **worker** uses it.

You can use automatic, manual, or both reallocation processes:

- Automatic reallocation - Location directives determine if the goods are available at another location. If possible, the work is updated and the warehouse user is directed to the alternative location.
- Manual reallocation - The warehouse user can select from one or more locations with unreserved quantities of goods.  
- Automatic and manual - If the system can't perform an automatic reallocation, and locations are available with unreserved quantities, the user is prompted to select a location.

## Set up work exceptions

Define several work exceptions with different item reallocation policies so the warehouse worker can choose one based on the needs of the shipment that they're processing.

This procedure uses the USMF demo data company.

1. Go to **Warehouse management > Setup > Work > Work exceptions**.
1. Select **New**.
1. In the **Work exception code** field, enter a value. This value is the title of the exception. For example, Short picking manual.
1. In the **Description** field, enter a value. This value is a short description of the usage of this exception. For example, Short picking - item not available.
1. In the **Exception** type field, select **Short pick**.
1. Select the **Adjust inventory** check box. If selected, inventory automatically adjusts to 0 at the short picked location.
1. In the **Default adjustment type code** field, enter or select a value. For example, in USMF you can select **Remove Res Adj Out**. Each Adjustment type code contains four characteristics: name, description, inventory journal name, and **Remove reservations**. If **Remove reservations** is enabled, the short-picked order line's reservations are removed.  
1. In the **Item reallocation** field, select a value, such as Manual. If you select Manual, or Automatic and Manual, enable the warehouse worker to use manual reallocation.

## Set up a worker to use manual item reallocation

This procedure uses the USMF demo data company.

1. Close the page.
1. Go to **Warehouse management > Setup > Worker**.
1. Select **Edit**.
1. In the list, select a worker. For example, Julia Funderburk.
1. Expand the **Users** FastTab.
1. In the list, select a **User ID**. For example, 24.
1. Expand the **Work** FastTab.
1. Select **Yes** in the **Allow manual item reallocation** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
