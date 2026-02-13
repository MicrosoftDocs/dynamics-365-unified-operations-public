---
title: Inbound inventory operation in POS
description: Learn about the capabilities of the point of sale (POS) inbound inventory operation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-06-20
ms.custom: 
  - bap-template
---

# Inbound inventory operation in POS

[!include [banner](includes/banner.md)]

This article describes the capabilities of the point of sale (POS) inbound inventory operation in Microsoft Dynamics 365 Commerce.

In Commerce version 10.0.10 and later, inbound and outbound operations in POS replace the picking and receiving operation.

> [!NOTE]
> In Commerce version 10.0.10 and later, the **Inbound operation** POS operation handles new features in the POS application that relate to receiving store inventory against purchase orders and transfer orders. If you're currently using the picking and receiving operation in POS, consider developing a strategy for moving from that operation to the new inbound and outbound operations. Although the picking and receiving operation remains in the product, the Commerce team makes no further functional or performance investments in it after Commerce version 10.0.9.

## Prerequisites

Before your organization can use the inbound operation functionality, complete the following prerequisites.

### Configure an asynchronous document framework

For information about how to configure an asynchronous document framework, see [Commerce asynchronous document framework](async-document-framework.md). You can skip this step if you already configured an asynchronous document framework for other operations.

### Add Inbound operation to the POS screen layout

Configure the **Inbound operation** POS operation on one or more of your [POS screen layouts](/dynamics365/unified-operations/retail/pos-screen-layouts). Before you deploy the new operation in a production environment, thoroughly test it and train your users to use it.

## Inbound inventory operation

The inbound inventory operation enables POS users to perform the following tasks:

- Receive inventory into store stock from either confirmed purchase order documents or shipped transfer order documents.
- View information about historical inventory receipts for seven days after the document is fully received.
- Create new inbound transfer order requests.

When you start the inbound operation from the POS application, a list page view appears. This view shows open purchase order and transfer order documents that have inventory lines that the current store schedules to receive. To find and select a specific document, you can scroll the list or use the search feature.

The inbound inventory document list has three tabs:

- **Active** – This tab shows documents that are fully or partially open, and that contain lines or quantities on lines that you must still receive.
- **Draft** – This tab shows new inbound transfer order requests that the store created. However, the documents are only saved locally. They aren't yet submitted to Commerce headquarters for processing.
- **Complete** – This tab shows a list of purchase order or transfer order documents that the store fully received during the last seven days. This tab is for informational purposes only. All the information about the documents is read-only data for the store.

When you view documents on any of the tabs, the **Status** field helps you understand the stage that the document is in.

- **Draft** – The purchase order or transfer order document is only saved locally to the store’s channel database. No information about the purchase order or transfer order request is submitted to headquarters.
- **Created** - The purchase order request is created in headquarters, but not yet confirmed.
- **Requested** – The purchase order or transfer order is created in headquarters, and is fully open. No receipts are yet processed against the document. For a purchase order, receiving can begin at any time while it's in **Requested** status.
- **Partially shipped** – The transfer order document has one or more lines or partial line quantities that the outbound warehouse posts as shipped. These shipped lines are available to be received through the inbound operation.
- **Fully shipped** – The transfer order has all its lines and full line quantities posted as shipped by the outbound warehouse. The whole document is available to be received through the inbound operation.
- **Partially received** – Some of the lines or line quantities on the purchase order or transfer order document are received by the store, but some lines remain open.
- **Fully received** – All lines and quantities on the purchase order or transfer order document are fully received. The documents are accessible only on the **Complete** tab and are read-only by store users.
- **In progress** – This status informs device users that another user is actively working on the document.
- **Paused** – This status is shown after **Pause receiving** is selected to temporarily stop the receiving process.
- **Processing in HQ** – The document is submitted to headquarters from the POS application, but it isn't yet successfully posted to headquarters. The document is going through the asynchronous document posting process. After the document is successfully posted to headquarters, its status is updated to **Fully received** or **Partially received**.
- **Processing failed** – The document is posted to headquarters and rejected. The **Details** pane shows the reason for the posting failure. You must edit the document to fix data problems, and then resubmit it to headquarters for processing.

