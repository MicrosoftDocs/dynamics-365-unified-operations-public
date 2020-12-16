---
# required metadata

title: Customer orders in Point of Sale (POS)
description: This topic provides information about customer orders in Point of Sale (POS). Customer orders are also known as special orders. The topic includes a discussion of related parameters and transaction flows.
author: josaw1
manager: AnnBe
ms.date: 09/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 260594
ms.assetid: 6fc835ef-d62e-4f23-9d49-50299be642ca
ms.search.region: global
ms.search.industry: Retail
ms.author: anpurush
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Release 10.0.14


---

# Customer orders in Point of Sale (POS)

[!include [banner](includes/banner.md)]

This topic provides information about how to create and manage customer orders in Point of Sale (POS). Customer orders can be used to capture sales where shoppers want to pick up products on a later date, pick up products from a different location, or have items shipped to them. 

In an omni-channel commerce world, many retailers provide the option of customer orders, or special orders, to meet various product and fulfillment requirements. Here are some typical scenarios:

- A customer wants products to be delivered to a specific address on a specific date.
- A customer wants to pick up products from a store or location that differs from the store or location where the customer purchased those products.
- A customer inside a store location wants to order products today and pick them up from the same store location on a later date.

Retailers can use customer orders to minimize lost sales that stock outages might otherwise cause, because the merchandise can be delivered or picked up at a different time or place.

## Set up customer orders
Before you try to use customer order functionality in POS, make sure that you complete all the required configurations in Commerce headquarters.

### Configure modes of delivery

