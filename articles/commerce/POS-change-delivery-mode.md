---
title: Change mode of delivery in POS
description: Learn how to configure and use the change mode of delivery operation in Microsoft Dynamics 365 Commerce point of sale (POS).
author: hhainesms
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2020-02-20
ms.custom: 
  - bap-template
---

# Change mode of delivery in POS

[!include [banner](includes/banner.md)]

This article describes how to configure and use the change mode of delivery operation in Microsoft Dynamics 365 Commerce point of sale (POS).

In Dynamics 365 Commerce versions 10.0.10 and later, you can add the **Change mode of delivery** operation (647) to your POS screen layouts.

The change mode of delivery feature provides you with the option to change the mode of delivery for one or more shipment-configured sales lines on the POS transaction. In previous versions of Commerce, you had to go through the full **Ship all** or **Ship selected** configuration flows if you wanted to change the mode of delivery on an existing line that was configured for shipment. This process was time consuming and could result in accidental changes to the delivery origin or delivery dates for the line. The new functionality provides an alternative method for efficiently updating the mode of delivery on these sales lines.

For more information about how to add an operation to a button on your POS button grid, see [Screen layouts for the point of sale](pos-screen-layouts.md).

After you configure this feature in POS, when you select **Change mode of delivery**, you see a list page that allows you to choose the lines of the transaction that you want to change the mode of delivery for. You can choose some or all of the lines, or exit without making any changes. The sales lines that you previously configured for shipment are the only lines in the list that you can change. If you want to change a line designated for pickup or carryout to ship, you must use the **Ship all** or **Ship selected** operations. Conversely, if you want to change a line designated as a shipment to a pickup or carryout, you must use the  **Pickup all**, **Pickup selected**, **Carryout all**, or **Carryout selected** operations.

After you select the lines that you want to change, select **Change mode of delivery** to be prompted to select the delivery mode options. If you selected multiple lines to change, POS only displays modes of delivery that you configured as allowable for all of the selected products. Modes of delivery can be configured to support specific products and delivery addresses. If there's a mode of delivery that's acceptable for one product and address combination but isn't acceptable for another selected product and address combination, the mode of delivery isn't available. You might need to select lines one by one and change the mode of delivery for each line separately if you want to select a mode of delivery for one product that isn't supported by another product.  

After you select the new mode of delivery, the transaction page is displayed. To review your new delivery mode selections, select the **Delivery** tab on the transaction list.

## Additional resources

[Create call center orders](tasks/create-call-center-orders.md)

[Customize transactional emails by mode of delivery](customize-email-delivery-mode.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
