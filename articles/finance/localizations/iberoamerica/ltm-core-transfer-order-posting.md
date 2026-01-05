---
title: Inventory transfer order for posting for Latin America
description: Learn about inventory transfer order posting for Latin America, including prerequisites and an outline on posting an inventory transfer order.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Inventory transfer order for posting for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

When you post an inventory transfer order in an extended LATAM section, you can add the information that's required for Latin American countries/regions.

## Prerequisites

Before you post an inventory transfer order that has LATAM information, the following configuration must be completed:

- Create a document class that's configured as an inventory transfer packing slip.
- On the **Inventory and warehouse management parameters** page, on the **LATAM** tab, select a document class to use in the inventory transfer order transaction.
- Configure at least one product with requirements to use in the inventory transfer order transaction.

## Post an inventory transfer order that has LATAM information

Follow these steps to post an inventory transfer order.

1. Go to **Inventory management** \> **Inbound orders** \> **Transfer order**, and create a transfer order.
1. Add an item, and select the warehouses to transfer the item from and to.
1. Select **Ship** \> **Ship transfer order**.
1. On the **LATAM** tab, complete the required fields.
1. Select **OK**.

## Review LATAM information from transfer order transactions

Follow these steps to view transaction information that's related to LATAM on a transfer order.

1. Go to **Inventory management** \> **Inbound orders** \> **Transfer order**.
1. Select a shipped transfer order.
1. Select **Transfer order** \> **Transfer order history**.
1. On the **LATAM** tab, review the LATAM information.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
