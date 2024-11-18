---
title: Receive unannounced sales returns
description: Learn how to set up Microsoft Dynamics 365 Supply Chain Management to support unannounced returns, and how to receive unannounced returns in the warehouse.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/11/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSParameters, ReturnDispositionCode, WHSDispositionTable, WHSReturnItemPolicy, WHSReturnItemReceivingPolicy, WHSRFMenuItem, WHSSourceSystemDispositionCode, WHSInboundShipmentOrder, WHSSourceSystem
---

# Receive unannounced sales returns

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, the [sales return process](../sales-marketing/sales-returns.md) is usually initiated by creating a return material authorization (RMA) order. The process of creating an RMA order supports a scenario where the reason for the return isn't immediately apparent or disclosed. The RMA order serves as the primary document that guides subsequent steps in the return process, including warehouse arrival and the receiving procedures.

However, in some business scenarios, customers might request to return products without providing advance notification or an associated order. In these scenarios, the standard RMA process is bypassed, and special considerations are made to accommodate the unplanned or unanticipated (unannounced) returns.

This article explains how to set up Supply Chain Management to support unannounced returns, and how to receive unannounced returns in the warehouse.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- To receive unannounced sales returns, you must be running Supply Chain Management version 10.0.39 or later.
- To use the integration with small parcel shipping (SPS), you must be running Supply Chain Management version 10.0.39 or later.
- To print license plate labels from a mobile device, you must be running Supply Chain Management version 10.0.40 or later.

## Receiving process for unannounced returns

The *Return item receiving* flow in the Warehouse Management mobile app supports two processes for receiving unannounced returns: *Blind return* and *Return details*.

The following illustration shows how the flow works for each process.

:::image type="content" source="media/unannounced-return-process.svg" alt-text="Diagram that shows the processes for receiving unannounced returns." lightbox="media/unannounced-return-process.svg":::

### <a name="blind-return-process"></a> Blind return process

A blind return is a return where no RMA order or return details record exists in advance, and where no original sales order or shipment must be specified during receiving. During the *Return item receiving* process, workers must use the mobile app to identify and confirm the following information:

