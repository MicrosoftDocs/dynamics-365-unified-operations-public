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

<!-- KFM: Describe what it means to be "blocked" and the effects it has. What are we blocked from doing? What can we do about it? --> 
*Work blocking* provides a standard way to block or unblock warehouse work. Blocking a work prevent it from being processed until it is unblocked. A work can be blocked either manually or automatically when certain conditions are met. We also offer visibility into the reasons why a work record is blocked. Multiple reasons can cause work to be blocked, and in some cases, a single work record can be blocked for several reasons at once. Only the work with status *Open* can be blocked. This article describes the work blocking functionality and reasons.

## Supported work blocking reasons

The following work blocking reasons are supported:

- *Unprocessed replenishment work* – The work is blocked because it's linked to an unprocessed replenishment work record.
- *Held wave* – The work is blocked by a wave with status *Held*.
- *Unprocessed production over pick work* – The work is blocked because it's linked to an unprocessed staging over-pick work record.
- *Unprocessed deferred put operation* – The work is blocked by an unprocessed deferred-put processing task.
- *Split work* – The work is blocked because it's being split.
- *Replenishment overflow capacity* – The replenishment work is blocked because it would overflow the capacity of the put location. <!-- Haoming: It exists. Also clean up those not-used ones. https://msdyneng.visualstudio.com/FinOps/_search?text=WHSWorkBlockingReasonType.xml&type=code&pageSize=25&filters=ProjectFilters%7BFinOps%7D&action=contents&result=DefaultCollection/FinOps/ApplicationSuite/GBmaster//Source/Metadata/ApplicationSuite/Foundation/AxEnum/WHSWorkBlockingReasonType.xml-->
- *Processing wave* – The work is blocked by a processing wave.
- *Undefined reason* – The work is blocked for an undefined reason.

No other blocking reasons are supported.

## View blocked work and blocking reasons

To find all blocked work and check the reasons why each of them blocked, follow these steps.

1. Go to **Warehouse management** \> **Work** \> **All work**.
1. Blocked work records show a check mark in the **Blocked wave** column. You can use the column filter to find all blocked work records at once. <!-- KFM: please confirm that this is the correct column to check. --> <!-- Haoming: Yes. -->
1. To see the reasons why a work record is shown as blocked, select the link in the **Work ID** column to open the **Work details** page for that work record. Then open the **Blocking reasons** tab, which shows all blocking reasons for that work record, along with who blocked it and the date and time when each reason was applied.

<!-- KFM: There is also a page called **Work blocked by replenishment work**. Should we describe that here too?-->
Also, to find all work blocked by replenishment work. You can go to **Work blocked by replenishment work** page.

## Manually block or unblock work

You can manually block work at any time. Manually blocked work shows a blocking reason of *Undefined reason*.

You can manually unblock work that is currently blocked for one of the following reasons:

- Held wave
- Undefined reason
- Replenishment overflow capacity <!-- KFM: Does this reason still exist (it's mentioned in the tooltip) --> <!-- Haoming: Yes. It exists.-->

<!-- KFM: Briefly mention how other types of blocking reasons get unblocked (I assume it's automatic and depends on the reason stated). Also, what happens if we manually unblock when there are multiple blocks and some allow manual unblock while others don't? -->
<!-- Haoming: Check in the UI. It seems we validate each selected work, and show info when succeeds or error when fails to each work.-->

To manually block or unblock work, go to **Warehouse management** \> **Work** \> **All work** and select one or more work records that you want to block or unblock. Then, on the Action Pane, select **Block work** or **Unblock work**.

The work that is blocked with other reasons will be automatically unblocked when its blocking reason is resolved.