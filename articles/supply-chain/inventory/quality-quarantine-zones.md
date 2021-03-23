---
# required metadata

title: Quarantine zones for nonconformances
description: This topic describes how to create and use quarantine zones for nonconformances.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventQuarantineZone
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quarantine zones for nonconformances

[!include [banner](../includes/banner.md)]

This topic describes how to create and use quarantine zones for nonconformances.

Use the **Quarantine zones** page to define zones that can be assigned to a nonconformance. When you create a nonconformance, you can specify the **Quarantine zone** and the **Quarantine type** on the **General** tab of the **Non conformances** page. The **Quarantine zone** typically indicates the area or location where the item is located. While the **Quarantine** type defines if the item is **Restricted usage** or **Unusable**.

When you print a nonconformance or corrections report for a nonconformance, you can view the **Quarantine zone** where the item is at.

You can also print a nonconformance tag for a nonconformance. This report will show the assigned quarantine zone and information about usage to provide guidance about how to handle defective material. The zones might correspond to inventory locations or operations resources.

## Examples of quarantine zones

You work at an electronics manufacturing company who produces and distributes televisions, speakers, and media players. You could configure the quarantine zones to represent these types of products. In another example, three bins and two racks are used to store items that are nonconforming. In this example, you could configure five quarantine zones to represent each bin and each rack.

## Create a quarantine zone

1. Go to **Inventory management >  Setup > Quality management > Quarantine zones**.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Quarantine zone** - Enter a unique ID or name for the problem type.
    - **Description** - Enter a detailed description for the problem type.
1. Close the page.

## Additional resources

- [Quality management overview](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Workers responsible for approving nonconformances](quality-responsible-workers.md)
- [Problem types for nonconformances](quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](quality-diagnostic-types.md)
- [Quality charges for nonconformances](quality-charges.md)
- [Operations for nonconformances](quality-operations.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]