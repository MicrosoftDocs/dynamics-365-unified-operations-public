---
title: Receive unannounced sales returns
description: This article explains how to set up Supply Chain Management to support unannounced returns and how to receive them in the warehouse.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSParameters, ReturnDispositionCode, WHSDispositionTable, WHSReturnItemPolicy, WHSReturnItemReceivingPolicy, WHSRFMenuItem
ms.topic: how-to
ms.date: 03/04/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Receive unannounced sales returns

[!include [banner](../includes/banner.md)]

In Supply Chain Management, the [sales return process](/dynamics365/supply-chain/warehousing/sales-returns) is normally initiated by creating a return material authorization (RMA) order, which supports a process where the reason for the return isn't immediately apparent or disclosed. This RMA order serves as the primary document guiding subsequent steps in the return process, including warehouse arrival and the receiving procedure.

However, in some business scenarios, your customers might request to return products without providing advance notification or without an associated order. In such cases, the standard RMA process is bypassed and special considerations are made to accommodate these unplanned or unanticipated returns.

This article explains how to set up Supply Chain Management to support unannounced returns and how to receive them in the warehouse.

## The unannounced return receiving process

The *Return item receiving* flow in the Warehouse Management mobile app supports two different process for receiving unannounced returns: *Blind return* and *Return details*.

The following illustration shows how the flow works for each of these processes.

:::image type="content" source="media/unannounced-return-process.svg" alt-text="Unannounced return receiving processes":::

### The blind return process

A blind return is a return where no RMA order or return-details record exists in advance and no original sales order or shipment needs to be specified during receiving. During the *Return item receiving* process, workers must use the mobile app to identify and confirm the following information.

- **Customer account** – The customer who is returning the item.
- **Item number and quantity** – How many of which items are being returned.
- **License plate ID** – The license plate of the location where the incoming items are stored after being received.
- **Disposition Code** – Depending on how the mobile device menu item is set up, workers might be able to decide what should be done with the returned products by selecting a disposition code. If this option isn't shown in the app during receiving, then a Supply Chain Management user must enter a disposition code when completing the mixed license plate.

### The return details process

The *Return details* return process makes use of a return-details record, which is automatically generated when an order is shipped and contains all the information needed to process a return, such as the return ID, original order ID, shipment ID, order lines, return-until dates, and so on.

Typically, the sending company prints and delivers a return label with each outgoing shipment. The return label includes a barcode with the return ID. When a customer needs to return an item, they pack the item and attach the return label that they received with the original shipment, without needing to contact the sending company.

> [!NOTE]
> Only the items/variants, tracking dimensions, and quantities listed in the specified return-details record can be returned with this process.

There are two ways to generate return-details records.

- *In a packing scenario*, the system generates a return-details record after each sales order has been packed into a container and the container has been closed.
- *In a nonpacking scenario*, the system generates a return-details record after a worker creates a shipment for a sales order and confirms it.

In each case, the shipment date and return-until date are filled when related shipment is confirmed.

During the *Return item receiving* process, workers must use the mobile app to identify and confirm the following information.

- **Return ID** – The ID number of the return-details record.
- **Item number and quantity** – How many of which items are being returned.
- **License plate ID** – The license plate of the location where the incoming items are stored after being received.
- **Disposition Code** – Depending on how the mobile device menu item is set up, workers might be able to decide what should be done with the returned products by selecting a disposition code. If this option isn't shown in the app during receiving, then a Supply Chain Management user must enter a disposition code when completing the mixed license plate.

## Set up unannounced sales return receiving

To prepare your system to receive returns without using an RMA order, you must enable the relevant features and make several related configurations. The following subsections describe each of the settings required.

### Enable unannounced returns

