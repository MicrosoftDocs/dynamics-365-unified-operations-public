---
# required metadata

title: Item quality groups
description: This article describes how to use and create item quality groups to logically group products so that they can be assigned to quality associations for the automatic generation of quality orders.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestQualityGroup, InventTestItemQualityGroup
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

# Item quality groups

[!include [banner](../includes/banner.md)]

A quality group represents common testing requirements for items. This article describes how to use and create item quality groups to logically group products so that they can be assigned to quality associations for the automatic generation of quality orders.

To set up, edit, and view the items that are assigned to a quality group, or the quality groups that are assigned to an item, go to **Inventory management \> Setup \> Quality groups**. After you define the test requirements on the **Test groups** page, you can define the rules for automatically generating quality orders. To simplify the process, you don't define rules for individual items. Instead, you can define the rules for a quality group on the **Quality associations** page.

## Example of an item quality group

A manufacturing company purchases various raw materials that have the same testing requirements for incoming inspection. Therefore, the company defines a quality group and then assigns the item numbers that are associated with the raw materials to that group. Later, the company purchases a new type of raw material that has the same testing requirements. Instead of setting up new testing requirements for the new material, the company adds the item number for the new material to the existing quality group.

The same company also produces items that have the same production testing requirements and ships items that have the same requirement for pre-shipment testing. Therefore, the company defines two additional quality groups and then assigns the relevant item numbers to each group.

## Create a quality group

To create a quality group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Quality groups**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Quality group** – Enter a unique ID or name for the quality group.
    - **Description** – Enter a detailed description of the quality group.

1. Close the page.

## Manually add items to a quality group

To manually add items to a quality group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Quality groups**.
1. Select the quality group that you want to add items to.
1. On the Action Pane, select **Items**.
1. On the **Items in quality groups** page, on the Action Pane, select **New** to add a row to the grid. Then, for the new row, set the **Item number** field to the item number that you want to add.
1. Repeat the previous step for each additional item that must be added.
1. Close the pages.

## Add multiple items to a quality group

To add multiple items to a quality group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Quality groups**.
1. Create or select the quality group that you want to add items to.
1. On the Action Pane, select **Add items**.
1. In the **Inquiry** dialog box, enter the filter criteria for the items that you want to add. For example, you might filter for all items in a specific item group.
1. Select **OK**.
1. In the **Add items** dialog box, a grid shows all the items that match your query. Review the results.

    If any changes are required, select **Select** to return to the **Inquiry** dialog box, and adjust your query.

1. When the results include all the items that you want to add, select **OK**.
1. Close the page.

## Manually associate an item with a quality group

To manually associate an item with a quality group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Item quality groups**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Item number** – Select the item number to add.
    - **Quality group** – Select the quality group to assign to the item.

1. Repeat the previous step for each additional combination of an item and a quality group that must be added.
1. Close the pages.

## Manually add a quality group from the Released products page

To manually add a quality group from the **Released products** page, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product that you want to assign a quality group to.
1. On the Action Pane, on the **Manage inventory** tab, in the **Quality** group, select **Item quality groups**.
1. On the **Items in quality groups** page, on the Action Pane, select **New** to add a row to the grid. Then, for the new row, set the **Quality group** field to the quality group that you want to assign to the product.
1. Repeat the previous step for each additional quality group that you want to assign to the product.
1. Close the pages.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management tests](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)
- [Quality management test variables](quality-test-variables.md)
- [Quality associations](quality-associations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
