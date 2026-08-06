---
title: Vendor collaboration invoicing workspace
description: Learn about how you can view vendor invoices and submit invoices from the vendor collaboration invoicing workspace.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: VendInvoiceWorkspace 
ms.dyn365.ops.version: Version 1611
ms.assetid: c4ed62f3-d351-41d7-a2ad-790576cde4ab
---

# Vendor collaboration invoicing workspace

[!include [banner](../includes/banner.md)]

This article explains how you can view vendor invoices and submit invoices from the **Vendor collaboration invoicing** workspace.

Use the **Vendor collaboration invoicing** workspace to view vendor invoice information and to submit invoices to the system by using workflow capabilities.

## Vendor collaboration invoicing workspace

### Summary tiles

The **Summary** tiles give an overview of the invoices for the selected vendor. You can view invoices by their state.

- Draft invoices aren't submitted to workflow.
- Submitted, but not approved, invoices are those invoices that the vendor submits, but the application doesn't post.
- Approved, but not paid, invoices are those invoices that the application posts, but aren't yet fully paid.
- Paid invoices are those that are fully paid in the application.

Selecting a tile opens a filtered view of the **Invoices list** page.

### Tabular lists

In the **Tabular lists** section, the status of the invoicing is broken down in similar ways as the summary tiles: **Draft** and **Submitted**, **Not approved** lists. While in the **Draft** state, you can submit an invoice to workflow or delete it. The last tabular list is an option to find invoices. You can filter as you search, to allow for faster searches.

### All vendor invoices list page

You can view all posted and unposted vendor invoices on the **Vendor collaboration invoices** list page. Use this list page to check the payment status of the invoices. The payment statuses include **Unposted**, **Unpaid**, **Partially paid**, and **Fully paid**.

#### Creating a new invoice from a purchase order

Create a new vendor invoice by selecting **New** in the **Vendor collaboration invoicing** workspace.

The confirmation dialog box prompts you for the following information:

- Purchase order (PO) number
- Invoice number

    > [!NOTE]
    > The vendor provides the invoice number.

- Invoice date
- Invoice description

If the vendor provides the PO number, the invoice associates with the PO. By default, all the lines from the vendor's PO appear on the new invoice. You can edit the quantity and cost information before you submit the vendor invoice to the workflow system. In addition, you can attach files, notes, images, and URLs to an invoice before you submit it.

If the vendor doesn't provide the PO number, the invoice is a non-PO invoice. Vendors can create non-PO invoices based on the items that have procurement categories that are granted.

For more information, see [Vendor collaboration with external vendors](../../supply-chain/procurement/vendor-collaboration-work-external-vendors.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
