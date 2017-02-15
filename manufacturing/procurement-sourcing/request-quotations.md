---
# required metadata

title: Request for quotations (RFQs)
description: This article provides an overview of requests for quotation (RFQs), which organizations issue when they must purchase items or services, and want to receive competitive offers from several vendors. In an RFQ, you ask vendors to provide the prices and delivery times for the item quantities that you specify. You can also ask vendors to specify whether there are any incidental charges, such as shipping costs, or any discounts for large orders or early payment of the vendor invoice.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08 - 08 - 48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PurchRFQCaseTable, PurchRFQCaseTableListPage, PurchRFQCompare, PurchRFQReplyTable, PurchRFQVendReplyTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 2154
ms.assetid: 025689a9-2f9c-4c49-b02d-a1ecc2e5887f
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Request for quotations (RFQs)

This article provides an overview of requests for quotation (RFQs), which organizations issue when they must purchase items or services, and want to receive competitive offers from several vendors. In an RFQ, you ask vendors to provide the prices and delivery times for the item quantities that you specify. You can also ask vendors to specify whether there are any incidental charges, such as shipping costs, or any discounts for large orders or early payment of the vendor invoice.

The request for quotation (RFQ) process covers the following tasks:

-   Creating and sending an RFQ to one or more vendors
-   Receiving and registering RFQ replies (bids)
-   Transferring accepted bids to a purchase order, purchase agreement, or purchase requisition

The following illustration provides an overview of the RFQ process. [![Request for quotation process](./media/rfq-process-458x1024.jpg)](./media/rfq-process.jpg) You can create an RFQ from planned orders, from a purchase requisition, or from a manual entry. The RFQ that you create is called an RFQ case, and this is the base document that you use to issue an RFQ to each vendor. After you prepare the RFQ case and add vendors, click **Send** on the RFQ case, and an RFQ journal is generated for each vendor that you sent the RFQ to. You can configure the print management settings for the Send action to either print a report for each vendor to an archive or send a report to each vendor's email address. In addition, the RFQ journal for each vendor can be used to generate a report that you can send or resend to a vendor later. You can also configure the Send action to generate a reply sheet that the vendor can fill out. If you must amend an RFQ after you send it, you can resend the RFQ to vendors when you've finished. When you receive bids, you must enter them on the **Request for quotation replies** page. If you select the **Copy data to reply** option, data such as the quantity and dates from the RFQ case is copied into the reply. You can change this data to reflect the vendor's bid. If a second iteration of a reply is required for a particular vendor, click **Return** on the **Request for quotation reply** page. The Return action generates a new journal and a report that will be printed, archived, and sent according to your print management settings. If you added scoring criteria to your RFQ case, the RFQ reply will have a scoring panel where you can enter the scores. The total scores will appear when you compare the replies on the **Compare replies** page, where you can also compare other reply data, such as the line price, delivery date, and total price. After you decide on a bid or partial bids, you can accept them and reject the rest. Acceptance journals, rejection journals, and corresponding reports are generated. These will be printed, archived, and sent according to your print management settings. When you accept a bid or specific lines in a bid, either a purchase agreement or purchase order is generated, or a purchase requisition is updated, depending on the RFQ purchase type. You can create a trade agreement that you can use later for any of the replies, regardless of whether you accepted or rejected them. The status of an RFQ appears in the RFQ header and depends on the status of the RFQ lines. The status indicates the extent to which you've processed the RFQ. Each RFQ has two values for the status: lowest and highest. The lowest status is the least advanced stage of any line in the RFQ, and the highest status is the most advanced stage of any line in the RFQ. For example, if the least advanced stage in an RFQ is for a line that has been created, the lowest status for the RFQ is **Created**. If the most advanced stage in the RFQ is for a line that has been sent to vendors, the highest status for the RFQ is **Sent**. The statuses are automatically updated as you process an RFQ. You can view the lowest and highest statuses for an RFQ header on the **All requests for quotations** page. You can view the lowest and highest statuses for an RFQ line on the **Lines** tab on the **Request for quotations** page. Here's the sequence of statuses for processing an RFQs:

1.  **Created**
2.  **Sent**
3.  **Received**
4.  **Accepted**/**Canceled**/**Rejected**

The statuses will be described in more detail in later sections of this article.

## Setting up RFQ functionality
Before you can create an RFQ case, you must set up RFQ information on the **Procurement and sourcing parameters** page. When you create an RFQ case, you can specify default values that are copied to the RFQ. You can specify the following default values:

