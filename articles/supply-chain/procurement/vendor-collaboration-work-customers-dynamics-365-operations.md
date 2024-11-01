---
title: Vendor collaboration with customers
description: Learn how you can use vendor collaboration to work with POs and monitor consignment inventory, including a list of workspaces.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.topic: article
ms.date: 09/15/2020
ms.reviewer: kamaybac
ms.search.form: ConsignmentProductReceiptLines, ConsignmentVendorPortalOnHand, PurchVendorPortalConfirmedOrders, PurchVendorPortalOriginalOrder, PurchVendorPortalResponsesHistoryList, PurchVendorPortalResponsesPart, VendVendorProfileCard, PurchVendorPortalAllResponse, PurchVendorPortalPendingResponsesPart, PurchVendorPortalResponses, PurchVendorPortalConfirmedOpenOrdersPart
ms.assetid: 6e69fb8b-6d3a-46ef-88cf-6d01212aa7c3
---

# Vendor collaboration with customers

[!include [banner](../includes/banner.md)]

This article describes how you can use vendor collaboration to work with customers in Microsoft Dynamics 365 Supply Chain Management. Vendors can complete a series of business processes from the following workspaces:

- **Purchase order confirmation** – Monitor and respond to purchase orders (POs).
- **Vendor bidding** – View requests for quotation (RFQs), and respond to them by entering bids.
- **Vendor information** – View and update vendor master data.
- **Invoicing** – Work with invoices. This article doesn't cover the **Invoicing** workspace. For more information about this workspace, see [Vendor collaboration invoicing workspace](../../finance/accounts-payable/vendor-portal-invoicing-workspace.md).

Vendors can also monitor information about consignment inventory.

## Working with POs in the Purchase order confirmation workspace

The **Purchase order confirmation** workspace lets you respond to the purchase orders (POs) that have been sent to you for review. It also lets you view information about POs that are awaiting action from the customer, and POs that have been confirmed but are still open.

There are three lists in the **Purchase order confirmation** workspace:

- **Purchase orders for review** – This list shows POs that have been sent to you and are awaiting a response from you. After you respond, the PO disappears from the list. If the customer sends you a new version of the PO before you've responded to the previous version, only the latest version is shown.
- **Awaiting customer action** – This list shows all the POs that you've responded to but that the customer hasn't yet confirmed. If you accept a PO, you can monitor it in this list until the status is changed to **Confirmed**. If you reject a PO or accept it with changes, you can monitor it here until the customer sends a new version.
- **Open confirmed purchase orders** – This list shows all the POs for your account that have a status of **Confirmed**. When products or services are fully received against the PO, the PO disappears from the list.

You can use the following pages to work with POs:

- **Purchase orders for review** – This page contains the same information as the **Purchase orders for review** list in the workspace. See the description earlier in this article.
- **Purchase order vendor confirmation history** – This page contains all POs and all versions of POs that have been sent to the vendor. It also contains all the responses that have been returned from the vendor.
- **Open confirmed purchase orders** This page contains the same information as the **Open confirmed purchase order** list in the workspace. See the description earlier in this article.
- **All confirmed purchase orders** – This page contains all the POs that have been confirmed. The POs that are shown on this page include POs where products or services have been received. You can use this list to monitor POs that you can send invoices for.

### Responding to POs

The POs that the customer sends you to review appear in the **Purchase order confirmation** workspace and on the **Purchase orders for review** page. After you open a PO, you can accept it, reject it, or accept it with changes. There might be attachments on the PO header or on individual lines. Additionally, you can attach information to your response on the PO header or individual lines. For example, you might suggest a substitute item for one of the lines.

You can preview and print the PO as a PDF file by using the **Preview/Print** option. You can also use the **Display dimensions** action to hide or show the following dimension columns: **Site**, **Warehouse**, **Color**, **Size**, **Style**, and **Configuration**. 

If you use the **Accept with changes** option, you can accept or reject individual lines. You can also make the following changes to lines:

- Change dates or quantities. To update the confirmed receipt date on all lines, use the **Update receipt date** option on the PO header.
- Split lines for different receipt dates or quantities.
- Substitute an item. In the **Line details** section, enter an item description and the item number in the **External** field.

You can't change pricing information or charges, but you can use notes to make suggestions for these changes.

If the customer sends you a new version of a PO, it will have a version suffix to indicate that it's a modified version of a PO that was previously sent. The **Purchase order vendor confirmation history** page lets you track the history of each order.

## Monitoring consignment inventory

If you're using consignment inventory, you can use the vendor collaboration interface to view information on the following pages:

- **Purchase orders consuming consignment inventory** – POs for consignment inventory are generated when the customer takes ownership of the inventory. These consignment POs are shown only on this page. They aren't included on the **All confirmed purchase orders** page.
- **Products received from consignment inventory** – This page lists all the transactions where the ownership of products has been transferred to the company that is consuming the inventory. You can use this information to invoice the customer.
- **On-hand consignment inventory** – This page shows the on-hand consignment inventory that is owned by your company, but that is on hand at the customer's warehouse.

