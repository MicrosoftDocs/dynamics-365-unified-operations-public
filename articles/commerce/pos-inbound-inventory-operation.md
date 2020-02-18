---
# required metadata

title: Inbound inventory operation in POS
description: This topic describes capabilities of the point of sale (POS) inbound inventory operation.
author: hhaines
manager: annbe

ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: hhaines
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.9


---

# Inbound inventory operation in POS

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

In Microsoft Dynamics 365 Commerce version 10.0.10 and later, inbound and outbound operations in the point of sale (POS) replace the picking and receiving operation.

> [!NOTE]
> In version 10.0.10 and later, any new features in the POS application that are related to receiving store inventory against purchase orders and transfer orders will be added to the inbound operations operation. If you're currently using the picking and receiving operation in POS, we recommend that you develop a strategy for moving from that operation to the new inbound and outbound operations. Although the picking and receiving operation won't be removed from the product, there will be no further investments in it, from a functional or performance perspective, after version 10.0.9.

## Prerequisite: Configure an asynchronous document framework

The inbound operation includes performance improvements to ensure that users who have high volumes of receipt postings across many stores or companies, and large inventory documents, can process those documents to Commerce Headquarters (HQ) without experiencing time-outs or failures. These improvements require use of an asynchronous document framework.

When an asynchronous document framework is used, you can commit inbound document changes from POS to HQ and then move on to other tasks while the processing to HQ occurs in the background. You can check the status of a document through the **Inbound operation** document list page in POS to make sure that posting was successful. You can also see any documents that could not be posted to HQ from the POS application through the inbound operation active document list. If a document fails, POS users can make corrections to it and then try again to process it to HQ.

> [!IMPORTANT]
> The asynchronous document framework must be configured before a company tries to use the inbound operation in POS.

To configure an asynchronous document framework, complete the following procedures.

### Create and configure a number sequence

1. Go to **Organization administration \> Number sequences \> Number sequences**.
2. On the **Number sequences** page, create a number sequence.
3. In the **Number sequence code** and **Name** fields, enter user-defined values.
4. On the **References** FastTab, select **Add**.
5. In the **Area** field, select **Commerce parameters**.
4. In the **Reference** field, select **Retail document operation identifier**.
5. On the **General** FastTab, in the **Setup** section, set the **Continuous** option to **No** to ensure that there are no performance issues.

### Create and schedule two batch jobs for the document processing and monitoring tasks

The batch jobs that you create will be used to process documents that fail or time out. They will also be used when the number of active inventory documents that are being processed from POS exceeds a system-configured value.

1. Go to **System administration \> Inquiries \> Batch jobs**.
2. On the **Batch job** page, create two batch jobs:

    - Configure one job to run the **RetailDocumentOperationMonitorBatch** class.
    - Configure the other job to run the **RetailDocumentOperationProcessingBatch** class.

2. Schedule the new batch jobs to run on a recurring basis. For example, set the schedule so that the jobs are run every five minutes.

## Prerequisite: Add Inbound operation to the POS screen layout

