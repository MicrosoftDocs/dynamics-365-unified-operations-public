---
# required metadata

title: POS inbound inventory operation
description: This topic describes capabilities of the POS inbound inventory operation.
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

# Inbound inventory operations in POS

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]


"Inbound operations" and "outbound operations" in the point of sale (POS) operation replace "picking and receiving" in POS in Commerce versions 10.0.10 and higher.

> [!NOTE] 
> Any new features that are added to the POS application related to store inventory receiving against purchase orders and transfer orders will be made to the inbound operations operation beginning with version 10.0.10. We recommend that users who are currently using the picking and receiving operation in POS establish a strategy for moving off of this operation and onto the new inbound and outbound operations. The picking and receiving POS operation will not be removed from the product, but there will be no additional investments made to this operation from a functional or performance perspective after version 10.0.9.

## Prerequisite: configure asynchronous document framework

The inbound operation contains performance improvements to ensure that users with high volumes of receipt postings across many stores or companies with large inventory documents can process these documents to Commerce Headquarters (HQ) without time outs or unnecessary failures. This capability requires the use of an asynchronous document framework.

With the asynchronous document framework, users can commit their inbound document changes from POS to HQ and move onto other tasks while the processing to HQ occurs in the background. Users can check the status of the document through the POS **Inbound operation** document list page to ensure the posting was successful. Users can also see any documents that failed to post to HQ from within the POS application through the inbound operation active document list. If a document fails, POS users can make corrections to the document and retry processing to HQ.

> [!IMPORTANT] 
> The asynchronous document framework must be configured before a company attempts to use the inbound operation in POS.

To configure the asynchronous document framework, complete the following tasks.

### Create and configure a new number sequence

  1. On the **Organization administration > Number sequences > Number Sequences** page, create a new number sequence.
  2. Enter user-defined information in the **Number sequence code** and **Name** fields.
  3. Expand the **References** section. Click **Add** and then choose **Commerce parameters** in the **Area** field.
  4. Choose **Retail document operation identifier** for the **Reference** field.
  5. To ensure there are no performance issues, set the **Continuous** parameter in the **General > Setup** section to **No**.

### Create and schedule two new batch jobs for the document processing and monitoring tasks  

The batch jobs you create will be used to process documents that have failed or timed out, or when the number of active inventory documents in processing from POS exceeds a system-configured value.

  1. From the **System Administration > Inquiries > Batch jobs** page, configure two new batch jobs.
      - Configure one job to run the **RetailDocumentOperationMonitorBatch** class.
      - Configure another job to run the **RetailDocumentOperationProcessingBatch** class.
  2. Schedule these batch jobs to run on recurrence. For example, set the schedule to run every five minutes.

## Prerequisite: add inbound operation to the POS screen layout

