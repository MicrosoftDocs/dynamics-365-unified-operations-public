---
# required metadata

title: Migrating to Planning Optimization for master planning
description: This topic provides information about Planning Optimization, which is the new master planning engine, and describes how to migrate from the existing engine. 
author: ChristianRytt
manager: tfehr
ms.date: 05/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 19311
ms.assetid: 5ffb1486-2e08-4cdc-bd34-b47ae795ef0f
ms.search.region: Global
ms.search.industry: 
ms.author: crytt
ms.search.validFrom: 2020-11-05
ms.dyn365.ops.version: 

---

# Migrating to Planning Optimization for master planning

[!include [banner](../includes/banner.md)]

The built-in master planning engine has be scheduled for deprecation and is being replaced by the *Planning Optimization Add-in for Dynamics 365 Supply Chain Management*. This topic provides information related to the impact on new and existing deployments, including any required actions.

Planning Optimization enables master planning calculations to occur outside of Supply Chain Management and its SQL database. The benefits associated with Planning Optimization include improved performance and minimal impact on the SQL database during master planning runs. Quick planning runs can even be done during office hours, which means that planners can immediately react to demand or parameter changes.

For more information about Planning Optimization, see the [Planning Optimization overview](planning-optimization/planning-optimization-overview.md).

## Deprecation of the existing master planning engine

We are in the process of deprecating the built-in planning engine in favor of Planning Optimization. This change affects all cloud environments. On-premises installations aren't affected. Starting with version 10.0.16, an error will be shown when if you run built-in master planning without generating planned production orders. However, the master planning run will complete successfully despite the error message.

For more information about built-in planning engine deprecation, see the announcements in [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md)

## Migrations, messages, and exceptions

Owners of existing environments who run the built-in master planning engine without generating planned production orders will receive a mail with details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

Starting in version 10.0.16, an error will be shown when running built-in master planning without generation of planned production orders. This error message includes guidance for migration and instructions on how to request an exception.

### New deployments

Planning Optimization should be considered as the default master planning engine for all new deployments in the cloud. In general Planning Optimization should be used for all new deployments that do not generate planned production orders during master planning. If a new deployment depends on functionality currently unsupported by Planning Optimization, you can request an exception to use the built-in master planning engine.

### Existing deployments

Owners of existing cloud-based deployments that depend on master planning should plan to migrate to Planning Optimization. If your implementation depends on functionality currently unsupported by Planning Optimization, you can request an exception.

For environments that currently use master planning processes that are being deprecated, Microsoft will send email to the environment admin. This email informs about the actions necessary to migrate or request an exception.

## The exception process

You can request an exception if you need to continue using the built-in master planning engine because your business processes heavily depends on at least one of the features currently not implemented in Planning Optimization. For a list of feature availability, see [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).

Currently, Planning Optimization migration exceptions are only provided if your master planning process does not include production (master planning generated planned production orders) and you require the built-in master planning engine beyond version 10.0.15.

Once the required features become available, we will provide a grace period until the exception expires. The environment admin will be informed when required features are available and the grace period starts.

## Frequently asked questions

### On-premises environments

My environment is on-premises, do I need an exception?

**Answer:** No, an exception isn't required for on-premises environments. You can continue to use the built-in master planning. Your environment admin will be informed if any action is needed.

### Production scenarios

We use planned production orders, but I'm concerned what will happen when we upgrade to version 10.0.16. Should I take any action?

**Answer:** You should not be concerned, we've got you covered. You can continue to use the built-in master planning with version 10.0.16. However, we recommend that you evaluate if migration to Planning Optimization can start with the current functionality and stay informed about new functionality.

### Mail from Microsoft

Our environment admin received a mail from Microsoft. This mail states that we should migrate to Planning Optimization or request an exception, do I need to take any actions?

**Answer:** Yes, your environment will be impacted unless you follow the instructions. Either you can migrate to Planning Optimization in due time or request an exception from the link in the mail. Once you have completed the questionnaire you will receive a reply via email. This is a manual process, but we try to reply within a week after submission.

### Is master planning blocked?

I'm using version 10.0.16, or later, and when running master planning, I get the following error message:

> You receive this error message because the built-in master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the current built-in master planning will be deprecated. Note that this master planning run did complete successfully.
>
> In case your migration has strong dependencies on pending features, an exception to continued usage of the built-in master planning engine can be requested.
>
> Please complete the following questionnaire to get started and if relevant request exception from migration to Planning Optimization.

**Answer:** No, your master planning run completed successfully, and you can use the result as usual. However, you need to migrate to Planning Optimization immediately, or request an exception using the link in the error message, to avoid this error in future master planning runs.
