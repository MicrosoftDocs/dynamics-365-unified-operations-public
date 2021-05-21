---
# required metadata

title: Create returns in point of sale (POS)
description: This topic describes how to initiate returns for cash and carry or customer orders in the Microsoft Dynamics 365 Commerce point of sale (POS) application.
author: hhainesms
ms.date: 05/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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
[!include [banner](includes/preview-banner.md)]

This topic describes how to initiate returns for cash and carry or customer orders in the Microsoft Dynamics 365 Commerce point of sale (POS) application.

> [!NOTE]
> Starting in the Commerce version 10.0.20 release, the **Unified return processing experience in POS** feature can be enabled. This feature provides a more consistent and unified returns process flow within POS, regardless of the transaction type (cash and carry or customer order) or the original channel the order was created in. It is recommended that all organizations enable this new capability to improve the overall processing reliability of returns through the POS application. Once this feature has been enabled, it cannot be disabled.

## Process returns using the return transaction operation

It is recommended that you add the return transaction operation to your POS [screen layout](pos-screen-layouts.md). Prior to the Commerce version 10.0.20 release, the return transaction operation only properly supported the processing of returns for cash and carry transactions. After enabling the **Unified return processing experience for POS** feature in Commerce version 10.0.20 release or later, this operation supports the processing returns originating from cash and carry transactions or customer orders such as "pick up" or "ship to home" orders that are already invoiced.

From the return transaction operation, users can search for a cash and carry transaction or a customer order to return against by entering any one of the following four search criteria:

- Receipt ID
- Order number
- Channel reference ID (also known as the order confirmation ID)
- Invoice ID

These criteria can be entered using a device keyboard, on-screen keypad, or barcode scanner.

After users input their transaction or order reference information, if a match is found the **returnable items** form will appear. This form is where users can specify the items that are being returned and enter return quantities and reason codes. 

For each order line in the returnable products list, the application will display information about the original purchase quantity and any previously processed return quantities. Users will only be able to return quantities that are equal to or less than the available to return quantity.

![Returnable products list](media/returnslist.png)

When processing a return, if a user has the physical product and it has a barcode, the user can scan the barcode of the item to register the return. Scanning a barcode will increase the return quantity by one item per scan, but if you have a barcode label with an embedded quantity, that quantity will be used and applied to the **Returning now** field. 

Users can also manually select items to return on the screen and update the "returning now" quantity using the details panel on the right side of the screen.  

If the maximum available "returning now" quantity is being specified for a transaction, a user can also use the **Select all** operation on the POS Appbar to set the maximum returnable quantity on all lines.

For each line that has a "returning now" quantity, users will need to select a return reason code for each line using the details panel. When returning a cash and carry order, the return reason codes are configured on the store's functionality profile as *infocodes*. When returning a customer order, the return reason codes are configured in the **return reason codes** form in Dynamics 365 Commerce headquarters.

After setting the return quantity and reason code for each item to be returned, users can choose the **Return** operation from the POS Appbar to proceed with the processing.  
Users will then be directed to the POS transaction form. The returnable items selected on the previous screen will be systematically added to the cart with their "returning now" quantities shown as negative quantity lines on the transaction, and the refund total will be calculated. 

It is possible for users to add additional lines to a return transaction if creating an exchange order. It is also possible for users to add more ad-hoc return items to a return transaction using the **Return product** operation for a selected positive quantity sales line that has been added.   

> [!NOTE]
> Using the **Return product** operation in POS will not provide any validation against any original transaction and will allow any product to be returned, so it is recommended that this operation only be allowed for authorized users, or that a manager override is required if used.

If there is a refund due at checkout, organizations can configure [refund payment policies](refund_policy_returns.md) that limit which payment methods the user can choose from to refund the customer. If the original transaction was paid with a credit card, depending on the payment processor and system configuration the user may be prompted with an option to [refund back to the original card](dev-itpro/linked-refunds.md). This option allows a refund to be processed without customers having to swipe their credit card again and leverages the original payment token to issue the refund.

