---
# required metadata

title: Set up Visual Studio 2017 build agent to build Modern POS
description: This topic explains how to set up a self-hosted Visual Studio build agent to build Microsoft Dynamics 365 Commerce Modern POS (MPOS) in a Microsoft Azure DevOps pipeline.
author: mugunthanm
ms.date: 12/13/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 2017-06-20
---

# Set up VS 2017 build agent to build Modern POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to set up a self-hosted Visual Studio build agent to build Microsoft Dynamics 365 Commerce Modern POS (MPOS) in a Microsoft Azure DevOps pipeline. 

## Why can't I use Azure DevOps hosted agent?

Modern POS(MPOS) can be compiled only using VS 2017, or if you are using Azure DevOps build pipeline the build agent specification must be vs2017-win2016. 
Starting **March 2022,** the [Windows Server 2016 with Visual Studio 2017 image is being deprecated](/azure/devops/pipelines/agents/v2-windows?view=azure-devops&preserve-view=true) and this will impact Azure DevOps pipeline which is using this build agent and you will not be able to build and package MPOS extensions.

To mitigate this issue, use a [self-hosted build agent in the Azure DevOps build pipeline](/azure/devops/pipelines/agents/v2-windows?view=azure-devops&preserve-view=true) to build MPOS extensions.

## Steps to create and configure the self-hosted build agent to build MPOS Extensions in the build pipeline:

1.	Create a new [VM in the Azure portal](/azure/virtual-machines/windows/quick-create-portal), use Windows Server 2022 Datacenter Image.

> [!NOTE]
> You can also use the existing VMs, or build VM provisioned in Lifecycle services, it’s not required to provision a new VM, if available use the existing VMs.

2.	Install Visual Studio 2017 and other prerequisites documented [here](retail-sdk-overview.md#prerequisites) in the VM.
3.	Create a Personal access token in the Azure DevOps project to authenticate the agent. Detailed steps are documented [here](/azure/devops/pipelines/agents/v2-windows?view=azure-devops#authenticate-with-a-personal-access-token-pat&preserve-view=true).
4.	Download and install the build agent in the VM created in the previous step, detailed steps to download and configure the agent are documented [here](/azure/devops/pipelines/agents/v2-windows?view=azure-devops#download-and-configure-the-agent&preserve-view=true).

![Agent setup.](media/![Commerce components.](media/AgentSetup.png)
 
5.	Update the Azure DevOps pipeline to use the new build agent pool. In pipeline select the Agent Pool in which you added your build agent configured in the previous steps.
    
> [!NOTE]
> The same build agent can be used to build other Dynamics 365 Commerce Extensions.

![Agent configure.](media/AgentConfigure.png)

6.	Save the pipeline and validate the changes by queuing a new build.
 
