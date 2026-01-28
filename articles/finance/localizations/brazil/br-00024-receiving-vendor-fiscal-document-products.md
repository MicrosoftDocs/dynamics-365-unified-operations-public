---
title: Receive vendor fiscal documents (products) (Brazil)
description: This article describes how to post a fiscal document you receive from the acquisition of inventory goods where PIS/COFINS taxes are deducted from the tax assessment payment in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.search.industry: Manufacturing;Distribution;Service industries
---

# Receive vendor fiscal documents (products) (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to post a fiscal document you receive from the acquisition of inventory goods where PIS/COFINS taxes are deducted from the tax assessment payment in Brazil with Microsoft Dynamics 365 Finance.

You can post a fiscal document that you received from the acquisition of inventory goods, where the ICMS, IPI, and PIS/COFINS taxes are deducted from the tax assessment payment. 

The following procedure uses the BRMF demo company.

To post a fiscal document you receive from the acquisition of inventory goods where PIS/COFINS taxes are deducted, follow these steps:

1. In Dynamics 365 Finance, go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. Close the page.
1. Go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Select **Default from: Product receipt quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select an option.
1. Select **OK**.
1. In the **Document model** field, enter or select a value.
1. In the **Access key** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. Select **Save**.
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
