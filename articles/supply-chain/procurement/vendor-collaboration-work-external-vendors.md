---
# required metadata

title: Vendor collaboration with external vendors
description: This topic explains how purchasing agents can collaborate with external vendors to exchange information about purchase orders and consignment inventory.
author: GalynaFedorova
ms.date: 11/02/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PurchRFQCaseTableListPage, VendVendorPortalInvoicePart, PurchaseOrderResponseActionRemarks, PurchVendorPortalAllResponse, PurchOrderInExternalReview, PurchVendorPortalPendingResponsesPart, PurchVendorPortalResponses, PurchVendorPortalConfirmedOpenOrdersPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 221264
ms.assetid: dde49743-1541-4353-a030-63ca3069cd7d
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration with external vendors

[!include [banner](../includes/banner.md)]

The **Vendor collaboration** module is targeted at vendors who don't have electronic data interchange (EDI) integration with Microsoft Dynamics 365 Supply Chain Management. It lets vendors work with purchase orders (POs), invoices, consignment inventory information, and requests for quotation (RFQs), and also lets them access parts of their vendor master data. This topic explains how you can collaborate with external vendors who use the vendor collaboration interface to work with POs, RFQs, and consignment inventory. It also explains how to enable a specific vendor to use vendor collaboration, and how to define the information that all vendors see when they respond to a PO.

For more information about what external vendors can do in the vendor collaboration interface, see [Vendor collaboration with customers](vendor-collaboration-work-customers-dynamics-365-operations.md).

> [!NOTE]
> The information about vendor collaboration in this topic applies only to the current version of Supply Chain Management. In Microsoft Dynamics AX 7.0 (February 2016) and Microsoft Dynamics AX application version 7.0.1 (May 2016), you collaborate with vendors by using the **Vendor portal** module. For information about the **Vendor portal** module, see [Collaborate with vendors by using the Vendor portal](collaborate-vendors-vendor-portal.md).

For more information about how vendors can use vendor collaboration in invoicing processes, see [Vendor collaboration invoicing workspace](../../finance/accounts-payable/vendor-portal-invoicing-workspace.md). For information about how to provision new vendor collaboration users, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md).

## Defining the information that is shown to vendors when they respond to POs

When vendors respond to a PO that you send them, they see one of three message boxes, where they must confirm that they want to accept the PO, reject it, or accept it with changes. Because the information that must be shown to the vendor at that point might be specific to your business, you can specify the text that appears in each confirmation message. For example, the text can inform the vendor about the next steps in the process, or about terms and conditions.

To define the text that's shown in the PO response, follow these steps

1. On the **Information for vendors responding to POs** page, select the response type, and then select **Edit**.
2. In the **Information message** box, enter the information that should be shown to vendors in the message box.

If you must add messages in more than one language, create separate messages, and specify the appropriate language code for each. The message that is shown to each vendor will be in the language that the vendor uses.

## Setting the vendor collaboration options for a specific vendor

An administrator configures the general settings for vendor collaboration, such as the security roles that are available for all vendors that you collaborate with. However, there are also settings that can differ for each vendor account. You should configure these settings.

- Enable vendor collaboration.
- Specify whether the vendor should see price information.

### Enabling vendor collaboration

Before user accounts can be created for an external vendor, you must configure the vendor account so that vendor can use vendor collaboration. On the **Vendors** page, on the **General** tab, set the **Collaboration activation** field. The following options are available:

- **Active (PO is auto-confirmed)** – POs are automatically confirmed if the vendor accepts them without changes.
- **Active (PO is not auto-confirmed)** – Your organization must manually confirm POs after the vendor has accepted them.

### Specifying whether the vendor should see price information

To share price information for POs via the vendor collaboration interface, you must set the **Purchase order prices/amount** option on the **Purchase order defaults** tab for the vendor account to **Yes**. This price information includes the unit price, discounts, and charges.

## Working with POs when vendor collaboration is used

### Sending a PO to a vendor

POs are prepared in Supply Chain Management. When a PO has a status of **Approved**, you send it to the vendor by selecting **Send for confirmation** on the **Purchase order** page. The PO status is then changed to **In External Review**. After the PO has been sent, the vendor can see it on the **Purchase orders for review** page in the vendor collaboration interface. The vendor can then accept the PO, reject it, or suggest changes to it. The vendor can also add comments to communicate information such as changes to the PO. If you want to draw the vendor's attention to a new PO, you can also use the Print management system to send the PO by email.

