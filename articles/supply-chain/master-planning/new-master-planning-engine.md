---
# required metadata

title: New master planning engine
description: This topic provides information about the new master planning engine and the migration needed. 
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
ms.author: kamaybac
ms.search.validFrom: 2020-11-05
ms.dyn365.ops.version: 

---

# New master planning engine

[!include [banner](../includes/banner.md)]

This topic describes the change in master planning engine used for Supply Chain Management. The new Planning Optimization will replace the current built-in master planning engine, that has started to deprecate. On this topic you will find information related to the impact on new and existing deployments, including the related actions needed.

## Planning Optimization

The Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management enables master planning calculation to occur outside Dynamics 365 Supply Chain Management and the related SQL database. The benefits that are associated with the Planning Optimization functionality include improved performance and minimal impact on SQL database during master planning runs. Quick planning runs can be done even during office hours, so that planners can immediately react to demand or parameter changes.

For more information, see [Planning Optimization overview.](https://docs.microsoft.com/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-overview)

## Deprecation

Currently we are in the process of deprecating the built-in planning engine in favor of Planning Optimization. This change affects all cloud environments. On premise are not affected. Starting in version 10.0.16, an error will be shown when running built-in master planning without generation of planned production orders. Note that the master planning run will complete successfully despite the error message.

See the announcements on [Removed or deprecated features.](https://docs.microsoft.com/dynamics365/supply-chain/get-started/removed-deprecated-features-scm-updates#use-of-built-in-supply-chain-management-master-planning-engine-for-manufacturing-scenarios)

## Migration

Owners of existing environments running the built-in master planning engine without generation of Planned production orders will receive a mail with details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

Starting in version 10.0.16, an error will be shown when running built-in master planning without generation of planned production orders. This error message includes guidance for migration and instructions on how to request an exception.

**New deployment**

Planning Optimization should be considered as the default master planning engine for all new deployments in the cloud. In general Planning Optimization should be used for all new deployments that do not generate planned production orders during master planning. In case a new deployment depends on functionality currently unsupported by Planning Optimization, an exception can be requested to use the built-in master planning engine.

**Existing deployment**

Existing deployments, in the cloud, that depend on master planning should plan migration to Planning Optimization. In case implementation depends on functionality currently unsupported by Planning Optimization, an exception can be requested.

For environments that currently utilize master planning processes that are being deprecated, an email is send to the environment admin. This email is informing about the actions necessary to migrate or request an exception.

## Exception process

You can request an exception and continue using the built-in master planning engine, if your business processes heavily depend on at least one of the features currently not implemented in Planning Optimization. The feature availability is listed in the Planning Optimization documentation, see [Planning Optimization fit analysis.](https://docs.microsoft.com/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-fit-analysis)

Currently an exception from migration to Planning Optimization is only relevant in case your master planning process does not include production (master planning generated planned production orders) and you require the built-in master planning engine beyond version 10.0.15.

Once the required features become available there will be a grace period until the exception expire. The environment admin will be informed when required features are available and the grace period start.

## Common questions

### On-premises
My environment is on-premises, do I need an exception?

**Answer:** No, exception is not required for on-premises environments. You can continue to use the built-in master planning. Your environment admin will be informed if any action is needed.

### Production scenarios
We use planned production orders, but I&#39;m concerned what will happen when we upgrade to 10.0.16. Should I take any action?

**Answer:** You should not be concerned, we got you covered. You can continue to use the built-in master planning with 10.0.16. However, we recommend that you evaluate if migration to Planning Optimization can start with the current functionality and stay informed about new functionality.

### Mail from Microsoft
Our environment admin received a mail from Microsoft. This mail is stating that we should migrate to Planning Optimization or request an exception, do I need to take any actions?

**Answer:** Yes, your environment will be impacted unless you follow the instructions. Either you can migrate to Planning Optimization in due time or request an exception from the link in the mail. Once you have completed the questionnaire you will receive a reply via email. This is a manual process, but we try to reply within a week after submission.

### Is master planning blocked?
I'm on version 10.0.16, or later, and when running master planning, I get the following error message:

_&quot;You receive this error message because the built-in master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the current built-in master planning will be deprecated. Note that this master planning run did complete successfully._

_In case your migration has strong dependencies on pending features, an exception to continued usage of the built-in master planning engine can be requested._

_Please complete the following questionnaire to get started and if relevant request exception from migration to Planning Optimization.&quot;_

**Answer:** No, your master planning run completed successfully, and you can use the result as normal. However, you need to migrate to Planning Optimization immediately, or request an exception using the link in the error message, to avoid this error in future master planning runs.
