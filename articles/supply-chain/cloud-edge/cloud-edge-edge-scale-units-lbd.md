---
# required metadata

title: Cloud and Edge - Edge Scale Units using LBD
description: Provision edge scale units on premises using custom hardware and LBD based deployment
author: cabeln
manager: 
ms.date: 11/03/2017
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
ms.dyn365.ops.version: AX 10.0.15
---

# Deploy custom edge scale units on custom hardware using LBD - public preview

> [!CAUTION]
> The scale unit capability for Dynamics 365 Supply Chain Management is made available on the condition you agree to these Preview Terms. [**LINK MISSING**]

Edge scale units can be deployed by creating a Local Business Data environment and then configuring it to function as a scale unit. This is achieved by associating the LBD environment with a Dynamics 365 Supply Chain Management Cloud environment, that has been configured to function as a hub for scale units.  

This document describes how to setup an on-premises LBD environment as an edge scale unit, which can then be associated to a hub-configured cloud service fabric based environment.

## Steps to create an environment for an on-premise edge scale unit using LBD deployment mechanics

This table provides an overview on the deployment steps

|Responsibility  |Step  |Details  |
|---------|---------|---------|
|Microsoft|Create LCS On-Premise Implementation project with one sandbox slot for Scale Unit environment.||
|Customer|Setup LBD environment with empty database.|[Documentation](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12)|
|Customer|Deploy LBD environment through LCS.|[Documentation](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12)|
|Customer / Microsoft|Upload package with the same app/plat build that was deployed on Hub to LCS asset library of On-Premise project.|         |
|Customer|Upload customization package that was deployed on Hub to LCS asset library of On-Premise project.|         |
|Customer|Service LBD environment with previously uploaded app/plat package.|This will ensure that Hub and Spoke have the same build deployed.|
|Microsoft|Service LBD environment with previously uploaded customization package.|This will make non-shippable models and customer's customizations available on LBD environment.|
|Customer|Setup Cloud&Edge Pre Deployment script on LBD environment.|This script will inject needed attributes in topology (instance id, triggers enabled and scale unit enabled).|
|Customer|Run Update Settings action through LCS.|Run this action with same settings that already exist on environment. This action will then deploy again what was already deployed on environment but it will run previously setup Pre Deployment script which will inject necessary attributes so they can be passed to DbSync execution.|
|Customer|Compete the scale unit configuration and workload assignment using the Scale Unit Manager portal.|[Scale Unit Manager](https://sum.dynamics.com)|

### Create LCS On-Premise Implementation project

Go to LCS main page (https://lcs.dynamics.com for production or https://lcs.tie.dynamics.com for test environments).
Click + button and create Implementation project.
Make sure there is at least one sandbox slot available to deploy.

:::image type="content" source="./media/cloud_edge-lbd-lcs2.png" alt-text="Select LCS project type":::

:::image type="content" source="./media/cloud_edge-lbd-lcs3.png" alt-text="Navigate to LCS to configure your environment":::

### Setup and deploy LBD environment with empty database

1. Follow the [documentation to setup LBD environment](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12)
1. Step 14. Configure databases describes how to setup database with either Demo data or Empty data. Use empty data .bak file on this step.
1. Final step in mentioned documentation is deploying environment. Deploy latest available application and platform version which is 10.0.8/PU34 at the moment.

### Upload target packages to LCS

1. Upload the same combined application/platform package that was applied to Hub environment to Asset Library of LCS On-Premise project.
1. Upload custom deployable package that was applied to Hub environment to Asset Library of LCS On-Premise project.

### Service LBD environment with target packages

1. Service LBD environment with combined application/platform package that was uploaded in previous step.
1. Service LBD environment with custom deployable package that was uploaded in previous step.

:::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbdenv1.png" alt-text="Service LBD Environment 1":::

:::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbdenv2.png" alt-text="Service LBD Environment 2":::

### Update topology

1. Download Infrastructure scripts.

    This is already part of setting up LBD environment as [described here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/setup-deploy-on-premises-pu12).

1. Setup PreDeployment script.

    - Copy Configure-CloudAndEdge.ps1 script from Infrastructure Scripts folder to the Scripts folder in agent file storage share that was setup on the environment. Example of a path is: \\lbdiscsi01\agent\Scripts\Configure-CloudAndEdge.ps1.
    - Copy D365FO-OP folder from Infrastructure Scripts folder to the Scripts folder in agent file storage share that was setup on the environment. Example of a path is: \\lbdiscsi01\agent\Scripts\D365FO-OP.
    - Create PreDeployment.ps1 script that will invoke Configure-CloudAndEdge.ps1 with necessary parameters. PreDeployment script needs to be placed in Scripts folder in agent share in order to be run. Example of a path is: \\lbdiscsi01\agent\Scripts\PreDeployment.ps1.
    - Content of PreDeployment.ps1 can look like this:
    >         $agentShare = '\\lbdiscsi01\agent'
    >         
    >         Write-Output "AgentShare is set to $agentShare"         
    >         & $agentShare\Scripts\Configure-CloudandEdge.ps1 -AgentShare $agentShare -InstanceId '@A' -DatabaseServer 'lbdsqla01.contoso.com' -DatabaseName 'AXDB'

1. Redeploy the environment.

- This can be done by triggering Update Settings action from LCS without changing any of the values in the form.
- That action will redeploy environment and PreDeployment.ps1 will be invoked before deployment which will update environment's topology.
- Update Settings action is used to update some topology values such as certificate thumbprints, but it can be used for this purposes if all the values are left unchanged.
- Update Settings action consists of two steps.
- Prepare - This is triggered through LCS Maintain > Update Settings.
- Deploy - This needs to be triggered after preparation step is done (takes couple of minutes). Deploy can be triggered from environment's details LCS page.

:::image type="content" source="./media/cloud_edge-lbd-lcs-servicelbd-updatesettings.png" alt-text="Deploy updates from LBD":::

### Assign your LBD edge scale unit to a hub

#### Configuration step on the hub environment

In order to assign your scale unit to a Dynamics 365 Supply Chain Management hub environment run the following steps in the hub environment:

- Navigate to the *ScaleUnitHubSetup* menu item
- Enter the following value
  - Name
  - Hub AAD client id (Available from  AAD App registrations in the Azure portal)
- Prepare workloads to be configured (see section below)
- Enter the scale units and their associated work loads
- Click on Setup Hub
:::image type="content" source="media/cloud_edge-lbd-configurehub.png" alt-text="Configure you hub for a edge scale unit":::

### Configuration step on the LBD scale unit environment

- Go to ScaleUnitSetup menuitem
- Enter the following value
  - Name (should match the value you have entered in the Hub setup)
  - Hub resource Id
    - https://usnconeboxax1aos.cloud.onebox.dynamics.com 
  - Hub url
    - https://usnconeboxax1aos.cloud.onebox.dynamics.com/  (note the trailing '/')
  - Hub AAD tenant id
    - https://login.windows-ppe.net/AX7Partner.ccsctp.net 
  - Hub AAD client id & Hub encrypted secret (Available from AAD App registrations in the Azure portal)
- Click on "Initialize scale unit" to bootstrap the scale unit with initialization data from the hub.
- Click Deploy.

#### Prepare workloads to be configured

##### WES

Before configuring the WES workload the **Organization-wide work blocking** and **Automatic assigning of the guids on WHS user creation** (should be enabled by default) features should be enabled from feature management.

##### MES

Nothing to be done here.
