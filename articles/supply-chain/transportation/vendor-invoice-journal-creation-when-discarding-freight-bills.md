---
title: Vendor invoice journal creation when discarding freight bills
description: Learn how to create vendor invoice journals when you discard freight bills.
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 03/03/2025
ms.reviewer: twheeloc
ms.search.form: TMSAuditMaster, TMSFreightBillInvoiceReconcile, TMSFreightBillSummary, TMSFreightBillType, TMSFreightMatchReason, TMSFBDetailReconcile, TMSInvoiceTable,TMSInvoiceLineReconcile,TMSReconcileInvoice, TMSFreightBillDetail, TMSFreightBillTypeAssignment, TMSRejectInvoiceLine, TMSMiscellaneousCharge
---

# Vendor invoice journal creation when discarding freight bills

This article provides guidance about how to create vendor invoice journals when you discard freight bills that are used in Microsoft Dynamics 365 Supply Chain Management.

As of Supply Chain Management version 10.0.42, you can use the **Freight bill discard vendor invoice journal creation policy** field on the **Transportation management parameters** page to control when vendor invoice journals are created. The default setting, *Only for reconciliation reasons with pay the freight vendor*, creates journals only for reconciliation reasons when functionality for paying the freight vendor is enabled.

## Set up the vendor invoice journal creation policy to always create journals

1. Go to **Transportation management** \> **Setup** \> **Transportation management parameters**.
1. On the **General** tab, on the **Vendor invoice** FastTab, in the **Freight bill discard vendor invoice journal creation policy** field, select *Always*.
1. Save your changes.
