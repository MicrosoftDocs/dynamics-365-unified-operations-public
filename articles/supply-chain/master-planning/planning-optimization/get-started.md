---
# required metadata

title: Get started with Planning Optimization
description: This topic explains how to start to use the Planning Optimization functionality. 
author: t-benebo
ms.date: 05/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Get started with Planning Optimization

[!include [banner](../../includes/banner.md)]

As [previously announced](../../get-started/removed-deprecated-features-scm-updates.md#use-of-built-in-supply-chain-management-master-planning-engine-for-distribution-scenarios), Planning Optimization is scheduled to replace the existing built-in master planning engine.

If you currently use the built-in master planning engine, you should start planning your migration to Planning Optimization now. It is important to start the migration process right away because your operations may be impacted when deprecation is enforced. To avoid last-minutes issues when deprecation is enforced, we strongly encourage you to complete the migration before December 1, 2020. 

The Planning Optimization functionality doesn't currently support all the features that are available in the planning engine that is built into Supply Chain Management. Therefore, it's important that you evaluate whether the feature set that is currently available in Planning Optimization will meet your requirements. The Planning Optimization functionality isn't currently turned on by default in Dynamics Lifecycle Services (LCS), so you have the opportunity to do your evaluation before the feature is turned on.

> [!NOTE]
> You need to request an exception from migration to Planning Optimization if your master planning process does not include production (master planning generated planned production orders) and you require the built-in master planning engine beyond version 10.0.15. Starting in version 10.0.16, an error will be shown in environments when running built-in master planning without generation of planned production orders. Planning Optimization should be used for all new deployments that do not generate planned production orders during master planning. Owners of existing environments running the built-in master planning engine without generation of Planned production orders, will receive a mail with details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

Before you turn on Planning Optimization, we strongly recommend that you evaluate the results of the Planning Optimization fit analysis. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

## Availability

Planning Optimization is currently available in the following Azure geographies: United States, Canada, Brazil, Europe, United Kingdom, Australia, Asia Pacific, Japan, and India. If you try to install the add-in from another geographic region, then LCS will show a message that this geographic is not supported. For more information about Azure geographies and the related regions, see [Azure geographies](https://azure.microsoft.com/global-infrastructure/geographies/#geographies).

Note that Planning Optimization does not support on-premises deployments of Dynamics 365 Supply Chain Management.

## Licensing

If you can run master planning by using your current license, you don't have to buy an additional license to start to use Planning Optimization.

## Install and enable Planning Optimization

To use Planning Optimization, you must make sure your system has all of the prerequisites in place and then enable its license key and install the Planning Optimization Add-in for Dynamics 365 Supply Chain Management.

### Prerequisites

Before you install the Planning Optimization Add-in, the following prerequisites must be in place:

- You must be running Supply Chain Management on an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation will not complete and you will need to cancel the installation.

- Your system must be set up for Power Platform integration. For more information, see [Microsoft Power Platform integration with Finance and Operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

### Enable the Planning Optimization license

To use Planning Optimization, you must enable its configuration key. To do so:

1. Put your system into maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, select the check box for **Planning Optimization**.
1. Turn off maintenance mode, as described in [Maintenance mode](../../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

### Install the Planning Optimization Add-in

You must install the add-in from your LCS project and then turn on the Planning Optimization functionality from the Supply Chain Management user interface.

To install the Planning Optimization Add-in:

1. Sign in to LCS, and open the desired environment.
1. Go to **Full details**.
1. Scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Planning Optimization**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that Planning Optimization is installing.
1. After a few minutes, **Installing** should change to **Installed** (you may need to refresh the page). When installed, you are ready to activate Planning Optimization in Dynamics 365 Supply Chain Management.

The main purpose of installing the Planning Optimization Add-in is to connect the service and the environment. Therefore, you must install the add-in separately on each environment where you will use Planning Optimization, regardless of any code moved between the environments.

## Integrate Planning Optimization with your system

To configure whether the Planning Optimization Add-in should be used for master planning, go to **Master planning** \> **Setup** \> **Planning Optimization parameters**.

### Connection status

The connection status indicates the current status of the connection between Supply Chain Management and the Planning Optimization service. The following table shows the possible values.

| Connection status | Description | Can Planning Optimization be used? |
|---|---|---|
| Connected | A connection has been established between the Planning Optimization service and Supply Chain Management. | Yes |
| Enabling connection | A request to turn on the connection to the Planning Optimization service is currently in progress. | No |
| Disconnected | There is no connection to the Planning Optimization service. The connection can be turned on from LCS, as described earlier in this topic. | No |
| Disabling connection | A request to turn off the connection to the Planning Optimization service is currently in progress. | No |
| Getting status | The system is waiting for status information from the Planning Optimization service. | No |

### The Use Planning Optimization option

The setting of the **Use Planning Optimization** option determines which planning engine is used for master planning:

- **Yes** – Planning Optimization is used for master planning.
- **No** – The built-in Supply Chain Management planning engine is used for master planning.

This setting applies to all legal entities (companies). It is not possible to use Planning Optimization in some legal entities and the built-in master planning in other legal entities.

> [!NOTE]
> If existing planning batch jobs that were created for the built-in Supply Chain Management planning engine are triggered while the **Use Planning Optimization** option is set to **Yes**, those jobs will fail.

### Integration with the setup

If the Planning Optimization is turned on, master planning is done by using the Planning Optimization Add-in. In this case, master planning results and features are affected.

## Additional resources

[Terms and conditions for the preview](https://go.microsoft.com/fwlink/?linkid=2015274)

[Planning Optimization overview](planning-optimization-overview.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
