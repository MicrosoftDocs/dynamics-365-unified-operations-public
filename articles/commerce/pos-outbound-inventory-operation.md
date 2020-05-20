---
# required metadata

title: Outbound inventory operation in POS
description: This topic describes capabilities of the point of sale (POS) outbound inventory operation.
author: hhaines
manager: annbe

ms.date: 05/14/2020
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

# Outbound inventory operation in POS

[!include [banner](includes/banner.md)]


In Microsoft Dynamics 365 Commerce version 10.0.10 and later, inbound and outbound operations in the point of sale (POS) replace the picking and receiving operation.

> [!NOTE]
> In version 10.0.10 and later, any new features in the POS application that are related to receiving store inventory against purchase orders and transfer orders will be added to the inbound operations operation. If you're currently using the picking and receiving operation in POS, we recommend that you develop a strategy for moving from that operation to the new inbound and outbound operations. Although the picking and receiving operation won't be removed from the product, there will be no further investments in it, from a functional or performance perspective, after version 10.0.9.

## Prerequisite: Configure an asynchronous document framework

The outbound operation includes performance improvements to ensure that users who have high volumes of receipt postings across many stores or companies, and large inventory documents, can process those documents to Commerce Headquarters without experiencing time-outs or failures. These improvements require use of an asynchronous document framework.

When an asynchronous document framework is used, you can commit outbound document changes from POS to Commerce Headquarters and then move on to other tasks while the processing to Commerce Headquarters occurs in the background. You can check the status of the document through the **Outbound operation** document list page in POS to make sure that posting was successful. In the POS application, you can also use the outbound operation active document list to see any documents that could not be posted to Commerce Headquarters. If a document fails, POS users can make corrections to it and then try again to process it to Commerce Headquarters.

> [!IMPORTANT]
> The asynchronous document framework must be configured before a company tries to use the outbound operation in POS.

To configure an asynchronous document framework, complete the following procedures.

### Create and configure a number sequence

1. Go to **Organization administration \> Number sequences \> Number Sequences**.
2. On the **Number sequences** page, create a number sequence.
3. In the **Number sequence code** and **Name** fields, enter user-defined values.
4. On the **References** FastTab, select **Add**.
5. In the **Area** field, select **Commerce parameters**.
6. In the **Reference** field, select **Retail document operation identifier**.
7. On the **General** FastTab, in the **Setup** section, set the **Continuous** option to **No** to ensure that there are no performance issues.

### Create and schedule two batch jobs for the document processing and monitoring tasks

The batch jobs that you create will be used to process documents that fail or time out. They will also be used when the number of active inventory documents that are being processed from POS exceeds a system-configured value.

1. Go to **System Administration \> Inquiries \> Batch jobs**.
2. On the **Batch job** page, create two batch jobs:

    - Configure one job to run the **RetailDocumentOperationMonitorBatch** class.
    - Configure the other job to run the **RetailDocumentOperationProcessingBatch** class.

3. Schedule the new batch jobs to run on a recurring basis. For example, set the schedule so that the jobs are run every five minutes.

## Prerequisite: Add Outbound operation to the POS screen layout

