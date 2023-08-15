---
title: Inbound inventory operation in POS
description: This article describes the capabilities of the point of sale (POS) inbound inventory operation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 09/01/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-06-20

---

# Inbound inventory operation in POS

[!include [banner](includes/banner.md)]

This article describes the capabilities of the point of sale (POS) inbound inventory operation in Microsoft Dynamics 365 Commerce.

In Commerce version 10.0.10 and later, inbound and outbound operations in POS replaced the picking and receiving operation.

> [!NOTE]
> In Commerce version 10.0.10 and later, any new features in the POS application that are related to receiving store inventory against purchase orders and transfer orders will be added to the **Inbound operation** POS operation. If you're currently using the picking and receiving operation in POS, we recommend that you develop a strategy for moving from that operation to the new inbound and outbound operations. Although the picking and receiving operation won't be removed from the product, from a functional or performance perspective, there will be no further investments in it after Commerce version 10.0.9.

## Prerequisites

Before your organization can use the inbound operation functionality, you must complete the following prerequisites.

### Configure an asynchronous document framework

For information about how to configure an asynchronous document framework, see [Commerce asynchronous document framework](async-document-framework.md). You can skip this step if you've already configured an asynchronous document framework for other operations.

### Add Inbound operation to the POS screen layout

You must configure the **Inbound operation** POS operation on one or more of your [POS screen layouts](/dynamics365/unified-operations/retail/pos-screen-layouts). Before you deploy the new operation in a production environment, ensure that you thoroughly test it and train your users to use it.

## Inbound inventory operation

The inbound inventory operation lets POS users perform the following tasks:

- Receive inventory into store stock from either confirmed purchase order documents or shipped transfer order documents.
- View information about historical inventory receipts for a period of seven days after the document has been fully received.
- Create new inbound transfer order requests.

When the inbound operation is started from the POS application, a list page view appears. This view shows open purchase order and transfer order documents that have inventory lines that are scheduled to be received by the current store. To find and select a specific document, you can scroll the list or use the search feature.

The inbound inventory document list has three tabs:

- **Active** – This tab shows documents that are fully or partially open, and that contain lines or quantities on lines that must still be received.
- **Draft** – This tab shows new inbound transfer order requests that the store has created. However, the documents have only been saved locally. They haven't yet been submitted to Commerce headquarters for processing.
- **Complete** – This tab shows a list of purchase order or transfer order documents that the store has fully received during the last seven days. This tab is for informational purposes only. All the information about the documents is read-only data for the store.

When you view documents on any of the tabs, the **Status** field helps you understand the stage that the document is in.

- **Draft** – The purchase order or transfer order document has only been saved locally to the store’s channel database. No information about the purchase order or transfer order request has been submitted to headquarters.
- **Created** - The purchase order request has been created in headquarters, but not yet confirmed.
- **Requested** – The purchase order or transfer order has been created in headquarters, and is fully open. No receipts have yet been processed against the document. For a purchase order, receiving can begin at any time while in **Requested** status.
- **Partially shipped** – The transfer order document has one or more lines or partial line quantities that have been posted as shipped by the outbound warehouse. These shipped lines are available to be received through the inbound operation.
- **Fully shipped** – The transfer order has had all its lines and full line quantities posted as shipped by the outbound warehouse. The whole document is available to be received through the inbound operation.
- **Partially received** – Some of the lines or line quantities on the purchase order or transfer order document have been received by the store, but some lines remain open.
- **Fully received** – All lines and quantities on the purchase order or transfer order document have been fully received. The documents are accessible only on the **Complete** tab and are read-only by store users.
- **In progress** – This status is used to inform device users that the document is being actively worked on by another user.
- **Paused** – This status is shown after **Pause receiving** is selected to temporarily stop the receiving process.
- **Processing in HQ** – The document was submitted to headquarters from the POS application, but it hasn't yet been successfully posted to headquarters. The document is going through the asynchronous document posting process. After the document is successfully posted to headquarters, its status should be updated to **Fully received** or **Partially received**.
- **Processing failed** – The document was posted to headquarters and rejected. The **Details** pane shows the reason for the posting failure. The document must be edited to fix data issues, and then it must be resubmitted to headquarters for processing.

