---
# required metadata

title: Vendor collaboration with customers
description: This topic describes how you can use vendor collaboration in Dynamics 365 for Operations to work with POs and to monitor consignment inventory.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-10-31 15 - 54 - 44
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ConsignmentProductReceiptLines, ConsignmentVendorPortalOnHand, PurchVendorPortalConfirmedOrders, PurchVendorPortalOriginalOrder, PurchVendorPortalResponsesHistoryList, PurchVendorPortalResponsesPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 221234
ms.assetid: 4a27c035-5d43-498b-8a9f-a2b8c6ca543a
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.dyn365.ops.intro: Nov-16
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration with customers

This topic describes how you can use vendor collaboration in Dynamics 365 for Operations to work with POs and to monitor consignment inventory.

This topic describes how you can use vendor collaboration to work with customers in Microsoft Dynamics 365 for Operations. It includes information about how to monitor and respond to purchase orders, and how to monitor consignment inventory. It's also possible to use vendor collaboration to work with invoices. For more information, see [Vendor collaboration invoicing workspace](vendor-portal-invoicing-workspace.md).

## Working with purchase orders
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


See also
--------

[Manage vendor collaboration users](manage-vendor-collaboration-users.md)

