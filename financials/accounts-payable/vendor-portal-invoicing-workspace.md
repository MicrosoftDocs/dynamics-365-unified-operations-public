---
# required metadata

title: Vendor collaboration invoicing workspace
description: This topic explains how you can view vendor invoices and submit invoices from the vendor collaboration invoicing workspace.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221534
ms.assetid: c4ed62f3-d351-41d7-a2ad-790576cde4ab
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Vendor collaboration invoicing workspace

[!include[banner](../includes/banner.md)]


This topic explains how you can view vendor invoices and submit invoices from the vendor collaboration invoicing workspace.

The **Vendor collaboration invoicing** workspace can be used to view vendor invoice information and to submit invoices to Microsoft Dynamics 365 for Operations using workflow capabilities.
Vendor collaboration invoicing workspace
----------------------------------------

### Summary tiles

The **Summary** tiles give an overview of the invoices for the selected vendor. You can view invoices by their state.
-   Draft invoices have not been submitted to workflow.
-   Submitted, not approved invoices are those invoices that the vendor has submitted, but they have not been posted in Dynamics 365 for Operations.
-   Approved, not paid invoices are those that have been posted in Dynamics 365 for Operations, but they have not yet been fully paid.
-   Paid invoices are those that have been fully paid in Dynamics 365 for Operations.

Clicking on a tile will open a filtered view of the **Invoices list** page.
### Tabular lists

In the **Tabular lists** section, the status of the invoicing is broken down in similar ways as the summary tiles: Draft and Submitted, not approved lists. While in the Draft state, an invoice can be submitted to workflow or deleted. The last tabular list is an option to find invoices. You can filter as you search, to allow for faster searches.
All vendor invoices list page
-----------------------------

You can view all posted and unposted vendor invoices on the **Vendor collaboration invoices** list page. You can use this list page to view the payment status of the invoices. The payment statuses include Unposted, Unpaid, Partially paid, and Fully paid.
Creating a new invoice from a purchase order
--------------------------------------------

You can create a new vendor invoice by selecting the **New** action on the **Vendor collaboration invoicing** workspace. The purchase order number and invoice number must be provided by the vendor. By default, all of the lines from the vendor's purchase order will appear on the new invoice. The quantity and cost information can be edited prior to submitting the vendor invoice to workflow. You can attach files, notes, images, and URLs to an invoice before submitting it.



For more information, see [Collaborating with vendors by using the Vendor portal](/dynamics365/operations/supply-chain/procurement/collaborate-vendors-vendor-portal)