When you select a document line in the list, a **Details** pane appears. This pane shows additional information about the document, such as shipment and date information. A progress bar shows how many items must still be processed. If the document wasn't successfully processed to headquarters, the **Details** pane also shows error messages that are related to the failure.

In the document list view, you can select **Order details** on the app bar to view the document details. You can also activate receipt processing on eligible document lines.

In the document list view, you can also create a new purchase order or inbound transfer order request for a store. The documents remain in **Draft** status and can be adjusted or deleted until they are submitted to headquarters for processing.

## Receiving process

After you select a purchase order or transfer order document on the **Active** tab, you can select **Order details** to begin the receiving process.

By default, the **Receiving now** view is shown. This view is optimized for bar code scanning. It can be used to build a list of the items that have been scanned, so that those items can be received. To begin the receiving process, you can start to scan item bar codes.

As item bar codes are scanned in the **Receiving now** view, the application validates the items against the selected purchase or transfer order document, to make sure that each scanned item matches a valid item on the document. In the **Receiving now** view, each scan of a bar code is assumed to represent the receipt of a quantity of one unit, unless a quantity is embedded in the bar code. You can repeatedly scan bar codes in this view to build a list of all the items and quantities for the receipt.

### Example scenario

A user receives a purchase order that contains 10 units of bar code 5657900266. The user can scan that bar code 10 times to update the **Receiving now** field by one unit per scan. When the user has completed the scans, the **Receiving now** field for the item's line will show that a quantity of 10 was received.

Alternatively, in a scenario where the item quantity is large, the user might prefer to manually enter the quantity instead of scanning the bar code for each item that is received. In this case, the user can scan the bar code one time to add the item to the **Receiving now** list. The user can then select the associated line in the **Receiving now** view and then, in the **Details** pane that appears on the right side of the page, update the **Receiving quantity** field for the item.

Although the **Receiving now** view is optimized for bar code scanning, users can also select **Receive product** on the app bar, and then enter the item ID or bar code data via a dialog box. After the item that was entered is validated, the user is prompted to enter the receipt quantity.

The **Receiving now** view provides a focused way for users to see which products they are receiving. Alternatively, the **Full order list** view can be used. This view shows the whole list of document lines for the selected purchase or transfer order document. Users can manually select lines in the list and then, in the **Details** pane, update the **Receiving quantity** field for the selected line. In the **Full order list** view, users can scan bar codes, or they can use the **Receive product** function to enter the item ID or bar code, and data about the received quantity, without first having to select the matching item line in the list.

### Over-receiving validations

Validations occur during the receiving process for the document lines. They include validations for over-delivery. If a user tries to receive more inventory than was ordered on a purchase order, but either over-delivery isn't configured or the amount that is received exceeds the over-delivery tolerance that is configured for the purchase order line, the user receives an error and isn't allowed to receive the excess quantity.

Over-receiving isn't permitted for transfer order documents. Users will always receive errors if they try to receive more than was shipped for the transfer order line.

### Close purchase order lines

You can close the remaining quantity on an inbound purchase order during the receiving process if the shipper has confirmed that they can’t ship the full quantity that was requested. To do so, the company must be configured to allow underdelivery of purchase orders. Additionally, an underdelivery tolerance percentage must be defined for the purchase order line.

To configure the company to allow underdelivery of purchase orders, in headquarters, go to **Procurement and sourcing** > **Setup** > **Procurement and sourcing parameters**. On the **Delivery** tab, turn on the **Accept underdelivery** parameter. Then run the **1070** (**Channel configuration**) distribution schedule job to sync the setting changes to channels.

