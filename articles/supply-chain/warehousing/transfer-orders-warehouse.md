---
# required metadata

title: Set up warehouses for transfer orders
description: This topic describes how you can set up warehouses for transfer orders.
author: Mirzaab
manager: AnnBe
ms.date: 12/14/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
#ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: 10.0

---

# Set up warehouses for transfer orders 

[!include [banner](../includes/banner.md)]

You can use warehouse levels to create a hierarchy that supports transfer orders between warehouses. Based on this setup, master scheduling calculates item requirements at the individual warehouse level and generates planned transfer orders from an assigned source warehouse to fulfill them.

1.  Click **Inventory management > Setup > Inventory breakdown > Warehouses**.

2.  Select the warehouse that you want to refill.

3.  On the **Master planning** FastTab, select the **Refilling** check box.

4.  In the **Main warehouse** field, select the warehouse that you want to assign as the refilling warehouse. Master scheduling calculates a transfer requirement for the selected warehouse and generates a planned transfer order from the assigned **Main warehouse**.
    

    > [!NOTE]
    > <P>If you clear the <STRONG>Refilling</STRONG> check box, the selected warehouse is assigned a warehouse level with regard to the <STRONG>Main warehouse</STRONG>, but the <STRONG>Main warehouse</STRONG> is not set up as a refilling warehouse.</P>


5.  Close the form to apply the new setup.


> [!TIP]
> <P>If you want to assign a warehouse for refilling, you must first set up the warehouse as a storage dimension in the <STRONG>Storage dimension groups</STRONG> form. In this form, select the <STRONG>Active</STRONG> field and the <STRONG>Coverage plan by dimension</STRONG> field for the warehouse.</P>
