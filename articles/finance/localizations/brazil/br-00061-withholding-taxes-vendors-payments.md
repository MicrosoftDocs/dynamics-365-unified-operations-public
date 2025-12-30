---
title: Withholding taxes on vendor payments (Brazil)
description: This article describes how to use the Journal voucher page to enter and post payments you make to a vendor for the purchase of items or services in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.search.industry: Manufacturing;Distribution;Service industries
---

# Withholding taxes on vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to use the Journal voucher page to enter and post payments you make to a vendor for the purchase of items or services in Brazil with Microsoft Dynamics 365 Finance.

You can use the Journal voucher page to enter and post payments that you make to a vendor for the purchase of items or services. When you post a vendor payment journal, the withholding tax group that is set up for the vendor is used to calculate the withholding tax on the transaction. 

The following procedure uses the BRMF demo company.

To use the Journal voucher page to enter and post payments you make to a vendor, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand the **Invoice and delivery** section.
1. Select **Edit**.
1. In the **Calculate withholding tax** field, select **Yes**.
1. In the **Withholding tax group** field, enter or select a value.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Close the page.
1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
1. Select **OK**.
1. In the **Item number** field, enter or select a value.
1. In the **Site** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Item sales tax group** field, enter or select a value.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Withholding tax group** field, enter or select a value.
1. In the **Item withholding tax group** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. In the **Service code** field, enter or select a value.
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
1. In the **Number** field, enter a value.
1. In the **Series** field, enter a value.
1. In the **Invoice date** field, enter a date.
1. Select **Post**.
1. Close the page.
1. Go to **Accounts payable \> Payments \> Payment journal**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the **Account** field, specify the desired values.
1. Select **Settle transactions**.
1. In the list, find and select the desired record.
1. Select the **Mark** checkbox.
1. Select the **Withholding tax** tab.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Description** field, enter or select a value.
1. In the **Offset account** field, enter the desired values.
1. Select **Post**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
