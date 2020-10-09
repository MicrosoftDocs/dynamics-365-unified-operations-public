---
# required metadata

title: Deploy custom edge scale units on custom hardware using LBD
description: Provision edge scale units on premises using custom hardware and LBD based deployment
author: cabeln
manager: 
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgShopSupervisorWorkspace, ProdTable, ProdTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: cabeln
ms.search.validFrom: 2020-09-23
ms.dyn365.ops.version: 10.0.15
---

# Deploy custom edge scale units on custom hardware using LBD

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Edge scale units can be deployed by creating a Local Business Data (LBD) environment and then configuring it to function as a scale unit. This is achieved by associating the LBD environment with a Supply Chain Management cloud environment that has been configured to function as a hub for scale units.  

This document describes how to set up an on-premises LBD environment as an edge scale unit, which can then be associated to a hub-configured cloud service fabric based environment.

## Create an environment for an on-premises edge scale unit using LBD deployment mechanics

The following table provides an overview of the deployment steps.

|Responsibility  |Step  |Details  |
|---------|---------|---------|
|Microsoft|An additional 60 day limited slot for an LBD environment will be provided based on customer situation.|Edge scale unit in preview target existing LBD customers.|
|Customer|Set up the LBD environment with empty database. | More information: [Set up and deploy on-premises environments (Platform update 12 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12.md) |
|Customer|Deploy the LBD environment through LCS.|More information: [Set up and deploy on-premises environments (Platform update 12 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12.md) |
|Customer / Microsoft|Upload a package with the same application and platform build that was deployed on the hub to the LCS asset library of the on-premises project.|         |
|Customer|Upload a customization package that was deployed on the hub to the LCS asset library of the on-premises project.|         |
|Customer|Service the LBD environment with the previously uploaded application and platform package.|This ensures that the hub and spoke have the same build deployed.|
|Customer|Service the LBD environment with the previously uploaded customization package.|This makes non-shippable models and your customizations available on the LBD environment.|
|Customer|Set up the cloud and edge pre-deployment script on the LBD environment.|This script injects the attributes needed by the topology (instance ID, triggers enabled, and scale unit enabled).|
|Customer|Run the "update settings" action through LCS.|Run this action with the same settings that already exist on the environment. This action then redeploys what was already deployed on the environment, but it will run the previously setup pre-deployment script, which will inject the necessary attributes so they can be passed to DbSync execution.|
|Customer|Compete the scale unit configuration and workload assignment using steps listed in [Assign your LBD edge scale unit to a hub](#assign-your-lbd-edge-scale-unit-to-a-hub) | |

## Set up and deploy an LBD environment with empty database

Do the following:

1. Follow the instructions given in [Set up and deploy on-premises environments (Platform update 12 and later)](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12.md).
1. [Step 14. Configure databases](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12.md#configuredb) describes how to set up database with either demo data or empty data. Use the empty data .bak file for this step.
1. Final step is deploying the environment. Deploy the latest available application and platform version.

## Upload target packages to LCS

Do the following:

1. Upload the same combined application/platform package that was applied to the hub environment to the asset library of the LCS on-premises project.
1. Upload the custom deployable package that was applied to the hub environment to the asset library of the LCS on-premises project.

## Service the LBD environment with target packages

Do the following:

1. Service the LBD environment with the combined application/platform package that was uploaded in previous step.
1. Service the LBD environment with the custom deployable package that was uploaded in the previous step.

    :::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbdenv1.png" alt-text="Service LBD Environment 1":::
    
    :::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbdenv2.png" alt-text="Service LBD Environment 2":::

## Update topology

Do the following:

1. Download the infrastructure scripts. (This is already part of [setting up an LBD environment](../../fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12.md).)

1. Set up the pre-deployment script.

    - Copy the `Configure-CloudAndEdge.ps1` script from the `Infrastructure Scripts` folder to the `Scripts` folder on the agent file storage share that was set up on the environment. A typical path is: `\\lbdiscsi01\agent\Scripts\Configure-CloudAndEdge.ps1`.
    - Copy the `D365FO-OP` folder from the `Infrastructure Scripts` folder to the `Scripts` folder in the agent file storage share that was set up on the environment. A typical path is: `\\lbdiscsi01\agent\Scripts\D365FO-OP`.
    - Create the `PreDeployment.ps1` script that will invoke `Configure-CloudAndEdge.ps1` with the necessary parameters. The pre-deployment must be placed in the `Scripts` folder on the agent share to be run. A typical path is: `\\lbdiscsi01\agent\Scripts\PreDeployment.ps1`.
    - The content of `PreDeployment.ps1` can look like this:

        ```plaintext
        $agentShare = '\\lbdiscsi01\agent'
        
        Write-Output "AgentShare is set to $agentShare" 
        & $agentShare\Scripts\Configure-CloudandEdge.ps1 -AgentShare $agentShare -InstanceId '@A' -DatabaseServer 'lbdsqla01.contoso.com' -DatabaseName 'AXDB'
        ```

1. Redeploy the environment.

    - This can be done by triggering the **Update settings** action from LCS without changing any of the values in the form.
    - That action will redeploy the environment and `PreDeployment.ps1` will be invoked before deployment, which will update environment's topology.
    - The **Update settings** action is often used to update some topology values such as certificate thumbprints, but it can also be used for this purposes if all the values are left unchanged.
    - The **Update settings** action consists of two steps:
        - **Prepare** - This is triggered through LCS by selecting **Maintain > Update settings**.
        - **Deploy** - This must be triggered after the preparation step is finished, which takes a few minutes. Deployment can be triggered from the environment's details LCS page.

        :::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbd-updatesettings.png" alt-text="Deploy updates from LBD":::

## Assign your LBD edge scale unit to a hub

> [!IMPORTANT]
> If want to use edge scale units with your preview deployment you need to do all scale unit configuration in the user experience on the hub as described below. The Scale Unit Manager Portal cannot be used if you include an edge scale unit.

### Configure the hub environment

To assign your scale unit to a Supply Chain Management hub environment, run the following steps on the hub environment:

1. Open the **ScaleUnitHubSetup** menu item.
1. Enter values for the following fields:
      - **Name** - Enter a name.
      - **Hub AAD client ID** - Available from AAD App registrations on the Azure portal.
1. Prepare workloads to be configured (see the next section).
1. Enter the scale units and their associated work loads.
1. Select **Set up hub**.
:::image type="content" source="media/cloud_edge-lbd-configurehub.png" alt-text="Configure you hub for a edge scale unit":::

### Configure the LBD scale unit environment

1. Go to the **ScaleUnitSetup** menu item
1. Enter values for the following fields:
      - **Name** - Should match the value you have entered for the hub setup.
      - **Hub resource ID** - Enter *https://contosohub.sandbox.operations.dynamics.com*.
      - **Hub URL** - Enter *https://contosohub.sandbox.operations.dynamics.com/*. (Note the trailing "/".)
      - **Hub AAD tenant ID** - Enter *https://login.windows.net/contoso.com*.
      - **Hub AAD client ID** - Available from AAD App registrations in the Azure portal.
      - **Hub encrypted secret** - Available from AAD App registrations in the Azure portal.
1. Select **Initialize scale unit** to bootstrap the scale unit with initialization data from the hub.
1. Select **Deploy**.

### Prepare workloads to be configured

#### Warehouse management workloads

Before configuring a warehouse management workload, please validate that on the hub in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) the following to features are enabled:

- *Organization-wide work blocking*
- *Automatic assigning of the guids on WHS user creation* (should be enabled by default)

#### Manufacturing execution workloads

No additional steps are needed.