-   The purchase type of new RFQs: **Purchase order** or **Purchase agreement**
-   Settings for expiration date and time
-   Delivery information and payment terms.
-   Fields that should be included in the RFQ reply

You can override these values for a specific RFQ case. You should also configure the amendment process. As part of this configuration, you can turn on field locking. When field locking is turned on, a procurement professional who wants to amend an RFQ must first click **Create** in the **Amendment** section of the **Quotation** tab. After the RFQ has been updated with the amendment, the procurement professional must complete the process by clicking **Finalize**.** **The Finalize action generates an email message that notifies the vendors about the amended RFQ. You select the template for the email notification that is sent to vendors on the **Procurement and sourcing parameters** page. When a template is created, it can contain the following replacement tokens:

-   %Reason for bid return%
-   %Reason for amendment%
-   %Amendment prepared by%
-   %Company%

The %Reason for bid return% and %Reason for amendment% tokens are replaced by text that the procurement professional can enter when he or she completes the amendment in the **Amendment** wizard. The values for the %Amendment prepared by% and %Company% tokens are automatically taken from the RFQ. If you want to use reason codes on a RFQ reply to indicate why a bid was rejected or accepted, you must set up reason codes on the **Vendor reasons** page. You can configure the appearance of your printed or stored RFQ documents on the **Form setup** page in Procurement and sourcing. When you create an RFQ for a purchase order and add an inventory item to the RFQ, an inventory transaction is generated that has a receipt status of **Quotation receipt**. Only RFQ lines that have this status are considered when you use a master plan to calculate supplies. If you want the master plan to include RFQ lines as an expected receipt, you must configure this behavior in the setup of master planning. As a purchasing manager or agent, you can create and maintain solicitation types to suit the procurement requirements of your organization. Each solicitation type can drive scoring methods. Scoring methods consist of a set of criteria that can be used when you score bids. You must set up solicitation types, scoring methods, and scoring criteria on the **Solicitation type** and **Scoring method** pages.

## Creating and sending an RFQ
You create an RFQ, select the vendors that you want to bid on the RFQ, and then send the RFQ to the vendors. You can use print management to route the RFQ report and reply sheet reports to your preferred destination. You can create an RFQ for the **Purchase order** or **Purchase agreement** purchase type. If the RFQ is generated from a purchase requisition, the **Purchase requisition** type is automatically assigned. You can't manually create an RFQ of the **Purchase requisition** type. If the RFQ is of the **Purchase order** type:

-   When RFQ lines are created, inventory transactions are generated that have a receipt status of **Quotation receipt**.
-   When you accept a bid, a purchase order is generated.

If the RFQ is of the **Purchase agreement** type:

-   The RFQ is used for an agreement to purchase a specific quantity or value of product over time. You must select the date range that applies to the purchase agreement and the name of the person who manages the purchase agreement.
-   When you accept a bid, a purchase agreement is generated.

You can create an RFQ from a purchase requisition only if the status of the purchase requisition is **In review** and you are assigned to do the next workflow task. The lines in the purchase requisition are updated automatically as you accept lines from RFQ replies (bids) that you received from vendors. You can't complete, reject, approve, or perform any other actions on the purchase requisition while the RFQ is in progress. When you create an RFQ, you can select a specific solicitation type. The solicitation type determines the set of scoring criteria that is used to score replies to the RFQ. You can add a questionnaire to an RFQ case. This questionnaire then appears on all replies after you send the RFQ. There are three ways to select the vendors to add to an RFQ case:

-    Add the vendors one by one.
-   Search for all vendors that meet specific criteria.
-   Automatically add all vendors that are approved for the procurement categories that are used on the RFQ lines.

When the RFQ case is ready, click **Send**. The Send action generates journals and reports that will be printed, archived, and sent according to your print management settings. If you selected the **Use vendor for recalculating prices** and **Use vendor specific item information** check boxes on the **Sending request for quotation** page when you sent the request to vendors, some vendor-specific information is automatically entered. You can modify this information on the **Request for quotation reply** page. The following table shows how the RFQ status changes when you create an RFQ and send it to vendors.

|                                    |                              |                                                 |                            |                             |
|------------------------------------|------------------------------|-------------------------------------------------|----------------------------|-----------------------------|
| **Action**                         | **Lowest RFQ header status** | **Highest RFQ header status**                   | **Lowest RFQ line status** | **Highest RFQ line status** |
| Create the RFQ header and line.    | Created                      | Created                                         | Created                    | Created                     |
| Send the RFQ to a specific vendor. | Sent                         | Sent                                            | Sent                       | Sent                        |
| Add another vendor.                | Created                      | Sent(The RFQ has been sent to only one vendor.) | Created                    | Sent                        |
| Send the RFQ to the second vendor. | Sent                         | Sent                                            | Sent                       | Sent                        |

