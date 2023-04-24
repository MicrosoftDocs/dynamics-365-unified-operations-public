--- 
# required metadata 
 
title: Reconcile freight manually
description: This procedure shows how to reconcile freight manually. 
author: Weijiesa
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSLoadPlanningWorkbench, TMSFreightBillDetail, TMSInvoiceTable, TMSFreightBillInvoiceReconcile, TMSInvoiceJournal, LedgerJournalTable, LedgerJournalTransDaily, TMSFBDetailReconcile
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Reconcile freight manually

[!include [banner](../../includes/banner.md)]

This procedure shows how to reconcile freight manually. This is typically done by a transportation coordinator. You can use this procedure in the USMF demo data company.

## Select a load to reconcile

1. Go to **Transportation management \> Planning \> Load planning workbench**.
2. Clear the **Hide shipped and received** checkbox.
3. In the list, select the load that has load ID *00006*.

## Create a carrier invoice

If you manually reconcile freight and don't automatically receive carrier invoices, you can create an invoice based on the freight bill.

1. Select **Related information**.
2. Select **Freight bill details**.
3. Select **Generate freight bill invoice**.
4. In the **Invoice** field, enter a value.
5. Select **OK**.

## Reconcile the invoice

When you reconcile a carrier invoice and a freight bill, the reconciliation is done line by line.

1. Select **Match freight bills and invoices**.
2. Expand the **Invoice details** section.
3. Expand the **Unmatched freight bill details** section.
4. In the list, mark the selected row.
5. Select **Match**.
6. Expand the **Matched freight bill details** section.

## Submit the invoice for approval

1. Select **Submit for approval**.
2. Close the page.
3. Clear the **Hide approved** checkbox.
4. Select **Vendor invoice journals**.
5. In the **Reference journal number** field, select the link.
6. Select **Lines**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