### Confirmation and acceptance of a PO by a vendor

After a vendor accepts a PO, the PO can be automatically confirmed, or it might have to be manually confirmed. The behavior depends on whether the **Collaboration activation** field is set to **Active (PO is auto-confirmed)** or **Active (PO is not auto-confirmed)** for the vendor.

The following table shows the typical exchange of information, depending on the vendor's response when you send a PO for confirmation.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr>
<th>Vendor response</th>
<th>Result</th>
</tr>
</thead>
<tbody>
<tr class="even">
<td>The vendor <strong>accepts</strong> the order, and Supply Chain Management is configured to automatically confirm POs that the vendor accepts.</td>
<td>The status of the order is updated to <strong>Confirmed</strong>. If the order can&#39;t be updated for some reason, the vendor response is still recorded as <strong>Accepted</strong>, but the status of the PO remains <strong>In External Review</strong>. 

The PO that was sent to the vendor and that has a status of <strong>In External Review</strong> is updated with confirmed delivery dates on the lines. This update initiates a new version that is automatically set to <strong>Confirmed</strong> status. When the PO is confirmed, it appears in the vendor collaboration interface.</td>
</tr>
<tr class="odd">
<td>The vendor <strong>accepts</strong> the order, but Supply Chain Management isn&#39;t configured to automatically confirm POs that the vendor accepts.</td>
<td>The vendor response is recorded as <strong>Accepted</strong>, but the status of the PO remains <strong>In External Review</strong>.

The PO that was sent to the vendor and that has a status of <strong>In External Review</strong> is updated with confirmed delivery dates on the lines. This update initiates a new version that is automatically set to <strong>In External Review</strong> status. You can then manually confirm the PO.</td>
</tr>
<tr class="even">
<td>The vendor <strong>rejects</strong> the order.</td>
<td>The vendor response is recorded as <strong>Rejected</strong>, and the status of the PO remains <strong>In External Review</strong>. The rejection is received together with the vendor&#39;s note.</td>
</tr>
<tr class="odd">
<td>The vendor <strong>accepts</strong> the order <strong>with changes</strong>. Changes are suggested at the line level. The vendor can accept or reject individual lines. Here are some other changes that the vendor can suggest:
<ul>
<li>Change dates or quantities.</li>
<li>Split lines for different delivery dates or quantities.</li>
<li>Substitute an item.</li>
</ul>
The vendor can&#39;t change price information and charges. However, the vendor can suggest these changes by using notes.</td>
<td>The vendor response is recorded as <strong>Accepted with changes</strong>, and the status of the PO remains <strong>In External Review</strong>. The statuses show the types of changes that the vendor has suggested. For information about the automatic consumption of changes, see the &quot;Update the PO when a vendor suggests changes&quot; section later in this topic. </td>
</tr>
</tbody>
</table>

You can use the **Purchase order preparation** workspace to monitor which POs the vendor has responded to. This workspace contains two lists that contain POs that have a status of **In External Review**:

- In external review requires action
- In external review awaiting vendor response

### Changing a PO

To change a PO that a vendor has already responded to, you must send the vendor a new version of the PO. The new PO will have a version suffix to indicate that it's a modified version of a PO that was previously sent. The **Purchase order vendor confirmation history** page lets you and your vendors track the history of each order. The previously confirmed version of a PO remains in the list of confirmed POs until the new PO has been confirmed.

### Canceling a PO

When you cancel a PO, the status is changed to **Approved**. You must send the PO back to the vendor, so that the vendor can confirm or reject the cancellation. After the cancellation is confirmed, the PO appears in the vendor's list of confirmed POs as **Cancelled**.

### Adding attachments to a PO

You can add attachments such as files, images, and notes to the PO by using the document management system. Attachments of the **External** type will be visible to the vendor when you send the PO.

## Updating a PO when a vendor suggests changes

If a vendor has responded to a PO and suggested changes, the next step is to process the response.

In the **Purchase order preparation** workspace, in the **In external review requires action** list, you can identify POs that a vendor has accepted with changes. From this list, you can also navigate to the vendor's response.