**Note:** You can add more vendors to an RFQ at any time, and the lowest and highest statuses change to reflect the new vendors. For example, if you received bids from all vendors and accepted at least one line on a bid, the lowest status in the RFQ header is **Rejected**, and the highest status is **Accepted**. If you add a new vendor, the lowest status on any line is now **Created**. Therefore, the lowest status in the RFQ header changes to **Created**, and the highest status remains **Accepted**.

## Amending an RFQ
Occasionally, you must change an RFQ after you send it. This can occur because, for example, the delivery dates have changed, or you want additional products or different quantities of products. You can configure the amendment process so that it is either more restrictive or less restrictive. If you use the more restrictive amendment process, you must click **Create** on the RFQ case to start an amendment before you can modify the fields on the RFQ case. After you've finished making your changes, you must click **Finalize**. You will then be guided through the process of adding information for the email message that is sent to notify vendors about the amendment. The updated RFQ report, which includes an amendment note, is automatically attached to the message. If you use the less restrictive amendment process, you don't have to create an amendment before you can modify the fields on an RFQ case that has already been sent. However, you must manually add an amendment note on the RFQ.

## Receiving and registering RFQ replies
When you send an RFQ, a reply sheet is automatically generated. As you receive replies (bids) to an RFQ, you must enter the information from each vendor on a vendor-specific RFQ reply sheet. If you have added scoring criteria, you can score the replies. You then compare the vendor bids and rank them according to your scoring criteria, such as best total price or best total delivery time. If a questionnaire is attached to the RFQ case, you must manually enter the answers to the questions in the reply sheet. If you must enter alternate lines, and the RFQ case allows for this, on the **Purchase quotation lines** FastTab, click **Add line**. Then enter the product information, such as the item number or procurement category, quantity, price, and discount. If you've entered a reply but require a new offer from the vendor, you can resend the RFQ. This will generate a new journal and report that you can use to request changes from the vendor. You can see an overview of all RFQs and their reply statuses on the **Request for quotation follow-up** page. The following table shows how the RFQ status changes as you receive bids and register the information in the RFQ reply sheet.

|                                                |                       |                        |                              |                               |                            |                             |
|------------------------------------------------|-----------------------|------------------------|------------------------------|-------------------------------|----------------------------|-----------------------------|
| **Action**                                     | **Lowest bid status** | **Highest bid status** | **Lowest RFQ header status** | **Highest RFQ header status** | **Lowest RFQ line status** | **Highest RFQ line status** |
| Register one vendor’s bid, and save it.        | Sent                  | Received               | Sent                         | Received                      | Sent                       | Received                    |
| Register the second vendor’s bid, and save it. | Received              | Received               | Received                     | Received                      | Received                   | Received                    |

**Note:** If you return a bid to a vendor for additional negotiation, the lowest and highest statuses both remain **Received**.

### Accepting and rejecting bids, and transferring accepted bids to downstream documents

After you've identified the best bid, such as the bid that offers the best total price, you accept the bid. The status of the RFQ reply for that vendor is updated to **Accepted**. When you accept a bid or specific lines in a bid, a purchase order or purchase agreement is generated automatically, and you can reject the bids from the other vendors. When you accept an RFQ reply of the **Purchase requisition** type, the RFQ reply lines update the purchase requisition lines with the following information:

-   Unit price
-   Discount percentage
-   Discount amount
-   Purchase charges
-   Line charges
-   Vendor
-   External number
-   External description

On the reply, you can add a reason code to explain why you accepted or rejected a bid. You can accept some lines in a bid and reject others. You can also accept lines from different vendors. Just be aware that if you accept some lines, you will be prompted to reject all the other lines. Therefore, if you want to accept other lines, you must click **Cancel** when you receive the prompt. The following table shows how the RFQ status changes as you accept and reject bids from vendors.

|                         |                       |                        |                              |                               |                            |                             |
|-------------------------|-----------------------|------------------------|------------------------------|-------------------------------|----------------------------|-----------------------------|
| **Action**              | **Lowest bid status** | **Highest bid status** | **Lowest RFQ header status** | **Highest RFQ header status** | **Lowest RFQ line status** | **Highest RFQ line status** |
| Accept one of the bids. | Received              | Accepted               | Received                     | Accepted                      | Received                   | Accepted                    |
| Reject the other bids.  | Rejected              | Accepted               | Rejected                     | Accepted                      | Rejected                   | Accepted                    |