## Working with RFQs in the Vendor bidding workspace

The **Vendor bidding** workspace lets you view the requests for quotation (RFQs) that your company has been invited to respond to. You can also respond to the RFQs.

The workspace also shows all the RFQs that you've lost or won. Additionally, if the system is configured for the public sector, the workspace shows the RFQs that are publicly available.

### Viewing RFQs

Open the **Vendor bidding** workspace to access the following information:

- Select **New bid invitations** to see the RFQs that your company has been invited to respond to. From here, you can view an RFQ and start the bidding process. You can also see amended RFQs that a new bid must be submitted for.
- Select **Returned bids** to see the RFQs that the customer has returned to you so that you can provide more information or update the bid.
- Select **Bids in progress** to see the RFQs that you or a contact person who represents your company has been working on but hasn't yet submitted.
- Select **Awarded bids** to see when the customer has awarded at least one line item in your bid.
- Select **Lost bids** to see bids where all lines have been rejected.
- Select the **Request for quotations** link to see a list of all the vendor's RFQ invitations and any bids that have been submitted. The **Request for quotations** page lists all the RFQs that a vendor has been involved in. You can search by status.
- Select the **Declined bids** link to see a list of all the RFQs where a vendor's contact person has declined to bid.

### Working with RFQs that are publicly available

People who work in the public sector can see open and expired RFQs that have been made available to the public.

- Select the **Open published requests for quotations** link to see a list of open RFQs that are available to the public. An open RFQ is an RFQ that hasn't yet expired. You can find the expiration date and time on the header of the RFQ.

    If you've been invited to bid, you can find the same RFQ on the **New bid invitations** page. Sometimes, you might want to bid on an open RFQ, but you haven't been invited to bid. In this case, you might be able to invite yourself, provided that the customer has enabled self-invitation for the RFQ case. 

    The **New bid invitations** page can provide a filter that lets you view the open RFQs and identify those that contain lines that match your approved procurement categories. To make this filter available, you must turn on the *Let vendors search for RFQs by procurement category* feature in your system. Admins can use the **Feature management** workspace to check the status of this feature and turn it on if it's required. There, the feature is listed in the following way:

    - **Module:** *Accounts payable*
    - **Feature name:** *Let vendors search for RFQs by procurement category* <!-- KFM: I don't see this here, is this right? -->

    You can enhance the accessibility of the **Open published requests for quotations** link by turning on the *Display the "Open published requests for quotation" link as a tile* feature. This feature converts the link to a tile and moves it to a prominent location so that it's easy to find. Admins can use the **Feature management** workspace to check the status of this feature and turn it on if it's required. (As of Supply Chain Management version 10.0.21, the feature is turned on by default.) There, the feature is listed in the following way:

    - **Module:** *Procurement and sourcing*
    - **Feature name:** *Display the "Open published requests for quotation" link as a tile*

- Select the **Closed published requests for quotations** link to see a list of closed RFQs that are available to the public. A closed RFQ is an RFQ that has expired. You can find the expiration date and time on the header of the RFQ.

    A closed RFQ shows all vendor bids down to the line level. As bids are awarded or rejected, this information is reflected in the closed RFQ. Any attachments that are included in the bid are also available.

> [!NOTE]
> This functionality is available only if the public sector configuration is turned on.

### Bidding

- Select **Bid** to start to bid on an RFQ.

    When the editing is enabled for bid fields on the headers and lines of an RFQ, you can enter your bid directly in the line grid. You must also consider any additional bid information that should be added in the line details.

    When you start to work on a bid, it appears in the **Bids in progress** section.

    At any time before the expiration date, you can save a bid. You can then return later to finish and submit the bid. After you submit a bid, you can recall and update it up until the expiration date.

- Select **Reset from RFQ** to reset the data that you entered for a bid and revert to the original RFQ. You can reset the header or the line.
- Select **Add alternate** or **Remove alternate** in the line grid to work with alternates.

    Some RFQs allow for alternate bids. You can specify alternate bids only for lines of the **Category** type, because specific items can't be added as alternates. 

- Select **RFQ attachment** or **RFQ lines attachment** to open any attachment that the customer has added to an RFQ. Select **Bid attachments** or **Bid line attachments** to upload attachments together with the bid.

    There might be questionnaires that you must answer before you're allowed to submit a bid.

- Select **Decline** if you don't want to bid. After you select **Decline**, you can't recall the action and enter a bid.

If an RFQ is amended, you must enter a new bid. You can find information about the amendment on the **Amendments** tab of the RFQ page. Amended RFQs appear on the **New bid invitations** page.

## Accessing vendor master data in the Vendor information workspace

As a vendor, you can access part of the information that the customer maintains in the vendor master record. Therefore, you can keep the information up to date. To update the information, you must have a vendor admin (external) role.

The accessible information is the vendor name, addresses, contact information, contact persons and their contact information, identification numbers, tax registration numbers, procurement categories that the vendor is approved to sell to the customer in, and information about certifications.

## Related information

[Manage vendor collaboration users](manage-vendor-collaboration-users.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
