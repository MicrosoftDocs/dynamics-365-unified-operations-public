---
# required metadata

title: Create returns in point of sale (POS)
description: This topic describes how to initiate returns for cash and carry or customers orders in the Dynamics 365 Commerce point of sale (POS) application
author: hhainesms
ms.date: 05/20/2021
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
ms.dyn365.ops.version: Release 10.0.20

---

# Create returns in point of sale (POS)

[!include [banner](includes/banner.md)]

> [!NOTE]
> Starting in version 10.0.20, the **Unified return processing experience in POS** feature can be enabled. This feature will provide a more consistent and unified returns process flow within POS, regardless of the transaction type (cash and carry or customer order) or the channel the order was created in originally.  It is recommended that all organizations enable this new capability to improve the overall processing reliability of your returns through the POS application.  It’s important to note that once this feature has been enabled, it cannot be disabled.

This document provides functional documentation for processing returns through the Point of Sale (POS) application when feature **Unified return processing experience in POS** has been enabled.

## Processing returns using the Return Transaction operation
It is recommended that the **Return Transaction** operation be added to your POS [screen layout](pos-screen-layouts.md). Prior to version 10.0.20, the **Return transaction** operation only properly supported the processing of returns for cash and carry transactions, but after enabling the **Unified return processing experience for POS** feature, this operation will now support processing returns originating from cash and carry transactions or customer orders such as pickup or ship to home orders that are already invoiced.

From the return transaction operation, the user can search for a cash and carry transaction or a customer order to return against by inputting any one of these 4 search criteria:

1.	Receipt ID
2.	Order number
3.	Channel reference ID (a.k.a. Order Confirmation)
4.	Invoice ID

This critera can be entered using the device keyboard, onscreen keypad, or barcode scanner.

After the user inputs their transaction/order reference information, if a match is found, the **returnable items** form appears.  This form is where the user can choose the items that are being returned and enter specific return quantities and reason codes. 

For each order line in the returnable products list, the application will display information about the original purchase quantity and any previously processed return quantities. Users will only be able to return quantities that are equal to or less than the available to return quantity.

![Returnable products list](media/returnslist.png)

When processing the return, if the user has the physical product and it is barcoded, the user may scan the barcode of the item to register the return.  The **Returning now** field will be updated with the return quantity.  Typically, scanning a barcode would increase the return qty by 1 per each scan, but if you have a barcode label with an embedded quantity, that quantity will be used and applied to the **Returning now** field. 

Users can also manually select items to return on the screen and update the returning now quantity using the details panel on the right side of the screen.  

If the full available to return quantity is being returned for the transaction, users can also use the **select all** operation from the Appbar to set the maximum returnable quantity on all lines.

For each line that has a **returning now** quantity, users will need to select a return reason code for each line through the details panel.  When returning a cash and carry order, the return reason codes are configured on the store’s **Functionality profile** as **infocodes**.   When returning a customer order, the return reason codes are configured in the **return reason codes** form in Dynamics 365 Commerce Headquarters (HQ).

After setting the return quantity and reason code for each item to be returned, the user can choose the **Return** operation from the Appbar to proceed with the processing.  
Users will be taken to the POS transaction form.  The returnable items chosen on the previous screen will be added systematically to the cart with their returning now quantities shown as negative quantity lines on the transaction.  At this time refund total will be calculated. 

It is possible for users to add additional lines to the returns transaction if creating an exchange order or even add more ad-hoc return items to the transaction using the **Return product** operation for a selected positive quantity sales line that has been added.   

> [!NOTE]
> Using the **Return product** operation in POS will not provide any validation against any original transaction and will allow any product to be returned, therefore this operation is recommended to only be given to authorized users or require a manager override if used.

At checkout, if there is a refund due, organizations may configure [refund payment policies](refund_policy_returns.md) which can limit which payment methods the user can choose from to refund the customer. If the original transaction was paid with a credit card, depending on your payment processor and system configuration, the user may be prompted with an option to [refund back to the original card](linked-refunds.md).  This allows a refund to be processed without the customer having to swipe their credit card again and leverages the original payment token to issue the refund.

