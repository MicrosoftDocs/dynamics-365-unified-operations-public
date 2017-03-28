---
# required metadata

title: Collaborate with vendors by using the Vendor portal
description: This topic describes how purchasing agents can use the Vendor portal to collaborate with external vendors during the purchase order confirmation process. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-01-28 15 - 01 - 22
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: PurchTable, PurchVendorPortalRequests
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 30211
ms.assetid: 3c7e0e1c-703c-4bbf-b90c-84d29a131360
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Collaborate with vendors by using the Vendor portal

This topic describes how purchasing agents can use the Vendor portal to collaborate with external vendors during the purchase order confirmation process. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.

The information in this topic applies only to the February 2016 and May 2016 versions of Dynamics AX. The Vendor portal functionality has been replaced by extended vendor collaboration functionality in Dynamics 365 for Operations version 1611. For more information about the new vendor collaboration functionality, see [Using vendor collaboration to work with external vendors](vendor-collaboration-work-external-vendors.md).  

The Vendor portal is targeted at vendors that don't have electronic data interchange (EDI) integration with Microsoft Dynamics AX for exchanging purchase order (PO) information. The portal lets purchasing agents send a PO to the vendor, and then receive a Confirmed or Rejected response directly in Dynamics AX.  

The process can be configured so that a confirmation from the vendor automatically confirms the order. In this case, follow-up is required only occasionally, when an order is rejected, or if the vendor confirmation is registered as a response but the status of the PO isn't updated to **Confirmed** because of an issue during the confirmation process.

## PO confirmation and rejection
POs are prepared in Dynamics AX. When you have a PO that has a status of **Approved**, you send it to the vendor by generating a confirmation request. If you want to draw the vendor’s attention to a new PO, you can also use the print management system to send the PO by email. The PO appears in the Vendor portal, and includes an option that the vendor can use to confirm or reject it. The vendor can also add comments to communicate information such as changes to the PO.  

In the Vendor portal, the vendor can see order lines. These lines include information such as the external product number, dimensions, price information, quantity, delivery date, and delivery address. The vendor can generate a report that shows the PO information and also the total price. Charges that are relevant to the vendor are shown if the vendor clicks the **Charges** button in the header or on the lines. Vendors can import PO information into their own system by using the **Export to Excel** functionality.  

The following table shows the typical exchange of information, depending on that way that the vendor responds when you send a PO for confirmation.

| Type of response                                                                                                  | Result                                                                                                                                                                                                                                                                                          |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The vendor confirms the order. The system is configured to automatically confirm POs when the vendor confirms.    | The status of the order is updated to **Confirmed**. If something prevents the order from being updated, the vendor response is still recorded as **Confirmed**, but the status of the PO remains **In External Review**.                                                                       |
| The vendor confirms the order. The system isn't configured to automatically confirm POs when the vendor confirms. | The vendor response is recorded as **Confirmed**, but the status of the PO remains **In External Review**.                                                                                                                                                                                      |
| The vendor rejects the order.                                                                                     | The vendor response is recorded as **Rejected**, and the status of the PO remains **In External Review**. The rejection is received together with the reason and a suggestion for change, such as an alternative delivery date. You update the PO and then send a new version for confirmation. |

## Changes to a PO
When you must change a PO that has already been confirmed, you can send a new PO to the vendor via the Vendor portal. The new PO will have a version suffix to indicate that it's a modified version of a PO that was previously communicated. The Vendor portal lets vendors track the history of each order. The previously confirmed version of the PO will remain in the list of confirmed POs until the new PO has been confirmed.  

When you cancel a PO, the status is changed back to **Approved**. You must send the PO back to the vendor via the Vendor portal, so that the vendor can confirm or reject the cancellation. After the cancellation is confirmed, the PO appears in the vendor's list of confirmed POs as **Cancelled**.

