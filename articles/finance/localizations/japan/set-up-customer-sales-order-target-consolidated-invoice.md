---
title: Set up a customer and sales order to be target of consolidated invoice
description: Learn how to set up customers and sales orders to be targets of consolidated invoices for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable, SalesTableListPage, SalesTable
ms.custom: 
  - bap-template
---

# Set up a customer and sales order to be target of consolidated invoice

[!include [banner](../../includes/banner.md)]

This article explains how to set up customers and sales orders to be targets of consolidated invoices for Japan in Microsoft Dynamics 365 Finance.

In Japan, customers usually use consolidated invoices for all transactions.

The following procedure uses the JPMF demo company data.

## Set up a customer to be a the target of a consolidated invoice

To set up a customer to be a target of consolidated invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the list, select the link in the selected row.
1. Expand the **Payment defaults** section.
1. Verify that the terms of payment uses the cutoff day method. If the method isn't "Cutoff day", unlock the task guide and then select **Edit** to update this field.  
1. Specify a consolidation day for the customer.  

## Set up a sales order to be the target of a consolidated invoice

To set up a sales order to be the target of a consolidated invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. In the list, select the link in the selected row.
1. Select **Header**.
1. Verify that the **Target of consolidation** slider is set to **Yes**. If the slider is set to **No**, unlock the task guide and then select **Edit** to update the field.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
