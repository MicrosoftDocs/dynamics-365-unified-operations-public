
# required metadata

title: Change mode of delivery operation in POS
description: This topic describes how to configure and use the new change mode of delivery operation in POS
author: hhainesms
manager: annbe
ms.date: 02/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hhainesms
ms.search.validFrom: 2020-02-20
ms.dyn365.ops.version: Release 10.0.11

---
# Using the Change mode of delivery operation in POS for customer orders

This topic describes how to setup and use the **Change mode of delivery** operation in your POS environment. 

In version 10.0.10, the **Change mode of delivery** operation (647) is now available for users to optionally add to their POS screen layouts.

The **Change mode of delivery** operation gives users the ability to make a mode of delivery configuration change to one or more shipment-configured sales lines on the POS transaction in an efficient manner.  In prior versions of the product, users would have to go through the entire **Ship all** or **Ship selected** configuration flows if they wished to change the mode of delivery on an existing line that was configured for shipment.   Requiring users to go through those order creation flows to change one configuration on the shipment was time consuming and could result in accidental changes to the delivery origin or delivery dates for the line that were not intended.   The new **Change mode of delivery** operation was added to provide an alternative method for efficiently updating the mode of delivery on these sales lines.

Refer to the documentation on how to [configure your screen layouts](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-screen-layouts) for more information on how to add this new operation to a button on your POS button grid.

Once configured in POS, when the user selects the **Change mode of delivery** operation, they will be presented with a list page that allows them to choose which lines of the transaction should have their mode of delivery changed.   The user can choose some or all of the lines to change.  Users may also exit without making any changes if necessary.

When presented with the list of lines that can have a mode of delivery change, only sales lines that were previously configured for shipment will be available to choose from.  If the user wishes to change a pickup or carryout designated order line to ship, they must use the **Ship all** or **Ship selected** operations of POS to configure this and not the **Change mode of delivery** operation.  Conversely, if the user wishes to change an existing shipment line to a pickup or carryout, they must use the  **Pickup all**, **Pickup selected**, **Carryout all** or **Carryout selected** operations to achieve that result as changing the mode of delivery on a shipment line to a **Carryout** or **Pickup** configured mode of delivery will not be supported.

Once the lines to update have been selected, the user can click the **Change mode of delivery** function on the Appbar to be presented with the delivery mode options.  If the user has selected multiple lines to change, the application will only display modes of delivery that have been configured to be allowable for all of the selected products.  Because modes of delivery can be configured to support specific products and delivery addresses, if there is a mode of delivery that might be acceptable for one product/address combination but is not acceptable for another selected product/address combination, then this mode of delivery would not be shown.   Users may need to select lines one by one and change the mode of delivery separately if they are trying to achieve a selection of mode of delivery for one product that cannot be supported by another product.  

After the user has selected the desired new mode of delivery, they will be returned to the transaction form.  Users can click on the **Delivery** tab of the transaction list to confirm the updated delivery mode selection on the changed line(s).   
