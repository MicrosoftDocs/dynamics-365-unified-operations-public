---
# required metadata

title: Setup VS 2017 Build agent to build Modern POS
description: TThis document explains how to setup self hosted build agent to build Modern POS(MPOS) in Azure DevOps pipeline. 
author: mugunthanm
ms.date: 12/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

audience: Developer
ms.reviewer: tfehr
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 12-13-2021
ms.dyn365.ops.version: AX 10.0.22


---


# Setup VS 2017 Build agent to build Modern POS

[!include [banner](../../../includes/banner.md)]

This document explains how to setup self-hosted build agent to build Modern POS(MPOS) in Azure DevOps pipeline. 

## Why can’t I use Azure DevOps hosted agent?

Modern POS(MPOS) can be compiled only using VS 2017, or if you are using Azure DevOps build pipeline the build agent specification must be vs2017-win2016. 
Starting **March 2022,** the [Windows Server 2016 with Visual Studio 2017 image is being deprecated]( https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops) and this will impact Azure DevOps pipeline which is using this build agent and you will not be able to build and package MPOS extensions.

To mitigate this issue, use a [self-hosted build agent in the Azure DevOps build pipeline]( https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops) to build MPOS extensions.

## Steps to create and configure the self-hosted build agent to build MPOS Extensions in the build pipeline:

1.	Create a new [VM in the Azure portal]( https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal), use Windows Server 2022 Datacenter Image.

> [!NOTE]
> You can also use the existing VMs, or build VM provisioned in Lifecycle services, it’s not required to provision a new VM, if available use the existing VMs.

2.	Install Visual Studio 2017 and other prerequisites documented [here]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-overview#prerequisites) in the VM.
3.	Create a Personal access token in the Azure DevOps project to authenticate the agent. Detailed steps are documented [here]( https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops#authenticate-with-a-personal-access-token-pat).
4.	Download and install the build agent in the VM created in the previous step, detailed steps to download and configure the agent are documented [here]( https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops#download-and-configure-the-agent).
 
5.	Update the Azure DevOps pipeline to use the new build agent pool. In pipeline select the Agent Pool in which you added your build agent configured in the previous steps.
    
> [!NOTE]
> The same build agent can be used to build other Dynamics 365 Commerce Extensions.

6.	Save the pipeline and validate the changes by queuing a new build.
 
