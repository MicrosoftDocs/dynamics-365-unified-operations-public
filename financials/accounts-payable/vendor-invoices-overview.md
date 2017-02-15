---
# required metadata

title: Vendor invoices overview
description: This article provides general information about vendor invoices. Vendor invoices are requests for payment for products and services that were received. Vendor invoices can represent a bill for ongoing services, or they can be based on purchase orders for specific items and services. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23 - 02 - 27
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 13971
ms.assetid: b4b4bc0c-4378-480e-9a44-4aab51d34a45
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Vendor invoices overview

This article provides general information about vendor invoices. Vendor invoices are requests for payment for products and services that were received. Vendor invoices can represent a bill for ongoing services, or they can be based on purchase orders for specific items and services. 

Vendor invoices
---------------

A vendor invoice from a purchase order is an invoice that is produced when products or services are received according to a purchase order that was placed with a vendor. The vendor invoice contains a header, and one or more lines for items or services. A vendor invoice completes the cycle from purchase order to product receipt to vendor invoice. Although some vendor invoices are connected to a purchase order, vendor invoices can also contain lines that don't correspond to purchase order lines. You can also create vendor invoices that aren't associated with any purchase order. These vendor invoices might represent ongoing services, such as a utility bill, and you don't have to reference a purchase order when you add them. There are several ways to enter a vendor invoice:

-   The vendor invoice register lets you quickly enter invoices that don't reference a purchase order, so that you can accrue the expense. By using the vendor invoice approval journal, you can select those invoices and post them to the vendor balance to reverse the accrual.
-   The vendor invoice journal lets you quickly enter invoices that don't reference a purchase order, in a single step.
-   Together with the vendor invoice pool, the vendor invoice register lets you quickly enter invoices to accrue the expense. You can open the associated purchase orders later to post the invoice against the expense account.
-   The **Open vendor invoices** and **Pending vendor invoices** pages let you create vendor invoices from confirmed purchase orders.

The following discussion provide more information about how to use the **Open vendor invoices** or **Pending vendor invoices** page to create a vendor invoice from a purchase order.

## Understanding invoice line quantities
When you open a vendor invoice from a related purchase order, invoice lines are created from the purchase order. By default, the quantities are taken from the product receipt quantity. However, you can use any of the following default behaviors:

-   **Receive now quantity** – Use this option for partial shipments. The default value in the **Quantity** field is taken from the **Receive now** quantity field on the purchase order.
-   **Ordered quantity** – Use this option for complete shipments. The default value in the **Quantity** field is taken from the **Ordered** quantity field on the purchase order.
-   **Registered quantity** – Use this option if the item requires registration, as specified on the **Item model groups** page. The default value in the **Quantity** field is the physical update quantity that has been registered.
-   **Product receipt quantity** – Use this option if a product receipt has already been received for the order. The default value in the **Quantity** field is taken from the total quantity of available product receipts.
-   **Registered quantity and services** – Use this option if quantities have been registered in arrival journals for stocked items or items that aren't stocked. This option also includes services, regardless of whether they are registered.

If your legal entity uses invoice matching, you can view the results of the quantity matching in the **Product receipt quantity match** column. You can also use the **Matching details** menu command on the **Review** tab to view the results of the quantity matching.

## Adding a line that wasn't on the purchase order
You can add a new line that wasn't on the purchase order to the vendor invoice. You must select an item number or procurement category. You can then add quantities, prices, and amounts to the line. The line will be included only in matching policies for invoice totals.

## Submitting a vendor invoice for review
Your organization might use workflows to manage the review process for vendor invoices. Workflow review can be required for the invoice header, the invoice line, or both. The workflow controls apply to the header or the line, depending on where the focus is when you click the control. Instead of the **Post** button, you will see a **Submit** button that you can use to send the vendor invoice through the review process.

## Matching vendor invoices to product receipts
You can enter and save information for vendor invoices, and you can match invoice lines to product receipt lines. You can also match partial quantities for a line. You can create a vendor invoice that is based on the product receipt line items that have been received to date, even if all the items for a particular purchase order haven't yet been received. For example, you might use this option if a vendor sends one invoice per month that covers all the deliveries that the vendor shipped during that month. Each product receipt represents a partial or complete delivery of the items on the purchase order. When you post the invoice, the **Invoice remainder** quantity for each item is updated with the total of the received quantities from the selected product receipts. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the purchase order are 0 (zero), the status of the purchase order is changed to **Invoiced**. If the **Invoice remainder** quantity isn't 0, the status of the purchase order remains unchanged, and additional invoices can be entered for it. This option assumes that at least one product receipt has been posted for the purchase order. The vendor invoice is based on these product receipts and reflects the quantities from them. The financial information for the invoice is based on the information that is entered when you post the invoice.

## Working with multiple invoices
You can work with multiple invoices at the same time and post them all at the same time. If you must create multiple invoices, use the **Pending vendor invoices** page. If you must post and print multiple vendor invoices, use the invoice approval journal page. If you're using the invoice approval journal, at least one product receipt must be posted for the purchase order, and an invoice for the purchase order must be posted in an invoice register. The financial information for the invoice comes from the invoice that was posted in the register.

See also
--------

[Enter and post invoices in the invoice journal](http://ax.help.dynamics.com/en/wiki/record-a-vendor-invoice-in-the-invoice-journal/)

[Enter and post invoices in the Invoice register form and invoice pool](http://ax.help.dynamics.com/en/wiki/key-invoice-data-in-ap-system-using-invoice-pool/)

[Enter and post invoice in the Invoice register using the approval journal](http://ax.help.dynamics.com/en/wiki/key-invoice-data-in-ap-system-using-invoice-register/)