To use customer orders, you must configure modes of delivery that the store channel can use. You must define at least one mode of delivery that can be used when order lines are shipped to a customer from a store. You must also define at least one pickup mode of delivery that can be used when order lines are picked up from the store. Modes of delivery are defined on the **Modes of delivery** page in Commerce headquarters. For more information about how to set up modes of delivery for Commerce channels, see [Define delivery modes](https://docs.microsoft.com/dynamics365/commerce/configure-call-center-delivery#define-delivery-modes).

![Modes of delivery page](media/customer-order-modes-of-delivery.png)


### Set up fulfillment groups

Some stores or warehouse locations might not be able to fulfill customer orders. By configuring fulfillment groups, an organization can specify which stores and warehouse locations are shown as options to users who create customer orders in POS. Fulfillment groups are configured on the **Fulfillment groups** page. Organizations can create as many fulfillment groups as they require. After a fulfillment group is defined, it's linked to a store by using a button on the **Set up** tab on the Action Pane of the **Stores** page.

In Commerce version 10.0.12 and later, organizations can define whether the warehouse or warehouse/store combinations that are defined in fulfillment groups can be used for shipping, for pickup, or for both shipping and pickup. Therefore, the store has additional flexibility to drive the warehouse and store options that are shown to users who create an order for pickup versus an order for shipment. To take advantage of these configuration options, you must turn on the **Ability to specify locations as "Shipping" or "Pickup" enabled within Fulfillment group** feature. If a warehouse that is linked to a fulfillment group isn't a store, it can be configured only as a shipping location. It can't be used when orders for pickup are configured in POS.

![Fulfillment groups page](media/customer-order-fulfillment-group.png)

### Configure channel settings

When you work with customer orders in POS, you must consider some of the settings of the store channel. These settings are found on the **Stores** page in Commerce headquarters.

- **Warehouse** – This field indicates the warehouse that is used to fulfill orders that are configured for shipment from the store.
- **Fulfillment group assignment** – Select this button (on the **Set up** tab on the Action Pane) to link the fulfillment groups that are referenced to show options for pickup locations or shipment origins when customer orders are created in POS.
- **Use destination-based tax** – This option indicates whether the shipping address is used to determine the tax group that is applied to order lines that are shipped to the customer's address.
- **Use customer-based tax** – This option indicates whether the tax group that is defined for the customer's delivery address is used to tax customer orders that are created in POS for shipment to the customer's home.

![Store channel setup on the Stores page](media/customer-order-all-stores.png)

### Set up customer order parameters

Before you try to create customer orders in POS, you must configure the appropriate parameters in Commerce headquarters. These parameters can be found on the **Customer orders** tab of the **Commerce parameters** page.

- **Default order type** – You can specify the order type that is assigned by default to customer orders that are created in POS. These customer orders can be either sales orders or quotation orders. Regardless of the default order type, users can still create both sales orders and customer orders from POS.
- **Default deposit percentage** – Specify the percentage of the order total amount that the customer must pay as a deposit before an order can be confirmed. Depending on their privileges, store associates might be able to override the amount by using the **Deposit override** operation in POS, if that operation is configured for the transaction screen layout.
- **Pickup mode of delivery** – Specify the mode of delivery that should be applied to sales order lines that are configured for pickup in POS.
- **Carryout mode of delivery** – Specify the mode of delivery that should be applied to sales order lines that are considered carryout order lines when a mixed cart is created, where some lines will be picked up or shipped, and other lines will be carried out by the customer immediately.
- **Cancellation charge percentage** – If a charge should be applied when a customer order is canceled, specify the amount of that charge.
- **Cancellation charge code** – Specify the Accounts receivable charge code that should be used when a cancellation charge is applied to canceled customer orders through POS. The charge code defines the financial posting logic for the cancellation charge.
- **Shipping charge code** – If the **Use advanced auto charges** option is set to **Yes**, this parameter setting has no effect. If that option is set to **No**, users will be prompted to manually enter a shipping charge when they create customer orders in POS. Use this parameter to map an Accounts receivable charge code that will be applied to orders when users enter a shipping charge. The charge code defines the financial posting logic for the shipping charge.
- **Use advanced auto charges** – Set this option to **Yes** to use system-calculated auto charges when customer orders are created in POS. These auto charges can be used to calculate shipping fees or other order or item-specific charges. For more information about how to set up and use advanced auto charges, see [Omni-channel advanced auto charges](https://docs.microsoft.com/dynamics365/commerce/omni-auto-charges).

![Customer orders tab on the Commerce parameters page](media/customer-order-parameters.png)

### Update transaction screen layouts in POS

Make sure that the POS [screen layout](https://docs.microsoft.com/dynamics365/commerce/pos-screen-layouts) is configured to support the creation and management of customer orders, and that all required POS operations are configured. Here are some of the POS operations that are recommended to correctly support customer order creation and management:
- **Ship all products** – This operation is used to specify that all lines in the transaction cart will be shipped to a destination.
- **Ship selected products** – This operation is used to specify that selected lines in the transaction cart will be shipped to a destination.
- **Pick up all products** – This operation is used to specify that all lines in the transaction cart will be picked up from a selected store location.
- **Pick up selected products** – This operation is used to specify that selected lines in the transaction cart will be picked up from a selected store location.
- **Carry out all products** – This operation is used to specify that all lines in the transaction cart will be carried out. If this operation is used in POS, the customer order will be converted to a cash-and-carry transaction.
- **Carryout out selected products** – This operation is used to specify that selected lines in the transaction cart are being carried out by the customer at the time of purchase. This operation is useful only in a [hybrid order](https://docs.microsoft.com/dynamics365/commerce/hybrid-customer-orders) scenario.
- **Recall order** – This operation is used to search and retrieve customer orders so that POS users can edit, cancel, or perform fulfillment-related operations on them as required.
- **Change mode of delivery** – This operation can be used to quickly change the mode of delivery for lines that are already configured for shipment, without requiring that users go through the "ship all products" or "ship selected products" flow again.
- **Deposit override** – This operation can be used to change the deposit amount that the customer will pay for the selected customer order.

![Operations on the POS transaction screen](media/customer-order-screen-layout.png)

## Working with customer orders in POS
> [!NOTE] Using Revenue recognition in Commerce channels - Revenue Recognition functionality is not currently supported for use in Commerce channels (e-Commerce, Point of Sale, Call Center).  Items configured with revenue recognition should not be added to orders created in Commerce channels. 

### Create a customer order for products that will be shipped to the customer

1. On the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Select **Ship selected** or **Ship all** to ship the products to an address on the customer account.
4. Select the option to create a customer order.
5. Confirm or change the "ship from" location, confirm or change the shipping address, and select a shipping method.
6. Enter the customer's desired order shipment date.
7. Use the payment functions to pay for any calculated amounts that are due, or use the **Deposit override** operation to change the amounts that are due, and then apply payment.
8. If the full order total wasn't paid, enter a credit card that will be captured for the balance that is due on the order when it's invoiced.

### Create a customer order for products that the customer will pick up

1. On the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Select **Pick up selected** or **Pick up all** to initiate the order pickup configuration.
4. Select the store location where the customer will pick up the selected products.
5. Select a pickup date.
6. Use the payment functions to pay for any calculated amounts that are due, or use the **Deposit override** operation to change the amounts that are due, and then apply payment.
7. If the full order total wasn't paid, select whether the customer will provide payment later (at pickup), or whether a credit card will be tokenized now, and then used and captured at the time of pickup.

### Edit an existing customer order

Retail orders that are created in either the online or store channel can be recalled and edited through POS as required.

> [!IMPORTANT]
> Orders that are created in a call center channel can't be edited through POS if the [Enable order completion](https://docs.microsoft.com/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) setting is turned on for the call center channel. To ensure correct payment processing, orders that originated in a call center channel and that use Enable order completion functionality must be edited through the call center application in Commerce headquarters.

In Commerce version 10.0.13 and earlier, users can edit supported customer orders through POS only if the orders are fully open. If any lines of an order have already been processed to fulfillment (pick, pack, and so on), the order becomes locked for editing in POS.

> [!NOTE]
> In Commerce version 10.0.14, a feature that has been released in [public preview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/public-preview-terms) lets POS users edit customer orders through POS, even if some of the order has already been fulfilled. However, orders that are fully invoiced still can't be edited through POS. To test this preview feature and provide additional feedback, turn on the **(Preview) Edit partially fulfilled orders in Point of Sale** feature in the **Feature management** workspace. Customer orders that originated in a call center channel and that use Enable order completion functionality can't be edited even after this feature is enabled.

1. Select **Recall order**.
2. Use **Search** to enter filters to find the order, and then select **Apply**.
3. Select the order in the list of results, and then select **Edit**. If the **Edit** button is unavailable, the order is in a state where it can't be edited.
4. From the transaction cart, make any necessary changes to the customer order. Some changes might be prohibited during editing.
5. Complete the editing process by selecting a payment operation.
6. To exit the editing process without saving any changes, you can use the **Void transaction** operation.



### Cancel a customer order

1. Select **Recall order**.
2. Use **Search** to enter filters to find the order, and then select **Apply**.
3. Select the order in the list of results, and then select **Cancel**. If the **Cancel** button is unavailable, the order is in a state where it can no longer be canceled.
4. If cancellation charges are configured, confirm them. You can adjust the cancellation charges before you confirm them, as required. 
5. From the transaction cart, complete the cancellation process by selecting a payment operation. If deposits that were paid exceed the cancellation charge, refund payments might be due.
6. To exit the cancellation process without saving any changes, you can use the **Void transaction** operation.

## Finalizing the customer order shipment or pickup from POS

After an order is created, the items will be picked up by the customer from a store location or shipped, depending on the configuration of the order. For more information about this process, see the [store order fulfillment](https://docs.microsoft.com/dynamics365/commerce/order-fulfillment-overview) documentation.

## Asynchronous transaction flow for customer orders

Customer orders can be created in POS in either synchronous mode or asynchronous mode. If you notice performance issues or user delays when you create customer orders in POS, consider turning on asynchronous order creation.

### Enable customer orders to be created in asynchronous mode

1. In Commerce headquarters, on the **Functionality profiles** page, select the functionality profile that corresponds to the store that you want to configure.
2. On the **General** FastTab, set the **Create customer order in async mode** option to **Yes**.

When the **Create customer order in async mode** option is set to **Yes**, customer orders are always created in asynchronous mode, even if Retail Transaction Service (RTS) is available. If you set this option to **No**, customer orders are always created in synchronous mode by using RTS. When customer orders are created in asynchronous mode, they're pulled and created as retail transactions in Commerce headquarters from the Commerce Pull (P) jobs. The corresponding sales orders for the retail transactions are created when **Synchronize orders** is run either manually or through a batch process.

## Additional resources

[Hybrid customer orders](hybrid-customer-orders.md)