When you select a document line in the list, a **Details** pane appears. This pane shows additional information about the document, such as shipment and date information. A progress bar shows how many items must still be processed. If the document wasn't successfully processed to headquarters, the **Details** pane also shows error messages that are related to the failure.

In the document list view, you can select **Order details** on the app bar to view the document details. You can also activate receipt processing on eligible document lines.

In the document list view, you can also create a new purchase order or inbound transfer order request for a store. The documents remain in **Draft** status and can be adjusted or deleted until they're submitted to headquarters for processing.

## Receiving process

After you select a purchase order or transfer order document on the **Active** tab, select **Order details** to start the receiving process.

By default, the **Receiving now** view appears. This view is optimized for barcode scanning. Use it to build a list of the scanned items so you can receive those items. To start the receiving process, begin scanning item barcodes.

As you scan item barcodes in the **Receiving now** view, the application validates the items against the selected purchase or transfer order document. This validation makes sure that each scanned item matches a valid item on the document. In the **Receiving now** view, each scan of a barcode represents the receipt of a quantity of one unit, unless a quantity is embedded in the barcode. You can repeatedly scan barcodes in this view to build a list of all the items and quantities for the receipt.

### Example scenario

A user receives a purchase order that contains 10 units of barcode 5657900266. The user scans that barcode 10 times to update the **Receiving now** field by one unit per scan. After the user completes the scans, the **Receiving now** field for the item's line shows that a quantity of 10 was received.

Alternatively, in a scenario where the item quantity is large, the user might prefer to manually enter the quantity instead of scanning the barcode for each item that is received. In this case, the user scans the barcode one time to add the item to the **Receiving now** list. The user then selects the associated line in the **Receiving now** view and then, in the **Details** pane that appears on the right side of the page, updates the **Receiving quantity** field for the item.

Although the **Receiving now** view is optimized for barcode scanning, users can also select **Receive product** on the app bar, and then enter the item ID or barcode data via a dialog box. After the item that you entered is validated, you're prompted to enter the receipt quantity.

The **Receiving now** view provides a focused way for users to see which products they're receiving. Alternatively, use the **Full order list** view. This view shows the whole list of document lines for the selected purchase or transfer order document. Users can manually select lines in the list and then, in the **Details** pane, update the **Receiving quantity** field for the selected line. In the **Full order list** view, users can scan barcodes, or they can use the **Receive product** function to enter the item ID or barcode, and data about the received quantity, without first having to select the matching item line in the list.

### Over-receiving validations

Validations occur during the receiving process for the document lines. They include validations for over-delivery. If a user tries to receive more inventory than was ordered on a purchase order, but either over-delivery isn't configured or the amount that is received exceeds the over-delivery tolerance that is configured for the purchase order line, the user receives an error and isn't allowed to receive the excess quantity.

Over-receiving isn't permitted for transfer order documents. Users always receive errors if they try to receive more than was shipped for the transfer order line.

### Close purchase order lines

You can close the remaining quantity on an inbound purchase order during the receiving process if the shipper confirms that they can't ship the full quantity that you requested. To close the remaining quantity, the company must be configured to allow underdelivery of purchase orders. Additionally, an underdelivery tolerance percentage must be defined for the purchase order line.

To configure the company to allow underdelivery of purchase orders, in headquarters go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**. On the **Delivery** tab, turn on the **Accept underdelivery** parameter. Then run the **1070** (**Channel configuration**) distribution schedule job to sync the setting changes to channels.

Predefine underdelivery tolerance percentages for a purchase order line on products as part of the product configurations in headquarters. Alternatively, set or overwrite them on a specific purchase order in headquarters.

