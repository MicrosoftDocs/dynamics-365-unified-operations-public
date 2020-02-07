---
# required metadata

title: POS Inbound Inventory Operation
description: This topic describes capabilities of the POS Inbound Inventory operation
author: hhaines
manager: annbe

ms.date: 01/23/2020
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

# Inbound Inventory Operations in POS

[!include [banner](includes/banner.md)]

## Inbound Inventory Operations in POS

The **Inbound operations** is a new POS operation that is available for public preview beginning with the April 2020 release (10.0.9/PU33). This operation, along with the new **Outbound operation** is intended to replace the existing **Picking and receiving** POS operation.  These operations will be generally available with the May 2020 (10.0.10) release.

> [!NOTE] 
>After May 2020, any new features that will be added to the POS application related to store inventory receiving against purchase orders and transfer orders will be made to the new **Inbound operations** operation. It is recommended that users who are currently leveraging the existing **Picking and receiving** operation in the POS begin to establish a strategy for moving off of this operation and onto the new Inbound an Outbound operations.   The **Picking and receiving** POS operation is not going to be removed from the product, but there will be no additional investments made to this operation from a functional or performance perspective after the 10.0.9 release.

## Pre-requisite: Using the Asynchronous Document Framework

The new **Inbound operation** contains performance improvements to ensure that users with high volumes of receipt postings across many stores or companies with large inventory documents can process these documents to HQ without time-outs or unnecessary failures.   This capability requires the use of an asynchronous document framework.

With the asynchronous document framework, users will now be able to commit their inbound document changes from POS to HQ and move onto other tasks while the processing to HQ occurs in the background.   Users can check on the status of the document through the POS **Inbound operation** document list page as desired to ensure the posting was successful.  Users will also be able to see any documents that failed to post to HQ from within the POS application through the **Inbound operation** active document list.  For any failed documents, POS users can make corrections to the document and retry processing of the document to HQ.

**The async document framework must be configured before a company attempts to use the Inbound operation in POS.**

To configure the asynchronous document framework, perform the following tasks:

**Create and configure a new number sequence**

  1. On the **Organization administration>Number sequences>Number Sequences** page, create a new number sequence.
  2. Enter a user-defined information in the **Number sequence code** and **Name** fields
  3. Expand the **References** section, click **Add** and choose **Commerce parameters** in the **Area**
  4. Choose **Retail document operation identifier** for the **Reference** field
  5. To ensure there are no performance issues, the **Continuous** setting found in the **General>Setup** section of this form should be set to **No**.

**Create and schedule two new batch jobs for the document processing and monitoring tasks.**  

These jobs will be used to process documents that have failed or timed out or when the number of active inventory documents in processing from POS exceeds a system configured value.

  1. From the **System Administration>Inquiries>Batch jobs** page, configure 2 new batch jobs
      - Configure one job to run the **RetailDocumentOperationMonitorBatch** class
      - Configure another job to run the **RetailDocumentOperationProcessingBatch** class
  2. Schedule these batch jobs to run on recurrence.  A suggested schedule would be to run them every 5 minutes.

## Pre-requisite: Adding the Inbound operation to your POS screen layout

