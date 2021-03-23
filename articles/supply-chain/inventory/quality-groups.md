---
# required metadata

title: Item quality groups
description: This topic describes how to use and create item quality groups to logically group products for assignment to a quality associations for the automatic generation of quality orders.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestQualityGroup, InventTestItemQualityGroup
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

# Item quality groups

[!include [banner](../includes/banner.md)]

A quality group represents common testing requirements for items. This topic describes how to create and use item quality groups to logically group products for assignment to quality associations for the automatic generation of quality orders.

Go to **Inventory management > Setup > Quality groups** to set up, edit, and view the items that are assigned to a quality group or the quality groups that are assigned to an item. After you define the test requirements on the **Test groups** page, you can define the rules for automatically generating quality orders. To simplify the process, you don't define rules for individual items. Instead, you can define rules for a quality group by using the **Quality associations** page.

## Example of an item quality group

A manufacturing company purchases various raw materials that have the same testing requirements for incoming inspection. The company defines a quality group and then assigns the item numbers that are associated with the raw materials to that group. Later, the company purchases a new type of raw material that has the same testing requirements. Instead of setting up new testing requirements for the new material, the company adds the item number for the new material to the existing quality group. The same manufacturing company also produces items that have the same production testing requirements and ships items that have the same requirement for pre-shipment testing. The company defines two additional quality groups and then assigns the relevant item numbers to each group.

## Create a quality group

To create a quality group:

1. Go to **Inventory management > Setup > Quality control > Quality groups**.
1. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Quality group** - Enter a unique ID or name for the quality group.
    - **Description** - Enter a detailed description for the quality group.
1. Close the page.

## Manually add items to a quality group

To manually add items to a quality group:

1. Go to **Inventory management > Setup > Quality control > Quality groups**.
1. Select the quality group that you want to add items to.
1. Select **Items** on the Action pane. The **Items in quality groups** page opens.
1. Select **New** on the Action Pane to add a new row to the grid. Then, for your new row, set the **Item number** to the item number you want to add.
1. Repeat the previous step for each additional item to be added.
1. Close the pages.

## Add multiple items to a quality group

To add multiple items to a quality group:

1. Go to **Inventory management > Setup > Quality control > Quality groups**.
1. Create or select the quality group that you want to add items to.
1. Select **Add items** on the action pane. The **Inquiry** dialog box opens.
1. Enter the filter criteria for the items you want to add. For example, you might filter for all items in a specific item group.
1. Select **OK**.
1. The **Add items** dialog box opens, showing a grid that includes all the items that match your query. Review the results.
    - If changes are needed, select **Select** to return to the **Inquiry** dialog box and adjust your query as needed.
    - Once the results include all the items you want to add, then select **OK**.
1. Close the page.

## Manually associate an item with a quality group

To manually associate an item with a quality group:

1. Go to **Inventory management > Setup > Quality control > Item quality groups**.
1. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Item number** - Select the item number to be added.
    - **Quality group** - Select the quality group to assign to the item.
1. Repeat the previous step for each additional item and quality group combination to be added.
1. Close the pages.

## Manually add a quality group from the Released products page

To manually add a quality group from the **Released products** page:

1. Go to **Product information management > Products > Released products**.
1. Select the product that you want to assign to a quality group to.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Quality** group, select **Item quality groups**.
1. The **Items in quality groups** page opens. Select **New** on the Action Pane to add a new row to the grid. Then, for your new row, set the **Quality group** to a quality group you want to assign to the product.
1. Repeat the previous step for each additional quality group you want to assign to the product.
1. Close the pages.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management tests](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)
- [Quality management test variables](quality-test-variables.md)
- [Quality associations](quality-associations.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]