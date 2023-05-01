---
title: Deprecated master planning overview
description: This article describes how the new Planning Optimization planning engine is now replacing the legacy build-in planning engine.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 11/11/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Deprecated master planning overview

[!include [banner](../../includes/banner.md)]

As [previously announced](../get-started/removed-deprecated-features-scm-updates.md#use-of-built-in-supply-chain-management-master-planning-engine-for-distribution-scenarios), Planning Optimization is scheduled to replace the existing built-in master planning engine.

If you currently use the deprecated master planning engine, you should start planning your migration to Planning Optimization now. It is important to get started right away because your operations could otherwise be impacted when deprecation is enforced (though enforcement isn't currently scheduled). We strongly encourage you to complete the migration as soon as Planning Optimization supports the features you require so that you can start taking advantage of the many performance improvements and other new capabilities provided by the new service.

The Planning Optimization functionality doesn't currently support all the features that are available in the planning engine that is built into Supply Chain Management. Therefore, it's important that you evaluate whether the feature set that is currently available in Planning Optimization will meet your requirements. The Planning Optimization functionality isn't currently turned on by default in Dynamics Lifecycle Services (LCS), so you have the opportunity to do your evaluation before the feature is turned on.

> [!NOTE]
> You need to request an exception from migration to Planning Optimization if your master planning process does not include production (master planning generated planned production orders) and you require the deprecated master planning engine beyond version 10.0.15. Starting in version 10.0.16, an error will be shown in environments when running the deprecated master planning engine without generation of planned production orders. Planning Optimization should be used for all new deployments that do not generate planned production orders during master planning. Owners of existing environments running the deprecated master planning engine without generation of Planned production orders, will receive a mail with details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

Before you switch to Planning Optimization, we strongly recommend that you evaluate the results of the Planning Optimization fit analysis. For more information, see [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).