To leverage the **Inbound operation** feature, your organization must first configure the **Inbound operations** POS operation on one or more of your [POS screen layouts](https://docs.microsoft.com/dynamics365/unified-operations/retail/pos-screen-layouts).  Please ensure you have properly tested and trained your users on the new operation before deploying it in a production environment.

##Inbound operation – overview

The **Inbound operations** will allow the POS user to perform the following tasks

1. Receive inventory into store stock from confirmed **Purchase order** documents or from shipped **Transfer order** documents
2. View information about historical inventory receipts for a period of 7 days after the document has been fully received
3. Create new inbound **Transfer order** requests

Upon launching the **Inbound operation** from the POS application, users will be presented with a list page view of open purchase order and/or transfer order documents that have inventory lines that are scheduled to be received by the user&#39;s current store.    The user can scroll this list or use the search feature to locate a document and select it.

This Inbound inventory document list will contain 3 different tabs:

- **Active** :  This tab shows documents that are fully or partially open and still contain lines or quantities on lines that are remaining to be received.
- **Draft** :  This tab shows Inbound transfer order request that the store has created, but has only saved locally and has not submitted them to HQ for processing.
- **Complete** :  This tab shows a list of Purchase or Transfer order documents that have been fully received by the store over the past 7 days.  This tab is for informational purposes only.   All information viewed about these documents will be read-only data for the store.

When viewing documents in any of the 3 tabs, the **Status** field can be used to help understand the stage the document is in:

- **Draft** : This Transfer order document is only saved locally to the store&#39;s channel database.  No information about this transfer order request has been submitted to HQ at this time.
- **Requested** :  The Purchase order or Transfer order is created in HQ and is fully open.  No receipts have yet to be processed against the document.  In the case of a Purchase order document type, receiving can begin at any time for documents in the Requested status.
- **Partially shipped** : Used when the Transfer order document has one or more lines or partial line quantities that have been posted as shipped by the outbound warehouse.   These shipped lines would now be available for receiving through the Inbound operation.
- **Fully shipped** : Used when the Transfer order has had all its lines and full line quantities posted as shipped by the outbound warehouse.  This entire document would be available for receiving through the Inbound operation.
- **Partially received** : Some of the lines or line quantities on the Purchase order or Transfer order document have been received by the store, but some lines remain open.
- **Fully received** : All lines and quantities on the Purchase order or Transfer order document have been fully received.  These documents will only be accessible on the Completed view tab and will be read-only by the store users.
- **In progress** : this status will be seen by users using other devices to inform them that the document is being actively worked on by another user.
- **Paused:** this status will be shown after a user has chosen the Pause receiving function to temporarily stop the receiving process with the intent to return to it soon.
- **Processing in**  **HQ:** The document has been submitted to HQ from the POS application and has not yet been successfully posted to HQ.   This document is running through the Async document posting process.  Once the document successfully posts to HQ is should update to a **Fully received** or **Partially received** status.
- **Processing failed** : This document was posted to HQ and rejected.  The user will be able to see the reason the posting failed as in the Details panel.   This document will need to be edited and issues fixed with the data and re-submitted back to HQ to attempt to process again.

Selecting any of the document lines from the list will display a **Details** panel where the user can view additional information about the document including a progress bar detailing how many items remain to be processed, as well as shipment and date info.  If the document has failed to process to HQ, error messages related to the failure will also be available on this **Details** panel.

From the document list page view, users may use the **Order details** function from the App bar to view the document details.  This is how the user can also begin to initiate receipt processing on eligible document lines.

The document list page view also provides users with an option for creating a new inbound Transfer order request for their store.  These documents remain in a draft state and can be adjusted or deleted until they are Submitted to HQ for processing.  Once submitted to HQ, these transfer order lines can no longer be changed from the POS application.

## Inbound operation – receiving process

Once the user has selected a Purchase order or Transfer order document from the Active tab, they may click the **Order details** function to begin the receiving process.

By default, the user will be shown the **Receiving now** view.   This view is optimized for barcode scanning.  This view can be used to build a list of the items the user has scanned to be received.   At this time, a user can begin to scan item barcodes to start the receiving process.

As a user scans item barcodes using the **Receiving now** view, the application will validate the item against the selected Purchase or Transfer order document to ensure the item scanned matches a valid item on the document.   From the **Receiving now** view, a scan of a barcode assumes a quantity of 1 has been received (unless the barcode has a quantity embedded).    Users can repeatedly scan barcodes from this view to build a list of all the items and quantities for their receipt.

> [!Example]
>A user is receiving a purchase order that contains 10 units of barcode 5657900266, the user can scan that barcode 10 times to continually update the **Receiving now** field by 1 unit per scan.  The **Receiving now** field for that items line will show a quantity of 10 received when the user has finished the scans.

Alternatively, if the user prefers to not scan the barcode for each item received in a large quantity scenario and would instead prefer to enter the quantity manually, the user can scan the barcode once to add the item to the **Receiving now** list, then touch the associated line on the **Receiving now** list to edit the **Receiving quantity** for the item through the Details panel that appears on the right side of the screen.

While the **Receiving now** view is optimized for barcode scanning, users may also click the **Receive product** function from the App bar and be prompted to enter in the Item ID or barcode data through a dialog page prompt.  Once the item entered is validated, the user will be prompted to enter the receipt quantity.

While the **Receiving now** list view is intended to provide a focused view for the user so they can see exactly which products they are receiving.  An alternative process for receiving, depending on your business needs, would be to change to the **Full order list** view.   The **Full order list** view will show the full list of document lines for the selected purchase or transfer order document.   From the **Full order list** view, users can select lines manually from the list and update the **Receiving quantity** field for the selected line from the **Details** panel.  Users may scan barcodes while in this view, or use the **Receive product** function while in the **Full order list** view to enter in the Item ID or barcode and received quantity data without having to first pre-select the matching item line from the list.

### Over-receiving validations

Validations will occur during the receiving process for the document lines, including over-delivery validation.  If a user attempts to receive more inventory than ordered on a purchase order and over-delivery has not been configured, or the amount received is above the configured over-delivery tolerance for the purchase order line, the user will be shown an error and will be prohibited from receiving the excess quantity.

Note that over-receiving is never allowed or possible for transfer order documents.  Users will always get errors if they attempt to receive more than was shipped for the transfer order line.

### Receiving location-controlled items

If the items being received are location controlled, users will be able to choose the location to receive the items into during the receiving process.   It is advised to configure a default receiving location for your store warehouse to make this process more efficient.  Even if a default location is configured, users can override the receiving location on select lines as desired.

This operation will respect the **Blank receipt allowed** configuration on the **Location** storage dimension and not require a location dimension to be entered if black receipt has been configured.  If blank receipt locations are not allowed for the item, the POS application will error and require a location to be entered before the receipt can be successfully posted to HQ.

### Receive All

If desired, users can use the **Receive all** function from the App bar to quickly update the **Receiving now** quantity for all of the document lines to the maximum value that is available to be received for those lines.

### Cancel Receiving

The **Cancel receiving** function on the App bar should only be used if the user wishes to back out of the document and not save any changes.  This may be necessary if the user picked the wrong document initially and does not want any of their previous **Receiving now** data saved.

### Pause Receiving

This can be used if the user who is receiving inventory wishes to take a break from the receiving process, perhaps to perform another operation from the POS (such as ringing a customer sale), or perhaps just to delay posting the receipt to HQ.

When the user chooses **Pause receiving**, the document will be placed in a **Paused** status.  This helps to ensure visibility to the fact that the document has data that has been entered but has not yet been committed to HQ.   When a user wishes to resume the receiving process, they can select the **Paused** document and resume receiving with the **Order details** function. Any previously saved **Receiving now** quantities will be retained and can be viewed from the **Full order list** view.

### Finish Receiving

When the user has completed entering all of the **Receiving now** quantities for products, in order for the receipt to be processed in HQ, the user must click the **Finish receiving** function on the App bar.

If configured, the user will be prompted to enter in the **Receipt number** when finishing a purchase order receipt – this is typically equivalent to the vendors packing slip identifier.  This **Receipt number** data will be stored in the **Product receipt journal** in HQ.   Receipt numbers are not capture for transfer order receipts.

With asynchronous document processing, the process of submitting the receipt to HQ will be done through an async document framework.   The time it takes for the document to post to HQ will depend on the size of the document (number of lines) and the general processing traffic happening on the server.   Typically, this process occurs in a matter of seconds.   If for any reason the document posting to HQ fails, users will be notified through the **Inbound operation** document list with an updated document status of **Processing failed**.   Users can view the error messages and reason for failure in the **Details** panel in POS when the select the failed document. A failed document is unposted in HQ and will require the user in POS to return to the document lines through the **Order details** function and update the document with any corrections based on the errors received.  Once correct, the user may try again to process the document using the **Finish receiving** function on the App bar.

## Inbound operation – create a new inbound Transfer order

From the Inbound operation in POS, users can create a new transfer order document.  Users can click the **New** operation from the App bar while in the main **Inbound operation** document list to begin this process.

After clicking **New** , the user will be prompted to select a **Transfer from** warehouse/store that will be providing the inventory to the user's store location.  In an inbound transfer request, the user's current store will always be the **Transfer to** warehouse for the transfer order and this cannot be changed.

Note that the selection of stores/warehouses the user can choose from for the **Transfer from** location will be limited to the selection defined for the store's fulfillment group configuration.

The user can populate **Ship date** , **Receive date** and **Mode of delivery** fields as desired.  Adding a **Note** to be stored with the transfer order header as an attachment to the document in HQ is also an option.

After the header information has been created, the user will be able to add products to the transfer order.  The user can use the **Add product** function to initiate the process of adding items and requested quantities.  Users may also add a line specific **Note** to the journal lines from the **Details** panel.  These notes will be stored in HQ as a line attachment.

After lines have been entered on the inbound transfer order, users can choose **Save** to save the document changes locally or **Submit request** to submit the order details to HQ for further processing.  Using **Save** will only store the draft document in the channel database and the document can not be executed upon by the outbound warehouse until it is successfully processed through the **Submit request** function to HQ.   Use **Save** only when not ready to commit the request to HQ for processing.

If a document is only saved locally, this document will be found on the **Drafts** tab of the **Inbound operation** document list.   While in draft status, the document can be edited by users using the **Edit** function and lines updated, added or deleted on the document as needed.   The entire document can also be deleted while in a draft state using the **Delete** function from the **Drafts** tab.

Once the draft document is successfully committed to HQ using the **Submit request** function, it will now appear on the **Active** document tab with a status of **Requested**.  This requested inbound transfer order document can no longer be edited by the inbound warehouse/store.  Only the outbound warehouse can make edits to this document through the POS application using the **Outbound operation**.   This editing lock is to ensure there are no conflicts caused by an inbound requestor making changes to the transfer order at the same time the outbound shipper is actively picking/shipping the order.   It is suggested that if changes are necessary from the inbound store/warehouse after submitting the transfer order to HQ that this be done by contacting the outbound shipper to have them edit the document and enter the changes necessary.

Once in a **Requested** state, this document is visible in the **Active** document tab, but the document is not yet receivable by the inbound store warehouse.  Only when some or all of the transfer order has been shipped by the outbound warehouse can receipts be posted by the inbound store/warehouse in POS.   These transfer order documents will move from a **Requested** status to a **Shipped** or **Partially Shipped** status when the outbound side processes them.  One these documents are in a **Shipped** or **Partially Shipped** status, the inbound store/warehouse can post receipts against them using the Inbound operation receiving process.

