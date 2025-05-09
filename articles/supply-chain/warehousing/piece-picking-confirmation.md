---
title: Piece picking confirmation
description: Piece picking allows you to confirm each piece of inventory through picking or counting work on a mobile device, including a table that defines options.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form:  WHSRFAutoConfirm, WHSRFMenuItem
---

# Piece picking confirmation

[!include [banner](../includes/banner.md)]

Piece picking allows you to confirm each piece of inventory through picking or counting work on a mobile device. For picks, you can confirm the quantity of work to be processed up to the quantity that is specified on work to be picked. For counting work, you can scan the inventory you are counting and track the total amount.

When you enable piece picking, product confirmation is automatically selected. For work-type picks, you can set a maximum number of pieces. This allows you to set a maximum to the number of pieces that must be confirmed during the work process. The maximum quantity is based on the current work unit that is being processed. The counting work type does not allow a maximum.

You can also use the quantity and unit of measure (UOM) that is associated with a scanned bar code. This will work for receiving on inbound flows including mixed license plate receiving, purchase order item, transfer order item, and load item. It also works for piece picking where scanning the bar code will add the quantity to the total number of confirmed pieces converting between the UOM on the bar code and the work unit. When counting the UOM on the bar code, if it is confirmed that the quantity is allowed for counting on the sequence group, the quantity will be added to the total count.

## Where it applies

Piece picking works for all counting work and for the initial pick for any type of work. Piece picking does not apply if the item is controlled by serial numbers or if it is a production or kanban pick from a license plate (LP) location and the item is set to staging.

## Set up piece picking

1.  On a mobile device menu item, open the setup form for work confirmation: Warehouse management > **Warehouse management** > **Setup** > **Mobile device** > **Mobile device menu items**. 
2. From the mobile device menu item, open Work confirmation setup.

The following options become available for selection when the work type is pick or counting.


|           Option           |                                                                            Description                                                                            |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Piece picking confirmation | Available for pick and counting work types. Product confirmation is automatically selected. Allows you to confirm each piece of inventory from the mobile device. |
|  Maximum number of pieces  |                   Available for pick work if piece picking confirmation is enabled. Sets a limit to the number of pieces that you must confirm.                   |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
