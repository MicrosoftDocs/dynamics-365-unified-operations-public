---
title: Create a corrective invoice (Spain)
description: Learn how to create a corrective invoice for Spain in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 07/11/2025
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---

# Create a corrective invoice (Spain)

[!include [banner](../../includes/banner.md)]

This article explains how to create a corrective invoice for Spain in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to create a corrective invoice. The procedures use the demo data company DEMF with a primary address in Spain.

## Create a purchase invoice

To create a purchase invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting** \> **Projects** \> **All projects**.
1. In the list, select the link in the selected row.
1. Select **Item task**.
1. Select **Purchase order**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. In the list, mark the selected row.
1. Select **Edit**.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **Default from: Product receipt quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select an option.
1. Select **OK**.
1. In the **Number** field, enter a value.
1. Select **Save**.
1. Select **Post**.

## **Post** a credit note on a purchase

To post a credit note on a purchase, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting** \> **Projects** \> **All projects**.
1. In the list, select the link in the selected row.
1. Select **Item task**.
1. Select **Purchase order**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. On the Action Pane, select **Purchase**.
1. Select **Credit note**.
1. Expand the **Invoices** section.
1. Select the **Select all** checkbox.
1. Expand the **Parameters** section.
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Select **Credit invoicing**.
1. In the **Reason code** field, select an option.
1. In the **Reason for correction** field, enter a value.
1. In the **Correction method** field, select an option.
1. Select **OK**.
1. Select **Financials**.
1. Select **Credit invoicing**.
1. In the **Reason code** field, select an option.
1. In the **Reason for correction** field, enter a value.
1. In the **Correction method** field, select an option.
1. Select **OK**.
1. Collapse the **Line details** section.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **No**.
1. In the **Number** field, enter a value.
1. Select **Post**.

## Verify the posted invoice has the correct information

To verify the posted invoice has the correct information, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. In the list, select the link in the selected row.
1. Select **Transactions**.
1. Select the **General** tab to verify the posted invoice.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
