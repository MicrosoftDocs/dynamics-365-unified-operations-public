---
# required metadata

title: Work with serialized items in the POS
description: This topic explains how to manage serialized items in the point of sale (POS) application.
author: boycezhu
ms.date: 01/08/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycez
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.11
---

# Work with serialized items in the POS

[!include [banner](includes/banner.md)]

Many retailers sell products that require serial control. These products are referred to as *serialized items*. Some retailers might want to maintain serial numbers in store or warehouse inventory for tracking purposes. Other retailers might want to capture serial numbers during the sales process, for service and warranty purposes. This topic explains how you can manage serialized items in the Microsoft Dynamics 365 Commerce point of sale (POS) application.

## Serial number configurations

An item is considered a serialized item if it's assigned a tracking dimension group that's set up to allow for serial numbers. In Commerce headquarters, on the **Tracking dimension groups** page, select the **Active** option to enable serial numbers for the inventory process, or select the **Active in sales process** option to enable serial numbers for the sales process.

On the **Tracking dimensions** FastTab, turn on the **Blank receipt allowed** parameter to allow serial number to be an optional input during the inventory receipt process of serialized item. Turning off this parameter enforces serial number to be a required input. Similarly, the **Blank issue allowed** parameter controls whether serial number is required during the inventory shipment process.

> [!NOTE]
> To use the **Inbound inventory** and **Outbound inventory** POS operations to register or validate serial numbers against a serialized item, you must configure that item to be assigned a tracking dimension group that's set up to allow for serial numbers for the **Active** option, not the **Active in sales process** option.

## Serial number management page

In the **Inbound inventory** and **Outbound inventory** POS operations, if the item that is being selected, received, or shipped is a serialized item, the **Details** pane contains a **Manage serial number** option that links to the **Serial number management** page where you can register or validate serial numbers for the item. Alternatively, you can open the **Serial number management** page either by selecting the **Serial number** action on the app bar of the order details view, or by selecting the **Manage serial number** option in the dialog box that prompts you during the receiving or shipping process. 

The **Serial number management** page lists all open serial number lines that are pending registration or validation. There might be two tabs on this page: one for the current item and another for all serialized items in the order.

The **Status** field on the **Serial number management** page provides information about the current stage that each serial number is in:

- **Not registered** – The serial number hasn't been provided, or the preregistered serial number hasn't yet been validated (in the receiving process).
- **Registering** – The serial number has been registered and saved locally to the store's channel database, or the preregistered serial number has been validated. Only serial numbers that have a status of **Registering** will be submitted to Commerce headquarters when you finish receiving or fulfillment.

## Receive serialized items

The **Inbound inventory** POS operation lets users perform the following tasks for serialized items:

- Register serial numbers against serialized items when those items are received in the store via a purchase order.
- Validate preregistered serial numbers against serialized items when those items are received in the store via a purchase order or transfer order.

### Register serial numbers against serialized items

For a purchase order, you'll be prompted with a dialog box with the **Manage serial number** option during the receiving process of a serialized item. You can select that option to open the **Serial number management** page and start to register serial numbers. You can also skip this step during the receiving process and provide the input later, before the receipt is posted.

By default, the tab for the current item is shown. All serial number lines have an empty serial number value and a status of **Not registered**. You can scan serial number bar codes, or you can select **Serial number** on the app bar to continuously enter serial numbers. The serial numbers that you enter appear in the list, and their status is changed to **Registering**. The maximum number of serial numbers that you can register in the list is equal to the receiving quantity. If you make a mistake, you can select **Edit** or **Clear** in the **Details** pane to make changes to the serial numbers that you entered.

You can also register serial numbers on the **All serialized items** tab of the **Serial number management** page. In the list, select the item that you want to register serial numbers against.

### Validate serial numbers on serialized items

For a transfer order, the outbound side must preregister serial numbers on the serialized items during the shipment process. For a purchase order, the supplier might provide serial number information through an Advance Shipment Notice (ASN), and you can preregister the numbers on the items that will be shipped. In both cases, the serial numbers are known before the receipt. Therefore, on the inbound side, you just have to validate that you received what you were supposed to receive.

To validate serial numbers, you can open the **Serial number management** page either during the receiving process or at any time before the receipt is posted. For each serialized item that has preregistered serial numbers, all the serial numbers are automatically set to an initial status of **Not registered** on this page. To validate serial numbers, you can scan or enter them. As serial number are entered, the application validates whether they match preregistered serial numbers. If they match, their status is changed to **Registering**. Otherwise, you receive an error message. Alternatively, you can directly select a serial number, then select the **Validate serial number** option in the **Details** pane to quickly mark that serial number as validated. The maximum number of serial numbers that you can validate in the list is equal to the receiving quantity.

You can also validate serial numbers on the **All serialized items** tab of the **Serial number management** page. In the list, select the item that you want to validate serial numbers against.

## Ship serialized items

You can use the **Outbound inventory** POS operation to register serial numbers against serialized items when shipping them out of current store via a transfer order.

### Register serial numbers against serialized items

For a transfer order, you'll be prompted with a dialog box with the **Manage serial number** option during the shipping process of a serialized item. You can select the option to open the **Serial number management** page and start to register serial numbers. You can also skip this step during the shipping process and provide the input later, before the shipment is posted.

By default, the tab for the current item is shown. All serial number lines have an empty serial number value and a status of **Not registered**. You can scan serial number bar codes, or you can select **Serial number** on the app bar to continuously enter serial numbers. The serial numbers that you enter appear in the list, and their status is changed to **Registering**. The maximum number of serial numbers that you can register in the list is equal to the shipping quantity. If you make a mistake, you can select **Edit** or **Clear** in the **Details** pane to make changes to the serial numbers that you entered.

