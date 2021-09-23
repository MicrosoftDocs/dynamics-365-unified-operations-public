---
# required metadata

title: Change mode of delivery in POS
description: This topic describes how to configure and use the change mode of delivery operation in POS.
author: hhainesms
ms.date: 03/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hhaines
ms.search.validFrom: 2020-02-20
ms.dyn365.ops.version: Release 10.0.11

---

# Change mode of delivery in POS

[!include [banner](includes/banner.md)]

This topic describes how to set up and use the "change mode of delivery" functionality in your point of sale (POS) environment. 

In Dynamics 365 Commerce versions 10.0.10 and later, the **Change mode of delivery** operation (647) is available to add to your POS screen layouts.

The change mode of delivery feature provides you with the option to change the mode of delivery for one or more shipment-configured sales lines on the POS transaction. In previous versions of Commerce, you had to go through the full **Ship all** or **Ship selected** configuration flows if you wanted to change the mode of delivery on an existing line that was configured for shipment. This process was time consuming and could result in accidental changes to the delivery origin or delivery dates for the line. The new functionality provides an alternative method for efficiently updating the mode of delivery on these sales lines.

For more information about how to add an operation to a button on your POS button grid, see [Screen layouts for the point of sale](pos-screen-layouts.md).

After this feature is configured in POS, when you select **Change mode of delivery**, you will be presented with a list page that allows you to choose the lines of the transaction that you want to change the mode of delivery for. You can choose some or all of the lines, or exit without making any changes. The sales lines that were previously configured for shipment are the only lines in the list that you can change. If you want to change a line designated for pickup or carryout to ship, you must use the **Ship all** or **Ship selected** operations. Conversely, if you want to change a line designated as a shipment to a pickup or carryout, you must use the  **Pickup all**, **Pickup selected**, **Carryout all**, or **Carryout selected** operations.

After you select the lines that you want to change, click **Change mode of delivery** to be prompted to select the delivery mode options. If you selected multiple lines to change, POS will only display modes of delivery that have been configured as allowable for all of the selected products. Modes of delivery can be configured to support specific products and delivery addresses. If there is a mode of delivery that is acceptable for one product and address combination but is not acceptable for another selected product and address combination, the mode of delivery is not available. You may need to select lines one by one and change the mode of delivery for each line separately if you want to select a mode of delivery for one product that is not supported by another product.  

After you select the new mode of delivery, the transaction page is displayed. To review your new delivery mode selections, select the **Delivery** tab on the transaction list.

## Additional resources

[Create call center orders](tasks/create-call-center-orders.md)

[Customize transactional emails by mode of delivery](customize-email-delivery-mode.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]