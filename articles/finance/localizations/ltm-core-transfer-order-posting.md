---
title: Inventory transfer order for posting for Latin America
description: This article provides information about inventory transfer order posting for Latin America. 
author: Fhernandez0088
ms.date: 05/18/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Inventory transfer order for posting for Latin America

[!include [banner](../includes/banner.md)]

You can add the information needed for Latin American countries when you an inventory transfer order in an extended LATAM section.

## Prerequisites

Before you post an inventory transfer order with LATAM information, the following configurations must be complete. 

- Create a document class that's configured as an inventory transfer packing slip.
- In the **Inventory and warehouse management parameters**, on the **LATAM** tab, select a document class to use in the inventory transfer order transaction.
- Configure at least one product with requirements that will be used in an inventory transfer order transaction.

## Post an inventory transfer order with LATAM information
Complete the following steps to post an intentory transfer order.

1. Go to **Inventory management** > **Inbound orders** > **Transfer order** and create a new transfer order.
2. Add an item, and select the warehouses to transfer the item.
3. Select **Ship** > **Ship transfer order**.
4. On the **LATAM** tab, complete the required fields and then select **OK**.

## Checking LATAM information from transfer order transactions
Complete the steps to view transaction information related to LATAM on the transfer order.

1. Go to **Inventory management** > **Inbound orders** > **Transfer order**.
2. Select a shipped transfer order.
3. Select **Transfer order** > **Transfer order history**.
4. Onthe **LATAM** tab, review the LATAM information.


[!include [banner](../includes/banner.md)]
