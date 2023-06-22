---
# required metadata

title: Quarantine zones for nonconformances
description: This article describes how to create and use quarantine zones for nonconformances.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventQuarantineZone
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quarantine zones for nonconformances

[!include [banner](../includes/banner.md)]

This article describes how to create and use quarantine zones for nonconformances.

You use the **Quarantine zones** page to define zones that can be assigned to nonconformances. When you create a nonconformance, you can set the **Quarantine zone** and **Quarantine type** fields on the **General** tab of the **Non conformances** page. The **Quarantine zone** field typically indicates the area or location where the item is located. The **Quarantine type** field defines the item as either *Restricted usage* or *Unusable*.

When you print a nonconformance or corrections report for a nonconformance, you can view the quarantine zone where the item is located.

You can also print a nonconformance tag for a nonconformance. This report shows the assigned quarantine zone and information about usage to provide guidance about how defective material should be handled. The quarantine zones might correspond to inventory locations or operations resources.

## Examples of quarantine zones

### Example 1

You work at an electronics manufacturing company that produces and distributes televisions, speakers, and media players. In this case, you can configure a quarantine zone to represent each type of product.

### Example 2

Three bins and two racks are used to store items that are nonconforming. In this case, you can configure five quarantine zones, one for each bin and each rack.

## Create a quarantine zone

1. Go to **Inventory management \> Setup \> Quality management \> Quarantine zones**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Quarantine zone** – Enter a unique ID or name for the quarantine zone.
    - **Description** – Enter a detailed description of the quarantine zone.

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
