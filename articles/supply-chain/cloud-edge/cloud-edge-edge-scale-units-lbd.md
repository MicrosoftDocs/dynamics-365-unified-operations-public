---
title: Deploy edge scale units on custom hardware using LBD (Preview)
description: This topic explains how to provision on-premises edge scale units by using custom hardware and deployment that is based on local business data (LBD). 
author: cabeln
ms.date: 04/13/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: cabeln
ms.search.validFrom: 2021-04-13
ms.dyn365.ops.version: 10.0.19
---

# Deploy edge scale units on custom hardware using LBD (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Edge scale units can be deployed by creating a local business data (LBD) environment and then configuring it to function as a scale unit in your distributed hybrid topology for Microsoft Dynamics Supply Chain Management. To achieve this effect, you associate the LBD environment with a hub Supply Chain Management cloud environment.

Edge scale units are still in preview. Therefore, you may use an environment of this type only according to the [preview terms](https://aka.ms/scmcnepreviewterms).

This topic describes how to set up an on-premises LBD environment as an edge scale unit and then associate it with a hub.

## Deployment overview

Here is an overview of the deployment steps.

1. **Enable an LBD slot in your LBD project in Microsoft Dynamics Lifecycle Services (LCS).**

    During preview, LBD edge scale units target existing LBD customers. An additional 60-day limited LBD sandbox slot will be provided in only specific customer situations.

1. **Set up and deploy an LBD environment with an *empty* database.**

    Use LCS to deploy the LBD environment with the latest topology and an empty database. For more information, see the [Setup and deploy an LBD environment with empty database](#set-up-deploy) section later in this topic.

1. **Upload target packages into LBD project assets in LCS.**

    Prepare application, platform, and customization packages that you use across the hub and the edge scale unit. For more information, see the [Upload target packages into LBD project assets in LCS](#upload-packages) section later in this topic.

1. **Service the LBD environment with the target packages.**

    This step ensures that the same build and customizations are deployed on the hub and the spoke. For more information, see the [Service the LBD environment with target packages](#service-target-packages) section later in this topic.

1. **Complete the scale unit configuration and workload assignment.**

    For more information, see the [Assign your LBD edge scale unit to a hub](#assign-edge-to-hub) section later in this topic.

The remaining sections of this topic provide more details about how to complete these steps.

## <a name="set-up-deploy"></a>Set up and deploy an LBD environment with an empty database

This step creates a functional LBD environment. However, the environment doesn't necessarily have the same application and platform versions as the hub environment. Additionally, it's still missing the customizations, and it hasn't yet been enabled to work as a scale unit.

1. Follow the instructions in [Setup and deploy on-premises environments (Platform update 41 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md).

    > [!IMPORTANT]
    > Read the rest of this section **before** you complete the steps in that topic.

1. When you describe your configuration in the infrastructure\\ConfigTemplate.xml file, don't specify any MR (Financial Reporting) nodes.
1. Set up a database that contains empty data, as described in [Configure databases](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu41.md#configuredb). Use the empty data.bak file for this step.
1. Set up the pre-deployment script. For more information, see [Local agent pre-deployment and post-deployment scripts](../../fin-ops-core/dev-itpro/lifecycle-services/pre-post-scripts.md).

    1. Copy the contents from the **ScaleUnit** folder in **Infrastructure Scripts** to the **Scripts** folder in the agent file storage share that was set up in the environment. A typical path is \\\\lbdiscsi01\\agent\\Scripts.
    2. Create the **PreDeployment.ps1** script that will invoke the scripts by using the required parameters. The pre-deployment script must be put in the **Scripts** folder in the agent file storage share. Otherwise, it can't be run. A typical path is \\\\lbdiscsi01\\agent\\Scripts\\PreDeployment.ps1.

        The contents of the PreDeployment.ps1 script will resemble the following example.

        ```powershell
        $agentShare = '\\lbdiscsi01\agent'
        
        Write-Output "AgentShare is set to $agentShare" 
        & $agentShare\Scripts\Configure-CloudandEdge.ps1 -AgentShare $agentShare -InstanceId '@A' -DatabaseServer 'lbdsqla01.contoso.com' -DatabaseName 'AXDB'
        ```

1. Deploy the environment by using the latest base topology that is available.

## <a name="upload-packages"></a>Upload target packages into LBD project assets in LCS

This step prepares the application version, platform version, and customizations that will be transitioned to your LBD scale unit environment.

1. Upload the same combined application/platform package that was applied to the hub environment into the asset library of the LCS on-premises project.
1. Get a copy of the custom deployable package that was applied to the hub environment, and upload it into the asset library of the LCS on-premises project.

## <a name="service-target-packages"></a>Service the LBD environment with target packages

This step aligns the application version, platform version, and customizations in your LBD scale unit environment with the hub.

1. Service the LBD environment with the combined application/platform package that you uploaded in the previous step.
1. Service the LBD environment with the custom deployable package that you uploaded in the previous step.

    ![Selecting Maintain > Apply updates in LCS](media/cloud_edge-LBD-LCS-ServiceLBDEnv1.png "Selecting Maintain > Apply updates in LCS")

    ![Selecting your customization package](media/cloud_edge-LBD-LCS-ServiceLBDEnv2.png "Selecting your customization package")

## <a name="assign-edge-to-hub"></a>Assign your LBD edge scale unit to a hub

While edge scale units are still in preview, you must use the [scale unit deployment and configuration tools](https://github.com/microsoft/SCMScaleUnitDevTools) that are available on GitHub to assign your LBD edge scale unit to a hub. The process enables an LBD configuration to function as an edge scale unit and associates it with the hub. The process resembles the process of configuring a One-Box development environment. For a step-by-step guide, see the [wiki for the configuration tool](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide).

When you use the tools, follow the guidance in the [Step by step usage guide](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide) to prepare the configuration file. Follow the entries and operations for the hub. For the LBD edge scale units, you must complete the `ScaleUnitConfiguration` section in the configuration file.

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
