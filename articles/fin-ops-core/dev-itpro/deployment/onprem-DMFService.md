---
# required metadata

title: Configure your environment with a dedicated Data Management Framework service
description: This article explains how to configure environments to use dedicated a separate service for the Data Management Framework.
author: faix
ms.date: 01/21/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.service: dynamics-365
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry:
ms.author: osfaixat
ms.search.validFrom: 2021-03-21
ms.dyn365.ops.version: 10.0.32
search.app:
  - financeandoperationsonprem-docs
---

# Configure your environment with a dedicated Data Management Framework service.

[!include[banner](../includes/banner.md)]

You can have dedicated nodes that contain SSIS, or you can install SSIS on other node types. If you want dedicated SSIS nodes, specify which machines host the node type by filling in the details for that node in the ConfigTemplate.xml file.

If your use of DMF is low, you might choose not to have dedicated nodes. Instead, you can choose which nodes have SSIS installed by updating the **hasSSIS** attribute to **true** for each VM in the **ServiceFabricCluster** section of your ConfigTemplate.xml file. In this case, you should set the **disabled** attribute to **true** for the **SSISNodeType** node type in your ConfigTemplate.xml file.

> [!NOTE]
> If you disable the **SSISNodeType** node type but don't set the **hasSSIS** attribute on any node, the scripts and installation logic provision the DMF service to all nodes of the **BatchOnlyAOSNodeType** type. If that node type doesn't exist, the DMF service is provisioned to all nodes of the **AOSNodeType** type.

## New environments (10.0.32 and later)

If you deploy an environment starting with Application Version 10.0.32 or later, your environment contains a dedicated service for the Data Management Framework.

## Existing environments (10.0.31 and earlier)

If you deployed your Microsoft Dynamics 365 for Finance + Operations (on-premises) environment before Application Version 10.0.32, you can manually configure your environment to use a dedicated service for the Data Management Framework.

> [!IMPORTANT]
> If you use an environment that was deployed before Application Version 10.0.32, you must update your environment to Application Version 10.0.32 or later before you can configure your environment to use a dedicated service for the Data Management Framework.

### Use new nodes

You can follow the guide to [Add an SSIS node to an existing environment](./ssis-node.md) to add a new node to your cluster.

### Use existing nodes

1. Ensure you download the latest infrastructure scripts: [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
1. If you don't already have a gMSA account for the DMF service, create it by updating your ConfigTemplate.xml file and run the following command.

```powershell
.\Create-GMSAAccounts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

1. Run the following script to create the file share.

```powershell
.\New-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
```

1. Run the following script to apply the required configuration and permissions to each file share.

```powershell
.\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
.\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "aos"
```

1. If you want to have the DMF service run on specific nodes, you can update the ConfigTemplate.xml file and set the **hasSSIS** property to **true** for the exact nodes you want.

> [!NOTE]
> Starting with infrastructure scripts 2.20.0 and local agent 3.3.0, node tag management is carried out automatically and no action is required if a node is restarted. If you use an older version of the infrastructure scripts or local agent, you must run the following command from a node that belongs to the Service Fabric cluster.
> ```powershell
> .\Set-SFDynamicNodeTags.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
> ```

1. Export the certificates

```PowerShell
# Exports certificates into a directory VMs\<VMName>. All of the certs are written to the infrastructure\Certs folder.
.\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```
1. Export the scripts

```PowerShell
.\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -D365FOVersion <application version: i.e. 10.0.40>
```

1. Complete the prerequisites

```powershell
.\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

1. Set up the following predeployment script: [TSG_EnableDixfService.ps1](./onprem-tsg-implementations.md#enableDixf)

1. Using the **Apply updates** option in Lifecycle Services, apply an update to the environment. The servicing flow automatically enables/deploys the new DMF service.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

