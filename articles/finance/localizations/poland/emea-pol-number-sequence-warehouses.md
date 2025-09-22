---
title: Set up number sequences by warehouse
description: Learn how to set up number sequences for purchase product receipts and sales packing slips by warehouse for Poland in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-05-31
---

# Set up number sequences by warehouse

[!include[banner](../../includes/banner.md)]

This article explains how to set up number sequences for purchase product receipts and sales packing slips by warehouse for Poland in Microsoft Dynamics 365 Finance.

## Set up a number sequence for purchase product receipts by warehouse

You can set up a number sequence for purchase product receipts by warehouse on the **Accounts payable parameters** page. You can number delivery documents separately for each warehouse. 

To set up a number sequence for purchase product receipts by warehouse, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**. 
2. In the left pane, select **Number sequences**. 
3. In the **Number sequence code** field, select a number sequence for the Internal product receipt reference type. 
4. Select **Warehouses**. 
5. On the **Purchase – delivery note numbering** page, in the **Warehouse** field, select a warehouse. 
6. In the **Number sequence code** field, enter a product receipt number sequence code for the selected warehouse. 
7. Repeat step 6 for each warehouse. 

> [!NOTE]
> You can also set up delivery document numbering by warehouse for a purchase order. To do this, select a specific warehouse on the **Posting product receipt** page. After you post a product receipt, the order status of the purchase order line will not change to **Delivered** or **Received** until all purchase lines for all warehouses are posted for the purchase order. 

## Set up a number sequence for sales packing slips by warehouse

You can set up a number sequence for sales packing slips by warehouse on the **Accounts receivable parameters** page. You can number delivery documents separately for each warehouse. 

To set up a number sequence for sales packing slips by warehouse, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**. 
2. In the left pane, select **Updates**. Select the **Independent delivery note numbering** checkbox. 
3. In the left pane, select **Number sequences**. Select a number sequence for the **Packing slip** reference type. 
4. Select **Warehouses**. 
5. On the **Sales - delivery note numbering** page, in the **Warehouse** field, select a warehouse. 
6. In the **Number sequence code** field, enter a packing slip number sequence code for the selected warehouse. 
7. Repeat step 6 for each warehouse. 

> [!NOTE]
> You can also set up delivery document numbering by warehouse for a sales order. To do this, select a specific warehouse on the **Packing slip** page. After you post a packing slip, the order status will not change to **Delivered** or **Received** in the sales order until all sales lines for all warehouses are posted for the sales order. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