## Versions, status transitions, and change management
When a PO is sent to the vendor, it's registered in the system as a specific version of the PO, and the status is changed from **Approved** to **In External Review**. If the PO is changed later, a new version of the PO is created, and the status is changed back to **Approved** (or **Draft**, if change management is turned on).  

The following table shows an example of the changes in status and version that a PO might go through.

| Action                                                   | Status and version                                                                                    |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| The initial version of the PO is created in Dynamics AX. | The status is **Approved**.                                                                           |
| The PO is sent to the Vendor portal.                     | A version is registered in the Vendor portal, and the status is changed to **In External Review**.    |
| You make some changes that are requested by the vendor.  | The state is changed back to **Approved**.                                                            |
| You send the new version of the PO to the Vendor portal. | A new version is registered in the Vendor portal, and the state is changed to **In External Review**. |
| The vendor approves the new version of the PO.           | The state is changed to **Confirmed**.                                                                |

To see the versions of the PO that have been sent to the vendor, and the vendor's responses, click **Journals** &gt; **Confirmation requests** from the PO.  

Orders that have been sent to the vendor for a response, and that have a status of **In External Review**, appear in either the **Purchase orders sent to vendor portal, awaiting response** list or the **Purchase orders sent to vendor portal, response requires action** list. When you change an order that has been sent to the vendor, so that the state is changed back to **Approved**, the order no longer appears in these lists. To see whether there has previously been a response to the order from the vendor, click **Journals** &gt; **Confirmation requests**.  

Vendors don't have to confirm the PO in the Vendor portal. They can also send an email message or communicate their acceptance of a PO via other channels. You can then confirm the order manually in Dynamics AX. In this case, you receive a warning that the order is being confirmed even though there is no response from the vendor. The PO then appears in the confirmation history in the Vendor portal as an open confirmed order that doesn't have any responses. In addition, the vendor no longer has the option to confirm or reject the PO.  

**Note:** The version of the PO that is available to other processes in Dynamics AX is always the latest version, even if that version hasn’t yet been registered.

### Change management

If you've turned on change management for a PO, the PO goes through an approval workflow to reach the **Approved** status. This process isn't visible to the vendor.  

When change management is turned on for a PO, the version is registered when the PO is approved, not when the PO is sent to the vendor or confirmed.  

The following table shows an example of the changes in status and version that a PO might go through when change management is turned on.

| Action                                                                                                        | Status and version                                                                                                                                                                                                                                                                                                                                                                          |
|---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The initial version of the PO is created in Dynamics AX.                                                      | The status is **Draft**.                                                                                                                                                                                                                                                                                                                                                                    |
| The PO is submitted to the approval process. (This is an internal process that the vendor isn't involved in.) | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn't rejected during the approval process. The approved PO is registered as a version.                                                                                                                                                                                                                     |
| The PO is sent to the Vendor portal                                                                           | The version is registered in the Vendor portal, and the status is changed to **In External Review**.                                                                                                                                                                                                                                                                                        |
| You make some changes that are requested by the vendor.                                                       | The status is changed back to **Draft**.                                                                                                                                                                                                                                                                                                                                                    |
| The PO is submitted to the approval process again.                                                            | The status is changed from **Draft** to **In Review** to **Approval** if the PO isn't rejected during the approval process. Alternatively, the system can be configured so that specific field changes don't require re-approval. In this case, the status is first changed to **Draft** and is then automatically updated to **Approved**. The approved PO is registered as a new version. |
| You send the new version of the PO to the Vendor portal.                                                      | The new version is registered in the Vendor portal, and the status is changed to **In External Review**.                                                                                                                                                                                                                                                                                    |
| The vendor approves the new version of the PO.                                                                | The status is changed to **Confirmed**, either automatically, or when you receive the response from the vendor and then confirm the PO.                                                                                                                                                                                                                                                     |
See also
--------

[Configuration of security for vendor collaboration users](configure-security-vendor-portal-users.md)

[Vendor collaboration invoicing workspace](/dynamics365/operations/financials/accounts-payable/vendor-portal-invoicing-workspace)

