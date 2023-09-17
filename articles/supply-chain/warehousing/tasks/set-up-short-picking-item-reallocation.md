--- 
# required metadata 
 
title: Set up short picking item reallocation
description: This article shows how to enable warehouse workers to quickly find alternative locations if there isn't sufficient inventory at the location they've been directed to. 
author: Mirzaab
ms.date: 06/29/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSWorkException, WHSWorker, WHSLocationWithWorkException    
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up short picking item reallocation

[!include [banner](../../includes/banner.md)]

This procedure shows how to enable warehouse workers to quickly find alternative locations if there isn’t sufficient inventory at the location they’ve been directed to. 

The reallocation process is controlled by a **Work exception** and used by the warehouse **worker.**

It is possible to use Automatic, Manual, or both reallocation processes:

- Automatic reallocation - Location directives are used to determine if the goods are available at another location. If possible, the work will be updated and the warehouse user will be directed to the alternative location.
- Manual reallocation - Allows the warehouse user to select from one or more locations with unreserved quantities of goods. 
- Automatic and manual - If the system is unable to perform an automatic reallocation, and locations are available with unreserved quantities, the user will be prompted to select a location.

## Set up work exceptions
It's possible to define several work exceptions with different item reallocation policies to enable the warehouse worker to choose one based on the needs of the shipment that they are processing.

The USMF demo data company was used to create this procedure.

1. Go to **Warehouse management > Setup > Work > Work exceptions**.
2. Click **New** 
3. In the **Work exception code** field, type a value. This will be the title of this exception . For example, Short picking manual.
4. In the **Description** field, type a value. This will be a short description of the usage of this exception. For example, Short picking - item not available.
5. In the **Exception** type field, select **Short pick**.
6. Select the **Adjust inventory** check box. If selected, inventory will automatically be adjusted to 0 at the short picked location.
7. In the **Default adjustment type code** field, enter or select a value. For example, in USMF you can select **Remove Res Adj Out**. Each Adjustment type code contains four characteristics: name, description, inventory journal name, and **Remove reservations**. If **Remove reservations** is enabled, the short-picked order line's reservations will be removed.  
8. In the **Item reallocation** field, select a value, such as Manual. If you select Manual, or Automatic and Manual, the warehouse worker needs to be enabled to use manual reallocation.

## Set up a worker to use manual item reallocation

The USMF demo data company was used to create this procedure.

1. Close the page.
2. Go to **Warehouse management > Setup > Worker**.
3. Click **Edit**.
4. In the list, select worker. For example, Julia Funderburk.
5. Expand the **Users** FastTab.
6. In the list, select a **User ID**. For example, 24.
7. Expand the **Work** FastTab.
8. Select **Yes** in the **Allow manual item reallocation** field.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]