---
# required metadata
title: Add an SSIS Node to an existing environment
description: This article explains how to add an SSIS node in an on-premises environment.
author: ttreen
ms.date: 08/17/2023
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: ttreen
ms.search.validFrom: 2023-08-17
ms.dyn365.ops.version: Platform update 58
search.app:
  - financeandoperationsonprem-docs
---

# Add an SSIS node

[!include[banner](../includes/banner.md)]

This article explains how to add an SSIS node in an existing on-premises environment. SSIS nodes were introduced in version 10.0.32 (Platform Update 56) and are used by Data management framework.

## Installation steps
1. Confirm your environment is on version 10.0.32 (Platform update 56) or higher.
2. Download and extract the latest setup scripts from Lifecycle Services [Download the infrastructure scripts](./obtain-infrascripts-onprem.md#download-the-infrastructure-scripts).
   > [!IMPORTANT]
   > The scripts must be run from a computer on the same domain as the on-premises infrastructure.
3. Update the infrastructure scripts. For more information, see [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
4. In the ConfigTemplate.xml file, in the SSISNodeType section, modify the SSIS node(s). Confirm the disabled parameter is false:
   ```XML
   <NodeType name="SSISNodeType" primary="false" namePrefix="SSIS" purpose="SSIS" disabled="false">
      <!-- Do not place hasSSIS on this node type. -->
      <VMList>
         <VM name="ssis1" ipAddress="10.179.108.22" faultDomain="fd:/fd0" updateDomain="ud0" />
         <VM name="ssis2" ipAddress="10.179.108.23" faultDomain="fd:/fd1" updateDomain="ud1" />
      </VMList>
   </NodeType>
   ```
5. Create the DIXF GMSA account. For more information, see [Step 8. Create gMSAs](./setup-deploy-on-premises-latest.md#setupgMSA). Option 1 creates just the new DIXF GMSA.
6. Set up and edit a new file share for DIXF. For more information, see [Step 9. Set up file storage](./setup-deploy-on-premises-latest.md#setupfile).
   > [!NOTE]
   > In the ConfigTemplate.xml file, set the disabled property to **True** for any existing file shares.  

7. Install SSIS on the nodes required. For more information, see [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupssis).
8. Open an Admin PowerShell, change to the Infrastructure scripts folder, and run the following script:
   ```PowerShell
   # Exports certificates into a directory VMs\<VMName>. All the certs will be written to the infrastructure\Certs folder.
   .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
   ```
9. Follow [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupvms).
10. Before adding the new node, update Service fabric to the latest version. For more information, see [Update fabric cluster](/azure/service-fabric/service-fabric-cluster-upgrade-windows-server)
11. If this is the first time adding in a DIXF node, add the node type to the existing Service fabric cluster. On one of the Orchestrator nodes, open an Admin PowerShell prompt and run the following commands:
```PowerShell
<#
SAMPLE CODE NOTICE

THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
#>

Param(
    # Path to the fileshare where the config.json is located for your deployment
    [Parameter(Mandatory)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({ Test-Path -Path $_ })]
    [string] $ClusterConfigFilePath,

    # Just test if section is not there
    [Switch] $Test
)

#requires -Version 5
$ErrorActionPreference = 'Stop'
$InformationPreference = 'Continue'
Import-Module "$PSScriptRoot\D365FO-OP" -Force

$SectionToAdd = '{
    "name": "SSISNodeType",
    "clientConnectionEndpointPort": "19000",
    "clusterConnectionEndpointPort": "19001",
    "leaseDriverEndpointPort": "19002",
    "serviceConnectionEndpointPort": "19003",
    "httpGatewayEndpointPort": "19080",
    "reverseProxyEndpointPort": "19081",
    "applicationPorts": {
        "startPort": "20001",
        "endPort": "20031"
    },
    "ephemeralPorts": {
        "startPort": "49152",
        "endPort": "65535"
    },
    "isPrimary": false,
    "placementProperties": {
        "HasSSIS": "True"
    }
}'

$ClusterConfigFile = Get-Content -Path $ClusterConfigFilePath -Raw
$ClusterConfigObject = $ClusterConfigFile | ConvertFrom-Json
$SSISNodeType = $ClusterConfigObject.properties.nodeTypes | Where-Object { $_.name -eq "SSISNodeType" }

if (-not $SSISNodeType) 
{
    if(-not $Test)
    {
        $NewNodeType = $SectionToAdd | ConvertFrom-Json
        $ClusterConfigObject.properties.nodeTypes += $NewNodeType
        Update-D365FOClusterConfigurationVersion -ConfigJson $ClusterConfigObject -Minor
        Save-D365FOJsonToFile -JsonObject $ClusterConfigObject -FilePath $ClusterConfigFilePath
        Write-Host "SSISNodeType added to file '$ClusterConfigFilePath'"
    }
    else
    {
        Write-Host "SSISNodeType does not exists."
    }
} 
else 
{
    Write-Host "SSISNodeType already exists."
}


```
Update the Service Fabric cluster to add in the new node type:

Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath C:\Temp\ClusterConfig.json


12.	Add the new DIXF Node and follow these steps:

a)	In Service fabric explorer, select **Cluster**. Note the Microsoft service fabric cluster version.
b)	On one of the orchestrator nodes, open File explorer. On the **View** tab, in the **Show/hide** group, confirm the **File name extensions** and **Hidden items** checkboxes are selected.
c)	Expand drive C, and drill down into the following folder: (The path varies depending on the node name and setup.)
C:\ProgramData\SF\ORCH1\Fabric\work\Applications\__FabricSystem\_App4294967295\work\Store\131811633624852852
d)	There's a list of folders for various versions of Service fabric.
e)	Open the folder with the same name as the version of Microsoft service fabric cluster noted earlier.
f)	Locate and copy the .cab file to C:\Temp. Rename the copied file MicrosoftAzureServiceFabric.cab.
g)	Open a PowerShell command prompt window as admin.
h)	Run the following command to connect to your Service fabric cluster. (Edit the command as needed.)

#Connect to Service Fabric Cluster. Replace 123 with server/star thumbprint and use appropriate IP address.
Connect-ServiceFabricCluster 

i)	Before running the following command to add the node, update the NodeName, IPAddress, UpgradeDomain, and FaultDomain parameters. 

Add-ServiceFabricNode -NodeName "SSIS1" -NodeType "SSISNodeType" -IpAddressOrFQDN "10.179.108.22" -UpgradeDomain "ud0" -FaultDomain "fd:/fd0" -FabricRuntimePackagePath "C:\Temp\MicrosoftAzureServiceFabric.cab"
Repeat the step above for any additional DIXF Nodes.

13.	Add in the predeployment script for enabling the DIXF Service. If you don’t have the base predeployment script, set up the script, and enable the script “TSG_EnableGMSAForAOS.ps1”. In the main predeployment script, uncomment out the line for the DIXF script, and confirm the DIXF share you created in the previous step is set.
  For more information, see [On-premises implementations](../deployment/onprem-tsg-implementations.md). 
14.	Log into LCS, select the project and environment. **Maintain** > **Update settings**. Click **Prepare**. After the config it downloaded, click **Update** in LCS to complete the process. 


