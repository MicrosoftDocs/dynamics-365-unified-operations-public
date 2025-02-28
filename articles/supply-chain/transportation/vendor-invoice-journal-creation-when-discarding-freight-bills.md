---
title: Vendor invoice journal creation when discarding freight bills
description: Learn how to discard a freight bill when creating a vendor invoice journal.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 02/27/2025
ms.reviewer: twheeloc
ms.search.form: TMSAuditMaster, TMSFreightBillInvoiceReconcile, TMSFreightBillSummary, TMSFreightBillType, TMSFreightMatchReason, TMSFBDetailReconcile, TMSInvoiceTable,TMSInvoiceLineReconcile,TMSReconcileInvoice, TMSFreightBillDetail, TMSFreightBillTypeAssignment, TMSRejectInvoiceLine, TMSMiscellaneousCharge
---

# Vendor invoice journal creation when discarding freight bills

This article provides guidance on how to create vendor invoice journals when discarding freight bills used in Microsoft Dynamics 365 Supply Chain Management.

Beginning in Dynamics 365 Supply Chain Management version 10.0.42, you can use the **Freight bill discard vendor invoice journal creation policy** parameter in the **Transportation management parameters** page to control when are the vendor invoice journals created. The default option (*Only for reconciliation reasons with pay the freight vendor*) is the journals are only created for reconciliation reasons when pay the freight vendor enabled.

## How to set up vendor invoice journal creation policy to always create journals

1. Go to **Transportation management** > **Setup** > **Transportation management parameters**.
1. Select the **General** tab.
1. Expand the **Vendor invoice** FastTab.
1. In the **Freight bill discard vendor invoice journal creation policy** parameter, select **Always**. 
1. Save the changes.
