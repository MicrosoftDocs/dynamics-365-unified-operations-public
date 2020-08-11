---
# required metadata

title: Customer orders in Modern POS (MPOS)
description: This topic provides information about customer orders in Modern POS (MPOS). Customer orders are also known as special orders. The topic includes a discussion of related parameters and transaction flows.
author: josaw1
manager: AnnBe
ms.date: 08/11/2020
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

To use customer orders, modes of delivery must be configured.  You will need to define at least one mode of delivery that can be used when order lines will be shipped to a customer from a store.  You must also define at least one pickup mode of delivery that can be used when order lines will be picked up from the store.  Modes of delivery are defined on the **Modes of delivery** form in Commerce Headquarters.  Refer to this document (LINK) for more information on how to set up modes of delivery

### Configure channel settings

When working with customer orders in Point of Sale, you will need to consider some of the configurations on the store channel setup.  These settings are found on the **Stores** form in Commerce Headquarters

-**Shipping warehouse**
-**Fulfillment group assignment**
-**Use destination-based tax**
-**Use customer-based tax**

### Set up customer order parameters

Before attempting to create customer orders in the Point of Sale (POS) application, ensure that you have configured the appropriate parameters for this feature in Commerce Headquarters (HQ).  These parameters can be found on the **Commerce parameters** form under the **Customer orders** tab:

-**Default order type**
-**Default deposit percentage** – Specify the amount that the customer must pay as a deposit before an order can be confirmed. The default deposit amount is calculated as a percentage of the order value. Depending on privileges, a store associate might be able to override the amount by using **Deposit override**.
-**Pickup mode of delivery**
-**Carryout mode of delivery**
- **Cancellation charge percentage** – If a charge will be applied when a customer order is canceled, specify the amount of that charge.
- **Cancellation charge code** – If a charge will be applied when a customer order is canceled, that charge will be reflected under a charge code on the sales order. Use this parameter to define the cancellation charge code.
- **Shipping charge code** – Retailers can charge an extra fee for shipping merchandise to a customer. The amount of that shipping charge will be reflected under a charge code on the sales order. Use this parameter to map the shipping charge code to shipping charges on the customer order.
-**Use advanced auto charges**

### Update transaction screen layouts in POS

## Working with customer orders in POS

### Create a customer order for products to ship to the customer

1. Add a customer to the transaction.
2. Add products to the cart.
3. Click **Create customer order**, and then select the order type. The order type can be either **Customer order** or **Quote**.
4. Click **Ship selected** or **Ship all** to ship the products to an address on the customer account, specify the requested shipping date, and specify shipping charges.
5. Click **Pick up selected** or **Pick-up all** to select products that will be picked up from the current store or a different store on a specific date.
6. Collect the deposit amount, if a deposit is required.

### Create a customer order for products to be picked up by the customer


### Edit an existing customer order

### Cancel an order

1. On the home page, click **Find an order**.
2. Select the order to cancel. At the bottom of the page, click **Cancel**.

## Finalzing customer orders in POS
Once the orders are created, depending on the configuration of the order, the items will either be picked up by a customer at a store location or shipped.  This section provides a high level overview of the process flow for execution of these processes

### Process customer order pickup in POS
If the customer order was configured for pickup at a store location, the store employee can use the **Recall order** or **Order fulfillment** operations of POS to locate the order and execute the pickup operation.   These operations must be added to the POS layout. 

To execute a pickup from the **Recall order** operation in POS, follow these steps:


To execute a pickup from the **Order fulfillment** operation in POS, follow these steps:

### Process customer order shipments in POS
If the customer order was configured for shipment from the store, the store employee can use the **Order fulfillment** operation in POS to mark these sales order lines as picked, packed and shipped.  For more information on this process, refer to[this document](https://docs.microsoft.com/en-us/dynamics365/commerce/order-fulfillment-overview)

### Mark customer orders as shipped in HQ
If the customers order is being fulfilled by a Distribution Center (DC) users may use basic order fulfillment processes available in Dynamics 365 Supply chain to execute order pick, pack and invoice processes.   Refer to [documentation found here](https://docs.microsoft.com/en-us/dynamics365/supply-chain/ for more information on processing sales orders in Commerce HQ.  

## Asynchronous transaction flow for customer orders

Customer orders can be created from the point of sale (POS) client in either synchronous mode or asynchronous mode.  If you are noting any performance issues or user delays when creating customer orders in POS, it is advised to consider enabling asychronous order creation. 

### Enable customer orders to be created in asynchronous mode

1. From Commerce Headquarters access the **Functionality profiles** form
2. Select the Functionality profile that corresponds with the store you want to configure
3. On the **General** FastTab, set the **Create customer order in async mode** option to **Yes**.

When the **Create customer order in async mode** option is set to **Yes**, customer orders are always created in asynchronous mode, even if Retail Transaction Service (RTS) is available. If you set this option to **No**, customer orders are always created in synchronous mode by using RTS. When customer orders are created in asynchronous mode, they are pulled and created as retail transactions in HQ from the Commerce Pull (P) jobs. The corresponding sales orders for the retail transactions are created when **Synchronize orders** is run either manually or through a batch process.

## Additional resources

[Hybrid customer orders](hybrid-customer-orders.md)
