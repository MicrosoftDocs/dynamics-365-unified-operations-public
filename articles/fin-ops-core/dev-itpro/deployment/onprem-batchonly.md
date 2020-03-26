---
# required metadata

title: Configuring Batch-only and Interactive-only AOS nodes in on-premises deployments
description: This topic explains how to configure your environment to be able to deploy Batch-only and Interactive-only AOS nodes.
author: faix
manager: AnnBe
ms.date: 03/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2020-04-30 
ms.dyn365.ops.version: Platform update 35 

---

# Batch-only and Interactive-only AOS nodes

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> This feature is only supported starting with application update 10.0.11, Platform update 35.

This topic explains how to configure your environment to be able to deploy Batch-only and Interactive-only AOS nodes.

To enable this feature, we have introduced two new ServiceFabric NodeTypes. For Batch-only AOS, the new NodeType is BatchOnlyAOSNodeType. For Interactive-only AOS the new NodeType is InteractiveOnlyAOSNodeType.

> [!NOTE]
> The traditional deployment option where an AOS node is Interactive and is running Batch will still be supported and is not affected by these changes. 

## Sizing

For sandbox environments we recommend that you have at least 2 nodes of each type. 

For production environments there should be at least 3 nodes of each type. 

## New deployments


1. When you are describing your configuration as stated in [Set up and deploy on-premises environments](./setup-deploy-on-premises-pu12.md#describeconfig), modify the configtemplate.xml to add the new node types. The new NodeType sections should like below. 

    ```xml
    <NodeType name="InteractiveOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS">
      <VMList>
        <VM name="LBDEN05FS1AOS01" ipAddress="192.168.5.11" faultDomain="fd:/fd0" updateDomain="ud0" />
        <VM name="LBDEN05FS1AOS02" ipAddress="192.168.5.12" faultDomain="fd:/fd1" updateDomain="ud1" />
        <VM name="LBDEN05FS1AOS03" ipAddress="192.168.5.13" faultDomain="fd:/fd0" updateDomain="ud2" />
      </VMList>
    </NodeType>
    <NodeType name="BatchOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS">
      <VMList>
        <VM name="LBDEN05FS1AOS04" ipAddress="192.168.5.14" faultDomain="fd:/fd0" updateDomain="ud0" />
        <VM name="LBDEN05FS1AOS05" ipAddress="192.168.5.15" faultDomain="fd:/fd1" updateDomain="ud1" />
        <VM name="LBDEN05FS1AOS06" ipAddress="192.168.5.16" faultDomain="fd:/fd0" updateDomain="ud2" />
      </VMList>
    </NodeType>
    ```
2. Follow the rest of the [Set up and deploy on-premises environments](./setup-deploy-on-premises-pu12.md#describeconfig) instructions as you normally would.

## Existing deployments

1. Follow the [Remove an AOS node](./onprem-remove-reinstall-AOS-node#option-1-use-a-configuration-file-preferred-option) guide up until you save the configuration file.

[!Important]
> You must use Option 1: Use a configuration file (preferred option) and *not* Option 2. 

2. Continue editing the ClusterConfig.json file and add the new node types to the NodeTypes section. After you have added the nodes, it should look something like this:

    ```json
    "NodeTypes": [
        {
            "Name": "AOSNodeType",
            "PlacementProperties": {
                "IsAosEnabled": "True"
            },
            "ClientConnectionEndpointPort": 19000,
            "HttpGatewayEndpointPort": 19080,
            "ReverseProxyEndpointPort": 19081,
            "LeaseDriverEndpointPort": 19002,
            "ClusterConnectionEndpointPort": 19001,
            "ServiceConnectionEndpointPort": 19003,
            "ApplicationPorts": {
                "StartPort": 20001,
                "EndPort": 20031
            },
            "IsPrimary": false
        },
        {
            "Name": "BatchOnlyAOSNodeType",
            "PlacementProperties": {
                "IsAosEnabled": "True"
            },
            "ClientConnectionEndpointPort": 19000,
            "HttpGatewayEndpointPort": 19080,
            "ReverseProxyEndpointPort": 19081,
            "LeaseDriverEndpointPort": 19002,
            "ClusterConnectionEndpointPort": 19001,
            "ServiceConnectionEndpointPort": 19003,
            "ApplicationPorts": {
                "StartPort": 20001,
                "EndPort": 20031
            },
            "IsPrimary": false
        },
        {
            "Name": "InteractiveOnlyAOSNodeType",
            "PlacementProperties": {
                "IsAosEnabled": "True"
            },
            "ClientConnectionEndpointPort": 19000,
            "HttpGatewayEndpointPort": 19080,
            "ReverseProxyEndpointPort": 19081,
            "LeaseDriverEndpointPort": 19002,
            "ClusterConnectionEndpointPort": 19001,
            "ServiceConnectionEndpointPort": 19003,
            "ApplicationPorts": {
                "StartPort": 20001,
                "EndPort": 20031
            },
            "IsPrimary": false
        },
        ...
    ]

3. Follow the [Remove an AOS node](./onprem-remove-reinstall-AOS-node#option-1-use-a-configuration-file-preferred-option) guide from where you left off before and until you are done removing the nodes from your cluster.

4. In the machines that you have removed from the Service Fabric Cluster do the following:
    1. Delete the contents of your FabricDataRoot (i.e. C:\\ProgramData\\SF) and FabricLogRoot (i.e. C:\\ProgramData\\SF\\Log).
    2. Copy or download the standalone package for Service Fabric for Windows Server to the VM/machine.
    3. Unzip the package (i.e. C:\Temp\ServiceFabricStandalone)
    4. Open PowerShell as an Administrator
    5. Run the following:
        ```powershell
            cd C:\Temp\ServiceFabricStandalone
            .\AddNode.ps1 -NodeName AOS_12 -NodeType BatchOnlyAOSNodeType -NodeIpAddressOrFQDN 192.168.5.12 -ExistingClientConnectionEndpoint 192.168.5.21:19000 -UpgradeDomain ud0 -FaultDomain fd:/fd0 -X509Credential -ServerCertThumbprint 1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A -AcceptEULA -StoreLocation LocalMachine -StoreName MY -FindValueThumbprint 1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A
        ```
        > [!Important]
        > Replace parameters as appropriate for your machine configuration.

        > [!Note]
        > When the node reappears in SF explorer it may show the old NodeType. If you wait for a few minutes it will show the updated nodetype.

5. Query the SF cluster again for the ClusterConfig.json:
    ```powershell
         Get-ServiceFabricClusterConfiguration -UseApiVersion -ApiVersion 10-2017 > C:\Temp\ClusterConfig.json
    ```

6. Under the *fabricSettings* section remove the *NodesToBeRemoved* parameter. It should look something like this when removed. 
    ```json
    "fabricSettings": [
        {
            "name": "Setup",
            "parameters": [
                {
                    "name": "FabricDataRoot",
                    "value": "C:\\\\ProgramData\\\\SF"
                },
                {
                    "name": "FabricLogRoot",
                    "value": "C:\\\\ProgramData\\\\SF\\\\Log"
                }
            ]
        }
    ]
    ```

7. Remember to remove the following lines from the *Security* section.
    ```json
    "WindowsIdentities": {
        "\$id": "3"
    },
    ```
    > [!Note]
    > If you don't remove these lines, you will receive the following error message later:
        ValidationException: Authentication type can't be changed from unsecured to Windows.

8. Increment the version number of the configuration file. Make this change at the lowest increment. In the following example, the version number went from 1.0.1 to 1.0.2.
    ```json
    "ClusterConfigurationVersion": "1.0.2"
    ```

9. Save the configuration file.

10. Start PowerShell as an Administrator and run:
    ```powershell
        Connect-ServiceFabricCluster
        Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath C:\Temp\ClusterConfig.json
        Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    ```
11. You can monitor the upgrade by using the following command:
    ```powershell
        Get-ServiceFabricClusterUpgrade
    ```