Underdelivery tolerance percentages for a purchase order line can be predefined on products as part of the product configurations in headquarters. Alternatively, they can be set or overwritten on a specific purchase order in headquarters.

After an organization completes the purchase order underdelivery configurations, POS users will see a new **Close remaining quantity** option in the **Details** pane when an inbound purchase order line is selected in the **Inbound inventory** operation. If the user closes the remaining quantity, POS performs a validation to verify whether the quantity being closed is within the underdelivery tolerance percentage defined on the purchase order line. If the underdelivery tolerance is exceeded, an error message is displayed and the user won’t be able to close the remaining quantity until the previously received quantity plus the **Receiving now** quantity meets or exceeds the minimal quantity that needs to be received based on the underdelivery tolerance percentage. 

With **Close remaining quantity** option turned on for a purchase order line, when the user completes the receipt by using the **Finish receiving** action, a closure request is also sent to headquarters, and any unreceived quantity of this order line will be canceled. At that point the line is considered fully received. 

### Receiving location-controlled items

If the items that are being received are location-controlled, users can select the location where they want to receive the items during the receiving process. We recommend that you configure a default receiving location for your store warehouse, to make this process more efficient. Even if a default location is configured, users can override the receiving location on selected lines as they require.

The operation respects the **Blank receipt allowed** configuration on the **Location** storage dimension and doesn't require that a location dimension be entered if blank receipt is configured. If blank receipt locations aren't allowed for an item, the POS application shows an error and requires that a location be entered before the receipt can be posted.

### Receive all

As you require, you can select **Receive all** on the app bar to quickly update the **Receiving now** quantity for all the document lines to the maximum value that is available to be received for those lines.

### Receipt of unplanned items on purchase orders

In Commerce version 10.0.14 and later, users can receive a product that was not originally on the purchase order. This feature only works for purchase order receiving. It's not possible to receive items against transfer orders when the items weren't previously ordered and shipped from the outbound warehouse.

Users can't add new products to the purchase order during POS receiving if purchase order [change management workflow](../supply-chain/procurement/purchase-order-approval-confirmation.md) is enabled in headquarters. To enable change management, all changes to a purchase order must first be approved before receiving is allowed. Because this process allows a receiver to add new lines to the purchase order, receiving will fail if the change management workflow is enabled. If change management is enabled for all purchase orders or for the vendor linked to the purchase order actively being received in POS, the user can't add new products to the purchase order during receiving in POS.

The functionality that enables adding lines can't be used as a workaround for receiving additional quantities of products already on the purchase order. Over-receiving is managed through the standard [over-receiving](#over-receiving-validations) settings for the product line on the purchase order.

When a user is receiving with the **Inbound operation** in POS, if the user scans or keys a product barcode or product number that is recognized as a valid item but isn't recognized as an item on the current purchase order, the user receives a message prompting them to add the item to the purchase order. If the user adds the item to the purchase order, the quantity entered in **Receiving now** is considered the ordered quantity for the purchase order line.

When the purchase order receipt is complete and submitted to headquarters for processing, the added lines are created on the purchase order master document. On the purchase order line in headquarters, there will be an **Added by POS** flag on the **General** tab of the purchase order line. The **Added by POS** flag indicates that the purchase order line was added by the POS receiving process and was not a line that was on the purchase order prior to receiving.

### Cancel receiving

You should use the **Cancel receiving** function on the app bar only if you want to back out of the document and don't want to save any changes. For example, you initially selected the wrong document and don't want any of the previous receiving data saved.

### Pause receiving

If you're receiving inventory, you can use the **Pause receiving** function if you want to take a break from the receiving process. For example, you might want to perform another operation from the POS, such as ringing up a customer sale, or delay posting of the receipt.

When you select **Pause receiving**, the document's status is changed to **Paused**. Therefore, users will know that data has been entered for the document, but the document hasn't yet been committed. When you're ready to resume the receiving process, select the paused document, and then select **Order details**. Any **Receiving now** quantities that were previously saved are retained and can be viewed from the **Full order list** view.

