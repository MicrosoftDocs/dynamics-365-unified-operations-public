---
# required metadata

title: Create a product hierarchy
description: This topic describes how to create a new product hierarchy in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Create a product hierarchy

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new product hierarchy in Microsoft Dynamics 365 Commerce.

## Overview

Microsoft Dynamics 365 Commerce supports multiple retail channels. These retail channels include online stores, call centers, and retail stores (also known as brick-and-mortar stores). Each retail store channel can have its own payment methods, price groups, point of sale (POS) registers, income accounts and expense accounts, and staff. You must set up all of these elements before you can create a retail store channel. 
A Retail product hierarchy is used to define the overall product hierarchy for your organization. You can use this hierarchy type for merchandising, pricing and promotions, reporting, and assortment planning. Only one retail product hierarchy can be assigned this hierarchy type.

## Create and configure category hierarchy

1. Go to **Navigation pane \> Modules \> Retail \> Products and categories \> Retail product hierarchy**.
1. If no hierachy exists yet, on the **Action pane**, select **New** to create the root of the hierarchy.
1. In the **General** section, provide a **Name**, **Description** and **Friendly Name** and set to **Active**.


## Add hierarchy nodes
1. On the **Action pane**, select **Edit category hierarchy**.
1. Select the parent node to add a new node to and press the "New category Node" button.
1. In the **General** section provide a **Name**, **Description**, **Friendly name** and **Keywords**.
1. Optionaly set a **Display order* for the node.
1. On the **Action pane**, select **Save**.
1. Repeat for any other needed nodes.

The following image shows the creation of a new product hierarchy node.

![Create product hierarchy](media/create-product-hierarchy.png)

## Other settings

Category attribute groups can also be assigned to each group as required.  

## Additional resources

[Retail hierarchies](retail-hierarchies.md)
