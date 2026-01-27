---
title: Outbound inventory operation in POS
description: Learn about the capabilities of the point of sale (POS) outbound inventory operation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-02-11
ms.author: yufeihuang
ms.custom: 
  - bap-template
---

# Outbound inventory operation in POS

[!include [banner](includes/banner.md)]

This article describes the capabilities of the point of sale (POS) outbound inventory operation in Microsoft Dynamics 365 Commerce.

In Commerce version 10.0.10 and later, inbound and outbound operations in the point of sale (POS) replace the picking and receiving operation.

> [!NOTE]
> In Commerce version 10.0.10 and later, the **Inbound operation** POS operation includes new features related to receiving store inventory against purchase orders and transfer orders. If you're currently using the picking and receiving operation in POS, develop a strategy for moving from that operation to the new inbound and outbound operations. Although the picking and receiving operation remains in the product, the product doesn't provide any further functional or performance investments after Commerce version 10.0.9.

## Prerequisites

Before your organization can use the outbound operation functionality, complete the following prerequisites.

### Configure an asynchronous document framework

For information about how to configure an asynchronous document framework, see [Commerce asynchronous document framework](async-document-framework.md). You can skip this step if you already configured an asynchronous document framework for other operations.

### Add Outbound operation to the POS screen layout

Configure the **Outbound operation** POS operation on one or more of your [POS screen layouts](/dynamics365/unified-operations/retail/pos-screen-layouts). Before you deploy the new operation in a production environment, thoroughly test it, and train your users to use it.

## Outbound inventory operation

The outbound inventory operation enables POS users to perform the following tasks:

- Post shipments for transfer order documents when the user's store is the designated outbound warehouse.
- View information about historical transfer order shipments that the store posted.
- Create new outbound transfer order requests.

When the user starts the outbound operation from the POS application, a list page view appears. This view shows open transfer order documents that have inventory lines that the user's current store is intended to ship and fulfill. To find and select a document, users can scroll the list or use the search feature.

The outbound inventory document list has three tabs.

- **Active** – This tab shows transfer orders that have a status of **Requested** or **Partially Shipped**. The orders contain lines or quantities on lines that the user's current store must ship. This tab also shows orders that have a status of **Processing in HQ** (that is, they're waiting for confirmation of successful posting from headquarters) or **Processing failed** (that is, posting to headquarters was unsuccessful, and the user must correct data and try again to submit the orders).
- **Draft** – This tab shows new outbound transfer order requests that the user's store created. However, the documents are only saved locally. They aren't yet submitted to headquarters for processing.
- **Complete** – This tab shows a list of transfer order documents that the store fully shipped during the last seven days. This tab is for informational purposes only. All the information about the documents is read-only data for the store.

When you view documents on any of the tabs, the **Status** field can help you understand the stage that the document is in.

- **Draft** – The transfer order document is only saved locally to the store's channel database. No information about the transfer order request is yet submitted to headquarters.
- **Requested** – The purchase order or transfer order is created in headquarters and is fully open. The user's current store hasn't yet processed any shipments against the document.
- **Partially shipped** – The transfer order document has one or more lines or partial line quantities that the outbound warehouse posted as shipped. These shipped lines are available to be received through the inbound operation.
- **Fully shipped** – The transfer order has all its lines and full line quantities posted as shipped by the outbound warehouse.
- **In progress** – This status informs device users that another user is actively working on the document.
- **Paused** – This status shows after **Pause receiving** is selected to temporarily stop the receiving process.
- **Processing in HQ** – The document was submitted to headquarters from the POS application, but it hasn't yet been successfully posted to headquarters. The document is going through the asynchronous document posting process. After the document is successfully posted to headquarters, its status should be updated to **Fully received** or **Partially received**.
- **Processing failed** – The document was posted to headquarters and rejected. The **Details** pane shows the reason for the posting failure. The document must be edited to fix data issues, and then it must be resubmitted to headquarters for processing.

When you select a document line in the list, a **Details** pane appears. This pane shows additional information about the document, such as shipment and date information. A progress bar shows how many items must still be processed. If the document wasn't successfully processed to headquarters, the **Details** pane also shows error messages that are related to the failure.

In the document list page view, you can select **Order details** on the app bar to view the document details. You can also activate receipt processing on eligible document lines.

In the document list page view, you can also create a new outbound transfer order for a store.

## Transfer order shipping process