### Review

Before the final commitment of the receipt to headquarters, you can use the review functionality to validate the inbound document. The review will alert you to any missing or incorrect data that may cause processing failure and provide you the opportunity to correct problems before submitting the receipt request. To enable the **Review** function on the app bar, enable the **Enable validation in POS inbound and outbound inventory operations** feature through the **Feature management** workspace in headquarters.

The **Review** function validates the following issues in an inbound document:

- **Over-receiving** – the receiving now quantity is greater than the ordered quantity. The severity of this issue is determined by the overdelivery configuration in headquarters.
- **Under-receiving** – the receiving now quantity is less than the ordered quantity. The severity of this issue is determined by the underdelivery configuration in headquarters.
- **Serial number** – the serial number is not provided or validated for a serialized item that requires serial number to be registered in inventory.
- **Location not set** – the location is not specified for a location-controlled item where blank location is not allowed.
- **Deleted lines** – the order has lines deleted by aa headquarters user that is not known to POS application.

Set the **Enable automatic validation** parameter to **Yes** in **Commerce parameters** > **Inventory** > **Store inventory** to have the validation executed automatically when **Finish receiving** is selected.

### Finish receiving

When you've finished entering all the **Receiving now** quantities for products, you must select **Finish receiving** on the app bar to process the receipt.

When users complete a purchase order receipt, they are prompted to enter a value in the **Receipt number** field, if this functionality is configured. Typically, this value is equivalent to the identifier of the vendor packing slip. The **Receipt number** data will be stored in the Product receipt journal in headquarters. Receipt numbers aren't captured for transfer order receipts.

When asynchronous document processing is used, the receipt is submitted through an asynchronous document framework. The time that it takes for the document to be posted depends on the size of the document (the number of lines) and the general processing traffic that is occurring on the server. Typically, this process occurs in a matter of seconds. If document posting fails, the user is notified through the **Inbound operation** document list, where the document status will be updated to **Processing failed**. The user can then select the failed document in POS to view the error messages and the reason for the failure in the **Details** pane. A failed document remains unposted and requires that the user return to the document lines by selecting **Order details** in POS. The user must then update the document with corrections, based on the errors. After a document is corrected, the user can try again to process it by selecting **Finish fulfillment** on the app bar.

## Create purchase orders

Users can create new purchase order requests from POS. To use this feature, ensure the **Ability to create purchase order request in POS** feature is enabled in the **Feature management** workspace, and the **Allow create purchase order** permission setting is enabled in the user's POS permission group.

To start the creation process, in the document list view, on the action pane, select **Create new**. In the dialog box, select **New purchase order**, then select a vendor from which you want the purchase order to be shipped. You can search for a specific vendor by entering the vendor account ID or vendor name. Your current store will always be the **Ship to** warehouse for the to-be-created purchase order, and this location can't be modified. Specify the **Accounting date** and **Delivery date** as needed. You can also add a note that will be stored together with the purchase order header as an attachment to the document in headquarters.

> [!NOTE]
> - You can't create purchase orders from POS if the purchase order [change management workflow](/dynamics365/supply-chain/procurement/purchase-order-approval-confirmation) is enabled in headquarters. In that case, the purchase orders can only be created in headquarters and must go through the approval workflow.
> - To use the vendor selection function, you must first run the **1220 (Vendors)** distribution schedule job to sync the predefined vendor master data from headquarters to channel databases. Intercompany vendors can't be selected during purchase order creation from POS. 

After the header information is created, you can add products to the purchase order request. To start the process of adding items and requested quantities, select **Add product**. In the dialog box, enter the product number, select a product variant (if applicable), and then specify the quantity. If you have a barcode scanning device, you can scan the product barcodes to streamline the process. In the **Details** pane, you can also add a line specific note that will be stored as a line attachment in headquarters.

