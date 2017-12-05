---
# required metadata

title: Vendor collaboration with customers
description: This topic describes how you can use vendor collaboration in Finance and Operations to work with POs and to monitor consignment inventory.
author: mkirknel
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ConsignmentProductReceiptLines, ConsignmentVendorPortalOnHand, PurchVendorPortalConfirmedOrders, PurchVendorPortalOriginalOrder, PurchVendorPortalResponsesHistoryList, PurchVendorPortalResponsesPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 221234
ms.assetid: 6e69fb8b-6d3a-46ef-88cf-6d01212aa7c3
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration with customers

[!include[banner](../includes/banner.md)]

This topic describes how you can use vendor collaboration to work with customers in Microsoft Dynamics 365 Finance and Operations. 
Vendors can complete a series of business processes from the following workspaces:

-	Purchase order confirmation: Allows vendors to monitor and respond to purchase orders. 
-	Vendor bidding: Allows vendors to view RFQs and enter bid replies.
-	Vendor information; Allows vendors to view and update vendor master data.
-	Invoicing: Allows vendors to work with invoices. For more information, see [Vendor collaboration invoicing workspace](../../financials/accounts-payable/vendor-portal-invoicing-workspace.md).

As a vendor, you can also monitor consignment inventory information.

## Working with purchase orders in the purchase order confirmation workspace
The **Purchase order confirmation** workspace enables you to respond to the PO’s that have been sent to you for review. It also enables you to view information about POs that are awaiting action from the customer, and POs that have been confirmed, but are still open. There are three lists in the **Purchase order confirmation** workspace:

-   **Purchase orders for review** -This list shows POs that have been sent to you and are awaiting a response from you. After you respond, the PO disappears from the list. If the customer sends you a new version of the PO before you’ve responded to the previous one, only the latest version is shown.
-   **Awaiting customer action** - This list allows you to see POs that you’ve responded to, but have not yet been confirmed by the customer. If you accepted the PO, you can monitor it in this list until the status changes to **Confirmed**. If you rejected the PO or accepted it with changes, you can monitor the PO here until the customer sends a new version.
-   **Open confirmed purchase orders** - This list contains all the POs for your account that have a status of **Confirmed**. When products or services are fully received against the PO, the PO disappears from the list.

The following list shows the four pages that you can use to work with purchase orders, two of which contain the same information as the lists in the workspace:

-   **Purchase orders for review** (see above)
-   **Purchase order vendor confirmation history** -This page contains all POs and all versions of POs that have been sent to the vendor, and all the responses that have been returned from the vendor.
-   **Open confirmed purchase orders** (see above)
-   **All confirmed purchase orders** - This page contains all the POs that have been confirmed, including those where products or services have been received. You can use this list to monitor which POs you can send invoices for.

### Responding to purchase orders

The purchase orders that the customer has sent you to review are visible in the **Purchase order confirmation** workspace and on the **Purchase orders for review** page. After you open a PO, you can choose to accept it, reject it, or accept it with changes. There could be attachments on the PO header or on individual lines. It's also possible for you to attach information to your response on the PO header or individual lines. For example, you might suggest a substitute item for one of the lines. You can preview and print the PO as a PDF file by using the **Preview/Print** option. You can hide or show the following dimension columns using the **Display dimensions** action: Site, Warehouse, Color, Size, Style, Configuration. If you use the **Accept with changes** option, you can accept or reject individual lines. You can also make the following changes to lines:

-   Change dates or quantities. If you want to update the confirmed delivery date on all lines, use the **Update delivery date** option on the PO header.
-   Split lines for different delivery dates or quantities
-   Substitute an item. To do this, enter an item description and your item number in the **External** field in the **Line details** section.

You can't change pricing information or charges, but you can make suggestions for changes to these using notes. If your customer sends you a new version of a PO, this will have a version suffix to indicate that it’s a modified version of a PO that was previously communicated. The **Purchase order vendor confirmation history** page allows you to track the history of each order.

## Monitoring consignment inventory
If you’re using consignment inventory, you can use the vendor collaboration interface to view information on the following pages:

