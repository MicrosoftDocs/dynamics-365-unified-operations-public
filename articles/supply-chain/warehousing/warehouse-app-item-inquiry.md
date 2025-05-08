---
title: Warehouse mobile app item inquiry
description: Warehouse mobile app item inquiry
author: alkorote
ms.author: alkorote
ms.topic: how-to
ms.date: 05/01/2025
---
# Query item data using Warehouse Management mobile app: Item Inquiry

The Item Inquiry capability in the Warehouse Management mobile app for Microsoft Dynamics 365 Supply Chain Management enables warehouse workers to quickly view key inventory details — such as location, available quantity, and reserved quantity — for specific items. This feature improves visibility into warehouse stock and supports efficient decision - making during daily operations.

> [!NOTE]
> This functionality does not display batch numbers or serial IDs.  
> If the item is a product variant, information will be shown for the captured product dimensions (such as color or size).

## Key capabilities
- Fast access to inventory details – workers can view where an item is stored and see how much stock is available or reserved.
- Support for product variants – if an item uses product dimensions (for example, color or size), the app will show data for the relevant variant based on the scanned or entered information.

## Example scenario
A warehouse worker wants to verify stock levels of a particular item before picking. Using the Item Inquiry menu item on the mobile app, the worker scans the item barcode. The app displays:
- The warehouse location(s) where the item is stored
- The available and reserved quantities
- Details based on the product variant (e.g., Red, Size L)

This allows the worker to confirm inventory without interrupting active picking or receiving workflows.

## Set up the mobile device menu item
To enable this functionality, you must configure the mobile device menu item in the system.

### Prerequisites

To work through the example scenarios that are described in this article, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the *USMF* legal entity (company) before you begin.

### Configure the menu item
Create the **Item inquiry** menu item by following these steps.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the Action Pane, **New** to add a mobile device menu item.
1. Set the following values for the new menu item:
    - **Menu item name:** *Item inquiry*
    - **Title:** *Item Inquiry*
    - **Mode:** *Indirect*

1. On the **General** FastTab, configure:

    - **Activity code:** *Item inquiry*
    - **Use process guide:** *Yes* (This value is automatically selected.)

Once configured, this menu item can be added to mobile device menus for warehouse users, enabling direct access from the Warehouse Management mobile app.
