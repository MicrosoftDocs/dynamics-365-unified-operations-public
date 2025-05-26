---
title: Query item data on a mobile device
description: Learn how to create a mobile device menu item that lets warehouse workers view key inventory details.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/14/2025
ms.custom: 
  - bap-template
---

# Query item data on a mobile device

*Item inquiry* mobile device menu items allow warehouse workers to view key inventory details for specific items, including location, available quantity, and reserved quantity. This feature improves visibility into warehouse stock and supports efficient decision-making during daily operations.

> [!NOTE]
> This functionality doesn't display batch numbers or serial IDs. If an item is a product variant, information is shown for the captured product dimensions (such as color or size).

## Key capabilities of the item inquiry feature

*Item inquiry* mobile device menu items provide the following key capabilities:

- **Fast access to inventory details** – Workers can view where an item is stored and see how much stock is available or reserved.
- **Support for product variants** – If an item uses product dimensions such as color or size, the app shows data for the relevant variant based on the scanned or entered information.

## Example scenario

A warehouse worker wants to verify stock levels of a particular item before picking. The worker selects the **Item Inquiry** menu item on the mobile app and then scans the item barcode. In response, the app displays the following information:

- Warehouse locations where the item is stored.
- Available and reserved quantities.
- Details based on the product variant (such as color or size values).

This information allows the worker to confirm inventory without interrupting active picking or receiving workflows.

## Set up the mobile device menu item

To enable this functionality, you must configure the mobile device menu item in the system. Create the **Item inquiry** menu item by following these steps.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, **New** to add a mobile device menu item.
1. Set the following values for the new menu item:
    - **Menu item name** – Enter an internal name for the menu item (for example, *Item inquiry*).
    - **Title** – Enter the title for the menu item as workers should see it (for example, *Item inquiry*).
    - **Mode** – Select *Indirect*.

1. On the **General** FastTab, set the following values:
    - **Activity code** – Select *Item inquiry*.
    - **Use process guide** – This setting is automatically set to *Yes* and can't be changed.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device menu** and add the new menu item to each menu where it should be available to workers. Learn more in [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).
