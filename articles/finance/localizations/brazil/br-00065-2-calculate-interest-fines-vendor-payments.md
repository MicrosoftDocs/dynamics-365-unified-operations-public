---
title: Calculate interest and fines on vendor payments (Brazil)
description: This article describes how to apply interest and fines on vendor payments that are delayed in Brazil with Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Calculate interest and fines on vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to apply interest and fines on vendor payments that are delayed in Brazil with Microsoft Dynamics 365 Finance.

You can apply interest and fines on vendor payments that are delayed. The interest and fine amounts that apply to a payment can be calculated when you make a payment to a vendor. Before you calculate interest or fine codes for vendor payments, you must set up a list of bank holidays and national/regional holidays. A holiday date that is set up on the **Payment calendar** form is considered a nonworking day. If an invoice is due on a nonworking day, the due date is moved to the next working day in the calendar, and the interest and fines are calculated accordingly. 

The following procedure uses the BRMF demo company.

To apply interest and fines on vendor payments that are delayed, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand the **Payment** section.
1. Select **Edit**.
1. In the **Payment schedule** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Fine code** field, enter or select a value.
1. In the list, select the link in the selected row.
1. In the **Interest code** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
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
1. In the **Access key** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. Select **Post**.
1. Close the page.
1. Go to **Accounts payable \> Payments \> Payment journal**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the **Date** field, enter a date.
1. In the **Account** field, enter a value.
1. In the **Description** field, enter or select a value.
1. Select **Settle transactions**.
1. In the list, find and select the desired record.
1. Select the **Mark** checkbox.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Offset account** field, enter a value.
1. Select **Post**.
1. Close the page.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
