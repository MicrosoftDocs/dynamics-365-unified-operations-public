---
title: Sales point relation for sales documents and remission
description: This article provides information about the sales point link configuration for Latin America.
author: Fhernandez0088
ms.date: 04/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Sales point relation for sales documents and remission

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can select the packing slip documents that are used with a sales document by linking sales points when you invoice a product sale. The sales points will then be assigned to the invoice in the transaction.

## Prerequisites

Before you can link sales points, you must create at least one sale point. Additionally, a sales invoice document class and a packing slip document class must be created, and they must have an automatically generated document number mask that a sales point is assigned to.

## Set up a sales point pair

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales Point Relation - Sales document and Remission**.
2. On the Action Pane, select **New** to add a line to the main grid.
3. In the **Sales document sales point** field, select a sales point.
4. In the **Remission sales point** field, select a sales point.
5. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
