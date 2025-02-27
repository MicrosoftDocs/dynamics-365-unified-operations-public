---
title: Vendor invoice journal creation when discarding freight bills
description: Learn about the vendor invoice journal creation when discarding freight bills.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 02/27/2025
ms.reviewer: twheeloc
ms.search.form: TMSAuditMaster, TMSFreightBillInvoiceReconcile, TMSFreightBillSummary, TMSFreightBillType, TMSFreightMatchReason, TMSFBDetailReconcile, TMSInvoiceTable,TMSInvoiceLineReconcile,TMSReconcileInvoice, TMSFreightBillDetail, TMSFreightBillTypeAssignment, TMSRejectInvoiceLine, TMSMiscellaneousCharge
---

# Vendor invoice journal creation when discarding freight bills

This article provides resolutions on how to create vendor invoice journals when discarding freight bills used in Microsoft Dynamics 365 Supply Chain Management.

Starting from [Dynamics 365 Supply Chain Management version 10.0.42](/dynamics365/supply-chain/get-started/whats-new-scm-10-0-42), you can use the **Freight bill discard vendor invoice journal creation policy** parameter in the **Transportation management parameters** page to control when are the vendor invoice journals created. The default option (*Only for reconciliation reasons with pay the freight vendor*) is that the journals will only be created for reconciliation reasons with pay the freight vendor enabled.

## How to setup vendor invoice journal creation policy to always create the journals

1. Navigate to the **Transportation management parameters** page by selecting **Transportation management** > **Setup** > **Transportation management parameters**.
1. Select the **General** tab.
1. Expand the **Vendor invoice** fast tab.
1. Select the *Always* option in the **Freight bill discard vendor invoice journal creation policy** parameter.
1. Save the changes.