After lines are entered on the purchase order request, you must select **Save** to save the document changes locally, or select **Submit request** to send the request to headquarters for further processing. If a document is saved locally, it can be found on the **Draft** tab of the document list view. When a document is in **Draft** status, you can edit it by selecting **Edit**. You can add, update, or delete lines as needed. You can also delete the entire document when it's in **Draft** status by selecting **Delete** on the **Draft** tab.

After the draft document is successfully submitted to headquarters, it appears on the **Active** tab of the document list view with **Created** status. For purchase orders in **Created** status, regardless of where (POS or headquarters) the document was initially created, and as long as the [purchase order change management workflow](/dynamics365/supply-chain/procurement/purchase-order-approval-confirmation) isn't enabled, users in the recipient store of the purchase order can edit the document by adding, updating or deleting lines as needed. You must resubmit the updated document to put the modification into effect. 

From POS, users can also confirm purchase order requests to indicate commitment from vendors to deliver the goods as requested in the purchase orders. To use this feature, ensure the **Ability to create purchase order request in POS** feature is enabled in the **Feature management workspace**, and the **Allow confirm purchase order** permission setting is enabled in the user's POS permission group. Only purchase orders in **Created** status can be confirmed. To confirm a purchase order, select the order in the document list view, select **View details** to open the document details view, and then select **Confirm order** on the action pane. After a purchase order is confirmed, its status is updated from **Created** to **Requested** and is ready for receiving.

## Create inbound transfer orders

From POS, users can create new transfer order documents. To begin the process, in the document list view, click **Create new** on the app bar, in the prompted dialog, select **New transfer order**, and then select a **Transfer from** warehouse or store that will provide the inventory to your store location. The values are limited to the selection that is defined in the configuration of the store's fulfillment group. In an inbound transfer request, your current store will always be the **Transfer to** warehouse for the transfer order. That value can't be changed.

You can enter values in the **Ship date**, **Receive date**, and **Mode of delivery** fields as you require. You can also add a note that will be stored together with the transfer order header, as an attachment to the document in headquarters.

After the header information is created, you can add products to the transfer order. To start the process of adding items and requested quantities, select **Add product**. In the **Details** pane, you can also add a line-specific note to the journal lines. These notes will be stored as a line attachment.

After lines are entered on the inbound transfer order, you must select **Save** to save the document changes locally or **Submit request** to submit the order details to headquarters for further processing. If you select **Save**, the draft document is stored in the channel database, and the outbound warehouse can't run the document until it has been successfully processed via **Submit request**. You should select **Save** only if you aren't ready to commit the request to headquarters for processing.

If a document is saved locally, it can be found on the **Draft** tab of the **Inbound operation** document list. While a document is in **Draft** status, you can edit it by selecting **Edit**. You can update, add, or delete lines as you require. You can also delete the whole document while it's in **Draft** status, by selecting **Delete** on the **Draft** tab.

After the draft document is successfully submitted to headquarters, it appears on the **Active** tab and has a status of **Requested**. At this point, users in the inbound store or warehouse can no longer edit the requested inbound transfer order document. Only users in the outbound warehouse can edit the document, by selecting **Outbound operation** in the POS application. The editing lock ensures that no conflicts occur because an inbound requestor changes the transfer order at the same time that the outbound shipper is actively picking and shipping the order. If changes are required from the inbound store or warehouse after the transfer order has been submitted, the outbound shipper should be contacted and asked to enter the changes.

After the document is in **Requested** status, it's visible on the **Active** tab. However, it can't yet be received by the inbound store or warehouse. After the outbound warehouse has shipped some or all of the transfer order, the inbound store or warehouse can post receipts in POS. When the outbound side processes the transfer order documents, their status is updated from **Requested** to **Shipped** or **Partially Shipped**. After the documents are in **Shipped** or **Partially Shipped** status, the inbound store or warehouse can post receipts against them using the inbound operation receiving process.

## Additional resources

[Outbound inventory operation in POS](pos-outbound-inventory-operation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
