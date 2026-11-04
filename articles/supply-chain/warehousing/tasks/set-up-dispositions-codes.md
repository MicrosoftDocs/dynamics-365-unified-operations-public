---
title: Set up mobile device disposition codes
description: Learn how to set up mobile device disposition codes, which control the inventory status, work template, and return handling for items that workers receive.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSDispositionTable
ms.topic: how-to
ms.date: 10/30/2026
ms.custom:
  - bap-template
---

# Set up mobile device disposition codes

[!INCLUDE [banner](../../includes/banner.md)]

A *mobile device disposition code* is a collection of rules that Supply Chain Management applies when a warehouse worker receives items by using a mobile device. When the worker scans or selects a code, that code determines the inventory status that's assigned to the received items, the work template that creates the putaway work, and, for customer returns, how the return is settled. For example, you might create one code for returned items that can go straight back into sellable inventory, and another for damaged items that must be scrapped.

Disposition codes apply to the following receiving processes:

- *Purchase order receiving* – A disposition code is optional.
- *Production order report as finished* – A disposition code is optional.
- *Sales order return receiving* – A disposition code is mandatory if the items are registered by using a mobile device.

Warehouse managers typically set up disposition codes as part of the initial mobile device configuration.

## Create a mobile device disposition code

Each disposition code is a single row that combines an inventory status, a work template, and a return disposition code. You only need to fill in the settings that are relevant for the processes where the code will be used. To create a disposition code, follow these steps:

1. Go to **Warehouse management** > **Setup** > **Mobile device** > **Disposition codes**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for it:

    - **Disposition code** – Enter a unique name for the code. Workers scan or select this value in the app, so keep it short and descriptive (for example, *RMA Credit* or *RMA Scrap*). You can't change this value after you save the record.
    - **Inventory status** – Select the inventory status that should be assigned to the items that are received under this code. This status overrides the default status on the order lines. Select a status that blocks inventory if the received items must be held back from other warehouse processes until someone inspects them. Leave this field blank to keep the default status from the order line.
    - **Work template** – Select the work template that should create the putaway work for the received items. Leave this field blank if you want the standard work template rules that are configured in your system to apply. The lookup shows only work templates that have a work order type of *Purchase orders*, *Finished goods put away*, or *Return orders*. Because the work template is tied to a work order type, selecting one limits the processes that the disposition code can be used with. For example, if you select a work template that has a work order type of *Purchase orders*, you can't use the code to register items that customers return.
    - **Return disposition code** – Select the return disposition code that determines the rest of the return order process for the registered items. The return disposition code carries the *disposition action*, which controls the physical and financial outcome of the return. For example, to credit the customer for returned items, select a return disposition code that uses the **Credit** action. Leave this field blank for disposition codes that are used only for purchase order or production receiving. Learn more in [Return reason codes and disposition codes](../../sales-marketing/disposition-and-return-reason-codes.md).

1. On the Action Pane, select **Save**.
1. Repeat these steps for each disposition code that your warehouse processes require.

## Rules for combining settings

Not every combination of settings is valid. Supply Chain Management validates the record when you save it, and it prevents you from saving a combination that it can't process. Keep the following restrictions in mind:

- You can't select a return disposition code that uses the **Credit only** action. The **Credit only** action credits the customer without expecting the items to be returned, so there's nothing for the warehouse to receive.
- If you fill in both the **Return disposition code** field and the **Work template** field, the work template must have a work order type of *Return orders*.
- If the return disposition code uses the *Scrap*, *Replace and scrap*, or *Return to customer* action, you can't set the **Inventory status** field to a status that blocks inventory. Items that these actions handle never enter storage, so there's nothing to block.
- If you set the **Inventory status** field to a status that blocks inventory, the work template can't be one that's defined only for the *Finished goods put away* work order type.

> [!NOTE]
> When a disposition code points to a return disposition code that uses the *Scrap*, *Replace and scrap*, or *Return to customer* action, Supply Chain Management doesn't create putaway work, and it doesn't print a license plate label for the received items. This behavior applies because these actions don't put the items into inventory.

## Make disposition codes available in the mobile app

Creating a disposition code doesn't make it appear on a mobile device. Workers are prompted to enter a code only when the mobile device menu item that they use is configured to ask for one.

To enable the prompt, go to **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**, select the relevant menu item, and set the **Display disposition code** option to *Yes*. Learn more in [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md).

For sales order returns, if the prompt isn't shown during receiving, a Supply Chain Management user must enter a disposition code when they complete the mixed license plate.

## Related information

- [Receive unannounced sales returns](../sales-returns-unannounced.md)
- [Create and configure mobile device menu items](../configure-mobile-devices-warehouse.md)
- [Control warehouse work by using work templates and location directives](../control-warehouse-location-directives.md)
- [Return reason codes and disposition codes](../../sales-marketing/disposition-and-return-reason-codes.md)
- [Set up return disposition codes](../../sales-marketing/set-up-disposition-codes.md)
