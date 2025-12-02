---
title: Set up vendor master and purchase order to be target of consolidated invoice
description: Learn how to set up a vendor master and purchases to be a target of consolidated invoices for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 05/09/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: VendTable, PurchTable
ms.custom: 
  - bap-template
---

# Set up vendor master and purchase order to be target of consolidated invoice

[!include [banner](../../includes/banner.md)]

This article explains how to set up a vendor master and purchases to be a target of consolidated invoices for Japan in Microsoft Dynamics 365 Finance.

In Japan, the vendors usually use consolidated invoice for transactions. 

The following procedures walk you through how to configure a vendor master and purchase order to use the consolidated invoice. 

The procedures use the demo data company JPMF.

## Set up a vendor master

To set up a vendor master, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Payment** section.
1. Verify that the terms of payment uses the cutoff day.  
1. Specify a consolidation day for the vendor. Before you can update this field, you might need to select **Edit** first.  

## Set a purchase order to be the target of a consolidated invoice

To set a purchase order to be the target of a consolidated invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. Confirm that the **Target of consolidation** slider option is set to **Yes**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
