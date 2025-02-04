---
title: Set up automatic freight reconciliation
description: Learn how to set up data for automatic freight reconciliation, including a step-by-step process for setting up freight bill types.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSFreightBillType, TMSFreightBillTypeAssignment, TMSCarrierCodeLookup, DefaultDashboard, TMSAuditMaster 
ms.topic: how-to
ms.date: 01/31/2025
ms.custom: 
  - bap-template
---

# Set up automatic freight reconciliation

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up data for automatic freight reconciliation. This is typically done by a warehouse manager.

## Set up the freight bill type

1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Freight bill type**. The freight bill type defines how freight bills and carrier invoices should be matched.
1. Select **New**.
1. In the **Freight bill type** field, type a value.
1. In the **Engine assembly field**, type *Microsoft.Dynamics.Ax.Tms.dll*. This is the standard Transportation management matching engine code library.  
1. In the **Engine class** field, type *Microsoft.Dynamics.Ax.Tms.Bll.GenericNormalizer*. This is the standard Transportation management matching engine class.  
1. Select **New**.
1. In the **Description** field, choose the value that should match on the freight bill and the carrier invoice.  
1. In the **Match required** field, select one of the following values:
    - *Yes* – The value selected in the **Description** field must match on both the freight bill and the carrier invoice.
    - *No* – The value selected in the **Description** field can be blank on the freight bill or the carrier invoice.  
1. Select **Save**.

## Set up the freight bill type assignment

1. Close the page.
1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Freight bill type assignments**. The freight bill type assignment is used to specify which freight bill type is used for a particular carrier.
1. Select **New**.
1. In the **Mode** field, enter or select a value.
1. In the **Shipping carrier** field, enter or select a value.
1. In the **Freight bill type** field, select the freight bill type that you created earlier.
1. Close the page.

## Set up the audit master

1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Audit master**. The audit master defines the tolerance limits for automatic freight reconciliation. It specifies by how much the monetary amounts on the freight bill and the carrier invoice can differ and still allow reconciliation to occur. It also defines how to handle discrepancies.
1. Select **New**.
1. In the **Audit master ID** field, type a value.
1. In the **Shipping carrier** field, select the same shipping carrier as you did earlier.
1. In the **Freight bill type** field, select the freight bill type that you created earlier.
1. Expand the **Tolerance** FastTab.
1. In the **Minimum tolerance level** field, enter a number.
1. In the **Maximum tolerance level** field, enter a number.
1. Expand the **Result** FastTab.
1. In the **Overpayment reason code** field, enter or select a value. If the monetary amounts differ on the freight bill and the carrier invoice, the overpayment and underpayment reason codes specify the accounts that the difference should be registered on, as long as the difference is within the tolerance levels.  
1. In the **Underpayment reason** code field, enter or select a value.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