After you select a transfer order document on the **Active** tab, select **Order details** to begin the fulfillment process. The **Full order list** view appears. This page shows all the document lines that contain the item. It also shows details of the ordered quantity.

Each scan of a bar code updates the quantity in the **Shipping now** field by one unit. Alternatively, you can enter a shipping quantity by selecting **Ship product** on the app bar, entering an item ID, and then entering the quantity. If the item is location-controlled, you can confirm or set the shipping location for the document line.

In the **Full order list** view, you can manually select a line in the list and then update the **Shipping now** quantity for the selected line in the **Details** pane.

### Over-delivery shipping validations

Validations occur during the fulfillment process for the document lines. They include validations for over-delivery. If a user tries to ship more inventory than was ordered on a transfer order, but either over-delivery isn't configured or the quantity that you ship exceeds the over-delivery tolerance that is configured for the transfer order line, the user receives an error and isn't allowed to ship the excess quantity.

### Underdelivery close lines

In Commerce version 10.0.12, functionality was added that lets POS users close or cancel remaining quantities during outbound order shipment if the outbound warehouse determines that it can't ship the full quantity that was requested. You can also close or cancel quantities later. To use this capability, the company must be configured to allow underdelivery of transfer orders. Additionally, an underdelivery percentage must be defined for the transfer order line.

To configure the company to allow underdelivery of transfer orders, in headquarters, go to **Inventory management \> Setup \> Inventory and warehouse management parameters**. On the **Inventory and warehouse management parameters** page, on the **Transfer orders** tab, turn on the **Accept underdelivery** parameter. Then run the **1070** distribution scheduler job to sync the parameter changes to your store channel.

Underdelivery percentages for a transfer order line can be predefined on products as part of product configuration in Commerce Headquarters. Alternatively, you can set or overwrite them on a specific transfer order line through headquarters.

After an organization completes configuring transfer order underdelivery, POS users see a new **Close remaining quantity** option in the **Details** pane when they select an outbound transfer order line through the **Outbound operation** function. When the user completes the shipment by using the **Finish fulfillment** operation, they can send a request to headquarters to cancel the remaining unshipped quantity. If the user closes the remaining quantity, Commerce performs a validation to verify that the quantity that's being canceled is within the underdelivery percentage tolerance defined on the transfer order line. If the underdelivery tolerance is exceeded, an error message is displayed and the user can't close the remaining quantity until the "previously shipped" and "ship now" quantities meet or exceed the underdelivery tolerance.

After the shipment is synced to headquarters, the quantities that you define in the **Ship now** field for the transfer order line in POS are updated to a shipped status in headquarters. Any unshipped quantities that previously would have been considered "ship remain" quantities (that is, quantities that are shipped later) are considered canceled quantities instead. The "ship remain" quantity for the transfer order line is set to **0** (zero), and the line is considered fully shipped.

### Shipping location-controlled items

If the items that you're shipping are location-controlled, choose the location that you want to issue the inventory from during the shipping process. Configure a default issue location for your store warehouse to make this process more efficient. Even if you configure a default location, you can override the issue location on selected lines as needed.

The operation respects the **Blank receipt allowed** configuration on the **Location** storage dimension and doesn't require that a location dimension is entered if **Blank receipt allowed** is configured. If blank receipt locations aren't allowed for an item, the POS application shows an error and requires that a location is entered before the receipt can be posted.

### Ship all

If you want, select **Ship all** on the app bar to quickly update the **Shipping now** quantity for all the document lines to the maximum value that the system can fulfill for those lines.

### Cancel fulfillment

Use the **Cancel fulfillment** function on the app bar only if you want to back out of the document and don't want to save any changes. For example, you initially selected the wrong document and don't want any of the previous shipping data saved.

### Pause fulfillment

If you're fulfilling the transfer order, use the **Pause fulfillment** function if you want to take a break from the process. For example, you might want to perform another operation from the POS, such as ringing up a customer sale, or delay posting of the shipment to headquarters.

When you select **Pause fulfillment**, the document's status changes to **Paused**. Therefore, the user knows that data is entered in the document, but the document isn't yet committed. When you're ready to resume the fulfillment process, select the paused document, and then select **Order details**. Any **Shipping now** quantities that you previously saved are retained and can be viewed from the **Full order list** view.

### Review

