---
title: Create a credit note against a purchase invoice
description: Learn how to create a credit note against a purchase order invoice in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: India
ms.search.validFrom: 2019-06-01
---

# Create a credit note against a purchase invoice

[!include [banner](../../includes/banner.md)]

This article explains how to create a credit note against a purchase order invoice in Microsoft Dynamics 365 Finance.

To create a credit note against a purchase order invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Create a purchase order.
1. On the Action Pane, on the **Purchase** tab, select **Create credit note**.
1. Select the invoice to issue a credit note against, and then select **OK**.
1. Verify that the **Original invoice number** and **Original invoice date** fields are automatically set on the order line.
1. Select **Tax information**.
1. Select the **GST** FastTab.
1. Select the **Vendor tax information** FastTab.
1. Select **OK**.

## Validate the tax details

To validate the tax details, follow these steps:

1. On the Action Pane, on the **Purchase** tab, in the **Tax** group, select **Tax document**.
1. Select **Close**, and then select **Confirm**.

## Post the purchase invoice

To post the purchase invoice, follow these steps:

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Invoice**.
1. In the **Default quantity for lines** field, select **Ordered quantity**.
1. Enter the invoice number.
1. On the **Lines** FastTab, verify that the **Invoice type** field is set to **Original**.

    > [!NOTE]
    > You can post a revised credit note by selecting **Revised** in the **Invoice type** field and then adding a reference to the original credit note.

1. On the Action Pane, select **Post \> Post**.
1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Invoice**. 
1. On the **Overview** tab, select **Voucher**.

> [!NOTE]
> The general journal also lets you create a purchase credit note that has details of the original invoice.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