After an organization completes the purchase order underdelivery configurations, POS users see a new **Close remaining quantity** option in the **Details** pane when an inbound purchase order line is selected in the **Inbound inventory** operation. If the user closes the remaining quantity, POS performs a validation to verify whether the quantity being closed is within the underdelivery tolerance percentage defined on the purchase order line. If the underdelivery tolerance is exceeded, an error message is displayed and the user can't close the remaining quantity until the previously received quantity plus the **Receiving now** quantity meets or exceeds the minimal quantity that needs to be received based on the underdelivery tolerance percentage. 

When a user turns on the **Close remaining quantity** option for a purchase order line and completes the receipt by executing the **Finish receiving** action, the POS app sends a closure request to headquarters and cancels any unreceived quantity of the order line. At this point, the line is considered fully received. 

### Receiving location-controlled items

If the items that you're receiving are location-controlled, select the location where you want to receive the items during the receiving process. Configure a default receiving location for your store warehouse to make this process more efficient. Even if you configure a default location, you can override the receiving location on selected lines as needed.

The operation respects the **Blank receipt allowed** configuration on the **Location** storage dimension, and doesn't require that a location dimension is entered if blank receipts are allowed. If blank receipt locations aren't allowed for an item, the POS application shows an error and requires that a location is entered before the receipt can be posted.

### Receive all

As you require, select **Receive all** on the app bar to quickly update the **Receiving now** quantity for all the document lines to the maximum value that's available to be received for those lines.

### Receipt of unplanned items on purchase orders

In Commerce version 10.0.14 and later, users can receive a product that wasn't originally on the purchase order. This feature only works for purchase order receiving. It's not possible to receive items against transfer orders when the items weren't previously ordered and shipped from the outbound warehouse.

Users can't add new products to the purchase order during POS receiving if the [purchase order change management workflow](../supply-chain/procurement/purchase-order-approval-confirmation.md) is enabled in headquarters. To enable change management, all changes to a purchase order must first be approved before receiving is allowed. Because this process allows a receiver to add new lines to the purchase order, receiving fails if the change management workflow is enabled. If change management is enabled for all purchase orders, or for the vendor linked to the purchase order actively being received in POS, the user can't add new products to the purchase order during receiving in POS.

You can't use the functionality that enables adding lines as a workaround for receiving extra quantities of products already on the purchase order. Over-receiving is managed through the standard [over-receiving](#over-receiving-validations) settings for the product line on the purchase order.

When a user is receiving with the **Inbound operation** in POS, if the user scans or keys a product barcode or product number that is recognized as a valid item but isn't recognized as an item on the current purchase order, the user receives a message prompting them to add the item to the purchase order. If the user adds the item to the purchase order, the quantity entered in **Receiving now** is considered the ordered quantity for the purchase order line.

When the purchase order receipt is complete and submitted to headquarters for processing, the added lines are created on the purchase order master document. On the purchase order line in headquarters, there's an **Added by POS** flag on the **General** tab of the purchase order line. The **Added by POS** flag indicates that the purchase order line was added by the POS receiving process and wasn't a line that was on the purchase order before receiving.

### Cancel receiving

Use the **Cancel receiving** function on the app bar only if you want to back out of the document and don't want to save any changes. For example, you initially selected the wrong document and don't want any of the previous receiving data saved.

### Pause receiving

If you're receiving inventory, you can use the **Pause receiving** function if you want to take a break from the receiving process. For example, you might want to perform another operation from the POS, such as ringing up a customer sale, or delay posting of the receipt.

When you select **Pause receiving**, the document's status changes to **Paused**. Users know that data is entered for the document, but the document isn't yet committed. When you're ready to resume the receiving process, select the paused document, and then select **Order details**. Any **Receiving now** quantities that you previously saved are retained and can be viewed from the **Full order list** view.

### Review

