---
# required metadata

title: Vendor collaboration invoicing workspace
description: This article explains how you can view vendor invoices and submit invoices from the vendor collaboration invoicing workspace.
author: abruer
ms.date: 01/15/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendInvoiceWorkspace 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 221534
ms.assetid: c4ed62f3-d351-41d7-a2ad-790576cde4ab
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration invoicing workspace

[!include [banner](../includes/banner.md)]

This article explains how you can view vendor invoices and submit invoices from the **Vendor collaboration invoicing** workspace.

The **Vendor collaboration invoicing** workspace can be used to view vendor invoice information and to submit invoices to the system using workflow capabilities.


## Vendor collaboration invoicing workspace

### Summary tiles

The **Summary** tiles give an overview of the invoices for the selected vendor. You can view invoices by their state.

- Draft invoices haven't been submitted to workflow.
- Submitted, not approved invoices are those invoices that the vendor has submitted, but they haven't been posted in the application.
- Approved, not paid invoices are those that have been posted, but they haven't yet been fully paid.
- Paid invoices are those that have been fully paid in the application.

Selecting a tile will open a filtered view of the **Invoices list** page.

### Tabular lists

In the **Tabular lists** section, the status of the invoicing is broken down in similar ways as the summary tiles: **Draft** and **Submitted**, **Not approved** lists. While in the **Draft** state, an invoice can be submitted to workflow or deleted. The last tabular list is an option to find invoices. You can filter as you search, to allow for faster searches.

### All vendor invoices list page

You can view all posted and unposted vendor invoices on the **Vendor collaboration invoices** list page. You can use this list page to view the payment status of the invoices. The payment statuses include **Unposted**, **Unpaid**, **Partially paid**, and **Fully paid**.

#### Creating a new invoice from a purchase order

You can create a new vendor invoice by selecting **New** in the **Vendor collaboration invoicing** workspace.

The confirmation dialog box will prompt you for the following information:

- Purchase order (PO) number
- Invoice number

    > [!NOTE]
    > The invoice number must be provided by the vendor.

- Invoice date
- Invoice description

If the vendor provides the PO number, the invoice will be associated with the PO. By default, all the lines from the vendor's PO will appear on the new invoice. You can edit the quantity and cost information before you submit the vendor invoice to the workflow system. In addition, you can attach files, notes, images, and URLs to an invoice before you submit it.

If the vendor doesn't provide the PO number, the invoice will be considered a non-PO invoice. Vendors can create non-PO invoices based on the items that have procurement categories that have been granted.

For more information, see [Vendor collaboration with external vendors](../../supply-chain/procurement/vendor-collaboration-work-external-vendors.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