Before your organization can use the inbound operation functionality, it must configure the **Inbound operation** POS operation on one or more of your [POS screen layouts](https://docs.microsoft.com/dynamics365/unified-operations/retail/pos-screen-layouts). Before you deploy the new operation in a production environment, make sure that you thoroughly test it and train your users to use it.

## Overview

The inbound operation lets POS users perform the following tasks:

- Receive inventory into store stock from either confirmed purchase order documents or shipped transfer order documents.
- View information about historical inventory receipts for a period of seven days after the document has been fully received.
- Create new inbound transfer order requests.

When the inbound operation is started from the POS application, a list page view appears. This view shows open purchase order and transfer order documents that have inventory lines that are scheduled to be received by the current store. To find and select a specific document, users can scroll the list or use the search feature.

The inbound inventory document list has three tabs:

- **Active** – This tab shows documents that are fully or partially open, and that contain lines or quantities on lines that must still be received.
- **Draft** – This tab shows new inbound transfer order requests that the store has created. However, the documents have only been saved locally. They haven't yet been submitted to HQ for processing.
- **Complete** – This tab shows a list of purchase order or transfer order documents that the store has fully received during the last seven days. This tab is for informational purposes only. All the information about the documents is read-only data for the store.

When you view documents on any of the tabs, the **Status** field can help you understand the stage that the document is in.

- **Draft** – The transfer order document has only been saved locally to the store's channel database. No information about the transfer order request has yet been submitted to HQ.
- **Requested** – The purchase order or transfer order has been created in HQ, and is fully open. No receipts have yet been processed against the document. For documents of the purchase order document type, receiving can begin at any time while the status is **Requested**.
- **Partially shipped** – The transfer order document has one or more lines or partial line quantities that have been posted as shipped by the outbound warehouse. These shipped lines are available to be received through the inbound operation.
- **Fully shipped** – The transfer order has had all its lines and full line quantities posted as shipped by the outbound warehouse. The whole document is available to be received through the inbound operation.
- **Partially received** – Some of the lines or line quantities on the purchase order or transfer order document have been received by the store, but some lines remain open.
- **Fully received** – All lines and quantities on the purchase order or transfer order document have been fully received. The documents are accessible only on the **Complete** tab and are read-only by store users.
- **In progress** – This status is used to inform device users that the document is being actively worked on by another user.
- **Paused** – This status is shown after **Pause receiving** is selected to temporarily stop the receiving process.
- **Processing in HQ** – The document was submitted to HQ from the POS application, but it hasn't yet been successfully posted to HQ. The document is going through the asynchronous document posting process. After the document is successfully posted to HQ, its status should be updated to **Fully received** or **Partially received**.
- **Processing failed** – The document was posted to HQ and rejected. The **Details** pane shows the reason for the posting failure. The document must be edited to fix data issues, and then it must be resubmitted to HQ for processing.

When you select a document line in the list, a **Details** pane appears. This pane shows additional information about the document, such as shipment and date information. A progress bar shows how many items must still be processed. If the document wasn't successfully processed to HQ, the **Details** pane also shows error messages that are related to the failure.

In the document list page view, you can select **Order details** on the app bar to view the document details. You can also activate receipt processing on eligible document lines.

In the document list page view, you can also create a new inbound transfer order request for a store. The documents remain in **Draft** status, and they can be adjusted or deleted until they are submitted to HQ for processing. After they are submitted to HQ, the transfer order lines can no longer be changed from the POS application.

## Receiving process

After you select a purchase order or transfer order document on the **Active** tab, you can select **Order details** to begin the receiving process.

By default, the **Receiving now** view is shown. This view is optimized for bar code scanning. It can be used to build a list of the items that have been scanned, so that those items can be received. To begin the receiving process, you can start to scan item bar codes.

As item bar codes are scanned in the **Receiving now** view, the application validates the items against the selected purchase or transfer order document, to make sure that each scanned item matches a valid item on the document. In the **Receiving now** view, each scan of a bar code is assumed to represent the receipt of a quantity of one unit, unless a quantity is embedded in the bar code. You can repeatedly scan bar codes in this view to build a list of all the items and quantities for the receipt.

### Example scenario

A user receives a purchase order that contains 10 units of bar code 5657900266. The user can scan that bar code 10 times to update the **Receiving now** field by one unit per scan. When the user has completed the scans, the **Receiving now** field for the item's line will show that a quantity of 10 was received.

Alternatively, in a scenario where the item quantity is large, the user might prefer to manually enter the quantity instead of scanning the bar code for each item that is received. In this case, the user can scan the bar code one time to add the item to the **Receiving now** list. The user can then select the associated line in the **Receiving now** view and then, in the **Details** pane that appears on the right side of the page, update the **Receiving quantity** field for the item.

Although the **Receiving now** view is optimized for bar code scanning, users can also select **Receive product** on the app bar, and then enter the item ID or bar code data through a dialog box. After the item that was entered is validated, the user is prompted to enter the receipt quantity.

The **Receiving now** view provides a focused way for users to see which products they are receiving. Alternatively, the **Full order list** view can be used. This view shows the whole list of document lines for the selected purchase or transfer order document. Users can manually select lines manually in the list and then, in the **Details** pane, update the **Receiving quantity** field for the selected line. In the **Full order list** view, users can scan bar codes, or they can use the **Receive product** function to enter the item ID or bar code, and data about the received quantity, without first having to select the matching item line in the list.

### Over-receiving validations

Validations occur during the receiving process for the document lines. They include validations for over-delivery. If a user tries to receive more inventory than was ordered on a purchase order, but either over-delivery isn't configured or the amount that is received exceeds the over-delivery tolerance that is configured for the purchase order line, the user receives an error and isn't allowed to receive the excess quantity.

Over-receiving isn't permitted for transfer order documents. Users will always receive errors if they try to receive more than was shipped for the transfer order line.

### Receiving location-controlled items

If the items that are being received are location-controlled, users can select the location where they want to receive the items during the receiving process. We recommend that you configure a default receiving location for your store warehouse, to make this process more efficient. Even if a default location is configured, users can override the receiving location on selected lines as they require.

The operation respects the **Blank receipt allowed** configuration on the **Location** storage dimension and doesn't require that a location dimension be entered if blank receipt is configured. If blank receipt locations aren't allowed for an item, the POS application shows an error and requires that a location be entered before the receipt can be posted.

### Receive all

As you require, you can select **Receive all** on the app bar to quickly update the **Receiving now** quantity for all the document lines to the maximum value that is available to be received for those lines.

### Cancel receiving

You should use the **Cancel receiving** function on the app bar only if you want to back out of the document and don't want to save any changes. For example, you initially picked the wrong document and don't want any of the previous receiving data saved.

### Pause receiving

If you're receiving inventory, you can use the **Pause receiving** function if you want to take a break from the receiving process. For example, you might want to perform another operation from the POS, such as ringing up a customer sale, or delay posting of the receipt.

When you select **Pause receiving**, the document's status is changed to **Paused**. Therefore, users will know that data has been entered for the document, but the document hasn't yet been committed. When you're ready to resume the receiving process, select the paused document, and then select **Order details**. Any **Receiving now** quantities that were previously saved are retained and can be viewed from the **Full order list** view.

### Finish receiving

When you've finished entering all the **Receiving now** quantities for products, you must select **Finish receiving** on the app bar to process the receipt.

When users complete a purchase order receipt, they are prompted to enter a value in the **Receipt number** field, if this functionality is configured. Typically, this value is equivalent to the identifier of the vendor packing slip. The **Receipt number** data will be stored in the Product receipt journal in HQ. Receipt numbers aren't captured for transfer order receipts.

When asynchronous document processing is used, the receipt is submitted through an asynchronous document framework. The time that it takes for the document to be posted depends on the size of the document (the number of lines) and the general processing traffic that is occurring on the server. Typically, this process occurs in a matter of seconds. If document posting fails, the user is notified through the **Inbound operation** document list, where the document status will be updated to **Processing failed**. The user can then select the failed document in POS to view the error messages and the reason for the failure in the **Details** pane. A failed document remains unposted and requires that the user return to the document lines by selecting **Order details** in POS. The user must then update the document with corrections, based on the errors. After a document is corrected, the user can try again to process it by selecting **Finish fulfillment** on the app bar.

## Create an inbound transfer order

From POS, users can create new transfer order documents. To begin the process, select **New** on the app bar while you're in the main **Inbound operation** document list. You're then prompted to select a **Transfer from** warehouse or store that will provide the inventory to your store location. The values are limited to the selection that is defined in the configuration of the store's fulfillment group. In an inbound transfer request, your current store will always be the **Transfer to** warehouse for the transfer order. That value can't be changed.

You can enter values in the **Ship date**, **Receive date**, and **Mode of delivery** fields as you require. You can also add a note that will be stored together with the transfer order header, as an attachment to the document in HQ.

After the header information is created, you can add products to the transfer order. To start the process of adding items and requested quantities, select **Add product**. In the **Details** pane, you can also add a line-specific note to the journal lines. These notes will be stored as a line attachment.

After lines are entered on the inbound transfer order, you must select **Save** to save the document changes locally or **Submit request** to submit the order details to HQ for further processing. If you select **Save**, the draft document is stored in the channel database, and the outbound warehouse can't run the document until it has been successfully processed via **Submit request**. You should select **Save** only if you aren't ready to commit the request to HQ for processing.

If a document is saved locally, it can be found on the **Drafts** tab of the **Inbound operation** document list. While a document is in **Draft** status, you can edit it by selecting **Edit**. You can update, add, or delete lines as you require. You can also delete the whole document while it's in **Draft** status, by selecting **Delete** on the **Drafts** tab.

After the draft document is successfully submitted to HQ, it appears on the **Active** tab and has a status of **Requested**. At this point, users in the inbound store or warehouse can no longer edit the requested inbound transfer order document. Only users in the outbound warehouse can edit the document, by selecting **Outbound operation** in the POS application. The editing lock ensures that no conflicts occur because an inbound requestor changes the transfer order at the same time that the outbound shipper is actively picking and shipping the order. If changes are required from the inbound store or warehouse after the transfer order has been submitted, the outbound shipper should be contacted and asked to enter the changes.

After the document is in **Requested** status, it's visible on the **Active** tab. However, it can't yet be received by the inbound store or warehouse. After the outbound warehouse has shipped some or all of the transfer order, the inbound store or warehouse can post receipts in POS. When the outbound side processes the transfer order documents, their status is updated from **Requested** to **Shipped** or **Partially Shipped**. After the documents are in **Shipped** or **Partially Shipped** status, the inbound store or warehouse can post receipts against them using the inbound operation receiving process.

## Related topics

[Outbound inventory operation in POS](pos-outbound-inventory-operation.md)
