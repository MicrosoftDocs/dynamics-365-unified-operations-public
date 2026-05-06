---
title: Deprecated master planning overview
description: Learn how the new Planning Optimization planning engine is now replacing the legacy build-in planning engine and when the deprecated engine will be removed.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 05/01/2026
ms.custom:
  - bap-template
ms.collection:
  - ai-assisted
---

# Deprecated master planning overview

[!include [banner](../../includes/banner.md)]

> [!NOTE]
> Although we strongly recommend that you migrate to Planning Optimization as soon as possible for the reasons outlined in this article, you can continue to use the deprecated master planning engine while you prepare to migrate without requesting an exception from Microsoft. For more information about how to do so, see [Continue to use deprecated master planning with existing companies](continue-using-deprecated-planning.md).

As [previously announced](../get-started/removed-deprecated-features-scm-updates.md#use-of-built-in-supply-chain-management-master-planning-engine-for-distribution-scenarios), the built-in master planning engine is deprecated. The engine has been deprecated for a long time and receives no meaningful support from Microsoft. Microsoft no longer invests in it (no new features are released).

Planning Optimization is the master planning engine for Supply Chain Management and completely replaces the built-in master planning engine.

> [!WARNING]
> If you're still using the deprecated master planning engine, you should strongly reconsider doing so. The engine receives no support and has no active development. We strongly encourage you to complete the migration to Planning Optimization as soon as possible so that you can take advantage of the many performance improvements and other new capabilities provided by the new service.

Work with a partner to evaluate and plan the migration to Planning Optimization.

Before you switch to Planning Optimization, evaluate the results of the Planning Optimization fit analysis. Learn more in [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).

## When will the deprecated planning engine be removed?

There's currently no timeline for the full removal of the deprecated master planning engine from Supply Chain Management. Microsoft isn't currently planning to remove it.

> [!IMPORTANT]
> If Microsoft decides to remove the deprecated master planning engine, the company will announce those plans at least 12 months before the removal date on the [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md) page. Monitor that page and the [What's new or changed in Dynamics 365 Supply Chain Management](../get-started/whats-new-home-page.md) page for the latest announcements.

Although the deprecated master planning engine isn't being removed right now, it's important to understand what *deprecated* means in practice:

- **No new features** – Microsoft isn't investing in new capabilities for the deprecated engine.
- **No support** – The deprecated master planning engine has been deprecated for a long time and receives no support from Microsoft. There are no bug fixes, no new features, and no investment in the engine going forward. Customers who continue to use it do so entirely at their own risk.
- **Version restrictions** – Starting in Supply Chain Management version 10.0.41, the deprecated master planning engine is blocked for all new deployments. Existing deployments can continue using it on a per-company basis.

We strongly recommend that you begin planning your migration to Planning Optimization now, even though there's no removal date. Learn more in [Migration to Planning Optimization for master planning](new-master-planning-engine.md).
