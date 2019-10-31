---
# required metadata

title: Get started with Planning Optimization
description: This topic explains how to get started with Planning Optimization. 
author: ChristianRytt
manager: AnnBe
ms.date: 10/29/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]


# Get started with Planning Optimization

Planning Optimization does not currently support all of the features that are available in the built-in Supply Chain Management planning engine. Therefore, it is important to evaluate if the currently available feature set in Planning Optimization covers your requirements. Planning Optimization is not enabled in LCS by default so that you have the opportunity to do your evaluation first.

Long term, Planning Optimization will replace the existing built-in Supply Chain Management planning engine.

We strongly recommend that you evaluate results from the Planning Optimization fit analysis before enabling Planning Optimization. Read the [Planning Optimization fit analysis](planning-optimization-fit-analysis.md) topic to learn more.

### Licensing

If you can run master planning with your current license, you don't need an additional license to start using Planning Optimization.

### Install the add-in

To use Planning Optimization, install the Planning Optimization Add-in for Dynamics 365 Supply Chain Management. Access the add-in from your Dynamics Lifecycle Services (LCS) project and enable the use of Planning Optimization from the Supply Chain Management user interface (UI).

1. Log in to LCS and navigate to the desired environment.
1. Go to **Full details**.
1. Click **Maintain** or scroll down to the **Environment add-ins** tab. 
1. Click **Install a new add-in**.
1. Click **Planning Optimization**.
1. Follow the installation guide and agree to the terms and conditions.
1. Click **Install**.

### Planning Optimization integration

To configure whether the Planning Optimization Add-in for Dynamics 365 Supply Chain Management will be used for master planning, go to **Master Planning** > **Setup** > **Planning Optimization integration** > **Integration parameters**.


#### Connection status

The connection status indicates the current status of the connection between Supply Chain Management and the Planning Optimization service. The table below shows the possible values.

| Connection status | Description | Can Planning Optimization be used |
| --- | --- | --- |
| **Connected** | Connection is established between the Planning Optimization service and Supply Chain Management. | Yes |
| **Enabling connection** | A request to enable the connection to the Planning Optimization service is currently in progress. | No |
| **Disconnected** | There is no connection to the Planning Optimization service. Connection can be enabled from LCS as described above. | No |
| **Disabling connection** | A request to disable the connection to the Planning Optimization service is currently in progress. | No |
| **Getting status** | The system is waiting for the status from the Planning Optimization service. | No |

#### Use Planning Optimization option

This option is used to control the planning engine used for master planning.

- **Yes**: Planning Optimization is used for master planning.

- **No**: The built-in Supply Chain Management planning engine is used for master planning.

> [!NOTE]
> If existing planning batch jobs created for the built-in Supply Chain Management planning engine are triggered when **Use Planning Optimization** is set to **Yes**, those jobs will fail.

### Integration with setup

If the Planning Optimization preview is enabled, master planning is done using the Planning Optimization Add-in for Supply Chain Management, which in turn impacts master planning results and features.

## Related resources
[Terms and conditions for the preview](https://go.microsoft.com/fwlink/?linkid=2015274)
