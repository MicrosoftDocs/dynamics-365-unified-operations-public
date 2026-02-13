---
title: Set up hub accessorial charges and accessorial masters
description: Learn how to create an accessorial master for a hub and use that master to create a hub accessorial charge, including step-by-step processes. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSCarrierAccessorial,TMSAccessorialMaster, TMSHubAccessorial
ms.topic: how-to
ms.date: 11/19/2025
ms.custom:
  - bap-template
---

# Set up hub accessorial charges and accessorial masters

[!include [banner](../../includes/banner.md)]

This procedure shows how to create an accessorial master for a hub and use that master to create a hub accessorial charge. A transportation coordinator typically performs this setup.

## Set up a hub master

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Accessorial masters**.
1. Select **New**.
1. In the **Accessorial master** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Accessorial type** field, select *Hub*.
1. Select **Save**.

## Set up a hub accessorial charge

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Hub accessorial charges**.
1. Select **New**.
1. In the **Hub accessorial ID field**, enter a value.
1. In the **Hub** field, find and select the desired record.
1. In the **Hub position** field, select an option. You can either create the charge as a pickup or drop-off. Depending on your selection, the charge applies to the corresponding transportation segment on your route.  
1. In the **Accessorial master** field, select the master you just created.  
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
