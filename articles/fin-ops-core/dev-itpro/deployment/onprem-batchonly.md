---
# required metadata

title: Configure batch-only and interactive-only AOS nodes in on-premises deployments
description: This article explains how to configure your environment so that you can deploy batch-only and interactive-only AOS nodes.
author: faix
ms.date: 07/08/2020
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2020-04-30 
ms.dyn365.ops.version: Platform update 36 
search.app:
  - financeandoperationsonprem-docs
---

# Configure Batch-only and Interactive-only AOS nodes in on-premises deployments

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This feature is supported starting in application update 10.0.12, Platform update 36.

This article explains how to configure your environment so that you can deploy batch-only and interactive-only Application Object Server (AOS) nodes.

To make this feature available, Microsoft has introduced two new Microsoft Azure Service Fabric node types. For batch-only AOS nodes, the new node type is **BatchOnlyAOSNodeType**. For interactive-only AOS nodes, the new node type is **InteractiveOnlyAOSNodeType**.

> [!NOTE]
> The traditional deployment option, where an AOS node is interactive and is running batch jobs, is still supported and isn't affected by these changes.

## Sizing

For sandbox environments, we recommend that you have at least two nodes of each type.

For production environments, there should be at least three nodes of each type.

## New deployments

1. When you're describing your configuration as explained in [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#describeconfig), edit the **configtemplate.xml** file to enable the new node types. When you are done, the template should resemble the following example.

```xml
<NodeType name="AOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="true">
    <VMList>
        <VM name="aos1" ipAddress="" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="aos2" ipAddress="" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="aos3" ipAddress="" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="InteractiveOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="LBDE05FS1AOS01" ipAddress="192.168.5.51" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="LBDE05FS1AOS02" ipAddress="192.168.5.52" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="LBDE05FS1AOS03" ipAddress="192.168.5.53" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="BatchOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="LBDE05FS1AOS04" ipAddress="192.168.5.54" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="LBDE05FS1AOS05" ipAddress="192.168.5.55" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="LBDE05FS1AOS06" ipAddress="192.168.5.56" faultDomain="fd:/fd0" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
```

2. Follow the remaining instructions in [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#describeconfig) in the usual way.

## Existing deployments

1. Follow the instructions in [Remove an AOS node](onprem-remove-reinstall-AOS-node.md#option-1-use-a-configuration-file-preferred-option) up through the point where you save the configuration file.

    > [!IMPORTANT]
    > You must use option 1, "Use a configuration file (preferred option)." Do **not** use option 2.

2. Continue to edit the **ClusterConfig.json** file to add the new node types to the **NodeTypes** section. When you've finished, the **NodeTypes** section should resemble the following example.

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
    ```

3. Continue to follow the instructions in [Remove an AOS node](onprem-remove-reinstall-AOS-node.md#option-1-use-a-configuration-file-preferred-option) from the point where you stopped until you've finished removing the nodes from your cluster.
4. On the machines that you've removed from the Service Fabric cluster, follow these steps:

    1. Delete the contents of your Service Fabric data root (**C:\\ProgramData\\SF**) and your Service Fabric log root (**C:\\ProgramData\\SF\\Log**).
    2. Copy or download the standalone package for Service Fabric for Windows Server to the virtual machine (VM) or machine.
    3. Unzip the package (**C:\\Temp\\ServiceFabricStandalone**).
    4. Open Windows PowerShell as an admin.
    5. Run the following commands.

        > [!IMPORTANT]
        > Replace parameters as appropriate for your machine configuration.

        ```powershell
        cd C:\Temp\ServiceFabricStandalone
        .\AddNode.ps1 -NodeName AOS_12 -NodeType BatchOnlyAOSNodeType -NodeIpAddressOrFQDN 192.168.5.12 -ExistingClientConnectionEndpoint 192.168.5.21:19000 -UpgradeDomain ud0 -FaultDomain fd:/fd0 -X509Credential -ServerCertThumbprint 1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A -AcceptEULA -StoreLocation LocalMachine -StoreName MY -FindValueThumbprint 1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A1A
        ```

        > [!NOTE]
        > When the node first reappears in Service Fabric Explorer, it might show the old node type. However, it should show the updated node type after a few minutes.

5. Query the Service Fabric cluster again for the **ClusterConfig.json** file.

    ```powershell
    Get-ServiceFabricClusterConfiguration -UseApiVersion -ApiVersion 10-2017 > C:\Temp\ClusterConfig.json
    ```

6. In the **fabricSettings** section, remove the **NodesToBeRemoved** parameter. When you've finished, the **fabricSettings** section should resemble the following example.

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

7. Remove the following lines from the **Security** section.

    ```json
    "WindowsIdentities": {
        "\$id": "3"
    },
    ```

    > [!NOTE]
    > If you don't remove these lines, you will receive the following error message later:
    >
    > *ValidationException: Authentication type can't be changed from unsecured to Windows.*

8. Increment the version number of the configuration file. Make this change at the lowest increment. In the following example, the version number went from **1.0.1** to **1.0.2**.

    ```json
    "ClusterConfigurationVersion": "1.0.2"
    ```

9. Save the configuration file.
10. Open Windows PowerShell as an admin, and run the following commands.

    ```powershell
    Connect-ServiceFabricCluster
    Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath C:\Temp\ClusterConfig.json
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    ```

11. To monitor the upgrade, you can run the following command.

    ```powershell
    Get-ServiceFabricClusterUpgrade
    ```

12. Once the upgrade is finished from LCS use the Update Settings button without changing any settings to trigger an environment refresh. Alternatively you could also apply the latest hotfix.

     > [!IMPORTANT]
    > This step causes downtime so be sure that your environment can be unavailable for some time. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
