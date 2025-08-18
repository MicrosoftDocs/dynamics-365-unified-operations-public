---
title: Piece picking confirmation
description: Piece picking allows workers to use a mobile device to confirm each piece of inventory during picking or counting work.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 08/18/2025
ms.reviewer: kamaybac
ms.search.form:  WHSRFAutoConfirm, WHSRFMenuItem
---

# Piece picking confirmation

[!include [banner](../includes/banner.md)]

*Piece picking confirmation* allows workers to use a mobile device to confirm each piece of inventory registered during picking or counting work. In this context, *confirm* means that the worker verifies the quantity of each item by scanning a bar code or manually entering the information on the device. For picks, workers can confirm the quantity of work to be processed up to the quantity that is specified on the work to be picked. For counting work, workers can scan the inventory they're counting and track the total amount.

When you enable piece picking, product confirmation is also required. For picking work, you can set the maximum number of pieces that workers can be required to confirm while doing picking work. The maximum quantity is based on the current work unit that is being processed. The counting work type doesn't allow a maximum.

The system considers both the quantity and unit of measure (UOM) that is stored in a scanned bar code. This functionality works for receiving inbound flows (including mixed license plate receiving, purchase order item, transfer order item, and load item). It also works for piece picking, where scanning a bar code quantity adds the quantity to the total number of confirmed pieces and converts between the UOM on the bar code and the work unit. When a worker scans a bar code quantity, the system checks the UOM on the bar code, confirms whether the quantity is allowed for counting on the sequence group and, if so, adds the quantity to the total count.

## Ways to confirm a product

There are two ways to confirm a product during piece picking:

- **Scanning a bar code** – Workers can scan a bar code, which can include quantity information depending on the configuration. If the bar code specifies a quantity, the system automatically adds that amount to the total confirmed pieces. If the bar code doesn't include quantity information, the worker is prompted to enter the quantity manually.
- **Manual entry** – Workers can manually enter the item number to confirm the product. In this case, they must also manually enter the quantity being picked or counted. This method is useful when bar codes aren't configured.

## Enable bar code scanning for products

To allow workers to scan bar codes to confirm a product, make sure the **Scanning** option is enabled for each relevant product. To enable the **Scanning** option, follow these steps:

1. Go to **Product information management \> Products \> Released products**.
1. In the list, find and select the desired product.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Bar codes**.
1. On the Action Pane, select **Edit**.
1. Select the desired bar code.
1. Open the **General** tab.
1. Set **Scanning** to *Yes*.
1. On the Action Pane, select **Save**.

Learn more in [Create a bar code for a product](../pim/tasks/create-bar-code-product.md).

## Where it applies

Piece picking works for all counting work and for the initial pick for any type of work. Piece picking doesn't apply for items that are controlled by serial numbers or for production or kanban picks from a license plate location where the item is set to staging.

## Set up piece picking

To set up piece picking, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Find and select the mobile device menu item that you want to configure.
1. On the Action Pane, select **Work confirmation setup**.
1. Use the buttons on the Action Pane, to add, remove, or edit confirmation settings for each work type as needed. For rows with a **Work type** of *Pick* or *Counting*, make the following settings:
    - **Piece picking confirmation** – Select this check box to allow workers to confirm each piece of inventory from the mobile device. While this box is selected, the **Product confirmation** checkbox is also selected automatically.
    - **Maximum number of pieces** – Enter the maximum number of pieces that workers can be required to confirm while doing picking work. For example, if the **Maximum number of pieces** is set to *1*, the system will prompt the worker to confirm only one product. After confirming the first piece, the worker can manually enter the remaining quantity without additional confirmation prompts. Set to *0* to remove the maximum limit, which means that workers will be prompted to scan or enter values as many times as needed until the entire picking quantity has been confirmed. This setting is only available when **Work type** is *Pick* and **Piece picking confirmation** is enabled.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
