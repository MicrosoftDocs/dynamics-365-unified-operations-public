---
title: Delivery slips (Brazil)
description: This article describes how to post delivery slips for sales orders with multiple sales order lines that have CFOP delivery codes in Brazil with Microsoft Dynamics 365 Finance.
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

# Delivery slips (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to post delivery slips for sales orders with multiple sales order lines that have Código Fiscal de Operações e Prestações (CFOP) delivery codes in Brazil with Microsoft Dynamics 365 Finance.

You can post a delivery slip for a sales order that has multiple sales order lines that have a delivery Código Fiscal de Operações e Prestações (CFOP) code. For each sales order line, you must specify the CFOP code that has a delivery CFOP code assigned to it. A delivery slip is used when the customer that you deliver items to differs from the customer that is invoiced. (In other words, the customer account and invoice account differ.) Delivery slips are posted in chronological order. You must attach fiscal references to delivery slips before you post them. 

The following procedure uses the BRMF demo company.

To post delivery slips for sales orders with multiple sales order lines that have CFOP delivery codes, follow these steps.

1. In Dynamics 365 Finance, go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. In the **Lines or header** field, select an option.
1. In the **Invoice account** field, enter or select the customer that ordered the goods.  
1. In the **Lines or header** field, select an option.
1. Select **Add line**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value. The CFOP codes that are available depend on the fiscal establishment of the site, the order type, the operation type, the location of the customer, and the delivery address of the customer.  
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Delivery item sales tax group** field, enter the item sales tax group for the delivery fiscal document.  
1. In the **Delivery sales tax group** field, enter the sales tax group for the delivery fiscal document.  
1. Select **Save**.
1. On the Action Pane, select **Pick and pack**.
1. Select **Delivery slip**.
1. Select **Fiscal reference**.
1. In the **Document model** field, enter or select a value.
1. In the **Access key** field, enter the access key from the NF-e that was issued by the customer ordering the goods and to whom the sales must be invoiced to.  
1. In the **Date** field, enter a date.
1. In the **Direction** field, select an option.
1. In the **Account** field, enter or select the customer account that generated the fiscal document.  
1. Select **Save**.
1. Close the page.
1. Select **OK**.
1. Select **OK**.
1. Close the page.
1. Go to **Accounts receivable \> Fiscal documents \> Electronic fiscal documents \> Export/import NF-e process**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
