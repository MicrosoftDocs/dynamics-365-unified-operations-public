---
# required metadata

title: Get started with Planning Optimization
description: This topic explains how to start to use the Planning Optimization functionality. 
author: ChristianRytt
manager: tfehr
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Get started with Planning Optimization

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

The Planning Optimization functionality doesn't currently support all the features that are available in the planning engine that is built into Microsoft Dynamics 365 Supply Chain Management. Therefore, it's important that you evaluate whether the feature set that is currently available in Planning Optimization will meet your requirements. By default, the Planning Optimization functionality isn't turned on in Dynamics Lifecycle Services (LCS) by default. Therefore, you have an opportunity to do your evaluation before it's turned on.

Eventually, Planning Optimization will replace the existing built-in Supply Chain Management planning engine.

Before you turn on Planning Optimization, we strongly recommend that you evaluate the results of the Planning Optimization fit analysis. For more information, see [Planning Optimization fit analysis](planning-optimization-fit-analysis.md).

### Licensing

If you can run master planning by using your current license, you don't have to buy an additional license to start to use Planning Optimization.

### Install the add-in

To use Planning Optimization, install the Planning Optimization Add-in for Dynamics 365 Supply Chain Management. You can access the add-in from your LCS project and turn on the Planning Optimization functionality from the Supply Chain Management user interface (UI).

> [!NOTE]
> The requirement for Planning Optimization is an LCS enabled high-availability environment (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later.

1. Sign in to LCS, and open the desired environment.
1. Go to **Full details**.
1. Scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Planning Optimization**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab you should see that Planning Optimization is installing.
1. After a few minutes **Installing** should change to **Installed** (you may need to refresh the page). When installed, you are ready to activate Planning Optimization in Dynamics 365 Supply Chain Management.

### Planning Optimization integration

To configure whether the Planning Optimization Add-in should be used for master planning, go to **Master planning** \> **Setup** \> **Planning Optimization parameters**.

#### Connection status

The connection status indicates the current status of the connection between Supply Chain Management and the Planning Optimization service. The following table shows the possible values.

| Connection status | Description | Can Planning Optimization be used? |
|---|---|---|
| Connected | A connection has been established between the Planning Optimization service and Supply Chain Management. | Yes |
| Enabling connection | A request to turn on the connection to the Planning Optimization service is currently in progress. | No |
| Disconnected | There is no connection to the Planning Optimization service. The connection can be turned on from LCS, as described earlier in this topic. | No |
| Disabling connection | A request to turn off the connection to the Planning Optimization service is currently in progress. | No |
| Getting status | The system is waiting for status information from the Planning Optimization service. | No |

#### The Use Planning Optimization option

The setting of the **Use Planning Optimization** option determines which planning engine is used for master planning:

- **Yes** – Planning Optimization is used for master planning.
- **No** – The built-in Supply Chain Management planning engine is used for master planning.

> [!NOTE]
> If existing planning batch jobs that were created for the built-in Supply Chain Management planning engine are triggered while the **Use Planning Optimization** option is set to **Yes**, those jobs will fail.

### Integration with the setup

If the Planning Optimization preview is turned on, master planning is done by using the Planning Optimization Add-in. In this case, master planning results and features are affected.

## Related resources

[Terms and conditions for the preview](https://go.microsoft.com/fwlink/?linkid=2015274)

[Planning Optimization overview](planning-optimization-overview.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)