To use the inbound operation functionality, your organization must first configure the inbound operations POS operation on one or more of your [POS screen layouts](https://docs.microsoft.com/dynamics365/unified-operations/retail/pos-screen-layouts). Ensure that you have properly tested and trained your users on the new operation before deploying it in a production environment.

## Overview of inbound operation

The inbound operations will allow the POS user to perform the following tasks.

- Receive inventory into store stock from confirmed purchase order documents or from shipped transfer order documents.
- View information about historical inventory receipts for a period of 7 days after the document has been fully received.
- Create new inbound transfer order requests.

When launching the inbound operation from the POS application, users will be presented with a list page view of open purchase order and transfer order documents that have inventory lines that are scheduled to be received by the user's current store. The user can scroll this list or use the search feature to locate a document and select it.

This inbound inventory document list has 3 tabs.

- **Active**: This tab shows documents that are fully or partially open and still contain lines or quantities on lines that are still to be received.
- **Draft**: This tab shows inbound transfer order requests that the store has created and have been saved locally and not submitted to HQ for processing.
- **Complete**: This tab shows a list of purchase or transfer order documents that have been fully received by the store over the past 7 days. This tab is for informational purposes only. All of the information about the documents is read-only data for the store.

When viewing documents in any of the tabs, the **Status** field can be used to help understand the stage the document is in.

- **Draft**: The transfer order document is only saved locally to the store's channel database. No information about the transfer order request has been submitted to HQ at that time.
- **Requested**: The purchase order or transfer order is created in HQ and is fully open. No receipts have yet to be processed against the document. In the case of a purchase order document type, receiving can begin at any time for documents in the requested status.
- **Partially shipped**: The transfer order document has one or more lines or partial line quantities that have been posted as shipped by the outbound warehouse. These shipped lines are available for receiving through the inbound operation.
- **Fully shipped**: The transfer order has had all its lines and full line quantities posted as shipped by the outbound warehouse. The entire document is available for receiving through the inbound operation.
- **Partially received**: Some of the lines or line quantities on the purchase order or transfer order document have been received by the store, but some lines remain open.
- **Fully received**: All lines and quantities on the purchase order or transfer order document have been fully received. The documents are only accessible on the **Complete** tab and are read-only by the store users.
- **In progress**: This is to inform device uers that the document is being actively worked on by another user.
- **Paused**: This status is displayed after a user has chosen the **Pause receiving** function to temporarily stop the receiving process.
- **Processing in HQ**: The document was submitted to HQ from the POS application and has not yet been successfully posted to HQ. The document is running through the async document posting process. Once the document successfully posts to HQ, it should update to a **Fully received** or **Partially received** status.
- **Processing failed**: The document was posted to HQ and rejected. The user will be able to see the reason the posting failed in the **Details** panel. The document will need to be edited and data issues fixed, and then re-submitted to HQ to attempt to process again.

Selecting any of the document lines from the list will display a **Details** panel where the user can view additional information about the document, including shipment and date information, and a progress bar detailing how many items remain to be processed. If the document failed to process to HQ, error messages related to the failure will also be available on the **Details** panel.

From the document list page view, users can use the **Order details** function from the app bar to view the document details. The user can also begin to initiate receipt processing on eligible document lines.

The document list page view also provides users with an option for creating a new inbound transfer order request for their store. These documents remain in a draft state and can be adjusted or deleted until they are submitted to HQ for processing. Once submitted to HQ, the transfer order lines can no longer be changed from the POS application.

## Receiving process

Once the user has selected a purchase order or transfer order document from the **Active** tab, they must click the **Order details** function to begin the receiving process.

By default, the **Receiving now** view is displayed. This view is optimized for barcode scanning and can be used to build a list of the items the user has scanned to be received. A user can begin to scan item barcodes to start the receiving process.

As a user scans item barcodes using the **Receiving now** view, the application will validate the item against the selected purchase or transfer order document to ensure the item scanned matches a valid item on the document. From the **Receiving now** view, a scan of a barcode assumes a quantity of 1 has been received, unless the barcode has a quantity embedded. Users can repeatedly scan barcodes from this view to build a list of all the items and quantities for their receipt.

### Example scenario
A user receives a purchase order that contains 10 units of barcode "5657900266". The user can scan that barcode 10 times to continually update the **Receiving now** field by 1 unit per scan. The **Receiving now** field for that items line will show a quantity of 10 received when the user finishes the scans.

Alternatively, if the user prefers to not scan the barcode for each item received in a large quantity scenario and instead prefers to enter the quantity manually, the user can scan the barcode once to add the item to the **Receiving now** list, then touch the associated line on the **Receiving now** list and edit the **Receiving quantity** for the item through the details panel that appears on the right side of the screen.

While the **Receiving now** view is optimized for barcode scanning, users may also click the **Receive product** function from the app bar and enter the item ID or barcode data through a dialog page prompt. Once the item entered is validated, the user will be prompted to enter the receipt quantity.

The **Receiving now** list view provides a focused view for the user so they can see which products they are receiving. An alternative process for receiving is the **Full order list** view. The **Full order list** view shows the enitre list of document lines for the selected purchase or transfer order document. From the **Full order list** view, users can select lines manually from the list and update the **Receiving quantity** field for the selected line from the **Details** panel. Users can scan barcodes in this view, or use the **Receive product** function while in the **Full order list** view to enter in the item ID or barcode and received quantity data without having to first preselect the matching item line from the list.

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

