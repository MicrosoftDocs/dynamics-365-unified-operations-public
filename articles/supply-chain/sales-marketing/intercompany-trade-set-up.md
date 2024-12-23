---
title: Set up intercompany trade
description: Learn how to set up intercompany trade, including outlines on what to do before setting up intercompany trade and setting up trading relations and products.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CustTable, VendTable, EcoResProductListPage, InterCompanyTradingRelationSetupCustomer
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Set up intercompany trade

[!include [banner](../../includes/banner.md)]

To enable Microsoft Dynamics 365 Supply Chain Management to run intercompany trade, you must set up customers and vendors to run intercompany trade. You must also set up Accounts payable, Accounts receivable, Procurement and sourcing, and Sales and marketing.

## Before you set up intercompany trade

Before you set up intercompany trade, you must decide which customers are intercompany customers, and which vendors are intercompany vendors. For each legal entity in Microsoft Dynamics 365 Supply Chain Management, you must decide which trading policy to apply to the intercompany trading relation with the specific intercompany customer or vendor.

In particular, we recommend that you and your organization become familiar with the intercompany parameters.

- Discuss the implications of the setup with the managers who are responsible for intercompany trade in each legal entity.
- Set up the appropriate values for each legal entity.

## Set up trading relations

To set up intercompany trade for customers and vendors, follow these steps.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select a customer account.
1. On the Action Pane, on the **General** tab, select **Intercompany**.
1. Specify intercompany setup parameters for the customer account. These parameters include the legal entity that contains the corresponding vendor and the vendor account. The parameters also include the purchase order policies, sales order policies, value mapping, and policies for sales agreements and purchase agreements. You also specify whether to use base data values from the customer account or from the vendor account in the other legal entity.
1. Repeat steps 1 through 4 for the remaining intercompany customers in the legal entity.
1. Go to **Accounts payable \> Vendors \> All vendors**.
1. Select a vendor account.
1. On the Action Pane, on the **General** tab, select **Intercompany**.
1. Specify intercompany setup parameters for the vendor account. These parameters include the legal entity that contains the corresponding customer and the customer account. The parameters also include the sales order policies, purchase order policies, value mapping, and policies for purchase agreements and sales agreements. You also specify whether to use base data values from the vendor account or from the customer account in the other legal entity.
1. Repeat steps 6 through 9 for the remaining intercompany vendors in the legal entity.

## Set up products

To enable products for intercompany trade, follow these steps.

1. Go to **Product information management \> Products \> All products and product masters**.
1. Define the products that are released to the legal entities where you want to do intercompany trade.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
