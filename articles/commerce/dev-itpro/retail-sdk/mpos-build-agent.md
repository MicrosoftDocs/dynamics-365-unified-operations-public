---
# required metadata

title: Set up Visual Studio 2017 build agent to build Modern POS
description: This topic explains how to set up a self-hosted Visual Studio build agent to build Microsoft Dynamics 365 Commerce Modern POS (MPOS) in a Microsoft Azure DevOps pipeline.
author: mugunthanm
ms.date: 12/16/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 2017-06-20
---

# Set up Visual Studio 2017 build agent to build Modern POS

[!include [banner](../../../includes/banner.md)]

This topic explains how to set up a self-hosted Visual Studio build agent to build Microsoft Dynamics 365 Commerce Modern POS (MPOS) in a Microsoft Azure DevOps pipeline. 

## Create and configure the self-hosted Visual Studio build agent to build MPOS extensions in an Azure DevOps build pipeline

To create and configure the self-hosted Visual Studio build agent to build MPOS extensions in an Azure DevOps build pipeline, follow these steps.

1.	Create a new [virtual machine in the Azure portal](/azure/virtual-machines/windows/quick-create-portal) using Windows Server 2022 Datacenter image.

    > [!NOTE]
    > It is not required to provision a new virtual machine (VM), you can also use the existing VMs or build VMs provisioned in Microsoft Dynamics Lifecycle Services.

1.	Install Visual Studio 2017 and other prerequisites in the VM  For more information, see [Retail software development kit (SDK)](retail-sdk-overview.md#prerequisites).
1.	Create a personal access token in the Azure DevOps project to authenticate the agent. For more information, see [Authenticate with a personal access token (PAT)](/azure/devops/pipelines/agents/v2-windows?view=azure-devops#authenticate-with-a-personal-access-token-pat&preserve-view=true).
1.	Download and install the build agent in the VM created in the previous step. For detailed steps on downloading and configuring the agent, see [Download and configure the agent](/azure/devops/pipelines/agents/v2-windows?view=azure-devops#download-and-configure-the-agent&preserve-view=true).

    ![Build agent setup](media/AgentSetup.png)
 
1.	Update the Azure DevOps pipeline to use the new build agent pool. In the pipeline, from the **Agent pool** drop-down list select the agent pool for which you added your build agent configured in the previous steps.
    
    ![Build agent configuration](media/AgentConfigure.png)

    > [!NOTE]
    > The same build agent can be used to build other Dynamics 365 Commerce extensions.

1.	Save the pipeline and validate the changes by queuing a new build.

### Why can't I use an Azure DevOps hosted agent?

Modern POS (MPOS) can only be compiled using Visual Studio 2017. If you are using a Azure DevOps build pipeline, the build agent specification must be **vs2017-win2016**. 
Starting in March 2022, the Windows Server 2016 with Visual Studio 2017 image will be deprecated which will impact Azure DevOps pipelines using this build agent. In this case you will not be able to build and package MPOS extensions.

To mitigate this issue, use a [self-hosted build agent in the Azure DevOps build pipeline](/azure/devops/pipelines/agents/v2-windows?view=azure-devops&preserve-view=true) to build MPOS extensions.
