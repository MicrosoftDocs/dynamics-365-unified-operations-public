---
title: Original invoice reference (Eastern Europe)
description: This article describes how to create sales orders and corrective lines in a credit note for a sales order in Estonia with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Estonia
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---

# Original invoice reference (Eastern Europe)

[!include [banner](../../includes/banner.md)]

This article describes how to create sales orders and corrective lines in a credit note for a sales order in Estonia with Microsoft Dynamics 365 Finance.

The following procedures use the demo data company DEMF with a primary address in Poland.

## Create a sales order

To create a sales order, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select an option.
1. Expand the **Setup** section.
1. In the **Sales date** field, enter a date.
1. In the list, mark the selected row.
1. Select **OK**.
1. Select **OK**.

## Create a credit note for a sales order

To create a sales order for a sales order, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. On the Action Pane, select **Sell**.
1. Select **Credit note**.
1. Select the **Select all** checkbox.
1. Expand the **Parameters** section.
1. In the **Reason code** field, enter or select a value.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the list, find and select the desired record.
1. In the **Quantity** field, enter a number.
1. Select **OK**.
1. Select **Save**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. In the list, find and select the desired record.
1. Select **OK**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