## Other return options in POS
When the **Unified return processing experience in POS** feature has been enabled, users will also be able to initiate a return for a cash and carry transaction or a customer order using the **Show journal** operation in POS.  Users can select a transaction from the journal and select the **Return** operation from the Appbar. This operation will only be enabled if there are returnable lines on the order. This will initiate the same user experience that the user would have if they had used the **Return transaction** operation.

Users in POS can also use the **Recall order** operation in POS to search for and recall customer orders (cash and carry transactions are not retrievable from this operation).  If using the **Recall order** operation, once a customer order has been selected, the **Return** operation on the Appbar can also be used to initiate the return of the customer order.  This operation will only be enabled if there are returnable lines on the order. Selecting the return operation from the **Recall orders** form will also initiate the same return product user experience that the user would have if they would have initiated the return using the  **Return transaction** or **Show journal** operations.

## Return orders post as sales orders to HQ
When the **Unified return processing experience in POS** feature is enabled, all returns created in POS will be written to Commerce Headquarters (HQ) as sales orders with negative lines.  In previous versions, and when this feature is not enabled, configurations are available to choose if return orders will be posted as sales orders with negative lines, or if they will be return ordders created through the RMA/Return order process. The option to create POS returns using the RMA process has been deprecated with the **Unified return processing experience in POS** feature, and all returns created after this feature is enabled will be created as sales orders with negative lines.

## Offline return processing improvements
In most cases, when a return is processed in POS, there is an effort made to validate the current available return quantities through a real time service (RTS) call to HQ. This validation is to guard against potential fraudulent scenarios whereby a customer may attempt to return the same item in multiple locations.

In situations where the RTS call is not possible due to network or connectivity issues, a new process has been put in place to periodically synchronize return quantity data from HQ to the Store's channel database. This 'channel-side' returns tracking can help to ensure the available to return quantities shown in POS, even when POS it is offline, are reasonably accurate and that the application can still validate the channel-side information to prevent over-returning of items.

To use this process appropriately, organizations should schedule and run the **update return quantities** batch job from Commerce Headquarters (HQ) on a frequent schedule. It is recommended that this job run at the same frequency as the P job which pulls new transactions from the Commerce channels into HQ.  The **update return quantities** job calculates the available return quantity for all sales orders found in HQ.   This 'available to return' data calculated by the job must then be sent to your channel databases to update the store channels using the **return quantities** (1200) distribution job.   By synchronizing the returnable quantity data from HQ, if a return is processed in POS when POS is not able to make the RTS call, POS can then rely on the channel-side returns information to validate the available to return quantities for a given sales line.  

When RTS is not available and the channel-side data is being used by POS for returns validations, users will be shown a warning so that they are aware that they are creating an “offline” return and that there is a small chance that the available to return quantity shown in POS is stale and no longer accurate since it's only as accurate as the last time the **update return quantities** job was processed and synced to the channel.  For example, if the customer had somehow recently processed a return for an order line in another channel and this data was not yet synced to the channel databases through the **update return quantities** job, this customer could go to a different store and attempt to return that same item.  If this happens, and the store cannot initiate the RTS call to HQ to get real time return data, the application would allow the return again, but would provide a warning to the user that potentially stale information is being used to validate the return.  The message the user will see is only a warning and does not prohibit the user from continuing to process the return.   If for some reason the channel-side information is not up to date and an offline return is processed for a qty greater than the actual available to return qty, when statement posting runs to create the transaction in HQ, there may be an error generated that will need to be addressed in HQ.

> [!NOTE]
> When the **Unified returns processing experience in POS** feature is enabled, this will also enable new optional features to support the verification of serialized product returns.  Please see the [Returning serial number controlled products](POS-serial-returns.md)documentation for more information.