Before your organization can use the outbound operation functionality, it must configure the **Outbound operation** POS operation on one or more of your [POS screen layouts](https://docs.microsoft.com/dynamics365/unified-operations/retail/pos-screen-layouts). Before you deploy the new operation in a production environment, make sure that you thoroughly test it and train your users to use it.

## Overview

The outbound operation lets POS users perform the following tasks:

- Post shipments for transfer order documents in cases where the user's store is the designated outbound warehouse.
- View information about historical transfer order shipments that were posted by the store.
- Create new outbound transfer order requests.

When the outbound operation is started from the POS application, a list page view appears. This view shows open transfer order documents that have inventory lines that the user's current store is intended to ship and fulfill. To find a select a document, users can scroll the list or use the search feature.

The outbound inventory document list has three tabs.

- **Active** – This tab shows transfer orders that have a status of **Requested** or **Partially Shipped**. The orders contain lines or quantities on lines that must be shipped by the user's current store. This tab also shows orders that have a status of **Processing in HQ** (that is, they are waiting for confirmation of successful posting from Commerce Headquarters) or **Processing failed** (that is, posting to Commerce Headquarters was unsuccessful, and the user must correct data and try again to submit the orders).
- **Draft** – This tab shows new outbound transfer order requests that the user's store created. However, the documents have only been saved locally. They haven't yet been submitted to Commerce Headquarters for processing.
- **Complete** – This tab shows a list of transfer order documents that the store has fully shipped during the last seven days. This tab is for informational purposes only. All the information about the documents is read-only data for the store.

When you view documents on any of the tabs, the **Status** field can help you understand the stage that the document is in.

- **Draft** – The transfer order document has only been saved locally to the store's channel database. No information about the transfer order request has yet been submitted to Commerce Headquarters.
- **Requested** – The purchase order or transfer order has been created in Commerce Headquarters and is fully open. The user's current store has yet processed any shipments against the document.
- **Partially shipped** – The transfer order document has one or more lines or partial line quantities that have been posted as shipped by the outbound warehouse. These shipped lines are available to be received through the inbound operation.
- **Fully shipped** – The transfer order has had all its lines and full line quantities posted as shipped by the outbound warehouse.
- **In progress** – This status is used to inform device users that the document is being actively worked on by another user.
- **Paused** – This status is shown after **Pause receiving** is selected to temporarily stop the receiving process.
- **Processing in HQ** – The document was submitted to Commerce Headquarters from the POS application, but it hasn't yet been successfully posted to Commerce Headquarters. The document is going through the asynchronous document posting process. After the document is successfully posted to Commerce Headquarters, its status should be updated to **Fully received** or **Partially received**.
- **Processing failed** – The document was posted to Commerce Headquarters and rejected. The **Details** pane shows the reason for the posting failure. The document must be edited to fix data issues, and then it must be resubmitted to Commerce Headquarters for processing.

When you select a document line in the list, a **Details** pane appears. This pane shows additional information about the document, such as shipment and date information. A progress bar shows how many items must still be processed. If the document wasn't successfully processed to Commerce Headquarters, the **Details** pane also shows error messages that are related to the failure.

In the document list page view, you can select **Order details** on the app bar to view the document details. You can also activate receipt processing on eligible document lines.

In the document list page view, you can also create a new outbound transfer order for a store.

## Transfer order shipping process

After you select a transfer order document on the **Active** tab, you can select **Order details** to begin the fulfillment process. The **Full order list** view appears. This page shows all the document lines that contain the item. It also shows details of the ordered quantity.

Each scan of a bar code updates the quantity in the **Shipping now** field by one unit. Alternatively, you can enter a shipping quantity by selecting **Ship product** on the app bar, entering an item ID, and then entering the quantity. If the item is location-controlled, you can confirm or set the shipping location for the document line.

In the **Full order list** view, you can manually select a line in the list and then update the **Shipping now** quantity for the selected line in the **Details** pane.

### Over-delivery shipping validations

Validations occur during the receiving process for the document lines. They include validations for over-delivery. If a user tries to receive more inventory than was ordered on a purchase order, but either over-delivery isn't configured or the quantity that is received exceeds the over-delivery tolerance that is configured for the purchase order line, the user receives an error and isn't allowed to receive the excess quantity.

### Underdelivery close lines

In Commerce version 10.0.12, functionality was added that lets POS users close or cancel remaining quantities during outbound order shipment if the outbound warehouse determines that it can't ship the full quantity that was requested. Quantities can also be closed or canceled later. To use this capability, the company must be configured to allow underdelivery of transfer orders. Additionally, an underdelivery percentage must be defined for the transfer order line.

To configure the company to allow underdelivery of transfer orders, in Commerce Headquarters, go to **Inventory management \> Setup \> Inventory and warehouse management parameters**. On the **Inventory and warehouse management parameters** page, on the **Transfer orders** tab, turn on the **Accept underdelivery** parameter. Then run the **1070** distribution scheduler job to sync the parameter changes to your store channel.

Underdelivery percentages for a transfer order line can be predefined on products as part of product configuration in Commerce Headquarters. Alternatively, they can be set or overwritten on a specific transfer order line through Commerce Headquarters.

After an organization has finished configuring transfer order underdelivery, users will see a new **Close remaining quantity** option in the **Details** pane when they select an outbound transfer order line through the **Outbound operation** operation in POS. Then when users complete the shipment by using the **Finish fulfillment** operation, they can send a request to Commerce Headquarters to cancel the remaining unshipped quantity. If a user chooses to close the remaining quantity, Commerce does a validation to verify that the quantity that is being canceled is within the underdelivery percentage tolerance that is defined on the transfer order line. If the underdelivery tolerance is exceeded, the user receives an error message and can't close the remaining quantity until the previously shipped and "ship now" quantity meets or exceeds the underdelivery tolerance.

After the shipment is synced to Commerce Headquarters, the quantities that are defined in the **Ship now** field for the transfer order line in POS are updated to a shipped status in Commerce Headquarters. Any unshipped quantities that previously would have been considered "ship remain" quantities (that is, quantities that will be shipped later) are considered canceled quantities instead. The "ship remain" quantity for the transfer order line is set to **0** (zero), and the line is considered fully shipped.

### Shipping location-controlled items

If the items that are being shipped are location-controlled, users can choose the location that they want to issue the inventory from during the shipping process. We recommend that you configure a default issue location for your store warehouse, to make this process more efficient. Even if a default location is configured, users can override the issue location on selected lines as they require.

The operation respects the **Blank receipt allowed** configuration on the **Location** storage dimension and doesn't require that a location dimension be entered if blank receipt is configured. If blank receipt locations aren't allowed for an item, the POS application shows an error and requires that a location be entered before the receipt can be posted.

### Ship all

As you require, you can select **Ship all** on the app bar to quickly update the **Shipping now** quantity for all the document lines to the maximum value that is available to be fulfilled for those lines.

### Cancel fulfillment

You should use the **Cancel fulfillment** function on the app bar only if you want to back out of the document and don't want to save any changes. For example, you initially selected the wrong document and don't want any of the previous shipping data saved.

### Pause fulfillment

If you're fulfilling the transfer order, you can use the **Pause fulfillment** function if you want to take a break from the process. For example, you might want to perform another operation from the POS, such as ringing up a customer sale, or delay posting of the shipment to Commerce Headquarters.

When you select **Pause fulfillment**, the document's status is changed to **Paused**. Therefore, user will know that data has been entered in the document, but the document hasn't yet been committed. When you're ready to resume the fulfillment process, select the paused document, and then select **Order details**. Any **Shipping now** quantities that were previously saved will be retained and can be viewed from the **Full order list** view.

### Finish fulfillment

When you've finished entering all the **Shipping now** quantities for products, you must select **Finish fulfillment** on the app bar.

When asynchronous document processing is used, the receipt is submitted through an asynchronous document framework. The time that it takes for the document to be posted depends on the size of the document (the number of lines) and the general processing traffic that is occurring on the server. Typically, this process occurs in a matter of seconds. If document posting fails, the user is notified through the **Outbound operation** document list on the **Active** tab, where the document status will be updated to **Processing failed**. The user can then select the failed document in POS to view the error messages and the reason for the failure in the **Details** pane. A failed document remains unposted and requires that the user return to the document lines by selecting **Order details** in POS. The user must then update the document with corrections, based on the errors. After a document is corrected, the user can try again to process it by selecting **Finish fulfillment** on the app bar.

## Create an outbound transfer order

From POS, users can create new transfer order documents. To begin the process, select **New** on the app bar while you're in the main **Outbound operation** document list. You're then prompted to select a **Transfer to** warehouse or store that your current store will send inventory to. The values are limited to the selection that is defined in the configuration of the store's fulfillment group. In an outbound transfer request, your current store will always be the **Transfer from** warehouse for the transfer order. That value can't be changed.

You can enter values in the **Ship date**, **Receive date**, and **Mode of delivery** fields as you require. You can also add a note that will be stored together with the transfer order header, as an attachment to the document in Commerce Headquarters.

After the header information is created, you can add products to the transfer order. To start the process of adding items and requested quantities, scan bar codes or select **Add product**.

After lines are entered on the outbound transfer order, you must select **Save** to save the document changes locally or **Submit request** to submit the order details to Commerce Headquarters for further processing. If you select **Save**, the draft document is stored in the channel database, and the outbound warehouse can't run the document until it has been successfully processed via **Submit request**. You should select **Save** only if you aren't ready to commit the request to Commerce Headquarters for processing.

If a document is saved locally, it can be found on the **Drafts** tab of the **Inbound operation** document list. While a document is in **Draft** status, you can edit it by selecting **Edit**. You can update, add, or delete lines as you require. You can also delete the whole document while it's in **Draft** status, by selecting **Delete** on the **Drafts** tab.

After the draft document is successfully submitted to Commerce Headquarters, it appears on the **Active** tab and has a status of **Requested**. At this point, only users in the outbound warehouse can edit the document, by selecting **Outbound operation** in the POS application. Users in the inbound warehouse can view the transfer order on the **Active** tab of the **Inbound operation** document list, but they can't edit or delete it. The editing lock ensures that no conflicts occur because an inbound requestor changes the transfer order at the same time that the outbound shipper is actively picking and shipping the order. If changes are required from the inbound store or warehouse after the transfer order has been submitted, the outbound shipper should be contacted and asked to enter the changes.

After the document is in **Requested** status, it's ready for fulfillment processing by the outbound warehouse. As the shipment is processed by using the outbound operation, the status of the transfer order documents is updated from **Requested** to **Fully shipped** or **Partially shipped**. After the documents are in **Fully shipped** or **Partially shipped** status, the inbound store or warehouse can post receipts against them by using the inbound operation receiving process.

Fully shipped transfer orders are moved to the **Complete** tab of the **Outbound operation** document list. There, they remain visible to users in the outbound store or warehouse, in read-only mode, for seven days.

## Related topics

[Inbound inventory operation in POS](pos-inbound-inventory-operation.md)