On a response, a vendor can change the following information on the header:
 
- Vendor document reference
- Mode of delivery
- Delivery terms
- Confirmed delivery date

The vendor can also add a note or attachment.

On the lines, the vendor can change the quantity and the delivery dates, add notes and attachments, reject a line, substitute a line with another product that is entered as text, and split a line into multiple deliveries. The status of a line varies, depending on the changes that the vendor has suggested:
	
- **Accepted with changes**
- **Rejected**
- **Substituted** – In this case, an extra line is added that has a status of **Substitute**.
- **Confirmed**
- **Split into schedule** – In this case, extra lines are added that have a status of **Schedule lines**.

If a line has no changes, the line status is **Accepted**.

On the response, the line statuses tell you the types of changes that the vendor made. Additionally, all fields that were changed appear bold to help you identify the changes.

You can update a PO by selecting **Process PO update** on the response or on one line at a time. An **Is PO update processed?** field on the header and the lines indicates whether the system has processed the header or lines to update the PO with changes that originate from the response. You can run the **Process PO update** action only one time per header or line.

Not all suggested changes can be updated on a PO. Only updates on the header, and updates of dates and quantities on lines, can be automatically updated on the PO. For other changes, you must manually update the PO. In this case, the value of the **Is PO update processed?** field is **Manual update**. For example, if a vendor suggests that a line be split into a schedule, this change must be made manually.

Every line that has a status of **Accepted** will have a confirmed delivery date. When you run the **Process PO update** action, this date is updated on the PO. Notes and attachments aren't automatically transferred to the current PO. Additionally, trade agreements aren't reassessed on the PO lines when you update the current PO via the **Process PO update** action.

## PO statuses and versions

This section describes the various statuses that a PO can have up to the time when it's confirmed. It also describes when new versions of a PO are made available to the vendor. The behavior varies, depending on whether you use change management for POs. 

### Versions and statuses if you don't use change management

The following table shows an example of the changes in status and version that a PO might go through.

| Action | Status and version |
|--------|--------------------|
| The initial version of the PO is created in Supply Chain Management. | The status is **Approved**. |
| The PO is sent to the vendor. | A version is registered in the vendor collaboration interface, and the status is changed to **In External Review**. |
| The vendor sends an **Accepted with changes** response. | The status is still **In External review**. |
| You make some changes that the vendor requested. | The state is changed to **Approved**. |
| You send the new version of the PO to the vendor. | A new version is registered in the vendor collaboration interface, and the status is changed to **In External Review**. |
| The vendor accepts the new version of the PO. | The status is still **In External Review**, unless the vendor account is configured to automatically set POs to **Confirmed** status when the vendor accepts them. |

Vendors don't have to confirm a PO by using the vendor collaboration interface. They can also send an email or communicate their acceptance of a PO via other channels. You can then manually confirm the order. In this case, you receive a warning that states that the order is being confirmed even though there is no response from the vendor. The PO then appears in the confirmation history as an open confirmed order that doesn't have any responses. At this point, the vendor no longer has the option to confirm or reject the PO.

> [!NOTE]
> The version of the PO that is available to other processes in Supply Chain Management is always the latest version, even if that version hasn't yet been registered in the vendor collaboration interface.

### Versions and statuses if you use change management

If change management is enabled for POs, POs go through an approval workflow to reach the **Approved** status. This process isn't visible to the vendor.

The following table shows an example of the changes in status and version that a PO might go through when change management is turned on. A version is registered when the PO is approved, not when the PO is sent to the vendor or confirmed.

