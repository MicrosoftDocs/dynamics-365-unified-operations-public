---
# required metadata

title: Customer orders in Point of Sale (POS)
description: This topic provides information about customer orders in Point of Sale (POS). Customer orders are also known as special orders. The topic includes a discussion of related parameters and transaction flows.
author: josaw1
manager: AnnBe
ms.date: 08/17/2020
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

This topic provides information about creating and managing customer orders in Point of Sale (POS). Customer orders can be used to capture sales whereby the shopper will be picking up products at a future time, picking up products from a different location, or if they wish to have items shipped to them. 

In an omni-channel commerce world, many retailers provide the option of customer orders, or special orders, to meet various product and fulfillment requirements. Here are some typical scenarios:

- A customer wants products to be delivered to a specific address on a specific date.
- A customer wants to pick up products from a store or location that differs from the store or location where the customer purchased those products.
- A customer inside a store location wishes to order products today and pick them up at the same store location at a later date.

Retailers can use customer orders to minimize lost sales that stock outages might otherwise cause, because the merchandise can be delivered or picked up at a different time or place.

## Customer order setup
Before attempting to use customer order functionality in POS, ensure you have made all necessary configurations in Commerce Headquarters

### Configure Modes of delivery

To use customer orders, modes of delivery must be configured that can be used by the store channel. You will need to define at least one mode of delivery that can be used when order lines will be shipped to a customer from a store. You must also define at least one pickup mode of delivery that can be used when order lines will be picked up from the store. Modes of delivery are defined on the **Modes of delivery** form in Commerce Headquarters. Refer to [this document](https://docs.microsoft.com/dynamics365/commerce/configure-call-center-delivery#define-delivery-modes) for more information on how to set up modes of delivery for Commerce channels.

![Configuration of Modes of delivery](media/customer-order-modes-of-delivery.png)


### Set up fulfillment groups

Fulfillment group setup is defined on the **Fulfillment groups** form. Organizations may create as many fulfillment groups as needed. Fulfillment groups are used to determine which store/warehouse locations are offered as options for selection when creating a customer order in POS. There may be certain stores or warehouse locations that are not able to fulfill customer orders so the fulfillment group configuration allows an organization to specifically indicate which stores or warehouses will be shown as options to users creating customer orders in POS. Once a fulfillment group is defined, it is linked to a store through the **Stores** form through the **Set up** tab.

Beginning in version 10.0.12, a feature was introduced to allow organizations to define if the warehouse or warehouse/store combinations defined in fulfillment groups can be used for shipping or pickup or both. This gives additional flexibility to the store to drive which warehouse/store options appear to users when creating an order for pickup vs. shipment. Enable feature **Ability to specify locations as “Shipping” or “Pickup” enabled within Fulfillment group** to take advantage of these additional configuration options. It's important to note that if a warehouse is linked to a fulfillment group and that warehouse is not a store, that warehouse can only be configured as a shipping location and cannot be used when configuring orders for pickup in POS.

![Configuration of Fulfillment group](media/customer-order-fulfillment-group.png)

### Configure channel settings

When working with customer orders in Point of Sale, you will need to consider some of the configurations on the store channel setup. These settings are found on the **Stores** form in Commerce Headquarters

- **Shipping warehouse** - indicate which warehouse will be used to fulfill orders configured for shipment from the store
- **Fulfillment group assignment** - link the fulfillment groups that will be referenced when displaying options for pickup locations or shipment origins when creating customer orders in POS
- **Use destination-based tax** - determines if the shipping address will be leveraged to determine the tax group to be applied to the order line for lines shipping to the customer's address.
- **Use customer-based tax** - determines if tax group as defined on the customer's delivery address will be used to tax a customer order created in POS for shipment to the customer's home.

![Configuration of Fulfillment group](media/customer-order-all-stores.png)

### Set up customer order parameters

Before attempting to create customer orders in the Point of Sale (POS) application, ensure that you have configured the appropriate parameters for this feature in Commerce Headquarters (HQ). These parameters can be found on the **Commerce parameters** form under the **Customer orders** tab:

- **Default order type** - when creating customer orders in POS, you can configure the default order type as a sales order or a quotation order. Regardless of the default type, users will still be able to create both sales orders and customer orders from POS.
- **Default deposit percentage** – Specify the percentage of the order total amount that the customer must pay as a deposit before an order can be confirmed. Depending on privileges, a store associate might be able to override the amount by using the **Deposit override** operation in POS if configured on the transaction screen layout.
- **Pickup mode of delivery** - Specify which mode of delivery will be applied to sales order lines that have been configured for pickup in POS.  
- **Carryout mode of delivery** - Specify which mode of delivery will be applied to sales lines that are considered carryout order lines when creating a mixed cart where some lines will be picked up or shipped while other lines will be carried out by the customer immediately.
- **Cancellation charge percentage** – If a charge will be applied when a customer order is canceled, specify the amount of that charge.
- **Cancellation charge code** – Specify which accounts receivable Charge code will be used when applying the cancelation charge to a canceled customer order through POS. The charges code will define the financial posting logic for the cancelation charge.
- **Shipping charge code** – Please note, if **Use advanced auto charges** is enabled, this parameter setting has no functionality. During creation of customer orders in POS, users will be prompted to enter a shipping charge manually if **Use advanced auto charges** is disabled. Use this parameter to map an accounts receivable charge code which will be applied to the order when shipping charges are entered by the user. The charges code defines the financial posting logic for the shipping charge
- **Use advanced auto charges** - Enable this feature to utilize system calculated auto-charges when creating customer orders in POS. These auto-charges can be used to calculated shipping fees or other order or item specific charges. Refer to [this document](https://docs.microsoft.com/dynamics365/commerce/omni-auto-charges) for more information on setting up and using advanced auto charges.

![Configuration of Fulfillment group](media/customer-order-parameters.png)

### Update transaction screen layouts in POS


Ensure the POS [screen layout](https://docs.microsoft.com/dynamics365/commerce/pos-screen-layouts) has been configured to support the creation and management of customer orders and that all necessary POS operations are configured. Some POS operations that are recommended to properly support customer order creation and management in POS are listed below.
- **Ship all products** - used to configure all lines in the transaction cart to be shipped to a destination
- **Ship selected products** - used to configure select lines in the transaction cart to be shipped to a destination
- **Pick up all products** - used to configure all lines in the transaction cart to be picked up at a select store location
- **Pick up selected products** - used to configure select lines in the transaction cart to be picked up at a select store location
- **Carry out all products** - used to configure all lines in the transaction cart to be carried out (note that if this operation is used in POS the customer order will be converted to a cash and carry transaction)
- **Carryout out selected products** - used to configure select lines in the transaction cart as being carried out by the customer at the time of purchase. This operation is only useful in a [hybrid order](https://docs.microsoft.com/dynamics365/commerce/hybrid-customer-orders) scenario.
- **Recall order** - used to search and retrieve customer orders so that POS users may edit, cancel or perform fulfillment related operations on these orders as needed.
- **Change mode of delivery** - can be used to quickly change the mode of delivery for lines already configured to be shipped without the user having to go through the Ship all products or Ship selected products flows again.
- **Deposit override** - can be used to change the deposit amount the customer will pay for the selected customer order.

![Configuration of Fulfillment group](media/customer-order-screen-layout.png)

## Working with customer orders in POS

### Create a customer order for products to ship to the customer

1. From the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Click **Ship selected** or **Ship all** to ship the products to an address on the customer account.
4. When prompted, choose to create a Customer order.
5. When prompted, confirm or change the ship from location, confirm or change the shipping address and select a shipping method.
6. Enter the customer's desired order shipment date when prompted.
7. Use payment functions to pay for any calculated amounts due or use **Deposit override** operation to change amounts due and then apply payment.
8. If the full order total was not paid, when prompted provide a credit card that will be captured for the balance due on the order when the order is invoiced.

### Create a customer order for products to be picked up by the customer

1. From the POS transaction screen, add a customer to the transaction.
2. Add products to the cart.
3. Click **Pick up selected** or **Pick up all** to initiate the pick up order configuration.
4. When prompted, choose a store location where the customer will pick up the selected products.
5. When prompted, choose a pick up date.
6. Use payment functions to pay for any calculated amounts due or use **Deposit override** operation to change amounts due and then apply payment.
7. If the full order total was not paid, when prompted choose if the customer will provide payment later (at pickup) or if a credit card will be tokenized now that will be used and captured at the time of pickup.

### Edit an existing customer order

Retail orders created in either the Online or Store channels can be recalled and edited through POS if needed.  

> [!IMPORTANT]
> Orders created in a Call center channel cannot be edited through the POS application if the call center channel has [enable order completion](https://docs.microsoft.com/dynamics365/commerce/set-up-order-processing-options#enable-order-completion) turned on. To ensure proper payment processing, Call center originated orders that use enable order completion logic must be edited through the Call center application in Commerce Headquarters.  

In versions 10.0.13 or earlier, users are only able to edit supported customer orders in POS if the order is fully open. If any lines of the order have already been processed to fulfillment (pick, pack, etc..), the order becomes locked for editing in POS.

> [!NOTE]
>In version 10.0.14 a feature has been released in [public preview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/public-preview-terms) that will allow for POS users to edit customer orders from POS even if some of the order has already been fulfilled. Orders that are fully invoiced remain un-editable through POS. To try out this preview feature and provide additional feedback, enable **(Preview) Edit partially fulfilled orders in Point of Sale** in feature management. Note that customer orders originated in a Call Center channel that uses enable order completion will continue to be un-editable even after this preview feature is enabled.

1. Select **Recall order** operation
2. Use **Search** function to enter desired filters to locate the order and click **Apply**
3. Select the order from the results list and click **Edit** (note that if **Edit** is disabled the order is in a state where it cannot be edited)
4. From the transaction cart, make any necessary changes to the customer order. Certain changes may be prohibited while editing.
5. Complete the editing process by choosing a payment operation.
6. If desired, exit the editing process without saving any changes by using the **Void transaction** operation.



### Cancel a customer order

1. Select **Recall order** operation
2. Use **Search** function to enter desired filters to locate the order and click **Apply**
3. Select the order from the results list and click **Cancel** (note that if **Cancel** is disabled the order is in a state where it can no longer be canceled)
4. If cancelation charges have been configured, user will be prompted to confirm or adjust and then confirm the cancelation fees/charges. 
5. From the transaction cart, complete the cancelatoin process by choosing a payment operation. If deposits were paid in excess of the cancelation charge, refund payments may be due.
6. If desired, exit the cancelatoin process without saving any changes by using the **Void transaction** operation.

## Finalizing the customer order shipment or pickup from POS
Once the orders are created, depending on the configuration of the order, the items will either be picked up by a customer at a store location or shipped. Refer to documentation on [store order fulfillment](https://docs.microsoft.com/dynamics365/commerce/order-fulfillment-overview) for more information on this process.

## Asynchronous transaction flow for customer orders

Customer orders can be created from the point of sale (POS) client in either synchronous mode or asynchronous mode. If you are noting any performance issues or user delays when creating customer orders in POS, it is advised to consider enabling asynchronous order creation. 

### Enable customer orders to be created in asynchronous mode

1. From Commerce Headquarters access the **Functionality profiles** form
2. Select the Functionality profile that corresponds with the store you want to configure
3. On the **General** FastTab, set the **Create customer order in async mode** option to **Yes**.

When the **Create customer order in async mode** option is set to **Yes**, customer orders are always created in asynchronous mode, even if Retail Transaction Service (RTS) is available. If you set this option to **No**, customer orders are always created in synchronous mode by using RTS. When customer orders are created in asynchronous mode, they are pulled and created as retail transactions in HQ from the Commerce Pull (P) jobs. The corresponding sales orders for the retail transactions are created when **Synchronize orders** is run either manually or through a batch process.

## Additional resources

[Hybrid customer orders](hybrid-customer-orders.md)
