---
title: Deploy edge scale units on custom hardware using LBD
description: Provision edge scale units on premises using custom hardware and LBD based deployment
author: cabeln
ms.date: 04/08/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: cabeln
ms.search.validFrom: 2021-04-08
ms.dyn365.ops.version: 10.0.19
---

# Preview: Deploy edge scale units on custom hardware using LBD

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Edge scale units can be deployed by creating a local business data (LBD) environment and then configuring it to function as a scale unit in your distributed hybrid topology for supply chain management. This is achieved by associating the LBD environment with a hub Supply Chain Management cloud environment.  

Edge scale units are still in preview. Therefore you may use such environment only according to the [preview terms](https://aka.ms/scmcnepreviewterms).

This document describes how to set up an on-premises LBD environment as an edge scale unit,and then how to associate it to a hub.

## Deployment overview

The following table provides an overview of the deployment steps.

|Actions  |Details  |
|---------|---------|
|1. Enable an LBD slot in your LBD Lifecycle Services (LCS) project.|LBD edge scale unit during preview target existing LBD customers. An additional 60-day limited LBD sandbox slot will be only provided in certain customer situations.|
|2. Set up and deploy an LBD environment with an *empty* database. | Deploy the LBD environment through LCS with latest Preview Early Access Program (PEAP) build and empty database. For more information, see [Setup and deploy an LBD environment with empty database](#set-up-deploy). |
|3. Upload target packages into LBD project assets  in LCS.|Prepare application, platform and customizations package that you use across hub and edge scale unit. For more information, see [Upload target packages into LBD project assets in LCS](#upload-packages) |
|4. Service the LBD environment with the target packages.|This ensures that the hub and spoke have the same build and customizations deployed. For more information, see [Service the LBD environment with target packages](#service-target-packages)|
|5. Compete the scale unit configuration and workload assignment as described in [Assign your LBD edge scale unit to a hub](#step-2-assign-your-lbd-edge-scale-unit-to-a-hub) |See [Assign your LBD edge scale unit to a hub](#assign-edge-to-hub) |

<a name="set-up-deploy"></a>

## Set up and deploy an LBD environment with empty database

This step creates a functional LBD environment. However, the environment won't necessarily have the same application and platform versions as the hub environment, will still be missing the customizations, and won't have been enabled to function as a scale unit.

Do the following:

1. Follow the instructions given in [Setup and deploy on-premises environments (Platform update 41 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md).

> [!IMPORTANT]
> Read the rest of this section before you proceed to carry out the steps in the guide above.

1. When describing your configuration in the infrastructure\ConfigTemplate.xml do not specify any MR (Financial Reporting) nodes.
1. Set up a database that contains empty data as described in [Configure databases](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md#configuredb). Use the empty `data.bak` file for this step.
1. Set up the pre-deployment script. For more information see [Local agent pre-deployment and post-deployment scripts](../../fin-ops-core/dev-itpro/lifecycle-services/pre-post-scripts.md)

    - Copy the contents from the `ScaleUnit` folder in the `Infrastructure Scripts` to the `Scripts` folder on the agent file storage share that was set up on the environment. A typical path is: `\\lbdiscsi01\agent\Scripts`.
    - Create the `PreDeployment.ps1` script that will invoke the scripts with the necessary parameters. The pre-deployment must be placed in the `Scripts` folder on the agent share to be run. A typical path is: `\\lbdiscsi01\agent\Scripts\PreDeployment.ps1`.
    - The content of `PreDeployment.ps1` will resemble the following example:

        ```powershell
        $agentShare = '\\lbdiscsi01\agent'
        
        Write-Output "AgentShare is set to $agentShare" 
        & $agentShare\Scripts\Configure-CloudandEdge.ps1 -AgentShare $agentShare -InstanceId '@A' -DatabaseServer 'lbdsqla01.contoso.com' -DatabaseName 'AXDB'
        ```

1. Deploy the environment using the latest base topology available.

<a name="upload-packages"></a>

## Upload target packages into LBD project assets in LCS

This step prepares the application version, platform version, and customizations that will be transitioned to your LBD scale unit environment.

Do the following:

1. Upload the same combined application/platform package that was applied to the hub environment to the asset library of the LCS on-premises project.
1. Get a copy of the custom deployable package that was applied to the hub environment and upload it to the asset library of the LCS on-premises project.

<a name="service-target-packages"></a>

## Service the LBD environment with target packages

This step aligns the application version, platform version, and customizations on your LBD scale unit environment with the hub.

Do the following:

1. Service the LBD environment with the combined application/platform package that you uploaded in previous step.
1. Service the LBD environment with the custom deployable package that you uploaded in the previous step.

    ![Service LBD Environment 1](media/cloud_edge-lbd-lcs-servicelbdenv1.png "Service LBD Environment 1")

    ![Service LBD Environment 2](media/cloud_edge-lbd-lcs-servicelbdenv2.png "Service LBD Environment 2")

<a name="assign-edge-to-hub"></a>

## Assign your LBD edge scale unit to a hub

While edge scale units are still in preview, you must use the [scale unit deployment and configuration tools available on GitHub](https://github.com/microsoft/SCMScaleUnitDevTools) to assign your LBD edge scale unit to a hub. The process enables an LBD configuration to function as an edge scale unit and associates it to the hub. The process is similar to configuring a One-Box development environment. For a step-by-step guide, see the [wiki for the configuration tool](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide).

When using the tools, please follow the guidance in the [Wiki](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide) to prepare the configuration file. Follow the entries and operations for the hub. For the LBD edge scale units, you must complete the `ScaleUnitConfiguration` section on the config file.