Before you commit the receipt to headquarters, use the review functionality to validate the inbound document. The review functionality alerts you to any missing or incorrect data that might cause processing failures and provides an opportunity to correct problems before submitting the receipt request. To enable the **Review** function on the action pane, first enable the **Enable validation in POS inbound and outbound inventory operations** feature through the **Feature management** workspace in headquarters.

The **Review** function validates the following issues in an inbound document:

- **Over-receiving** – The **Receiving now** quantity is greater than the ordered quantity. The severity of this issue is determined by the overdelivery configuration in headquarters.
- **Under-receiving** – The **Receiving now** quantity is less than the ordered quantity. The severity of this issue is determined by the underdelivery configuration in headquarters.
- **Serial number** – The serial number isn't provided or validated for a serialized item that requires a serial number to be registered in inventory.
- **Location not set** – The location isn't specified for a location-controlled item where a blank location isn't allowed.
- **Deleted lines** – The order has lines deleted by a headquarters user that the POS application doesn't know about.

Set the **Enable automatic validation** parameter to **Yes** in **Commerce parameters** > **Inventory** > **Store inventory** to automatically run the validation when **Finish receiving** is selected.

### Finish receiving

When you finish entering all the **Receiving now** quantities for products, select **Finish receiving** on the action pane to process the receipt.

If **Review** functionality is configured, when users complete a purchase order receipt, they're prompted to enter a value in the **Receipt number** field. Typically, this value is equivalent to the identifier of the vendor packing slip. The **Receipt number** data is stored in the product receipt journal in headquarters. Receipt numbers aren't captured for transfer order receipts.

When you use asynchronous document processing, the asynchronous document framework submits the receipt. The time that it takes for the document to be posted depends on the size of the document (the number of lines) and the general processing traffic that's occurring on the server. Typically, this process occurs in a matter of seconds. If document posting fails, the **Inbound operation** document list notifies the user, and the document status updates to **Processing failed**. The user can then select the failed document in POS to view the error messages and the reason for the failure in the **Details** pane. A failed document remains unposted and requires that the user return to the document lines by selecting **Order details** in POS. The user must then update the document with corrections, based on the errors. After a document is corrected, the user can try again to process it by selecting **Finish fulfillment** on the app bar.

## Create purchase orders

Users can create new purchase order requests from POS. To use this feature, ensure the **Ability to create purchase order request in POS** feature is enabled in the **Feature management** workspace, and the **Allow create purchase order** permission setting is enabled in the user's POS permission group.

To start the creation process, on the action pane of the document list view, select **Create new**. In the dialog box that appears, select **New purchase order**, and then select a vendor from which you want the purchase order to be shipped. You can search for a specific vendor by entering the vendor account ID or vendor name. Your current store is always the **Ship to** warehouse for the to-be-created purchase order, and you can't modify this location. Specify the **Accounting date** and **Delivery date** as needed. You can also add a note that is stored together with the purchase order header as an attachment to the document in headquarters.

> [!NOTE]
> - You can't create purchase orders from POS if the [purchase order change management workflow](/dynamics365/supply-chain/procurement/purchase-order-approval-confirmation) is enabled in headquarters. In that case, you can only create purchase orders in headquarters and they must go through the approval workflow.
> - To use the vendor selection function, you must first run the **1220 (Vendors)** distribution schedule job to sync the predefined vendor master data from headquarters to the channel databases. You can't select intercompany vendors during purchase order creation from POS. 

After you create the header information, add products to the purchase order request. To start the process of adding items and requested quantities, select **Add product**. In the dialog box, enter the product number, select a product variant (if applicable), and then specify the quantity. If you have a barcode scanning device, you can scan the product barcodes to streamline the process. In the **Details** pane, you can also add a line-specific note that is stored as a line attachment in headquarters.