- **Customer account or Source system** – The source that is returning the item. *Customer account* is used for sales return orders and *Source system* is used when using [inbound shipment orders](wms-only-mode-using.md#inbound-shipment-orders) as part of the [Warehouse management only mode](wms-only-mode-overview.md) process.
- **Item number and quantity** – The items that are being returned and the quantity that's being returned for each item.
- **License plate ID** – The license plate of the location where the incoming items are stored after they're received.
- **Disposition code** – Depending on the setup of the mobile device menu item, workers might be able to select a disposition code to specify what should be done with the returned products. If this option isn't shown in the app during receiving, a Supply Chain Management user must enter a disposition code when they complete the mixed license plate.

> [!NOTE]
> When running the return process for [inbound shipment orders](wms-only-mode-using.md#inbound-shipment-orders), you must also define [source system disposition codes](#source-system-disposition-codes).

### <a name="return-details-process"></a> Return details process

The *Return details* return process uses a return details record. This record is automatically generated when an order is shipped. It contains all the information that's required to process a return, such as the return ID, original order ID, shipment ID, order lines, and return-until dates.

Typically, the sending company prints a return label for each outgoing shipment and delivers it together with that shipment. The return label includes a bar code that contains the return ID. Then, if a customer must return an item, they don't have to contact the sending company. Instead, they can just pack the item and attach the return label that they received together with the original shipment.

> [!NOTE]
> Only the items/variants, tracking dimensions, and quantities that are listed in the specified return details record can be returned through this process.

There are two ways to generate a return details record:

- In a *packing scenario*, the system generates a return details record after each sales order is packed into a container and the container is closed.
- In a *nonpacking scenario*, the system generates a return details record after a worker creates a shipment for a sales order and confirms it.

In both cases, the shipment date and return-until date are filled in when related shipment is confirmed.

During the *Return item receiving* process, workers must use the mobile app to identify and confirm the following information:

- **Return ID** – The ID number of the return details record.
- **Item number and quantity** – The items that are being returned and the quantity that's being returned for each item.
- **License plate ID** – The license plate of the location where the incoming items are stored after they're received.
- **Disposition code** – Depending on the setup of the mobile device menu item, workers might be able to select a disposition code to specify what should be done with the returned products. If this option isn't shown in the app during receiving, a Supply Chain Management user must enter a disposition code when they complete the mixed license plate.

## Set up unannounced sales return receiving

To prepare your system to receive returns without using an RMA order, you must enable the relevant features and complete several related configurations. The following subsections describe the settings that are required.

### Enable unannounced returns

Before you can use blind returns and/or automatic generation of return details during receiving, you must follow these steps to turn on and set up each feature in your system.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. If you plan to use the *Return details* return process, follow these steps to specify the number sequences that support this process:

    1. On the **Number Sequences** tab, find the row where the **Reference** field is set is *Return ID*. For this row, set the **Number sequence code** field to the number sequence that you want to use.
    1. Find the row where the **Reference** field is set to *Load line inventory pick*. For this row, set the **Number sequence code** field to the number sequence that you want to use.

    For more information about how to set up number sequences for these purposes, see [Number sequences overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

1. If you plan to use the *Return details* process, on the **Loads** tab, set the **Enable sales load line picking route** option to *Yes*. This setting enables load lines to be linked to sales line inventory transactions. The linking is done at the shipment level. This option uses the *Load line inventory pick* number sequence when work is completed and containers are closed.
1. On the **General** tab, on the **Returns** FastTab, set the following options:

    - **Enable return details creation** – Set this option to *Yes* to enable return details to be created when a container is closed and during shipment confirmation. This option is required only for the *Return details* process.
    - **Enable return order creation from mobile device** – Set this option to *Yes* to enable return orders to be created from a mobile device flow. The flow uses mixed license plate receiving planned lines. This option is required for both the *Return details* process and the *Blind return* process.

1. If you're using [Warehouse management only mode](wms-only-mode-overview.md), then you must set up returns for each source system by following these steps:
    1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source systems**.
    1. From the list pane, select the source system you want to set up for returns.
    1. Make the following settings on the **Inbound shipment orders** FastTab:
        - **Enable returns process** – Set to *Yes* to enable the return process for the current source system.
        - **Number sequence code** – Select the number sequence to use to generate order numbers for [inbound shipment orders](wms-only-mode-using.md#inbound-shipment-orders).
        - **Return order type** – Enter text used to stamp the created inbound shipment order. This value is used to distinguish return orders from other inbound shipment orders.
    1. Repeat these steps for each relevant source system.

### Set up disposition codes

Disposition codes are collections of rules that can be used when items are received in Supply Chain Management. They help determine the inventory status, the work template, and the location directive for the items, based on the scanned code.

For example, when a warehouse worker uses a mobile device to receive items that were damaged, the worker must scan a disposition code for damaged items.

- If you want to credit the item to your inventory and make it available for repurchase, set up a disposition code that sets the inventory status of the received item to *Available*.
- If you receive items that you can't resell and must therefore dispose of, you can use a disposition code for RMA scrap. This disposition code then returns a *return disposition code*.

Disposition codes can be used for different processes, such as *purchase order receiving*, *production order report as finished*, and *sales order return receiving*. For the *sales order return receiving* process, if the items are registered by using a mobile device, the use of disposition codes is mandatory.

#### Return disposition codes

To view and set up your return disposition codes, go to **Sales and Marketing** \> **Setup** \> **Returns** \> **Disposition codes**. You define each code by specifying an ID number, an action, and a description. The action defines how items that are assigned to the code should be handled.

For more information about return disposition codes and the actions that are available, see [Disposition codes and disposition actions](../sales-marketing/sales-returns#disposition-codes-and-disposition-actions).

#### Mobile device disposition codes

To set up disposition codes that can be used on a mobile device, go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Disposition codes**. Disposition codes that you create here are available to mobile devices and can support several types of operations, including returns, sales orders, and inventory management. Disposition codes for returns must be linked to a return disposition code that's defined at **Sales and Marketing** \> **Setup** \> **Returns** \> **Disposition codes**, and that assigns a return action for the code.

For more information about mobile disposition codes and how to set them up, see [Set up dispositions codes](tasks/set-up-dispositions-codes.md).

#### <a name="source-system-disposition-codes"></a> Source system disposition codes

If you're using [Warehouse management only mode](wms-only-mode-overview.md), then you must map local dispositions codes with the *source system disposition codes* used in each relevant [source systems](wms-only-mode-setup.md#source-systems). These codes are used when processing [inbound shipment orders](wms-only-mode-using.md#inbound-shipment-orders).

To set up source system disposition codes, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management integration** \> **Source system disposition codes**.
1. On the Action pane, select **New** to add a new code. Then make the following settings for the new code:
    - **Disposition code** – Select the local disposition code that you want to map.
    - **Source system** – Select the source system that you want to map the local disposition code to.
    - **Source system disposition code** – Enter the disposition code that is used in the source system.

1. Repeat the previous step until you have set up all of the disposition codes that you need to map.

### Set up return item policies

Return item policies let you control the conditions under which the system allows items to be returned. You can set policies for each item, groups of items, or all items, as you require. To set up your policies, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Return items** \> **Return item policies**.
1. On the Action Pane, select **New** to create a policy.
1. In the **Item code** field, select one of the following values to specify the scope that the new policy applies to:

    - *Table* – The return item policy applies only to a specific product.
    - *Group* – The return item policy applies to a specific product group.
    - *All* – The return item policy applies to all products.

1. In the **Item** field, if you set the **Item code** field to *Table* in the previous step, select the item number that the new policy applies to. If you set the **Item code** field to *Group*, select the item group that the new policy applies to. If you set the **Item code** field to *All*, the **Item** field is unavailable.
1. In the **Return acceptance** field, select one of the following values:

    - *Always allowed* – Items that match the selected **Item code** and **Item** values can always be returned.
    - *Never allowed* – Items that match the selected **Item code** and **Item** values can never be returned.
    - *Allowed days after shipment* – Items that match the selected **Item code** and **Item** values can be returned only for a limited time after they were sold, as defined in the **Allowed days for return** field.

1. If you set the **Return acceptance** field to *Allowed days after shipment*, set the **Allow days for return** field to the number of allowed days.
1. Repeat this procedure for each item or item group, as you require. When returns are processed, the most specific return item policy applies to each item in the return.
1. On the Action Pane, select **Save**.

### <a name="return-receive-policy"></a>Create return item receiving policies

You must define the required return item receiving policies before you create the related mobile device menu items. These policies enable each menu item to process the return correctly.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**.
1. On the Action Pane, select **New** to add a return item receiving policy.
1. Set the following fields for the new policy:

    - **Return item receiving policy ID** – Enter a name for the policy (for example, *Blind return* or *Return details*).
    - **Description** – Enter a short description of the policy.
    - **Return process** – Select the type of return process that the policy represents (*Return details* or *Blind return*).
    - **Create return order** – Select the type of return order that the system should create to manage returns:

        - *Return order* – The system creates a return order for each return. Select this value if you aren't using [Warehouse management only mode](wms-only-mode-overview.md).
        - *Inbound shipment order* – The system creates an [inbound shipment order](wms-only-mode-using.md#inbound-shipment-orders) for each return. Select this value if you're using [Warehouse management only mode](wms-only-mode-overview.md).

    - **Return order identification** – This field is available only when the **Return process** field is set to *Blind return* and the **Create return order** field is set to *Inbound shipment order*. The way that you use it depends on the needs of your external system. (See the documentation for your external system.) Select the type of extra identifying information that the system should return to the source system when it registers a return order:

        - *None* – The system doesn't return any extra identifying information, and the app doesn't prompt the worker to enter any extra information during receiving.
        - *Account number* – The system returns an account number to help identify the return order. This value is typically the ID of the customer who is returning the items (the customer account number). The mobile app prompts the worker to scan or enter this number during receiving.

    - **Return order type** – This field is available only when the **Return order identification** is available and set to *Account number*. Like the account number, the value in this field is returned to the source system when a return order is registered. It's intended to hold the name that identifies the document type for return orders in the source system. The way that you use it depends on the needs of your external system. (See the documentation for your external system.) If you leave this field blank, the value is inherited from the relevant [source system configuration](wms-only-mode-unannounced-returns-setup.md#source-systems).

    > [!IMPORTANT]
    > If your source system is Dynamics 365 Supply Chain Management (as is the case when you run an [external shared warehouse scenario](wms-only-mode-external-shared-warehouse.md)), you must set the following values for your blind return policies:
    >
    > - **Return order identification** – Select *Account number*, and instruct workers to enter the customer ID (account number) when the mobile app prompts them during receiving.
    > - **Return order type** – Enter *Return*, which is the return order type that is used in Supply Chain Management. (Alternatively, if *Return* is already specified as the default return order type for the source system, leave this field blank.)

1. If you support both types of unannounced return processes (*Return details* and *Blind return*), repeat this procedure to add a return item receiving policy for the other process.

### <a name="mdmi"></a>Set up mobile device menu items to process unannounced returns

To enable workers to process unannounced returns, you must create a separate mobile device menu item for each type of unannounced return process (*Return details* or *Blind return*) that you support.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. On the Action Pane, select **New** to add a mobile device menu item.
1. Set the following fields for the new menu item:

    - **Menu item name** – Enter an internal name for the menu item (for example, *Blind returns*).
    - **Title** – Enter the name that should be shown for the menu item in the mobile app (for example, *Blind return item receiving*).
    - **Mode** – Select *Work*.
    - **Use existing work** – Set this option to *No*.
    - **Work creation process** – Select *Return item receiving*.
    - **Barcode data policy** – Select the policy to use if multiple fields are filled in based on a single bar code scan. Learn more in [GS1 bar codes](gs1-barcodes.md).
    - **Generate license plate** – Set this option to *Yes* to automatically create new license plates as they're needed. Set it to *No* if the worker must always select an existing license plate.
    - **Display disposition code** – Select whether workers should be prompted to select a disposition code during the receiving process. The disposition code determines the inventory status, work template, and location directive for the returned items.
    - **Print label** – Set this option to *Yes* to always print a license plate label after all steps in the related work template are completed (regardless of whether a print step is included in the work template). If you want to allow the work template to print the license plate label at a different point in the process, set this option to *No*. The license plate label includes a bar code that provides the ID of the license plate where the worker places the returned items. Learn more in [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md).
    - **Return item receiving policy ID** – Select the [item receiving policy](#return-receive-policy) that you created for the type of return process (*Return details* and *Blind return*) that this menu item supports.

1. If you support both types of unannounced return processes (*Return details* and *Blind return*), repeat steps 2 and 3 to create a menu item for the other process
1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**.
1. Add the new menu items to an appropriate place in your mobile device menu structure.

## Integrate return label printing with small parcel shipping

Small parcel shipping (SPS) integration lets you retrieve shipping labels from the SPS carriers or carrier hubs that you integrate with your system. However, some customization is required. The integration supports preaddressed and prepaid return labels, which make returns more convenient for your customers. The return labels can include a bar code that identifies the return details record ID. Warehouse workers can then scan this bar code when the package arrives at your warehouse.

For more information about how to set up SPS integration, see [Small parcel shipping](small-parcel-shipping.md).

Follow these steps to enable return details with SPS integration.

1. Go to **Transportation management** \> **Setup** \> **Transportation management parameters**.
1. On the **Shipping carriers** FastTab, set the **Enable shipping label request type** option to *Yes*. This setting adds a new **Print container return shipping label rule** field to the **Container packing policies** page. You can use this field to select the conditions under which return labels should be printed as part of the container packing process. For details about how to use this setting, see the next section.

## Print return labels

When you use a *Return details* return process, you must print a return label for each shipment and include that label with the shipment. The *container packing policy* that applies to each shipment establishes the printing options. Depending on the setup of your system, return labels are typically printed as part of the container closing process. However, you can manually print or reprint them for a selected return details record at any time.

The return label includes the shipping address of your returns warehouse and a bar code that contains the return details record ID. Therefore, warehouse workers can scan this bar code when the package arrives at your warehouse.

Follow these steps to configure the label printing options for a container packing policy.

1. Go to **Warehouse management** \> **Setup** \> **Containers** \> **Container packing policies**.
1. Select or create the container packing policy that you want to set up.
1. On the **Container manifest** FastTab, set the following fields:

    - **Automatic manifest at container close** – Set this option to *Yes*.
    - **Manifest requirements for container** – Set this field to *Transportation management*.

1. On the **Carrier label printing** FastTab, set the following fields:

    - **Print container shipping label rule** – Select one of the following options to specify the rule for printing outbound shipping labels:

        - *Never* – Users can close containers without printing a shipping label.
        - *Always* – A shipping label is required. Users can't close the container unless the system can retrieve a label.
        - *If setup exists* – For containers where a shipping label setup exists, the system must retrieve the required label before users can close the container. For containers where no shipping label setup exists, users can close the container without printing a label.

    - **Print container return shipping label rule** – Select one of the following options to specify the rule for printing return labels to include in each container:

        - *Never* – Users can close containers without printing a return label.
        - *Always* – A return label is required. Users can't close the container unless the system can retrieve a label.
        - *If setup exists* – For containers where a return label setup exists, the system must retrieve the required label before users can close the container. For containers where no return label setup exists, users can close the container without printing a label.

    - **Printer name** – Select the Zebra Programming Language (ZPL) printer where the system should print shipping and/or return labels when this container packing policy is used.

Follow these steps to manually print or reprint a return label for a return details record.

1. Go to **Warehouse management** \> **Inquiries and reports** \> **Return details**.
1. In the list pane, select the return details record that you want to print a label for.
1. On the Action Pane, select **Print** \> **Return shipping label**.

The return label is printed on the printer that's specified in the relevant container packing policy that's associated with the **Container ID** value that's listed for the return details record.

## Example scenarios for the sales return order creation process

This section provides example scenarios that show how to set up and process unannounced returns.

### Scenario prerequisites

Before you work through the example scenarios, you must complete all the prerequisites that are described in the following subsections.

#### Enable sample data

To work through the example scenarios by using the sample records and values that are specified here, you must be on a system where the standard [demo data](/dynamics365/fin-ops-core/dev-itpro/get-started/demo-data) is installed. Additionally, you must select the **USMF** legal entity before you begin. The example scenarios use the demo data that's associated with the worker/person *Julia Funderburk*.

You can also use these scenarios as guidance for using the feature on a production system. However, in that case, you must substitute your own values for each setting that's described here.

#### Set up number sequences

You must have number sequences that generate unique return IDs and load line inventory pick numbers.

1. Go to **Organization administration** \> **Number sequences** \> **Number sequences**.
1. On the Action Pane, on the **Number sequence** tab, in the **New** group, select **Number sequence** to create a number sequence that generates return ID numbers.
1. Set the following values for the new number sequence:

    - **Number sequence code:** *ReturnID*
    - **Name:** *ReturnID*
    - **Scope:** *Company*
    - **Company:** *USMF*

1. On the Action Pane, select the **Back** button.
1. On the Action Pane, on the **Number sequence** tab, in the **New** group, select **Number sequence** to create a number sequence that generates load line inventory pick numbers.
1. Set the following values for the new number sequence:

    - **Number sequence code:** *LLIP*
    - **Name:** *LLIP*
    - **Scope:** *Company*
    - **Company:** *USMF*

1. On the Action Pane, select **Save**.

#### Enable unannounced return features

Follow these steps to enable the features that are required to support unannounced returns.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **Number sequences** tab, set the **Number sequence code** field to *ReturnID*.
1. Set **Number sequence code** field to *LLIP*.
1. On the **General** tab, turn on the **Enable return details creation** option.
1. Turn on the **Enable return order creation from mobile device** option.
1. On the **Loads** tab, turn on the **Enable sales load line picking route** option.

For information about how to configure these settings, see the [Enable unannounced returns](#enable-unannounced-returns) section.

#### Create return item policies

Follow these steps to create return item policies for the items that are used in the scenarios.

1. Go to **Warehouse management** \> **Setup** \> **Return items** \> **Return item policies**.
1. Add a return item policy to define the conditions under which the item that's used in the scenarios can be returned.
1. Set the following values for the new policy:
    - **Item code:** *Table*
    - **Item:** *A0001*
    - **Return acceptance:** *Allowed days after shipment*
    - **Allowed days for return:** *28*

Learn more in the [Set up return item policies](#set-up-return-item-policies) section.

#### Set up return item receiving policies

Follow these steps to create return item receiving policies for the scenarios.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Return item receiving policies**.
1. Add two return item receiving policies: one for the *Blind return* process and one for the *Return details* process.

Learn more in the [Create return item receiving policies](#return-receive-policy) section.

#### Set up mobile device menu items and menus

Follow these steps to create mobile device menu items for the scenarios.

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Create two mobile device menu items for handling unannounced returns: one for the *Blind return* process and one for the *Return details* process.
1. Set up the new menu items in the following way:

    - Give each menu item a name that identifies the type of return that it's intended to process (for example, *Blind return receiving* or *Return details receiving*).
    - For each menu item, set the **Work creation process** field to *Return item receiving*.
    - For each menu item, enable both the **Generate license plate** option and the **Display disposition code** option.
    - For each menu item, set the **Return item receiving policy ID** field to the policy that matches the type of return that the menu item should handle (*blind returns* or *return details*).

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu**.
1. Add both menu items to an appropriate place in your mobile device menu structure.

Learn more in the [Set up mobile device menu items](#mdmi) section.

## Example scenario 1: Customer return with a blind return policy

In the blind receiving process, warehouse workers can receive return items without matching them to an original sales order or shipment. Warehouse workers just have to enter the customer account ID, item IDs, and quantities.

The following illustration shows a flowchart for the blind receiving process.

:::image type="content" source="media/blind-return-policy.svg" alt-text="Diagram that shows the blind receiving process." lightbox="media/blind-return-policy.svg":::

### Use the mobile app to receive a blind return to a mixed license plate

Follow these steps to receive products to a mixed license plate in a warehouse when there's a blind return policy.

1. Open the Warehouse Management mobile app, and sign in by using *62* as the user ID and *1* as the password.
1. Open the menu item that you created for receiving blind returns (for example, **Inbound** \> **Blind returns receiving**).
1. In the **Customer account** field, enter *US-003*.
1. In the **Item** field, enter or scan item number *A0001*.
1. Accept the license plate number that's suggested.
1. In the **qty** field, enter *1*.
1. In the **Disposition code** field, select *RMA Credit*.
1. Select **OK** to complete the receiving work.
1. Select **Cancel** to exit the flow and close the menu item.

    > [!NOTE]
    > You must exit the flow to unlock the license plate. If the license plate is locked, you can't complete mixed license plate receiving in Supply Chain Management, as described in the next section. In some setups, you can finish processing mixed license plates during the *Return item receiving* flow. However, in this scenario, you'll process the license plate in Supply Chain Management.

### <a name="complete-mixed-license-plate-receiving"></a> Complete mixed license plate receiving

The returned products have now been put onto a mixed license plate for further processing. (Learn more in [Mixed license plate receiving](mixed-license-plate-receiving.md).) Follow these steps to finish receiving the returned items.

1. Go to **Warehouse Management** \> **Inquiries and reports** \> **Mixed license plate receiving**.
1. In the **License plate** grid, find the mixed license plate that you processed by using the mobile app.
1. On the Action Pane, on the **License plate** tab, select **Complete license plate** to complete mixed license plate receiving.

After you complete mixed license plate receiving, Supply Chain Management automatically creates an RMA order that's prepared for further downstream processing, as described in [Sales returns](../sales-marketing/sales-returns.md).

> [!TIP]
> You can set up your mobile device menu item for processing returns to include a step that lets workers complete mixed license plate receiving directly from the mobile device while receiving the return. Then you won't need to [complete this step](mixed-license-plate-receiving.md) later in the Supply Chain Management web client. To do so, create a [detour](warehouse-app-detours.md) item with the **Activity code** *Complete mixed license plate*. Learn more in [Set up a mobile device menu item for completing mixed license plates](mobile-device-complete-mixed-lp-menu.md).

## Example scenario 2: Customer return with a return details policy

For this scenario, return details are generated when an order is processed for shipment at the packing station, and matching labels are included with the shipment. If any items must be returned, the customer packs the return items, attaches the return label that they received together with the original shipment, and ships the return items back to the seller. When the returned items arrive at the seller's warehouse, a worker scans the return label and the item to get the return ID. The return ID identifies a return details record that includes the original order details. This process helps prevent fraud, inventory errors, and lost packages.

The following illustration shows the steps that are required to create a sales order and complete the work of moving the ordered items to the packing area. Workers then pack the order, and return details are generated when the container is closed.

:::image type="content" source="media/generate-return-details.svg" alt-text="Diagram that shows the process for generating return details." lightbox="media/generate-return-details.svg":::

The following illustration shows a flowchart of the receiving process where the *Return item receiving* mobile menu item is used to process a return that has return details.

:::image type="content" source="media/return-details-policy.svg" alt-text="Diagram that shows the return details receiving process." lightbox="media/return-details-policy.svg":::

### Create a sales order and release it to the warehouse for packing

For this scenario, a related sales order must already exist, and the item must have been shipped before the return. Therefore, you must create the required records before you can work through the related return. Follow these steps to create a sales order and complete the work of moving the ordered items to the packing area.

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, set the **Customer account** field to *US-001*.
1. Select **OK** to close the dialog box.
1. The new sales order is opened. The **Sales order lines** FastTab includes a single, blank order line. Set the following values for this line:

    - **Item number:** *A0001*
    - **Quantity:** *1*
    - **Site:** *6*
    - **Warehouse:** *62*

1. While the order line is still selected on the **Sales order lines** FastTab, select **Inventory** \> **Reservation** on the toolbar.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. On the Action Pane, select the **Back** button to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, select **Release to warehouse**. A message shows the shipment and wave IDs for the order.
1. While the order line is still selected on the **Sales order lines** FastTab, select **Warehouse** \> **Work details** on the toolbar. If you use batch processing to run your waves, you might have to wait a short time for the work to be created.
1. On the **Work** page, on the Action Pane, on the **Work** tab, select **Complete work**.
1. On the **Work completion** page, set the **User ID** field to *62*.
1. On the Action Pane, select **Validate work**.
1. When you receive a message that indicates that your work is valid, select **Complete work** on the Action Pane to complete the process of picking the inventory items and putting them in the *Pack* location.
1. Make a note of the **Shipment ID** value that's shown for the work in the upper grid.

### Pack the ordered items into a container and generate return details

The inventory items have now been brought to the packing area and are ready to be packed into containers. Follow these steps to create a new container in the system, and to pack and close the container. After you close the container, the system automatically creates a return details record. This record can be referenced later, when returned items are received back into the warehouse. At this point, a return label can be printed and delivered together with the container.

1. Go to **Warehouse Management** \> **Packing and containerization** \> **Pack**.
1. In the **Select packing station** dialog box, set the following values:

    - **Site:** *6*
    - **Warehouse:** *62*
    - **Location:** *Pack*
    - **Packing profile ID:** *WH62*

1. Select **OK** to close the dialog box and return to the **Pack** page.
1. On the **Packing station** FastTab, in the **License plate or shipment** field, enter the shipment ID that you noted at the end of the previous procedure. Then select **Return**.
1. On the Action Pane, select **New container** to start the *container creation* process.
1. In the dialog box, set the **Container type** field to *SmallBox*. Then select **OK** to return to the **Pack** page.
1. On the **Item packing** FastTab, set the **Identifier** field to *A0001*. Then select **Return**. A quantity of *1* of item number *A0001* is moved to the container for the shipment. On the **All lines** FastTab, the line for item number *A0001* now shows a check mark in the **Complete** column.
1. On the Action Pane, select **Close container** to start the *container closing* process.
1. In the dialog box, select the **Get system weight** link to load the weight of the shipment into the **Gross weight** section. Then select **OK** to return to the **Pack** page.
1. Now that the container is closed, the system automatically creates return details. Go to **Warehouse Management** \> **Inquiries and reports** \> **Return details**.
1. The **Return details** page should list a new return details record that shows the order number and line item that you just packed. Make a note of the **Return ID** value for the new record. You'll need this value later in this scenario.
1. Go to **Warehouse Management** \> **Shipments** \> **All shipments**.
1. Select the shipment that has the shipment ID that you noted at the end of the previous procedure.
1. On the Action Pane, on the **Shipments** tab, select **Confirm Shipment**.

    A message shows that the shipment is confirmed.

> [!NOTE]
> If you return to the **Return details** page and open the record that has the return ID that you noted earlier, the **Lines** FastTab should now show a **Return until date** value that matches the [return item policy](#create-return-item-policies) that you set for the packed item. The system automatically adds this value after you confirm the shipment.

### Receive a product with return details to a mixed license plate

Follow these steps to receive returned items into the warehouse.

1. Open the Warehouse Management mobile app, and sign in by using *62* as the user ID and *1* as the password.
1. Open the menu item that you created for receiving by using the *Return details* process (for example, **Inbound** \> **Return details receiving**).
1. In the **Return ID** field, enter the return ID that you noted during the previous procedure. In a real-world scenario, the warehouse worker typically scans this value from the return label that's attached to the package. (This label was sent to the customer together with the original shipment.)
1. In the **Item** field, enter or scan item number *A0001*.
1. Accept the license plate number that's suggested.
1. In the **qty** field, enter *1*.
1. In the **Disposition code** field, select *RMA Credit*.
1. Select **OK** to complete the receiving work.
1. Select **Cancel** to exit the flow and close the menu item.

    > [!NOTE]
    > You must exit the flow to unlock the license plate. If the license plate is locked, you can't complete mixed license plate receiving in Supply Chain Management, as described in the next section. In some setups, you can finish processing mixed license plates during the *Return item receiving* flow. However, in this scenario, you'll process the license plate in Supply Chain Management.

### Complete mixed license plate receiving

The returned products have now been put onto a mixed license plate for further processing. (Learn more in [Mixed license plate receiving](mixed-license-plate-receiving.md).) Follow these steps to finish receiving the returned items.

1. Go to **Warehouse Management** \> **Inquiries and reports** \> **Mixed license plate receiving**.
1. In the **License plate** grid, find the mixed license plate that you processed by using the mobile app.
1. On the Action Pane, on the **License plate** tab, select **Complete license plate** to complete the mixed license plate receiving.

After you complete mixed license plate receiving, Supply Chain Management automatically creates an RMA order that's prepared for further downstream processing, as described in [Sales returns](../sales-marketing/sales-returns.md).

> [!TIP]
> You can set up your mobile device menu item for processing returns to include a step that lets workers complete mixed license plate receiving directly from the mobile device while receiving the return. Then you won't need to [complete this step](mixed-license-plate-receiving.md) later in the Supply Chain Management web client. To do so, create a [detour](warehouse-app-detours.md) item with the **Activity code** *Complete mixed license plate*. Learn more in [Set up a mobile device menu item for completing mixed license plates](mobile-device-complete-mixed-lp-menu.md).

## Example scenario 3: Nonpacking scenarios for return details

The *Return details* process can also be used in scenarios where you don't use a packing station to prepare outgoing shipments. In this case, your outgoing shipments are delivered on a pallet to the bay door, where they're packed and shipped directly. Therefore, the system doesn't generate the return details record after the container is packed and closed (from the **Pack** page in Supply Chain Management). Instead, it generates the return details record when the outbound shipment is confirmed (from the **All loads** page in Supply Chain Management). Otherwise, this scenario works in the same way as the [previously described packing scenario](#example-scenario-2-customer-return-with-a-return-details-policy).

For this scenario, it's important that your system is configured to create return details, generate load line inventory picking numbers, and use sales load line picking routes, as described in the [Scenario prerequisites](#scenario-prerequisites) section.
