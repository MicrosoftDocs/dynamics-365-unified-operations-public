---
# required metadata

title: Customer orders in Point of Sale (POS)
description: This topic provides information about customer orders in Point of Sale (POS). Customer orders are also known as special orders. The topic includes a discussion of related parameters and transaction flows.
author: josaw1
manager: AnnBe
ms.date: 08/21/2020
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

This topic provides information about creating and managing customer orders in Point of Sale (POS). Customer orders can be used to capture sales where the shopper will be picking up products at a future time, picking up products from a different location, or if they wish to have items shipped to them. 

In an omni-channel commerce world, many retailers provide the option of customer orders, or special orders, to meet various product and fulfillment requirements. Here are some typical scenarios:

- A customer wants products to be delivered to a specific address on a specific date.
- A customer wants to pick up products from a store or location that differs from the store or location where the customer purchased those products.
- A customer inside a store location wishes to order products today and pick them up at the same store location at a later date.

Retailers can use customer orders to minimize lost sales that stock outages might otherwise cause because the merchandise can be delivered or picked up at a different time or place.

## Set up customer orders
Before attempting to use customer order functionality in POS, make sure you complete all necessary configurations in Commerce headquarters.

### Configure modes of delivery

To use customer orders, modes of delivery that can be used by the store channel must be configured. You need to define at least one mode of delivery that can be used when order lines are shipped to a customer from a store. You must also define at least one pickup mode of delivery that can be used when order lines are picked up from the store. Modes of delivery are defined on the **Modes of delivery** page in Commerce headquarters. Refer to [this topic](https://docs.microsoft.com/dynamics365/commerce/configure-call-center-delivery#define-delivery-modes) for more information on how to set up modes of delivery for Commerce channels.

![Configuration of Modes of delivery](media/customer-order-modes-of-delivery.png)


### Set up fulfillment groups

Fulfillment group configuration is defined on the **Fulfillment groups** page. Organizations can create as many fulfillment groups as needed. Fulfillment groups are used to determine which store/warehouse locations are offered as options to select when creating a customer order in POS. There may be certain stores or warehouse locations that aren't able to fulfill customer orders so the fulfillment group configuration allows an organization to specifically indicate which stores or warehouses are shown as options to users creating customer orders in POS. Once a fulfillment group is defined, it is linked to a store through the **Stores** form through the **Set up** tab.

In Commerce version 10.0.12 and later, organizations can define if the warehouse or warehouse/store combinations defined in fulfillment groups can be used for shipping or pickup or both. This gives additional flexibility to the store to drive which warehouse/store options appear to users when creating an order for pickup vs. shipment. Enable the **Ability to specify locations as “Shipping” or “Pickup” enabled within Fulfillment group** feature to take advantage of these configuration options. If a warehouse is linked to a fulfillment group and that warehouse is not a store, the warehouse can only be configured as a shipping location and cannot be used when configuring orders for pickup in POS.

![Configuration of Fulfillment group](media/customer-order-fulfillment-group.png)

### Configure channel settings

When working with customer orders in POS, you need to consider some of the configurations on the store channel setup. These settings are found on the **Stores** page in Commerce headquarters.

- **Shipping warehouse** - Indicates which warehouse is used to fulfill orders configured for shipment from the store.
- **Fulfillment group assignment** - Links the fulfillment groups that are referenced when displaying options for pickup locations or shipment origins when creating customer orders in POS.
- **Use destination-based tax** - Determines if the shipping address is used to determine the tax group to be applied to the order line for lines shipping to the customer's address.
- **Use customer-based tax** - Determines if tax group as defined on the customer's delivery address is used to tax a customer order created in POS for shipment to the customer's home.

![Configuration of Fulfillment group](media/customer-order-all-stores.png)

### Set up customer order parameters

Before attempting to create customer orders in the POS application, configure the appropriate parameters in Commerce headquarters. The parameters can be found on the **Commerce parameters** page under the **Customer orders** tab.

- **Default order type** - When creating customer orders in POS, you can configure the default order type as a sales order or a quotation order. Regardless of the default type, users can still create both sales orders and customer orders from POS.
- **Default deposit percentage** – Specify the percentage of the order total amount that the customer must pay as a deposit before an order can be confirmed. Depending on privileges, a store associate might be able to override the amount by using the **Deposit override** operation in POS, if it's configured on the transaction screen layout.
- **Pickup mode of delivery** - Specify which mode of delivery will be applied to sales order lines that are configured for pickup in POS.  
- **Carryout mode of delivery** - Specify which mode of delivery will be applied to sales lines that are considered carryout order lines when creating a mixed cart where some lines will be picked up or shipped, and other lines will be carried out by the customer immediately.
- **Cancellation charge percentage** – If a charge is to be applied when a customer order is canceled, specify the amount of that charge.
- **Cancellation charge code** – Specify which accounts receivable charge code is used when applying the cancelation charge to a canceled customer order through POS. The charges code defines the financial posting logic for the cancelation charge.
- **Shipping charge code** – If **Use advanced auto charges** is enabled, this parameter setting has no functionality. During creation of customer orders in POS, users are prompted to enter a shipping charge manually if **Use advanced auto charges** is disabled. Use this parameter to map an accounts receivable charge code which will be applied to the order when shipping charges are entered by the user. The charges code defines the financial posting logic for the shipping charge.
- **Use advanced auto charges** - Enable this feature to utilize system-calculated auto-charges when creating customer orders in POS. These auto-charges can be used to calculate shipping fees or other order or item-specific charges. Refer to [this topic](https://docs.microsoft.com/dynamics365/commerce/omni-auto-charges) for more information on setting up and using advanced auto charges.

![Configuration of Fulfillment group](media/customer-order-parameters.png)

### Update transaction screen layouts in POS

Make sure the POS [screen layout](https://docs.microsoft.com/dynamics365/commerce/pos-screen-layouts) is configured to support the creation and management of customer orders and that all necessary POS operations are configured. Some of the POS operations that are recommended to properly support customer order creation and management in POS are listed below.
- **Ship all products** - Used to specify that all lines in the transaction cart are to be shipped to a destination.
- **Ship selected products** - Used to specify that select lines in the transaction cart are to be shipped to a destination.
- **Pick up all products** - Used to specify that all lines in the transaction cart are to be picked up at a select store location.
- **Pick up selected products** - Used to specify that select lines in the transaction cart are to be picked up at a select store location.
- **Carry out all products** - Used to specify that all lines in the transaction cart are to be carried out. If this operation is used in POS, the customer order will be converted to a cash and carry transaction.
- **Carryout out selected products** - Used to specify that select lines in the transaction cart are being carried out by the customer at the time of purchase. This operation is only useful in a [hybrid order](https://docs.microsoft.com/dynamics365/commerce/hybrid-customer-orders) scenario.
- **Recall order** - Used to search and retrieve customer orders so that POS users may edit, cancel, or perform fulfillment-related operations on these orders as needed.
- **Change mode of delivery** - Can be used to quickly change the mode of delivery for lines already configured to be shipped without the user having to go through the "ship all products" or "ship selected products" flows again.
- **Deposit override** - Can be used to change the deposit amount the customer will pay for the selected customer order.

![Configuration of Fulfillment group](media/customer-order-screen-layout.png)

## Working with customer orders in POS

### Create a customer order for products to ship to the customer

1. From the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Select **Ship selected** or **Ship all** to ship the products to an address on the customer account.
4. Select the option to create a customer order.
5. Confirm or change the ship from location, confirm or change the shipping address, and select a shipping method.
6. Enter the customer's desired order shipment date.
7. Use payment functions to pay for any calculated amounts due, or use the **Deposit override** operation to change amounts due, and then apply payment.
8. If the full order total wasn't paid, enter a credit card to be captured for the balance due on the order when the order is invoiced.

### Create a customer order for products to be picked up by the customer

1. From the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Select **Pick up selected** or **Pick up all** to initiate the pick up order configuration.
4. Select a store location where the customer will pick up the selected products.
5. Select a pick up date.
6. Use payment functions to pay for any calculated amounts due, or use the **Deposit override** operation to change amounts due, and then apply payment.
7. If the full order total wasn't paid, select whther the customer will provide payment later (at pickup) or if a credit card will be tokenized now that will be used and captured at the time of pickup.

### Edit an existing customer order

Retail orders created in either the online or store channels can be recalled and edited through POS if needed.  

> [!IMPORTANT]
> Orders created in a call center channel can't be edited through the POS application if the call center channel has ["enable order completion"](https://docs.microsoft.com/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) turned on. To ensure proper payment processing, call center originated orders that use enable order completion logic must be edited through the call center application in Commerce headquarters.  

In Commerce version 10.0.13 and earlier, users can only edit supported customer orders in POS if the order is fully open. If any lines of the order have already been processed to fulfillment (pick, pack, etc.), the order becomes locked for editing in POS.

> [!NOTE]
> In Commerce version 10.0.14, a feature has been released in [public preview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/public-preview-terms) that allows POS users to edit customer orders from POS even if some of the order has already been fulfilled. Orders that are fully invoiced remain uneditable through POS. To test this preview feature and provide additional feedback, enable **(Preview) Edit partially fulfilled orders in Point of Sale** in the **Feature management** workspace. Customer orders that originated in a call center channel and use "enable order completion" functionality will continue to be uneditable even after this feature is enabled.

1. Select **Recall order**.
2. Use **Search** to enter filters to locate the order, and then select **Apply**.
3. Select the order from the results list and click **Edit**. If **Edit** is disabled, the order is in a state where it can't be edited.
4. From the transaction cart, make any necessary changes to the customer order. Some changes may be prohibited while editing.
5. Complete the editing process by selecting a payment operation.
6. If desired, exit the editing process without saving any changes by using the **Void transaction** operation.



### Cancel a customer order

1. Select **Recall order**.
2. Use **Search** to enter desired filters to locate the order, and then click **Apply**.
3. Select the order from the results list and click **Cancel**. If **Cancel** is disabled, the order is in a state where it can no longer be canceled.
4. If cancelation charges are configured, confirm or adjust and confirm the cancelation charges. 
5. From the transaction cart, complete the cancelation process by choosing a payment operation. If deposits were paid in excess of the cancelation charge, refund payments may be due.
6. If desired, exit the cancelatoin process without saving any changes by using the **Void transaction** operation.

## Finalizing the customer order shipment or pickup from POS

Once the orders are created, depending on the configuration of the order, the items will either be picked up by a customer at a store location or shipped. Refer to documentation on [store order fulfillment](https://docs.microsoft.com/dynamics365/commerce/order-fulfillment-overview) for more information on this process.

## Asynchronous transaction flow for customer orders

Customer orders can be created from the POS application in either synchronous mode or asynchronous mode. If you note performance issues or user delays when creating customer orders in POS, consider enabling asynchronous order creation. 

### Enable customer orders to be created in asynchronous mode

1. In Commerce headquarters, go to the **Functionality profiles** page.
2. Select the functionality profile that corresponds with the store you want to configure.
3. On the **General** FastTab, set the **Create customer order in async mode** option to **Yes**.

When the **Create customer order in async mode** option is set to **Yes**, customer orders are always created in asynchronous mode, even if Retail Transaction Service (RTS) is available. If you set this option to **No**, customer orders are always created in synchronous mode by using RTS. When customer orders are created in asynchronous mode, they're pulled and created as retail transactions in Commerce headquarters from the Commerce Pull (P) jobs. The corresponding sales orders for the retail transactions are created when **Synchronize orders** is run either manually or through a batch process.

## Additional resources

[Hybrid customer orders](hybrid-customer-orders.md)
