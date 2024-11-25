---
title: Sales point relation for sales documents and remission
description: Learn about the sales point link configuration for Latin America, including prerequisites and a step-by-step process for setting up a sales point pair.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Sales point relation for sales documents and remission

[!include [banner](../../includes/banner.md)]

You can select the packing slip documents that are used with a sales document by linking sales points when you invoice a product sale. The sales points will then be assigned to the invoice in the transaction.

## Prerequisites

Before you can link sales points, you must create at least one sale point. Additionally, a sales invoice document class and a packing slip document class must be created, and they must have an automatically generated document number mask that a sales point is assigned to.

## Set up a sales point pair

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales Point Relation - Sales document and Remission**.
2. On the Action Pane, select **New** to add a line to the main grid.
3. In the **Sales document sales point** field, select a sales point.
4. In the **Remission sales point** field, select a sales point.
5. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
