---
title: Work blocking and blocking reasons
description: Learn about work blocking functionality and reasons.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSWorkTable, WHSWorkTableListPage
ms.topic: how-to
ms.date: 06/30/2025
ms.custom: 
  - bap-template
---

# Work blocking and blocking reasons

[!include [banner](../includes/banner.md)]

*Work blocking* provides a standard way to block or unblock warehouse work. The system prevents blocked work from being processed until it's unblocked. You can block work records automatically when certain conditions are met and you can also block them manually at any time. Multiple reasons can cause work to be blocked, and in some cases, a single work record can be blocked for several reasons at once. The system provides visibility into the reasons why a work record is blocked. You can only block work records with the status *Open*. This article describes the work blocking functionality and reasons.

## Supported work blocking reasons

The following work blocking reasons are supported:

- **Unprocessed replenishment work** – The work is blocked because it's linked to an unprocessed replenishment work record.
- **Held wave** – The work is blocked by a wave with status *Held*.
- **Unprocessed production over pick work** – The work is blocked because it's linked to an unprocessed staging over-pick work record.
- **Unprocessed deferred put operation** – The work is blocked by an unprocessed deferred-put processing task.
- **Split work** – The work is blocked because it's being split.
- **Replenishment overflow capacity** – The replenishment work is blocked because it would overflow the capacity of the put location.
- **Processing wave** – The work is blocked by a processing wave.
- **Undefined reason** – The work is blocked for an undefined reason.

No other blocking reasons are supported.

## View blocked work and blocking reasons

To find all blocked work and check the reasons why each of them blocked, follow these steps.

1. Go to **Warehouse management** \> **Work** \> **All work**.
1. Blocked work records show a check mark in the **Blocked wave** column. You can use the column filter to find all blocked work records at once.
1. To see the reasons why a work record is shown as blocked, select the link in the **Work ID** column to open the **Work details** page for that work record. Then open the **Blocking reasons** tab, which shows all blocking reasons for that work record, along with who blocked it and the date and time when each reason was applied.

> [!TIP]
> If you only want to find work that is blocked by replenishment work, you can go to **Warehouse management** \> **Work** \> **Outbound** \> **Work blocked by replenishment work**.

## Manually block or unblock work

You can manually block work at any time. Manually blocked work shows a blocking reason of *Undefined reason*.

You can manually unblock work that is currently blocked for one of the following reasons:

- Held wave
- Undefined reason
- Replenishment overflow capacity

To manually block or unblock work, go to **Warehouse management** \> **Work** \> **All work** and select one or more work records that you want to block or unblock. Then, on the Action Pane, select **Block work** or **Unblock work**.

The system automatically unblocks work that is blocked for other reasons when the blocking reason is resolved.