After you enter lines on the purchase order request, select **Save** to save the document changes locally, or select **Submit request** to send the request to headquarters for further processing. If you save a document locally, you can find it on the **Draft** tab of the document list view. When a document is in **Draft** status, you can edit it by selecting **Edit**. You can add, update, or delete lines as needed. You can also delete the entire document when it's in **Draft** status by selecting **Delete** on the **Draft** tab.

After you successfully submit the draft document to headquarters, it appears on the **Active** tab of the document list view with a status of **Created**. For purchase orders in **Created** status, regardless of where (POS or headquarters) the document was initially created, and as long as the [purchase order change management workflow](/dynamics365/supply-chain/procurement/purchase-order-approval-confirmation) isn't enabled, users in the recipient store of the purchase order can edit the document by adding, updating, or deleting lines as needed. You must resubmit the updated document to put the modification into effect. 

From POS, users can also confirm purchase order requests to indicate commitment from vendors to deliver the goods as requested in the purchase orders. To use this feature, ensure the **Ability to create purchase order request in POS** feature is enabled in the **Feature management** workspace, and the **Allow confirm purchase order** permission setting is enabled in the user's POS permission group. Only purchase orders in **Created** status can be confirmed. To confirm a purchase order, select the order in the document list view, select **View details** to open the document details view, and then select **Confirm order** on the action pane. After a purchase order is confirmed, its status updates from **Created** to **Requested** and is ready for receiving.

## Create inbound transfer orders

Users can create new inbound transfer order documents from POS. To start the process, on the action pane of the document list view, select **Create new**. In the dialog box that appears, select **New transfer order**, and then select a **Transfer from** warehouse or store that provides the inventory to your store location. The **Transfer from** values are limited to the selection defined in the configuration of the store's fulfillment group. In an inbound transfer request, your current store is always the **Transfer to** warehouse for the transfer order. You can't change the **Transfer to** value.

Enter values in the **Ship date**, **Receive date**, and **Mode of delivery** fields as needed. You can also add a note that is stored together with the transfer order header as an attachment to the document in headquarters.

After you create the header information, add products to the transfer order. To start the process of adding items and requested quantities, select **Add product**. In the **Details** pane, you can also add a line-specific note to the journal lines. These notes are stored as a line attachment.

After you enter lines on the inbound transfer order, select **Save** to save the document changes locally or **Submit request** to submit the order details to headquarters for further processing. If you select **Save**, the draft document is stored in the channel database, and the outbound warehouse can't run the document until it's successfully processed via **Submit request**. Select **Save** only if you're not ready to commit the request to headquarters for processing.

If you save a document locally, you can find it on the **Draft** tab of the **Inbound operation** document list. While a document is in **Draft** status, you can edit it by selecting **Edit**. You can update, add, or delete lines as needed. You can also delete the whole document while it's in **Draft** status by selecting **Delete** on the **Draft** tab.

After you successfully submit the draft document to headquarters, it appears on the **Active** tab and has a status of **Requested**. At this point, users in the inbound store or warehouse can no longer edit the requested inbound transfer order document. Only users in the outbound warehouse can edit the document, by selecting **Outbound operation** in the POS application. The editing lock ensures that no conflicts occur because an inbound requester changes the transfer order at the same time that the outbound shipper is actively picking and shipping the order. If changes are required from the inbound store or warehouse after the transfer order is submitted, the outbound shipper should be contacted and asked to enter the changes.

After the document is in **Requested** status, it's visible on the **Active** tab. However, the inbound store or warehouse can't yet receive it. After the outbound warehouse ships some or all of the transfer order, the inbound store or warehouse can post receipts in POS. When the outbound side processes the transfer order documents, their status is updated from **Requested** to **Shipped** or **Partially Shipped**. After the documents are in **Shipped** or **Partially Shipped** status, the inbound store or warehouse can post receipts against them using the inbound operation receiving process.

## Additional resources

[Outbound inventory operation in POS](pos-outbound-inventory-operation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
