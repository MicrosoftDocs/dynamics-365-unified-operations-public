---
title: Set up number sequences by warehouse
description: Learn about setting up number sequences for purchase product receipts and sales packing slips by warehouse for Poland, including a step-by-step process.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
---

# Set up number sequences by warehouse

[!include[banner](../../includes/banner.md)]

This article walks you through setting up number sequences for purchase product receipts and sales packing slips by warehouse for Poland.

## Set up a number sequence for purchase product receipts by warehouse

You can set up a number sequence for purchase product receipts by warehouse on the **Accounts payable parameters** page. You can number delivery documents separately for each warehouse. 

1. Click **Accounts payable > Setup > Accounts payable parameters**. 
2. On the **Accounts payable parameters** page, in the left pane, click **Number sequences**. 
3. In the **Number sequence code** field, select a number sequence for the Internal product receipt reference type. 
4. Click **Warehouses**. 
5. On the **Purchase – delivery note numbering** page, in the **Warehouse** field, select a warehouse. 
6. In the **Number sequence code** field, enter a product receipt number sequence code for the selected warehouse. 
7. Repeat step 6 for each warehouse. 

> [!NOTE]
> You can also set up delivery document numbering by warehouse for a purchase order. To do this, select a specific warehouse on the **Posting product receipt** page. After you post a product receipt, the order status of the purchase order line will not change to **Delivered** or **Received** until all purchase lines for all warehouses are posted for the purchase order. 

## Set up a number sequence for sales packing slips by warehouse

You can set up a number sequence for sales packing slips by warehouse on the **Accounts receivable parameters** page. You can number delivery documents separately for each warehouse. 

1. Click **Accounts receivable > Setup > Accounts receivable parameters**. 
2. In the left pane, click **Updates**. Select the **Independent delivery note numbering** check box. 
3. In the left pane, click **Number sequences**. Select a number sequence for the Packing slip reference type. 
4. Click **Warehouses**. 
5. On the **Sales - delivery note numbering** page, in the **Warehouse** field, select a warehouse. 
6. In the **Number sequence code** field, enter a packing slip number sequence code for the selected warehouse. 
7. Repeat step 6 for each warehouse. 

> [!NOTE]
> You can also set up delivery document numbering by warehouse for a sales order. To do this, select a specific warehouse on the **Packing slip** page. After you post a packing slip, the order status will not change to **Delivered** or **Received** in the sales order until all sales lines for all warehouses are posted for the sales order. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
