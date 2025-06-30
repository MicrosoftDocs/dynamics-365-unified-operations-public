---
title: Work blocking reasons
description: Learn about Work blocking reasons.
author: yanghaomingms
ms.author: yanghaomingms
ms.topic: faq
ms.date: 06/30/2025
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: WHSWorkTable, WHSWorkTableListPage
---

# Work blocking reasons

[!include [banner](../includes/banner.md)]

This article describes the work blocking functionality and reasons.

**Work blocking** provides a standardized way to block or unblock warehouse work and offers greater visibility into the reasons why a work is blocked. Multiple reasons can cause a work to be blocked, and in some cases, a single work may be blocked for several reasons at once.

The following are the supported work blocking reasons:

- **Unprocessed deferred put operation**: The work is blocked by a deferred put processing task that is not processed.

- **Demand replen wave in process**: The work is blocked by a demand wave that is in process.

- **Processing wave**: The work is blocked by a processing wave.

- **Held wave**: The work is blocked by a wave with status Held.

- **Split work**: The work is blocked because it is being splitted.

- **Unprocessed production over pick work**: The work is blocked because it is linked to a unprocessed staging over pick work.

- **Unprocessed replenishment work**: The work is blocked because it is linked to a unprocessed replenishment work.

- **Undefined reason**: The work is blocked by undefined reason.

- **Initial pick work in progress**: Used when the work cannot be blocked or unblocked because it is in an in progress state.

**Only these blocking functionalities are supported.**

You can select multiple works to block or unblock them at once. If you manually block work, it will be assigned the reason **Undefined reason**.

To view blocking reasons, go to **Work details** > **Blocking reasons** tab.