You can also register serial numbers on the **All serialized items** tab on the **Serial number management** page. In the list, select the item that you want to register serial numbers against.

Optionally, you can enable serial number availability validation during the serial number registration against an outbound transfer order. With this validation, if you attempt to ship a serial number that is not available in the inventory of the shipping store, you will receive an error message and must provide a different number.

To enable such validation, as a prerequisite, you need to schedule the following jobs to run on a recurring basis:

- **Retail and Commerce** > **Retail and Commerce IT** > **Products and inventory** > **Product availability with tracking dimensions**
- **Retail and Commerce** > **Distribution schedules** > **1130** (**Product availability**)

## Sell serialized items in POS

While the POS application has always supported selling serialized items, in Commerce version 10.0.17 and later, organizations can enable functionality that enhances the business logic that's triggered when selling products that are configured for serial number tracking.

When the **Enhanced serial number validation in POS order capture and order fulfillment** feature is enabled, the following product configurations are evaluated when selling serialized products in POS:

- **Serial type** setup for the product (**active** or **active in sales**).
- **Blank issue allowed** settings for the product.
- **Physical negative inventory** settings for the product and/or the selling warehouse.

### Active serial configurations

When items are sold in POS that are configured with an **Active** serial number tracking dimension, POS initiates validation logic that prevents users from completing the sale of a serialized item with a serial number that can't be found in the selling warehouse’s current inventory. There are two exceptions to this validation rule:

- If the item is also configured with **Blank issue allowed** enabled, users can skip the entry of the serial number and sell the item with no serial number designation.
- If the item and/or the selling warehouse is configured with **Physical negative inventory** enabled, the application accepts and sells a serial number that can't be confirmed to be in inventory at the warehouse that it’s being sold against. This configuration allows the inventory transaction for that specific item/serial number to go negative, and therefore the system will allow for sales of unknown serial numbers.

> [!IMPORTANT]
> To ensure that the POS application can properly validate whether the serial numbers being sold for **Active** serial type items are in the selling warehouse's inventory, it's required that organizations run the **Product availability with tracking dimensions** job in Commerce headquarters and the accompanying **1130** product availability distribution job through Commerce headquarters on a frequent basis. As new serialized inventory is received into selling warehouses, in order for the POS to validate inventory availability of serial numbers being sold, the inventory master must frequently update the channel database with the most up-to-date inventory availability data. The **Product availability with tracking dimensions** job takes a current snapshot of master inventory, including serial numbers, for all company warehouses. The **1130** distribution job takes that inventory snapshot and shares it with all configured channel databases.

### Active in sales process serial configurations

Items configured with the serial dimension as **Active in sales process** don't go through any inventory validation logic, as this configuration implies that the inventory serial numbers aren't pre-registered into stock and the serial numbers are only captured at the time of sale.  

If **Blank issue allowed** is also configured for **Active in sales process** configured items, the serial number entry can be skipped. If **Blank issue allowed** isn't configured, the application requires the user to enter a serial number, even though it won’t be validated against available inventory.

### Apply serial numbers during creation of POS transactions

The POS application immediately prompts users for serial number capture when selling a serialized item, but the application allows users to skip the entry of serial numbers up to a certain point in the selling process. When the user begins to capture payment, the application enforces and requires serial number entry for any items that aren't configured to be fulfilled through future shipments or pickups. Any serialized items configured for cash and carry or carryout fulfillment require the user to capture the serial number (or agree to leave it blank if the item configuration allows for it) before completing the sale.

For serialized items sold for future pickup or shipment, POS users can skip entering the serial number initially and still complete the customer order creation.   

> [!NOTE]
> When selling or fulfilling serialized products through the POS application, a quantity of "1" is enforced for the serialized items on the sales transaction. This is a result of how the serial number information is tracked on the sales line. When selling or fulfilling a transaction for multiple serialized items through POS, each sales line must be only configured with a quantity of "1". 

### Apply serial numbers during customer order fulfillment or pickup

When fulfilling customer order lines for serialized products using the **Order Fulfillment** operation in POS, POS enforces the capture of the serial number before final fulfillment. Therefore, if a serial number wasn't provided during the initial order capture, it must be captured during the pick, pack, or ship processes in POS. A validation is done at each step and the user will only be asked for serial number data if it's missing or no longer valid. For example, if a user skips the pick or pack steps and immediately initiates a shipment, and a serial number hasn't been registered for the line, POS will require the serial number to be entered before completion of the final invoice step. When enforcing the capture of the serial number during order fulfillment operations in POS, all rules mentioned previously in this topic still apply. Only serialized items configured as **Active** go through a serial number inventory stock validation. Items configured as **Active in sales process** won't get validated. If **Physical negative inventory** is allowed for **Active** products, any serial number will be accepted, regardless of stock availability. For both **Active** and **Active in sales process** items, if **Blank issue allowed** is configured, a user can leave serial numbers blank if desired during the pick, pack, and ship steps.

Validations for serial numbers will also occur when a user performs the pick up operations on customer orders in POS. The POS application doesn't allow a pick up to be finalized on a serialized product unless it passes the validations as mentioned earlier. The validations are always based on the product's tracking dimension and selling warehouse configurations. 

## Additional resources

[Inbound inventory operation in POS](./pos-inbound-inventory-operation.md)

[Outbound inventory operation in POS](./pos-outbound-inventory-operation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]