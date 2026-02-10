--- 
title: Create product packages for purchase orders
description: Learn how to create a product package and use it on a purchase order in Microsoft Dynamics 365 Commerce. 
author: josaw1
ms.date: 02/10/2026
ms.topic: how-to 
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Create product packages for purchase orders

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to create a product package and use it on a purchase order in Microsoft Dynamics 365 Commerce.

The following procedures walk through creating a product package and using it on a purchase order. The purchase order is used to create an order for a predefined set of products. The procedures use the USRT demo data company.

To create a product package, follow these steps:

1. In Commerce headquarters, go to Retail and Commerce > Inventory management > Replenishment > Product packages.
1. Select **New**.
1. In the **Package number** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Add**.
1. In the **Item number** field, enter "0160."
1. In the **Size** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. Select **Add**.
1. In the **Item number** field, enter "0160."
1. In the **Variant number** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. Select **Add**.
1. In the **Item number** field, enter "0175."
1. In the **Quantity** field, enter a number.
1. Select **Save**.
1. Close the page.

To add a package to a purchase order, follow these steps:

1. In headquarters, go to **Accounts payable** > **Purchase orders** > **All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, select the same vendor that you previously created the product package for, if you selected a vendor.
1. Expand the **General** section.
1. In the **Site** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Warehouse** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Expand the **Line details** section.
1. Select the **Product packages** tab.
1. Select **Purchase order line**.
1. Select **Create lines from package**.
1. In the list, find and select the product package you created in the previous step.
1. In the **Quantity** field, enter a number.
1. Select **Create**.
1. Select **Save**.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]