--- 
title: Quantity is not valid when registering inbound orders 
description: "If the quantity that's allocated for a license plate exceeds the quantity that must still be received, you'll receive the error: 'The quantity is not valid.'"
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# License plate quantity is not valid when registering inbound orders

## Symptoms

When registering inbound orders, you might receive the following error message:

> The quantity is not valid.

If the **License plate grouping policy** field is set to *User defined* for a mobile device menu item that's used to register inbound orders, you receive this error and you can't complete the registration.

## Cause

When *User defined* is used as a license plate grouping policy, the system splits the incoming inventory into separate license plates, as indicated by the unit sequence group. If batch or serial numbers are used to track the item that's being received, the quantities of each batch or serial must be specified per license plate that's registered. If the quantity that's specified for a license plate exceeds the quantity that must still be received for the current dimensions, you receive this error message.

## Resolution

When you register an item by using a mobile device menu item where the **License plate grouping policy** field is set to *User defined*, the system might require that you confirm or enter license plate numbers, batch numbers, or serial numbers.

On the license plate confirmation page, the system will show the quantity that's allocated for the current license plate. On the batch or serial confirmation pages, the system will show the quantity that must still be received on the current license plate. It will also include a field where you can enter the quantity to register for that combination of license plate and batch or serial number. In this case, make sure that the quantity that's being registered for the license plate doesn't exceed the quantity that must still be received.

Alternatively, if too many license plates are being generated on inbound order registration, the value of the **License plate grouping policy** field can be changed to *License plate grouping*, a new unit sequence group can be assigned to the item, or the **License plate grouping** option for the unit sequence group can be inactivated.