Before you commit the fulfillment to headquarters, use the **Review** function to validate the outbound document. This function alerts you to potential missing or incorrect data that might cause a processing failure, and gives you the opportunity to correct problems before submitting the fulfillment request. To enable the **Review** function on the app bar, enable the **Enable validation in POS inbound and outbound inventory operations** feature through Feature management in headquarters.

The **Review** function validates the following issues in an outbound document:
- **Over-shipping** – The shipping now quantity is greater than the ordered quantity. The severity of this issue is determined by the overdelivery configuration in headquarters.
- **Under-shipping** – The shipping now quantity is less than the ordered quantity. The severity of this issue is determined by the underdelivery configuration in headquarters.
- **Serial number** – The serial number isn't provided or isn't available for a serialized item that requires a serial number to be registered in inventory.
- **Location not set** – The location isn't specified for a location-controlled item where location isn't allowed to be blank.
- **Deleted lines** – The order has lines deleted by a headquarters user that the POS application doesn't know about.

If you set the **Enable automatic validation** parameter to **Yes** in **Commerce parameters** > **Inventory** > **Store inventory operations**, validation runs automatically when you select the **Finish fulfillment** function.

### Finish fulfillment

When you finish entering all the **Shipping now** quantities for products, select **Finish fulfillment** on the app bar.

When you use asynchronous document processing, the system submits the receipt through an asynchronous document framework. The time that it takes for the document to post depends on the size of the document (the number of lines) and the general processing traffic that occurs on the server. Typically, this process occurs in a matter of seconds. If document posting fails, the **Outbound operation** document list on the **Active** tab notifies the user. The document status updates to **Processing failed**. The user can then select the failed document in POS to view the error messages and the reason for the failure in the **Details** pane. A failed document remains unposted and requires that the user return to the document lines by selecting **Order details** in POS. The user must then update the document with corrections, based on the errors. After a document is corrected, the user can try again to process it by selecting **Finish fulfillment** on the app bar.

## Create an outbound transfer order

From POS, users can create new transfer order documents. To begin the process, select **New** on the app bar while you're in the main **Outbound operation** document list. You're then prompted to select a **Transfer to** warehouse or store that your current store sends inventory to. The values are limited to the selection that is defined in the configuration of the store's fulfillment group. In an outbound transfer request, your current store is always the **Transfer from** warehouse for the transfer order. You can't change that value.

Enter values in the **Ship date**, **Receive date**, and **Mode of delivery** fields as you require. You can also add a note that stores together with the transfer order header, as an attachment to the document in headquarters.

After you create the header information, add products to the transfer order. To start the process of adding items and requested quantities, scan bar codes or select **Add product**.

After you enter lines on the outbound transfer order, select **Save** to save the document changes locally, or **Submit request** to submit the order details to headquarters for further processing. If you select **Save**, the system stores the draft document in the channel database, and the outbound warehouse can't run the document until it is successfully processed via **Submit request**. Select **Save** only if you aren't ready to commit the request to headquarters for processing.

If you save a document locally, you can find it on the **Drafts** tab of the **Inbound operation** document list. While a document is in **Draft** status, you can edit it by selecting **Edit**. You can update, add, or delete lines as you require. You can also delete the whole document while it's in **Draft** status, by selecting **Delete** on the **Drafts** tab.

After the system successfully submits the draft document to headquarters, it appears on the **Active** tab and has a status of **Requested**. At this point, only users in the outbound warehouse can edit the document, by selecting **Outbound operation** in the POS application. Users in the inbound warehouse can view the transfer order on the **Active** tab of the **Inbound operation** document list, but they can't edit or delete it. The editing lock ensures that no conflicts occur because an inbound requester changes the transfer order at the same time that the outbound shipper is actively picking and shipping the order. If changes are required from the inbound store or warehouse after the transfer order is submitted, you should contact the outbound shipper and ask them to enter the changes.

After the document is in **Requested** status, it's ready for fulfillment processing by the outbound warehouse. As the shipment is processed by using the outbound operation, the status of the transfer order documents updates from **Requested** to **Fully shipped** or **Partially shipped**. After the documents are in **Fully shipped** or **Partially shipped** status, the inbound store or warehouse can post receipts against them by using the inbound operation receiving process.

Fully shipped transfer orders move to the **Complete** tab of the **Outbound operation** document list. They remain visible to users in the outbound store or warehouse, in read-only mode, for seven days.

## Additional resources

[Inbound inventory operation in POS](pos-inbound-inventory-operation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
