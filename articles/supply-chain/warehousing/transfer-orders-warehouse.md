---
# required metadata

title: Set up warehouses for transfer orders
description: This topic describes how you can set up warehouses for transfer orders.
author: Mirzaab
ms.date: 01/18/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventLocation,CustVendTransportPoint2Point
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2018-4-30
ms.dyn365.ops.version: 8.0

---

# Set up warehouses for transfer orders 

[!include [banner](../includes/banner.md)]

You can use warehouse levels to create a hierarchy that supports transfer orders between warehouses. Based on this setup, master scheduling calculates item requirements at the individual warehouse level and generates planned transfer orders from an assigned source warehouse to fulfill them.

1.  Click **Inventory management > Setup > Inventory breakdown > Warehouses**.

2.  Select the warehouse that you want to refill.

3.  On the **Master planning** FastTab, select the **Refilling** check box.

4.  In the **Main warehouse** field, select the warehouse that you want to assign as the refilling warehouse. Master scheduling calculates a transfer requirement for the selected warehouse and generates a planned transfer order from the assigned **Main warehouse**.
   
    > [!NOTE]
    > <P>If you clear the <STRONG>Refilling</STRONG> check box, the selected warehouse is assigned a warehouse level in regard to the <STRONG>Main warehouse</STRONG>, but the <STRONG>Main warehouse</STRONG> is not set up as a refilling warehouse.</P>

5.  Close the page to apply the new setup.


> [!TIP]
> <P>If you want to assign a warehouse for refilling, you must first set up the warehouse as a storage dimension on the <STRONG>Storage dimension groups</STRONG> page. On this page, select the <STRONG>Active</STRONG> field and the <STRONG>Coverage plan by dimension</STRONG> field for the warehouse.</P>

## Set up transport lead time

You must also set up the transport lead time between the warehouses on the **Transport days** page. 
1. Go to **Inventory management > Setup > Distribution > Transport days**.
2. In the **Receiving point** field, select **warehouse**.
3. Select the **Shipping warehouse**, **Receiving warehouse**, and **Transport days**. 
4. (Optional) You can also set transport time, depending on the mode of delivery, under the **Transport days per mode of delivery** tab.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]