| Action | Status and version |
|--------|--------------------|
| The initial version of the PO is created in Supply Chain Management. | The status is **Draft**. |
| The PO is submitted to the approval process. (The approval process is an internal process that the vendor isn't involved in.) | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn't rejected during the approval process. The approved PO is registered as a version. | 
| The PO is sent to the vendor. | The version is registered in the vendor collaboration interface, and the status is changed to **In External Review**. |
| You make some changes that the vendor requested, either manually or by using the **Process PO update** action on the response to update the PO. | The status is changed back to **Draft**. |
| The PO is submitted to the approval process again. | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn't rejected during the approval process. Alternatively, the system can be configured so that specific field changes don't require re-approval. In this case, the status is first changed to **Draft** and is then automatically updated to **Approved**. The approved PO is registered as a new version. |
| You send the new version of the PO to the vendor. | The new version is registered in the vendor collaboration interface, and the status is changed to **In External Review**. |
| The vendor approves the new version of the PO. | The status is changed to **Confirmed**, either automatically, or when you receive the response from the vendor and then confirm the PO. |

## Sharing information about consignment inventory

If you're using consignment inventory, vendors can use the vendor collaboration interface to view information on the following pages:

- **Purchase orders consuming consignment inventory** – POs for consignment inventory are generated when the ownership of the inventory is changed from the vendor to your company. A product receipt is posted at the same time. These consignment POs are shown only on the **Purchase orders consuming consignment inventory** page. They aren't included on the **All confirmed purchase orders** page in the **Vendor collaboration** module.
- **Products received from consignment inventory** – This page lists all the transactions where the ownership of products has been transferred from the vendor to your company. Vendors can use this information to invoice the customer.
- **On-hand consignment inventory** – This page shows the vendor-owned on-hand consignment inventory that has been received at your warehouse.

## Working with RFQs when you use vendor collaboration

This section describes the interactions between customers and vendors during the RFQ process. It also explains how information is communicated to the vendors. 
For a basic overview of support for the RFQ process, see [Requests for quotation (RFQs) overview](request-quotations.md).

### Alternates, attachments, amendments, and returns

- **Alternates** – On the header of an RFQ case, you can specify that alternates are allowed for non-catalog item lines. When alternates are enabled, vendors can add an alternate line for each requested line.
- **Attachments** – Attachments can be added at both the header level and the line level of an RFQ case. Attachments can be classified as either internal or external. Internal attachments can be viewed only on the customer side, whereas vendors can view external attachments after they are sent.

    Vendors can also add attachments on their bid reply. These attachments can be viewed on the customer side after a vendor submits the bid reply. Attachments that vendors add are always classified as external. To access an attachment that a vendor has submitted together with a bid, select **Bid attachments** or **Bid line attachments**.
    
    To open attachments that were sent together with the RFQ case, use the document handling paper clip symbol on the reply.

- **Amendments** – When an amendment is finalized, the existing bid replies are removed so that they can be replaced by updated values. Information such as the line price and quantity from previous bid replies can be viewed via the journals on the RFQ case.

    To enforce amendment processing, on the **Procurement and sourcing parameters** page, on the **Request for quotations** FastTab, set the **Lock RFQs when they are sent** option to **Yes**. (This option is set and required for Public sector.)

- **Returns** – If a vendor has submitted a bid, but more or modified information is required for the RFQ case, the customer can return the bid to the vendor. The data from the bid that was previously submitted is retained, and the vendor can make the requested modifications without having to restart the bid process.

## Public sector extensions

For Public sector, the extended functionality enables an RFQ case to be sent to vendors and published. When you publish an RFQ, anyone who requests the information can view the work that complies with most public-sector regulations. All available work is reflected on the **Open published requests for quotations** list page, and the canceled, pending, or awarded RFQs can be viewed on the **Closed published requests for quotations** list page. These documents can also be viewed on a site outside Supply Chain Management through integrations with the following data entities:

- Published requests for quotations
- Published requests for quotations line
- Published requests for quotations header attachments

These entities let people who aren't provisioned users in Supply Chain Management, but who have anonymous access to the external site, view the available and closed work. Additionally, extended functionality in **Send and publish** lets the user who sets up parameters for the RFQ process define an email template. Then, when the procurement professional creates the RFQ case, they must select the email template to send the required information to the vendors on the RFQ case. 

The user who sets up parameters for the RFQ process can create multiple email templates. These email templates can contain both static text and the following replacement tokens. The tokens will be replaced with contextual values when an email is created.

- %RFQCase%
- %RFQCaseName%
- %bidType%
- %inviteOnly%
- %expiryDateTime%
- %requester%
- %requestingDepartment%
- %accountnum%
- %todaysdate%
- %createddate%

If an amendment is required and is sent after the RFQ is sent, the RFQ will be resent to all invited vendors. The published document will also be updated on the **Open published requests for quotations** page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]