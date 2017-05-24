---
# required metadata

title: Vendor collaboration with external vendors
description: This topic describes how purchasing agents can collaborate with external vendors to exchange information about purchase orders and consignment inventory.
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221264
ms.assetid: dde49743-1541-4353-a030-63ca3069cd7d
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration with external vendors

[!include[banner](../includes/banner.md)]


This topic describes how purchasing agents can collaborate with external vendors to exchange information about purchase orders and consignment inventory.

The **Vendor collaboration** module is targeted at vendors who don’t have electronic data interchange (EDI) integration with Microsoft Dynamics 365 for Operations. It allows vendors to work with purchase order, invoice, and consignment inventory information. This topic describes how you can collaborate with external vendors who are using the vendor collaboration interface to work with POs and consignment inventory. It also describes how to enable a specific vendor to use vendor collaboration, and how to define the information that all vendors will see when they respond to a PO. For more information about what external vendors can do in the vendor collaboration interface, see [Vendor collaboration with customers](vendor-collaboration-work-customers-dynamics-365-operations.md).  

For more information about how vendors can use vendor collaboration in invoicing processes, see [Vendor collaboration invoicing workspace](/dynamics365/operations/financials/accounts-payable/vendor-portal-invoicing-workspace). For information about how to provision new vendor collaboration users, see [Manage vendor collaboration users](manage-vendor-collaboration-users.md).

## Define the information shown to vendors when they respond to POs
When vendors respond to a PO that you send them, they see a dialog box where they need to confirm that they want to accept, reject, or accept the PO with changes. The information that needs to be shown to the vendor at that point may be specific for your business, so you can specify the text that will show on each of the three confirmation messages. For example, the text could inform the vendor about the next steps in the process, or about terms and conditions.  

To define the text that's shown in the PO response:

1.  Open the **Information for vendors responding to POs** page.
2.  Select one of the response types.
3.  Click **Edit.**
4.  Enter the information that you want vendors to see in the **Information message** box.

If you need to add messages in more than one language, create separate messages with the appropriate language codes. The vendor will be shown the message in the language that they use.

## Set the vendor collaboration options for a specific vendor
The general settings for vendor collaboration in Dynamics 365 for Operations are configured by an administrator. For example, they'll determine which security roles are available for all the vendors that you collaborate with. There are also some settings which can differ for each vendor account, and you should set these:

-   Enable vendor collaboration.
-   Decide whether you want vendor to see price information.

### Enable vendor collaboration

Before user accounts can be created for an external vendor, you must configure the vendor account to allow them to use vendor collaboration. To do this, set the **Collaboration activation** field to active on the **General** tab on the **Vendors** page. There are two options that you can choose:

-   **Active (PO is auto-confirmed)** - Purchase orders are automatically confirmed when the vendor accepts them without changes.
-   **Active (PO is not auto-confirmed)** - Purchase orders need to be manually confirmed by your organization, after the vendor has accepted them.

### Decide whether you want the vendor to see price information

If you want to share price information such as unit price, discounts, and charges via the collaboration interface, you need to set the **Purchase order prices/amount** option to **Yes** on the vendor account. This option is available on the **Purchase order defaults** tab.

## Work with POs when using vendor collaboration
### Sending a PO to the vendor

Purchase orders are prepared in Dynamics 365 for Operations. When the PO has a status of **Approved**, you send it to the vendor using the **Send for confirmation **action on the **Purchase order** page. The PO status changes to **In External Review**. After the PO has been sent, the vendor can see it on the **Purchase orders for review** page in the vendor collaboration interface, where they can accept, reject or suggest changes to the order. The vendor can also add comments to communicate information such as changes to the PO. If you want to draw the vendor’s attention to a new PO, you can also use the print management system to send the PO by email.

### Confirmation and acceptance of the PO by the vendor

When a vendor has accepted a purchase order, the PO may be automatically confirmed, or it may need to be manually confirmed. This depends on whether the **Vendor activation **field is set to **Active (PO is auto-confirmed)** for the vendor, or to **Active (PO is not auto-confirmed)**.  

The following table shows the typical exchange of information, depending on how the vendor responds when you send a PO for confirmation.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Vendor response</strong></td>
<td><strong>Result</strong></td>
</tr>
<tr class="even">
<td>The vendor <strong>accepts</strong> the order. Dynamics 365 for Operations is configured to automatically confirm POs when the vendor accepts.</td>
<td>The status of the order is updated to <strong>Confirmed</strong>. If something prevents the order from being updated, the vendor response is still recorded as <strong>Accepted</strong>, but the status of the PO remains <strong>In External Review</strong>.</td>
</tr>
<tr class="odd">
<td>The vendor <strong>accepts</strong> the order. Dynamics 365 for Operations is not configured to automatically confirm POs when the vendor accepts.</td>
<td>The vendor response is recorded as <strong>Accepted</strong>, but the status of the PO remains <strong>In External Review</strong>.</td>
</tr>
<tr class="even">
<td>The vendor <strong>rejects</strong> the order.</td>
<td>The vendor response is recorded as <strong>Rejected</strong>, and the status of the PO remains <strong>In External Review</strong>. The rejection is received together with the vendors note.</td>
</tr>
<tr class="odd">
<td>The vendor <strong>accepts the order with changes</strong>. Changes are suggested at the line level. It’s possible to accept or reject individual lines. Other possible changes include:
<ul>
<li>Changing dates or quantities.</li>
<li>Splitting lines for different delivery dates or quantities.</li>
<li>Substituting an item.</li>
</ul>
Price information and charges cannot be changed by the vendor. Suggestions for changes to these can be made using notes.</td>
<td>The vendor response is recorded as <strong>Accepted with changes</strong>, <strong></strong> and the status of the PO remains <strong>In External Review</strong>.</td>
</tr>
</tbody>
</table>

