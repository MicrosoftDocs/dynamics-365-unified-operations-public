---
title: Issue fiscal documents for vendors (Brazil)
description: This article describes how to create and post vendor invoices on behalf of nontaxpayer vendors in Brazil with Microsoft Dynamics 365 Finance.
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

# Issue fiscal documents for vendors (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to create and post vendor invoices on behalf of nontaxpayer vendors in Brazil with Microsoft Dynamics 365 Finance.

You can create and post vendor invoices on behalf of nontaxpayer vendors. You must assign a fiscal establishment to a site. You must also set up a fiscal document type for purchase orders that you create and post on behalf of nontaxpayer vendors. Before you can create and post vendor invoices on behalf of a nontaxpayer vendor, you must specify the vendor as a nontaxpayer vendor. 

The following procedure uses the BRMF demo company.

To create and post vendor invoices on behalf of nontaxpayer vendors, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand the **Fiscal information** section.
1. Select **Edit**.
1. In the **Generate incoming fiscal document** field, select **Yes** to indicate that the vendor is a nontaxpayer.  
1. Select **Yes in the Use and consumption** field.
1. Select **No in the ICMS contributor** field.
1. Select **Save**.
1. Close the page.
1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the Vendor account field, enter or select a vendor account that is classified as a nontaxpayer.  
1. Select **OK**.
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
1. Select **Post**.
1. Close the page.
1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
