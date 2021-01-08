---
# required metadata

title: Process a customer order pickup in POS
description: This topic explains functionality available in the POS application for processing a customer order pickup.
author: Hhainesms
manager: annbe
ms.date: 01/06/2021
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: hhaines
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: 10.0.8
---

# Process a customer order pickup in POS

When a [customer order](customer-orders-overview.md) is created for a store pickup, a store user can start the pickup of inventory using the point of sale (POS) application. POS will execute the final payment capture as needed, and complete the inventory and financial posting steps for the quantities that are picked up.

A store user can perform the pickup with the **Recall order** operation or the **Order fulfillment** operation in POS. To enable the **Pick up** operation, the user must first search for and locate the order to be picked up and select the order (if using the **Recall order** operation), or search for and select one or more order lines (if using the **Order fulfillment** operation). If the selected order or order lines aren't configured for pickup at the specific store, or if the order has already been fully picked up, the **Pick up** operation will be disabled.

![Pick up operation](media/pickupoperation.png)

In Commerce version 10.0.17 and later, the **Improved user experience for pick up order processing in Point of Sale** feature can be enabled through **Feature management** in Commerce headquarters. If this feature isn't enabled, users can't choose pick up quantities. In other words, the full quantity ordered for the line is by default the quantity to be picked up. This experience can be problematic because a user may forget to select certain items for pickup when executing the pickup operation through order fulfillment. When the **Improved user experience for pick up order processing in Point of Sale** feature is enabled, users have more control over selecting which products will be picked up and the quantity of the products to be picked up. Users don't have to select every line of the sales order from the order fulfillment page before they select pickup. All of the items that can be picked up will be displayed. The user can choose multiple lines for pickup even if only one product line is selected.

When the **Improve user experience for pick up order processing in Point of Sale** feature is enabled and the user selects the **Pick up** operation, a dialog is displayed where the user can select the specific items and quantities to be picked up. By default, any ordered quantity with inventory in a picked or packed state is considered eligible for pickup and that quantity is the default pickup quantity. The user can change the quantity as long as the quantity entered isn't zero and doesn't exceed the total open (non-invoiced) quantity for the selected line.  

![Pick up line selection dialog](media/pickupselect.png)

When the user chooses the quantities to be picked up and selects **Pick up**, the **Transaction** page is displayed. If the [omni-channel payments](omni-channel-payments.md) feature is enabled and there are pre-authorized credit card payments on file, the user must apply the payment.  

Once on the transaction page, the system calculates the amounts due by computing the total due for the selected pickup items and subtracting any previously applied deposits or credit card authorized payments. The user must process payment to complete the pickup transaction. If the [transaction screen is configured](pos-screen-layouts.md) with the **Conclude transaction** operation and there's no amount due, the user can complete the transaction without choosing a payment method. If the **Conclude transaction** operation isn't available, the user can select the **$0.00 amount due** link in the **Totals** panel to conclude the transaction without having to choose a payment method.

![Pick up transaction screen 1](media/pickupcart.png)

## Change pick up lines or quantities

If the user needs to change the pickup quantity after they've selected the items to be picked up, they can select **Set quantity** and make the change. The user can't set the pickup quantity to "0" or increase the quantity to a value that's greater than the non-invoiced quantity that remains for the ordered line. If the user wants to remove a pickup line from the transaction cart, they can select **Void transaction**. The current transaction will be stopped and the **Pick up** operation flow will be restarted.

If the **Improve user experience for pick up order processing in Point of Sale** feature is enabled, organizations can add the **Change pickup lines** operation button to their POS transaction screen layout. After a user creates the pickup transaction cart in POS and selects items, the user can select **Change pickup lines** if they need to change the pickup items but don't want to void the entire transaction. With the **Change pickup lines** operation, the user can change the pickup items and quantities. The transaction cart is then updated with the changes.

![Pick up transaction screen 2](media/pickupchange.png)