To use blind returns and/or automatic generation of return details during receiving, you must turn on and set up each of these features for your system as needed. Follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. If you'll use receiving with return details, then you must specify some number sequences to support this process. Follow these steps.
    1. Open the **Number Sequences** tab.
    1. Find the row where **Reference** is *Return ID*. For this row, set the **Number sequence code** to the number sequence you want to use.
    1. Find the row where **Reference** is *Load line inventory pick*. For this row, set the **Number sequence code** to the number sequence you want to use.

    For more information about how to set up number sequences for these purposes, see [Number sequences overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

1. If you'll use receiving with return details, then open the **Loads** tab and set **Enable sales load line picking route** to *Yes*. This setting enables load lines to be linked to sales line inventory transactions. The linking is done at the shipment level. This option makes use of the *Load line inventory pick* number sequence when completing work and closing containers.
1. Open the **General** tab.
1. On the **Returns** FastTab, make the following settings.
    - **Enable return details creation** – Set to *Yes* to enable return details to be created when closing a container and during shipment confirmation. You only need to use this option if you want to support the return-details process.
    - **Enable return order creation from mobile device** – Set to *Yes* to enable return orders to be created from a mobile device flow. The flow uses mixed license plate receiving planned lines. This option is required for both the return-details and blind-return processes.

### Set up disposition codes

Disposition codes are a collection of rules that can be used when items are received in Supply Chain Management. They help to decide the inventory status, the work template, and the location directive for the items based on the scanned code.

For example, when a warehouse worker uses a mobile device to receive items that were damaged, the worker must scan a disposition code for damaged items.

- If you want to credit the item to your inventory and make it available for repurchase, you'll set up a disposition code that sets the inventory status for the received item to *Available*.
- If you receive items that you can't resell and therefore need to dispose, you can use a disposition code for RMA scrap, which will return a *return disposition code*.

Disposition codes can be used for different processes, such as for *purchase order receiving*, *production order report as finished*, and *sales order return receiving*. For the *sales order return receiving* process, if the items are registered using a mobile device, the use of disposition codes is mandatory.

#### Return disposition codes

To view and set up your return disposition codes, go to **Sales and Marketing** \> **Setup** \> **Returns** \> **Disposition codes**. Each code is defined using an ID number, and action (which defines how to handle items assigned to that code), and a description.

For more information about return disposition codes and the actions available, see [Disposition codes and disposition actions](/dynamics365/supply-chain/warehousing/sales-returns#disposition-codes-and-disposition-actions).

#### Mobile device disposition codes

To set up disposition codes that can be used on a mobile device, go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Disposition codes**. Disposition codes created here are available to mobile devices and can support several types of operations (including returns, sales orders, and inventory management). Codes for returns must be linked to a return disposition code defined on **Sales and Marketing** \> **Setup** \> **Returns** \> **Disposition codes**, which assigns a return action for the code.

For more information about mobile disposition codes and how to set them up, see [Set up disposition codes](/dynamics365/supply-chain/warehousing/tasks/set-up-dispositions-codes).

### Set up return item policies

Return item policies let you control the conditions under which the system allows items to be returned. You can set policies for each item, groups of items, or all items, as needed. To set up your policies, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Return items** \> **Return item policies**.
1. On the Action Pane, select **New** to create a new policy.
1. Set the scope where the new policy applies by choosing one of the following values in the **Item code** field.
    - *Table* – The return item policy applies only to a specific product.
    - *Group* – The return item policy applies to a specific product group.
    - *All* – The return item policy applies to all products.

1. In the **Item** field, select the item number (if **Item code** is set to *Table*) or item group (if **Item code** is set to *Group*) where the new policy applies. If **Item code** is set to **All**, then the **Item** field is inactive.
1. Set **Return acceptance** to one of the following values.
    - *Always allowed* – Items matching the selected **Item code** and **Item** can always be returned.
    - *Never allowed* – Items matching the selected **Item code** and **Item** can never be returned.
    - *Allowed days after shipment* – Items matching the selected **Item code** and **Item** can only be returned for a limited time after they were sold (as defined in the **Allowed days for return** field).

1. If **Return acceptance** is *Allowed days after shipment*, then set **Allow days for return** to the number of allowed days.
1. Repeat this procedure for each item or item group as needed. When returns are processed, the most specific return item policy applies for each item in the return.
1. On the Action Pane, select **Save**.

### Create return item receiving policies

You must define the return item receiving policies that you need prior to creating the related mobile device menu items. These policies enable each menu item to process the return correctly.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**.
1. On the Action Pane, select **New** to add a new return item receiving policy and then make the following settings for it.
    - **Return item receiving policy ID** – Enter a name for the policy. For example, *Blind return* or *Return details*.
    - **Description** – Enter a short description of the policy.
    - **Return process** – Select the type of return process that the policy represents (*Return details* or *Blind return*).

1. If you're supporting both types of unannounced return processes, then repeat this procedure for the other process (*Return details* or *Blind return*).

### Set up mobile device menu items

To enable workers to process unannounced returns, you must create one or more mobile device menu items for this purpose (one for each type of returns process, such as blind returns and/or return details).

- Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
- Select **New** on the Action Pane to add a new mobile device menu item.
- Make the following settings for the new menu item.
    - **Menu item name** - Enter an internal name for the menu item, such as *Blind returns*.
    - **Title** - Enter name for the menu item as it should be shown in the mobile app (for example, *Blind return item receiving*)
    - **Mode** - Select *Work*.
    - **Use existing work** – Select *No*.
    - **Work creation process** – Select *Return item receiving*.
    - **Barcode data policy** – Select the policy to use when multiple fields are filled in based on a single bar code scan. For more information, see [GS1 bar codes](/dynamics365/supply-chain/warehousing/gs1-barcodes).
    - **Generate license plate** – Set this option to *Yes* to automatically create new license plates as they're needed. Set it to *No* if the worker must always select an existing license plate.
    - **Display disposition code** – Choose whether to ask workers to select a disposition code during the receiving process.
    - **Return item receiving policy ID** – Choose the [item receiving policy](#create-return-item-receiving-policies) that you created for the type of returns this menu item supports (return details or blind return).

- If you support both return details and blind return processes, then repeat the previous two steps to create a menu item for the other process.
- Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu** and add the new menu items to an appropriate place in your mobile device menu structure.

## Example scenarios

This section provides example scenarios that show how to set up and process unannounced returns.

### Scenario prerequisites

Before working through the example scenarios provided in this article, you must first complete all of the prerequisites described in this section.

#### Enable sample data

To work through the example scenarios by using the sample records and values that are specified here, you must be on a system where the standard [demo data](/dynamics365/fin-ops-core/dev-itpro/get-started/demo-data) is installed. Additionally, you must select the **USMF** legal entity before you begin. The example scenarios use the demo data associated with the worker/person *Julia Funderburk*.

You can also use these scenarios as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that is described here.

#### Set up number sequences

You must have number sequences for generating unique return IDs and load line inventory pick numbers. Follow these steps.

1. Go to **Organization administration** \> **Number sequences** \> **Number sequences**.
1. On the Action pane, open the **Number sequence** tab and, from the **New** group, select **Number sequence**. You'll use this sequence to generate return ID numbers. Make the following settings for it.
    - **Number sequence code**: *ReturnID*
    - **Name**: *ReturnID*
    - **Scope**: *Company*
    - **Company**: *USMF*

1. On the Action Pane, select the **Back** button.
1. On the Action pane, open the **Number sequence** tab and, from the **New** group, select **Number sequence**. You'll use this sequence to generate load line inventory pick numbers. Make the following settings for it.
    - **Number sequence code**: *LLIP*
    - **Name**: *LLIP*
    - **Scope**: *Company*
    - **Company**: *USMF*

1. On the Action Pane, select the **Save**.

#### Enable unannounced return features

Go to the **Warehouse management parameters** page and make the following settings.

- On the **Number sequences** tab, set **Number sequence code** to *ReturnID*.
- On the **Number sequences** tab, set **Number sequence code** for *LLIP*.
- On the **General** tab, turn on **Enable return details creation**.
- On the **General** tab, turn on **Enable return order creation from mobile device**.
- On the **Loads** tab, turn on **Enable sales load line picking route**.

For information about how to make these settings, see [Enable unannounced returns](#enable-unannounced-returns).

#### Create return item policies

Go to **Warehouse management** \> **Setup** \> **Return items** \> **Return item policies** and set up a return item policy to establish the conditions for when the item used in the scenarios can be returned. Use the following settings.

- **Item code**: *Table*
- **Item**: *A0001*
- **Return acceptance**: *Allowed days after shipment*
- **Allowed days for return**: *28*

For more information, see [Set up return item policies](#set-up-return-item-policies).

#### Set up return item receiving policies

Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies** and set up two return item receiving policies, one for *Blind return* and one for *Return details*.

For instructions, see [Create return item receiving policies](#create-return-item-receiving-policies).

#### Set up mobile device menu items and menus

Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items** and create two mobile device menu items for handling unannounced returns. Set them up as described in the following list.

- Create one menu item for *Blind return* and one for *Return details*.
- Give each menu item a name that identifies the type of return it's intended to process (for example *Blind return receiving* and *Return details receiving*).
- For each menu item, set **Work creation process** to *Return item receiving*.
- For each menu item, enable both **Generate license plate** and **Display disposition code**.
- For each menu item, set **Return item receiving policy ID** to the policy that matches the type of return that menu item should handle (*blind returns* or *return details*).

Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu** and add both menu items to an appropriate place in your mobile device menu structure.

For instructions, see [Set up mobile device menu items](#set-up-mobile-device-menu-items).

## Example scenario 1: Customer return with blind return policy

Blind receiving is a process that allows warehouse workers to receive return items without matching them to an original sales order or shipment. The warehouse worker just needs to enter the customer account ID, item IDs, and quantities.

The following illustration shows a flowchart of the blind receiving process.

:::image type="content" source="media/blind-return-policy.svg" alt-text="The blind receiving process":::

### Use the mobile app to receive a blind return to a mixed license plate

Follow these steps to receive products into a warehouse mixed license plate with blind return policy.

1. Open the Warehouse Management mobile app and sign in using **User ID** *62* and **Password** *1*.
1. Open the menu item that you created for receiving blind returns (for example **Inbound** \> **Blind returns receiving**).
1. Enter the **Customer account** *US-003*.
1. Enter/scan **Item** *A0001*.
1. Accept the suggested **license plate** number.
1. Enter **qty** *1*.
1. Select **Disposition code** *RMA Credit*.
1. Select **OK** to complete the receiving work.
1. Select **Cancel** to exit the flow and close the menu item.

    > [!NOTE]
    > You must exit the flow to unlock the license plate. If the license plate is locked, you won't be able to complete mixed license place receiving in Supply Chain Management, as described in the next section. With some setups, it's possible finish processing mixed license plates during the *Return item receiving* flow, but in this scenario, we'll process the license plate in Supply Chain Management.

### Complete Mixed license plate receiving

The returned products have now been put onto a mixed license plate for further processing (see also [Mixed license plate receiving](/dynamics365/supply-chain/warehousing/mixed-license-plate-receiving)). Follow these steps to finish receiving the returned items.

1. Go to **Warehouse Management** \> **Inquiries and reports** \> **Mixed license plate receiving**.
1. In the **Licensed plate** grid, find the mixed license plate that you processed using the mobile app.
1. On the Action Pane, open the **License plate tab** and select **Complete license plate** to complete the mixed license plate receiving.

When you have completed mixed license plate receiving, Supply Chain Management automatically creates a return material authorization (RMA) order, which is prepared for further downstream processing, as described in [Sales returns](/dynamics365/supply-chain/warehousing/sales-returns).

## Example scenario 2: Customer return with return details policy

With return details, when an order is processed at the packing station for shipment, return details are generated and matching labels are included with the shipment. If any items need to be returned, the customer packs the return items, attaches the return label they received with the original shipment, and ships the return items back to the seller. When the returned items arrive at the seller's warehouse, a worker scans the return label and the item to get the return ID, which identifies a return-details record that includes the original order details. This process helps you prevent fraud, inventory errors, and lost packages.

The following illustration shows the steps needed to create a sales order and complete the work of moving the ordered items to the packing area. Workers then pack the order and, on closing the container, return details are generated.

:::image type="content" source="media/generate-return-details.svg" alt-text="Process for generating return details":::

The following illustration shows a flowchart of the receiving process using the *Return item receiving* mobile menu item to process a return with return details.

:::image type="content" source="media/return-details-policy.svg" alt-text="The return-details receiving process":::

### Create a sales order and release it to the warehouse for packing

For this scenario, a related sales order must already exist and the item must already have been shipped prior to the return. Therefore, you must create these required records before you can work through the related return. Follow these steps to create a sales order and complete the work of moving the ordered items to the packing area.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, set **Customer account** to *US-001*.
1. Select **OK** to close the dialog box.
1. The new sales order opens and includes a single, empty line on the **Sales order lines** FastTab. Set the following values for the new order line.
    - **Item number:** *A0001*
    - **Quantity:** *1*
    - **Site:** *6*
    - **Warehouse:** *62*

1. While the order line is still selected, select **Inventory** \> **Reservation** on the toolbar of the **Sales order lines** FastTab.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. On the Action Pane, select the **Back** button to return to the sales order.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse**. A message shows the shipment and wave IDs for the order.
1. While the order line is still selected, select **Warehouse** \> **Work details** on the toolbar of the **Sales order lines** FastTab. If you use batch processing to run your waves, you might have to wait a short time for the work to be created.
1. On the **Work** page, on the Action Pane, open the **Work** tab and select **Complete work**.
1. On the **Work completion** page, set the **User ID** field to *62*.
1. On the Action Pane, select **Validate work**.
1. When you receive a message that indicates that your work is valid, select **Complete work** on the Action Pane to complete the process of picking the inventory items and putting them in the *Pack* location.
1. Make a note of the **Shipment ID** value that is shown for the work in the upper grid.

### Pack the ordered items into a container and generate return details

The inventory items have now been brought to the packing area and are ready to be packed into containers. Follow these steps to create a new container in the system and pack and close the container. After you close the container, the system automatically creates a return details record, which can be referenced later when receiving returned items back into the warehouse. At this point, a return label can be printed and delivered with the container.

1. Go to **Warehouse Management** \> **Packing and containerization** \> **Pack**.
1. In the **Select packing station** dialog, set the following values.
    - **Site:** 6
    - **Warehouse:** 62
    - **Location:** Pack
    - **Packing profile ID:** WH62

1. Select **OK** to close the dialog box and return to the **Pack** page.
1. On the **Packing station** FastTab, in the **License plate or shipment** field, enter the shipment ID you noted at the end of the previous procedure and press Return.
1. On the Action Pane, select **New container** to start the *container creation* process.
1. In the dialog, set **Container type** to *SmallBox* and then select **OK** to return to the **Pack** page.
1. On the **Item packing** FastTab, set **Identifier** to *A0001* and press Return. This moves qty 1 of item A0001 to the container for the shipment. On the **All lines** FastTab, the line for **Item number** *A0001* now shows a check in the **Complete** column.
1. On the Action Pane, select **Close container** to start the *container closing* process.
1. In the dialog, select the **Get system weight** link to load the weight of the shipment into the **Gross weight** section. Then select **OK** to return to the **Pack** page.
1. Now that the container is closed, the system automatically creates return details. Go to **Warehouse Management** \> **Inquiries and reports** \> **Return details**, where you should see that a new return details record is now listed that shows the order number and line item that you just packed. Make a note of the **Return ID** value for the new record; you'll need it later in this scenario.
1. Go to **Warehouse Management** \> **Shipments** \> **All shipments**. Select the shipment with the shipment ID you noted at the end of the previous procedure.
1. On the Action Pane, open the **Shipments** tab and select **Confirm Shipment**.

    A message shows that the shipment is confirmed.

> [!NOTE]
> If you go back to the **Return details** page and open the record with the return ID you noted earlier, you should see that the **Lines** FastTab now shows a **Return until date** that matches the [return item policy](#create-return-item-policies) that you set for the packed item. The system adds this value automatically after you confirm the shipment.

### Receive product with return details into a mixed license plate

Follow these steps to receive returned items into the warehouse.

1. Open the Warehouse Management mobile app and sign in using **User ID** *62* and **Password** *1*.
1. Open the menu item that you created for receiving using the return details method (for example, **Inbound** \> **Return details receiving**).
1. In the Return ID field, enter the return ID that you noted while working through the previous procedure. In a real scenario, the warehouse worker would typically scan this value from the return label attached to the package, which was sent to the customer together with the original shipment.
1. Enter/scan **Item** *A0001*.
1. Accept the suggested **license plate** number.
1. Enter **qty** *1*.
1. Select **Disposition code** *RMA Credit*.
1. Select **OK** to complete the receiving work.
1. Select **Cancel** to exit the flow and close the menu item.

    > [!NOTE]
    > You must exit the flow to unlock the license plate. If the license plate is locked, you won't be able to complete mixed license place receiving in Supply Chain Management, as described in the next section. With some setups, it's possible finish processing mixed license plates during the *Return item receiving* flow, but in this scenario, we'll process the license plate in Supply Chain Management.

### Complete mixed license plate receiving

The returned products have now been put onto a mixed license plate for further processing (see also [Mixed license plate receiving](/dynamics365/supply-chain/warehousing/mixed-license-plate-receiving)). Follow these steps to finish receiving the returned items.

1. Go to **Warehouse Management** \> **Inquiries and reports** \> **Mixed license plate receiving**.
1. In the **Licensed plate** grid, find the mixed license plate that you processed using the mobile app.
1. On the Action Pane, open the **License plate** tab and select **Complete license plate** to complete the mixed license plate receiving.

When you have completed mixed license plate receiving, Supply Chain Management automatically creates a return material authorization (RMA) order, which is prepared for further downstream processing, as described in [Sales returns](/dynamics365/supply-chain/warehousing/sales-returns).

## Example scenario 3: Nonpacking scenarios for return details

The return-details process can also be used in scenarios where you don't use a packing station to prepare outgoing shipments. In this case, your outgoing shipments are delivered on a pallet to the bay door, where they're packed and shipped directly. The system therefore generates the return-details record when the outbound shipment is confirmed (from the **All loads** page in Supply Chain Management), rather than after the container is packed and closed (from the **Pack** page in Supply Chain Management). Other than these details, this scenario works the same as the [packing scenario described previously](#example-scenario-2-customer-return-with-return-details-policy).

For this scenario it's important that your system is configured to create return details, generate load line inventory picking numbers, and use sales load line picking routes, as described in the [Scenario prerequisites](#scenario-prerequisites).