-   **Purchase orders consuming consignment inventory** - Purchase orders for consignment inventory are generated when the customer takes ownership of the inventory. These consignment purchase orders are only displayed on the **Purchase orders consuming consignment inventory** page. They are not included on the **All confirmed purchase orders** page.
-   **Products received from consignment inventory** - This page lists all the transactions where the ownership of products has been transferred to the company that’s consuming the inventory. You can use this information to invoice the customer.
-   **On-hand consignment inventory** - This page shows the on-hand consignment inventory owned by your company that is on-hand at the customers warehouse.

## Working with RFQs from the Vendor bidding workspace
The Vendor bidding workspace enables you to view the RFQs that you have been invited to and to respond. It also shows which RFQs that you lost or won. 

If the system is configured for the public sector, you will also be able to see the RFQs that are publicly available.

### View RFQs from Vendor bidding
Open the Vendor bidding workspace to access the following sections:  
- Click **New bid invitations** to see the RFQs that your company has been invited to respond to. From here, you can view an RFQ and start the bidding process. You will also find amended RFQs which require submission of a new bid.
- Click **Returned bids** to see the RFQs that the customer has returned to get more information or updates on the bid.
- Click **Bids in progress** to see the RFQs that you or a contact person representing your company has been working on but has not submitted yet.
- Click **Awarded bids** to see when the customer has awarded at least one line item in your bid.
- Click **Lost bids** to see bids where all lines have been rejected.
- Click the link to **Request for quotations** to see a list of all the vendor’s RFQ invitations as well as any submitted bids. The **Request for quotations** page lists all the RFQs that a vendor has been involved in and you can search across statuses. 
Click the link to **Declined bids** to see a list of all the RFQs where a vendor’s contact person has declined to bid. 

### Working with RFQs from the Public sector

From the link Open published requests for quotations you can access a list of RFQs that are available for the public. An open RFQ is an RFQ that has not yet expired. You can find the expiration date and time on the header of the RFQ.
If you have been invited to bid, you can find the same RFQ on the New bid invitations page. If you want to bid on an open RFQ without an invitation, you may be able to invite yourself to bid. This is possible if he RFQ case has been enabled for self-invitation by the customer.

From the link Closed published requests for quotations you can access a list of RFQs that are available for the public. A closed RFQ is an RFQ that has expired. You can find the expiration date and time on the header of the RFQ.
A closed RFQ will show all vendor bids down to a line level. As bids get awarded or rejected this will be reflected in the closed RFQ. 
Any attachments that are included in the bid will also be available.

## Bidding
- Click Bid to start bidding on an RFQ. 

When the bid fields on the headers and lines of the RFQ are enabled for editing you can enter your bid directly on the line grid. You must also consider any additional bid information to be added on the line details.  
If you want to reset the data you entered for a bid and revert to the original RFQ then click  Reset from RFQ on the line or on the header depending on what you want to reset.
When you start working on a bid, it will appear in the Bids in progress section.
Some RFQs allow alternate bids. This only applies to lines of the type Category since specific items cannot be added as alternates.   Click Add alternate and Remove alternate on the line grid to work with alternates.
There may be attachments added to an RFQ by the customer. Click RFQ attachment or RFQ lines attachment to open an attachment. If you need to upload attachments as part of the bidding, click Bid attachments or Bid line attachments.
There might be questionnaires that needs to be answered before you are allowed to submit a bid.
At any time before the expiration date, you can save a bid and return later to finish and submit the bid. After you have submitted a  bid,  and if it is still before the expiration date, you can recall and update the bid.
If you do not want to bid, you can decline the bid. Once you click Decline, you will not be able to recall the action and enter a bid.
If an RFQ is amended, you will have to enter a new bid. You can find information about the amendment in the Amendments tab on the RFQ page. The Amended RFQ will appear on the New bid invitations page. 

## Accessing vendor master data in the Vendor information workspace

As a vendor, you can access part of the information that the customer maintains in the vendor master record. This allows you to keep the information up to date. You must have a vendor admin (external) role to be allowed to update the information.
The accessible information is vendor name, addresses, contact information, contact persons and their contact information, Identification numbers tax registration numbers  , Procurement categories in which the vendor is approved to sell to the customer and information about certifications.


See also
--------

[Manage vendor collaboration users](manage-vendor-collaboration-users.md)



