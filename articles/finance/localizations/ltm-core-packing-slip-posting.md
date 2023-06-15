---
title: Post packing slips for Latin America
description: This article explains how to post packing slips for Latin America.
author: Fhernandez0088
ms.date: 06/05/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Post packing slips for Latin America

[!include [banner](../includes/banner.md)]

You can add the information that's required for Latin American countries when you post a packing slip in an extended **LATAM** section. The information can be added to a sales order packing slip, a purchase order packing slip, and a packing slip from a project.

## Prerequisites

Before you can post a packing slip that has LATAM information, the following prerequisites must be met:

- Create a document class that's configured as a packing slip.
- Configure a customer and a vendor that have the required LATAM information.
- Create and configure a project to post invoices that have items.

## Post a packing slip from a sales order with LATAM information

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**, and create a sales order.
2. Add an item, and then assign a quantity and a unit price.
3. On the Action Pane, select **Post packing slip**.
4. On the **LATAM** tab, complete the required fields.
5. Select **OK**.

## Post a packing slip from a purchase order with LATAM information

1. Go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**, and create a purchase order.
2. Add an item, and then assign a quantity and a unit price.
3. Confirm the purchase order, and generate the product receipt.
4. On the **LATAM** tab, complete the required fields.
5. Select **OK**.

## Post a packing slip from a project with LATAM information

1. Go to **Project management and accounting** \> **Item tasks** \> **Item requirements**, and create a line.
2. Select the project.
3. Select an item and the quantity, and then select values in the remaining required fields.
4. On the Action Pane, select **Post packing slip**.
5. On the **Posting** page, in the **LATAM** section, complete the required fields according to the document class configuration.
6. Select **OK**.

## View LATAM information on a packing slip

1. Go to **Sales and marketing** \> **Sales orders** \> **Order shipping** \> **Packing slip**, and select a packing slip.
2. On the **LATAM** tab, review the LATAM information.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
