---
# required metadata

title: Process a customer order pick up through Point of Sale
description: This topic explains user capabilities available in the Point of Sale application for processing a customer order pickup.
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
ms.reviewer: 
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: hhaines
ms.search.validFrom:
ms.dyn365.ops.version: 
---

# Customer order pick up processing in Point of Sale

When a [customer order](https://docs.microsoft.com/en-us/dynamics365/commerce/customer-orders-overview) is created for a store pick up, the Point of Sale (POS) application provides capability to allow store users to initiate the pick up of inventory which executes the final payment capture (if needed) and executes the finalization of inventory and financial posting steps for the product quantities that are picked up.

Users can execute the pick up operation from the **Recall order** operation in POS or from the **Order fulfillment** operation in POS.  Users must first search for and locate the order to be picked up and select the order (if using the Recall order operation) or search for and select one or more order lines (if using the Order fulfillment operation) to enable the **Pick up** operation.   If the selected order or order lines are not configured for pick up at the user's store, or if the order has already been fully picked up, the **Pick up** operation will be disabled.

 ![Pick up operation](media/pickupoperation.png)

In version 10.0.17 and later, the **Improved user experience for pick up order processing in Point of Sale** feature has been added and can be enabled through **Feature management** in Commerce Headquarters (HQ).  When this feature is not enabled, the POS application is limited in allowing users to choose pick up quantities and always assumes the full quantity ordered for the line will be picked up. The older pick up user experience seen when the feature is not enabled can be problematic in that it does allow users to accidentally forget to select certain items for pick up when executing the pick up operation through order fulfillment.  When the new **Improved user experience for pick up order processing in Point of Sale** feature is enabled, users will have more control of selecting which products will be picked up and the quantity of these products that will be picked up.  Users will also not be forced to select every line of the sales order from the order fulfillment form before clicking pickup as the new user experience will ensure the user is aware of all eligble items available for pick up for the order and give them the opportunity to choose multiple lines for pick up, even if only one product line is selected.

When the **Improve user experience for pick up order processing in Point of Sale** feature is enabled, after selecting the **Pick up** operation, the user will be provided with a dialog that will allow them to select the specific items and quantities that will be picked up.  By default, any ordered quantity that has it's inventory in a picked or packed state will be considered eligible for pick up and this quantity will be defaulted as the assumed pick up quantity.  Users can edit this quantity if desired.  As long as the quantity entered does not exceed the total open (non-invoiced) quantity for the selected line, it can be picked up.  

   ![Pick up line selection dialog](media/pickupselect.png)

After the user has chosen their pick up quantities, clicking the **Pick up** button from the dialog will transfer the user to the POS **Transaction** form.  If any pre-authorized credit card payments are on file and the [omni-channel payments](https://docs.microsoft.com/en-us/dynamics365/commerce/omni-channel-payments) feature is enabled, the user will also be prompted to apply the payment before being transfered to the transaction form.  

Once in the transaction form, the system will calculate any amounts due by calculating the total due for the selected pick up items and subtracting out any previously applied deposits or credit card authorized payments.   Users will be required to process payment to complete the pick up transaction.   If there is no payment due, it is possible to [configure your transaction screen layout](https://docs.microsoft.com/en-us/dynamics365/commerce/pos-screen-layouts) with the **Conclude transaction** operation, this operation allows the user to complete the transaction without having to choose a payment method and can only be used when the amount due is =$0.  If the **Conclude transaction** operation is not available on the screen layout, users can also just click the $0.00 amount due hyperlink found in the totals panel to conclude the transaction without having to choose a payment method.

![Pick up transaction(media/pickupcart.png)

##Changing pick up lines or quantities from the transaction form

After users have chosen the items to pick up, if the user decides to change the quantity to be picked up, the **Set quantity** operation can be utilized to raise or lower the pick up quantity.   Users will not be allowed to set the pick up quantity to "0" using this operation.  Users will also not be able to increase the quantity for pick up to a value that is greater than the non-invoiced quantity remaining for the ordered line.   If a user wishes to remove a pick up line completely from the transaction cart, they should use the **Void transaction** operation to abort the current pick up transaction and start the **Pick up** operation flow over again (and this time not select the product that will not be picked up).

If the **Improve user experience for pick up order processing in Point of Sale** feature is enabled, organizations will also be able to add a new **Change pickup lines** operation button to their POS transaction screen layout.  After a user has created the pick up transaction cart in POS with selected items, if they decide to change the pick up items but do not wish to void the entire transaction, using the **Change pickup lines** operation will provide users with the dialog to allow them to re-select/change the pick up items and quantities. Changes made by the user will update the transaction cart. Users will receive an error if they attempt to set all line pickup quantities to zero using this operation as this is not supported.

![Pick up transaction(media/pickupchange.png)
