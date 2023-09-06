---
# required metadata
title: Add an SSIS node to an existing environment
description: This article explains how to add a Microsoft SQL Server Integration Services (SSIS) node in an on-premises environment.
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

# Add an SSIS node to an existing environment

[!include[banner](../includes/banner.md)]

This article explains how to add a Microsoft SQL Server Integration Services (SSIS) node in an on-premises environment. SSIS nodes were introduced in version 10.0.32 (Platform update 56) and are used by the Data management framework.

## Installation steps

1. Confirm that your environment is on version 10.0.32 (Platform update 56) or later.
1. Download and extract the latest setup scripts from Microsoft Dynamics Lifecycle Services. For more information, see [Download the infrastructure scripts](./obtain-infrascripts-onprem.md#download-the-infrastructure-scripts).

    > [!IMPORTANT]
    > The scripts must be run from a computer that's in the same domain as the on-premises infrastructure.

1. Update the infrastructure scripts. For more information, see [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
1. In the *ConfigTemplate.xml* file, in the `SSISNodeType` section, modify the SSIS nodes. Confirm that the `disabled` parameter is set to *false*.

    ```XML
    <NodeType name="SSISNodeType" primary="false" namePrefix="SSIS" purpose="SSIS" disabled="false">
        <!-- Do not place hasSSIS on this node type. -->
        <VMList>
            <VM name="ssis1" ipAddress="10.179.108.22" faultDomain="fd:/fd0" updateDomain="ud0" />
            <VM name="ssis2" ipAddress="10.179.108.23" faultDomain="fd:/fd1" updateDomain="ud1" />
        </VMList>
    </NodeType>
    ```

1. Create the Data import/export framework (DIXF) group managed service account (gMSA). For more information, see [Step 8. Create gMSAs](./setup-deploy-on-premises-latest.md#setupgMSA). Option 1 creates just the new DIXF gMSA.
1. Set up and edit a new file share for DIXF. For more information, see [Step 9. Set up file storage](./setup-deploy-on-premises-latest.md#setupfile).

    > [!NOTE]
    > In the *ConfigTemplate.xml* file, set the `disabled` property to *true* for any existing file shares.

1. Install SSIS on the required nodes. For more information, see [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupssis).
1. Open an Admin PowerShell window, change to the *Infrastructure scripts* folder, and run the following script.

    ```PowerShell
    # Exports certificates into a directory VMs\<VMName>. All the certs will be written to the infrastructure\Certs folder.
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Set up the new virtual machines (VMs). For more information, see [Step 14. Set up VMs](./setup-deploy-on-premises-latest.md#setupvms).
1. Before you add the new node, update Azure Service Fabric to the latest version. For more information, see [Upgrade the Service Fabric version that runs on your cluster](/azure/service-fabric/service-fabric-cluster-upgrade-windows-server).
1. Copy the contents of the following PowerShell script, and save them to your *Infrastructure scripts* folder as a file that's named *UpdateNodeTypes.ps1*.

    ```PowerShell
    <#
    SAMPLE CODE NOTICE

    THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,
    OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.
    THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.
    NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.
    #>

    Param(

        # Input XML file that specifies cluster topology such as .\ConfigTemplate.xml.
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string] $ConfigurationFilePath,

        # Output file path, by default this will be this current working directory ($pwd) with a file name ClusterConfig.json.
        [ValidateNotNullOrEmpty()]
        [string] $TemplateConfig = "$PSScriptRoot\ClusterConfig.json",

        # Path to the fileshare where the config.json is located for your deployment
        [ValidateNotNullOrEmpty()]
        [ValidateScript({ Test-Path -Path $_ })]
        [string] $TopologyFilePath ="$PSScriptRoot\D365FO-OP\NodeTopologyDefinition.xml",

        [Parameter(ParameterSetName = "UpdateNodeTypes")]
        [switch] $UpdateNodeTypes

    )

    function Set-ClusterNodeTypes
    {
        param
        (
            [ValidateNotNull()]
            $TopologyXml,

            [ValidateNotNull()]
            $NodeTypes,

            [ValidateNotNull()]
            [psobject] $ConfigJson
        )

        Write-Information "Setting node types..."
        for ($i = 0; $i -lt $NodeTypes.Count; $i++)
        {
            $nodeType = $NodeTypes[$i]
            #Get the purposes and the placement criteria from the topology document.
            $placementProperties = New-Object psobject
            [string[]] $purposes = $nodeType.purpose -split ","
            $invalidProperties = New-Object System.Collections.Generic.List[System.String]

            foreach ($purpose in $purposes)
            {
                $templatePropertiesXml = Get-D365FOPlacementProperties -XmlDoc $TopologyXml -ComponentName $purpose
                if ($templatePropertiesXml -and $templatePropertiesXml.Property)
                {
                    $templatePropertiesXml.Property | ForEach-Object {
                        if ($placementProperties.PSObject.Properties.Name -eq $_.name)
                        {
                            $invalidProperties.Add($_.name);
                        }
                        else
                        {
                            $placementProperties | Add-Member -MemberType NoteProperty -Name $_.name -Value $_.value
                        }
                    }
                }
            }

            if ($nodeType.PlacementProperties -and $nodeType.PlacementProperties.Property)
            {
                $nodeType.PlacementProperties.Property | ForEach-Object {
                    if ($placementProperties.PSObject.Properties.Name -eq $_.name)
                    {
                        $invalidProperties.Add($_.name);
                    }
                    else
                    {
                        $placementProperties | Add-Member -MemberType NoteProperty -Name $_.name -Value $_.value
                    }
                }
            }

            if ($invalidProperties.Count -gt 0)
            {
                $propertyList = $invalidProperties.ToArray() | Select-Object -Unique
                if ($propertyList -eq 1)
                {
                    throw "The placement property $($propertyList -join ",") already exists for node type $($nodeType.name). Make sure the placement property is not a reserved property and is not a duplicate"
                }
                else
                {
                    throw "The placement properties $($propertyList -join ",") already exist for node type $($nodeType.name). Make sure the placement property is not a reserved property and is not a duplicate"
                }
            }

            if ($i -eq 0)
            {
                if(-not ($configJson.properties.nodeTypes | Where-Object {$_.name -eq $nodeType.name}))
                {
                    $ConfigJson.properties.nodeTypes[$i].name = $nodeType.name
                    $ConfigJson.properties.nodeTypes[$i] | Add-Member -MemberType NoteProperty -Name 'placementProperties' -Value $placementProperties
                    $ConfigJson.properties.nodeTypes[$i].isPrimary = [bool]::Parse($nodeType.primary)
                }
            }
            else
            {
                if(-not ($configJson.properties.nodeTypes | Where-Object {$_.name -eq $nodeType.name}))
                {
                    $newNodeType = $ConfigJson.properties.nodeTypes[0].psobject.Copy()
                    $newNodeType.name = $nodeType.name
                    $newNodeType.isPrimary = [bool]::Parse($nodeType.primary)
                    $newNodeType.placementProperties = $placementProperties

                    $ConfigJson.properties.nodeTypes += $newNodeType
                }
            }
        }
    }

    #requires -Version 5
    $ErrorActionPreference = 'Stop'
    $InformationPreference = 'Continue'
    Import-Module "$PSScriptRoot\D365FO-OP" -Force

    [xml] $configXml = Get-Content -Path $ConfigurationFilePath -Raw -ErrorAction Stop
    [xml] $topologyXml = Get-Content -Path $TopologyFilePath -Raw -ErrorAction Stop
    $minimumConfigTemplateVersion = 1.7

    Assert-D365FOConfigurationFileVersion -XmlFilePath $ConfigurationFilePath -MinimumVersion $minimumConfigTemplateVersion

    if (-not (Get-Command Connect-ServiceFabricCluster -ErrorAction SilentlyContinue))
    {
        throw "This script needs to be executed from a node in the Service Fabric Cluster."
    }
    Connect-ServiceFabricCluster
    $configJson = Get-ServiceFabricClusterConfiguration | ConvertFrom-Json

    if ($UpdateNodeTypes)
    {
        $nodeTypes = $configXml.SelectNodes('/Config/ServiceFabricCluster/NodeType')
        Set-ClusterNodeTypes -NodeTypes $nodeTypes -ConfigJson $configJson -TopologyXml $topologyXml
        Save-D365FOJsonToFile -JsonObject $configJson -FilePath $TemplateConfig
        Write-Host "NodeTypes reviewed and updated as needed"
    }
    ```

1. Open Windows PowerShell in elevated mode, change the directory to the *Infrastructure* folder in your file share, and run the following commands. These commands add any new node types to the *ClusterConfig.json* Service Fabric template file.

    ```PowerShell
    .\UpdateNodeTypes.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateNodeTypes
    ```

1. Apply the updated configuration to your Service Fabric cluster. For more information, see [Appendix A](#appendix-a) later in this article.
1. Add the new DIXF node, and follow these steps:

    1. In Service Fabric Explorer, select **Cluster**. Make a note of the Microsoft Service Fabric cluster version.
    1. On one of the orchestrator nodes, open File Explorer. On the **View** tab, in the **Show/hide** group, confirm that the **File name extensions** and **Hidden items** checkboxes are selected.
    1. Expand drive C, and drill down into the following folder. (The path varies, depending on the node name and setup.)

        *C:\\ProgramData\\SF\\ORCH1\\Fabric\\work\\Applications\_\_FabricSystem\_App4294967295\\work\\Store\\131811633624852852*

        You should find a list of folders for different versions of Service fabric.

    1. Open the folder that the same name as the Microsoft Service Fabric cluster version that you made a note of earlier.
    1. Find the .cab file, and copy it to *C:\Temp*. Rename the copied file *MicrosoftAzureServiceFabric.cab*.
    1. Open a PowerShell Command Prompt window as an admin.
    1. Run the following command to connect to your Service Fabric cluster. (Edit the command as required.)

        ```PowerShell
        #Connect to Service Fabric Cluster.
        Connect-ServiceFabricCluster
        ```

    1. Before you run the following command to add the node, update the `NodeName`, `IPAddress`, `UpgradeDomain`, and `FaultDomain` parameters.

        ```PowerShell
        Add-ServiceFabricNode -NodeName "SSIS1" -NodeType "SSISNodeType" -IpAddressOrFQDN "10.179.108.22" -UpgradeDomain "ud0" -FaultDomain "fd:/fd0" -FabricRuntimePackagePath "C:\Temp\MicrosoftAzureServiceFabric.cab"
        ```

    1. Repeat these step for any additional DIXF nodes.

1. Add in the predeployment script to enable the DIXF service. If you don't have the base predeployment script, set up the script, and enable the *TSG\_EnableGMSAForAOS.ps1* script. In the main predeployment script, uncomment the line for the DIXF script, and confirm that the DIXF share that you created in the previous step is set. For more information, see [Scripts for resolving issues in on-premises environments](../deployment/onprem-tsg-implementations.md).
1. Sign in to Lifecycle Services, and select the project and environment. Select **Maintain** \> **Update settings**, and then select **Prepare**. After the configuration is downloaded, select **Update** in Lifecycle Services to complete the process.

## <a name="appendix-a"></a>Appendix A

After you generate the updated Service Fabric cluster configuration, run the following PowerShell commands to apply the upgrade to your Service Fabric cluster.

```powershell
# Connect to the Service Fabric Cluster
Connect-ServiceFabricCluster

# Get path of ClusterConfig.json for following command
# Note that after running the following command, you need to manually cancel using the red button (Stop Operation) in Windows PowerShell ISE or Ctrl+C in Windows PowerShell. Otherwise, you receive the following notification, "Start-ServiceFabricClusterConfigurationUpgrade : Operation timed out.". Be aware that the upgrade will proceed.
Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath ClusterConfig.json

# If you are using a single Microsoft SQL Server Reporting Services node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will timeout
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# To monitor the status of the upgrade, run the following and note UpgradeState and UpgradeReplicaSetCheckTimeout
Get-ServiceFabricClusterUpgrade

# While monitoring the status of the upgrade, if UpgradeReplicaSetCheckTimeout was reset to the default (example 49710.06:28:15), run the following command again
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# When UpgradeState shows RollingForwardCompleted, the upgrade is finished
```