You can use the **Purchase order** **preparation** workspace to monitor which POs the vendor has responded to. This workspace contains two lists that contain purchase orders with a status of **In External Review**:

-   In external review requires action.
-   In external review awaiting vendor response.

### Changing a PO

When you need to change a PO that has already been responded to, you'll send a new version of the PO to the vendor. The new PO will have a version suffix to indicate that it’s a modified version of a PO that was previously communicated. The **Purchase order vendor confirmation history** page allows you and your vendors to track the history of each order. The previously confirmed version of the PO remains in the list of confirmed POs until the new PO has been confirmed.

### Cancelling a PO

When you cancel a PO, the status is changed to **Approved**. You must send the PO back to the vendor via the Vendor portal, so that the vendor can confirm or reject the cancellation. After the cancellation is confirmed, the PO appears in the vendor’s list of confirmed POs as **Cancelled**.

### Adding attachments to a PO

You can add attachments such as files, images, and notes to the PO using the document management system. The attachments added with the restriction of type **External** will be visible for the vendor when you send the PO to them.

## Purchase order statuses and versions
This section describes the different statuses that a PO can have up to the time when it's confirmed, and at what point new versions of the PO are made available to the vendor. There are differences in this, depending on whether you use change management for purchase orders. 

### Versions and statuses if you don't use change management

The following table shows an example of the changes in status and version that a PO might go through.

|                                                                          |                                                                                                                                                              |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Action**                                                               | **Status and version**                                                                                                                                       |
| The initial version of the PO is created in Dynamics 365 for Operations. | The status is **Approved**.                                                                                                                                  |
| The PO is sent to the vendor.                                            | A version is registered in the vendor collaboration interface, and the status is changed to **In External Review**.                                          |
| The vendor sends an **Accepted with changes** response.                  | The status is still **In External review**.                                                                                                                  |
| You make some changes that are requested by the vendor.                  | The state is changed to **Approved**.                                                                                                                        |
| You send the new version of the PO to the vendor.                        | A new version is registered in the vendor collaboration interface, and the status is changed to **In External Review**.                                      |
| The vendor accepts the new version of the PO.                            | The status is still **In External Review** unless the vendor account is configured to automatically set the PO to a **Confirmed** state when they accept it. |

Vendors don’t have to confirm the PO using the vendor collaboration interface. They can also send an email message or communicate their acceptance of a PO via other channels. You can then confirm the order manually in Dynamics 365 for Operations. If you do this, you'll receive a warning that the order is being confirmed even though there is no response from the vendor. The PO then appears in the confirmation history as an open confirmed order that doesn’t have any responses. The vendor no longer has the option to confirm or reject the PO.  

**Note:** The version of the PO that is available to other processes in Dynamics 365 for Operations is always the latest version, even if that version hasn’t yet been registered in the vendor collaboration interface.

### Versions and statuses if you use change management

If change management is enabled for POs, the PO goes through an approval workflow to reach the **Approved** status. This process isn’t visible to the vendor.  

The following table shows an example of the changes in status and version that a PO might go through when change management is turned on. The version is registered when the PO is approved, not when the PO is sent to the vendor or confirmed.

|                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Action**                                                                                                    | **Status and version**                                                                                                                                                                                                                                                                                                                                                                      |
| The initial version of the PO is created in Dynamics 365 for Operations.                                      | The status is **Draft**.                                                                                                                                                                                                                                                                                                                                                                    |
| The PO is submitted to the approval process. (This is an internal process that the vendor isn’t involved in.) | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn’t rejected during the approval process. The approved PO is registered as a version.                                                                                                                                                                                                                     |
| The PO is sent to the vendor                                                                                  | The version is registered in the vendor collaboration interface, and the status is changed to **In External Review**.                                                                                                                                                                                                                                                                       |
| You make some changes that are requested by the vendor.                                                       | The status is changed back to **Draft**.                                                                                                                                                                                                                                                                                                                                                    |
| The PO is submitted to the approval process again.                                                            | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn’t rejected during the approval process. Alternatively, the system can be configured so that specific field changes don’t require re-approval. In this case, the status is first changed to **Draft** and is then automatically updated to **Approved**. The approved PO is registered as a new version. |
| You send the new version of the PO to the vendor.                                                             | The new version is registered in the vendor collaboration interface, and the status is changed to **In External Review**.                                                                                                                                                                                                                                                                   |
| The vendor approves the new version of the PO.                                                                | The status is changed to **Confirmed**, either automatically, or when you receive the response from the vendor and then confirm the PO.                                                                                                                                                                                                                                                     |

## Share information about consignment inventory
If you’re using consignment inventory, vendors can use the vendor collaboration interface to view information on the following pages:

-   **Purchase orders consuming consignment inventory** - Purchase orders for consignment inventory are generated when the ownership of the inventory is changed from the vendor to your company. A product receipt is posted at the same time. These consignment purchase orders are only displayed on the **Purchase orders consuming consignment inventory** page. They are not included in the **All confirmed purchase orders** page in the **Vendor collaboration** module.
-   **Products received from consignment inventory** - This page lists all the transactions where the ownership of products has been transferred from the vendor to your company. Vendors can use this information to invoice the customer.
-   **On-hand consignment inventory** - This page shows the vendor owned on-hand consignment inventory that has been received at your warehouse.