## Other return options in POS

When the **Unified return processing experience in POS** feature has been enabled, users will also be able to initiate a return for a cash and carry transaction or a customer order using the **Show journal** operation in POS. Users can select a transaction from the journal and select the **Return** operation from the POS Appbar. This operation will only be enabled if there are returnable lines on the order and will initiate the same user experience as the **Return transaction** operation.

Users in POS can also use the **Recall order** operation to search for and recall customer orders (cash and carry transactions are not retrievable from this operation). If using the **Recall order** operation, once a customer order has been selected, the **Return** operation on the POS Appbar can also be used to initiate the return of the customer order. This operation will only be enabled if there are returnable lines on the order. Selecting the return operation from the **Recall orders** form will initiate the same user experience as the  **Return transaction** or **Show journal** operations.

## Return orders post as sales orders to headquarters

When the **Unified return processing experience in POS** feature is enabled, all returns created in POS will be written to Commerce headquarters as sales orders with negative lines. When this feature is not enabled in releases prior to Commerce version 10.0.20, users can choose if return orders will be posted as sales orders with negative lines, or if they will be return orders created through the return merchandise authorization (RMA) return order process. The option to create POS returns using the RMA process has been deprecated with the **Unified return processing experience in POS** feature, and all returns created after this feature is enabled will be created as sales orders with negative lines.

## Offline return processing improvements

In most cases, when a return is processed in POS, there is an effort made to validate the current available return quantities through a real time service (RTS) call to headquarters. This validation is to guard against potential fraudulent scenarios where a customer may attempt to return the same item in multiple locations.

In situations where the RTS call is not possible due to network or connectivity issues, a process has been put in place to periodically synchronize return quantity data from headquarters to a store's channel database. This "channel-side" returns tracking can help to ensure that the "available to return" quantities shown in POS are reasonably accurate (even when POS is offline), and that the POS application can still validate the channel-side information to prevent fraudulent returns.

To use the offline return process appropriately, organizations should schedule the **Update return quantities** batch job in Commerce headquarters to run frequently. It is recommended that this job run at the same frequency as the **P job** that pulls new transactions from the Commerce channels into headquarters. The **Update return quantities** job calculates the available return quantity for all sales orders found in headquarters. The "available to return" data calculated by the job must then be sent to your channel databases to update the store channels using the **return quantities** (1200) distribution job. By synchronizing the returnable quantity data from headquarters, if a return is processed in POS when POS is not able to make the RTS call, POS can then rely on the channel-side returns information to validate the "available to return" quantities for a given sales line.  

When RTS is not available and channel-side data is being used by POS for returns validations, users will be shown a warning so that they are aware that they are creating an "offline" return and that there is a small chance that the "available to return" quantity shown in POS is stale and no longer accurate since it's only as accurate as the last time the **update return quantities** job was processed and synchronized to the channel. For example, if a customer had somehow recently processed a return for an order line in another channel and this data was not yet synchronized to the channel databases through the **Update return quantities** job, the customer could go to a different store and attempt to return that same item. If that happens, and the store cannot initiate the RTS call to headquarters to get real-time return data, the application would allow the return again, but would provide a warning to the user that potentially stale information is being used to validate the return. The message the user sees is only a warning and does not prohibit the user from continuing to process the return. If for some reason the channel-side information is not up-to-date and an offline return is processed for a quantity greater than the actual "available to return" quantity, an error may be generated when statement posting runs to create the transaction in headquarters that will need to be addressed.

> [!NOTE]
> When the **Unified returns processing experience in POS** feature is enabled, this will also enable new optional features to support the verification of serialized product returns. For more information, see [Return serial number-controlled products](POS-serial-returns.md).

## Additional resources

[Return serial number-controlled products](POS-serial-returns.md)

[Linked refunds of previously approved and confirmed transactions](dev-itpro/linked-refunds.md)

[Create and update a returns and refunds policy for a channel](refund_policy_returns.md)

[POS user interface visual configurations](pos-screen-layouts.md)


