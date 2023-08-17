---
# required metadata
title: Add an SSIS Node to an existing environment
description: This article explains add an SSIS Node in your existing on-premises environment.
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

# Add an SSIS Node

[!include[banner](../includes/banner.md)]

This article explains add an SSIS Node(s) in your existing on-premises environment. SSIS only nodes were introduced in 10.0.32 (Platform Update 56), and are used by the Data Management Framework.

## Installation steps
1. Ensure your environment is on version 10.0.32 (Platform Update 56) or higher.
2. Download and extract the latest setup scripts from Lifecycle Services - [Download the infrastructure scripts](./obtain-infrascripts-onprem.md#download-the-infrastructure-scripts).
   > [!IMPORTANT]
   > The scripts must be run from a computer that's in the same domain as the on-premises infrastructure.
3. Follow the steps here to update from your old infrastructure scripts - [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
4. In the ConfigTemplate.xml file, within the SSISNodeType section, add edit and modify for you SSIS node(s) as needed, check the disabled parameter is false:
   ```XML
   <NodeType name="SSISNodeType" primary="false" namePrefix="SSIS" purpose="SSIS" disabled="false">
      <!-- Do not place hasSSIS on this node type. -->
      <VMList>
         <VM name="ssis1" ipAddress="10.179.108.22" faultDomain="fd:/fd0" updateDomain="ud0" />
         <VM name="ssis2" ipAddress="10.179.108.23" faultDomain="fd:/fd1" updateDomain="ud1" />
      </VMList>
   </NodeType>
   ```
5. Create the DIXF GMSA account – see this section [Step 8. Create gMSAs](./setup-deploy-on-premises-latest.md#setupgMSA). Use option 1 to just create the new DIXF GMSA:
6. Setup a new file share for DIXF. Edit the File Share section for the new DIXF file share – Follow steps in section [Step 9. Set up file storage](./setup-deploy-on-premises-latest.md#setupfile).
   > [!NOTE]
   > In the ConfigTemplate.xml file set the disabled property to True  for any existing file shares. You only want the DIXF one to be created. 

7. Install SSIS on the nodes required – see this section [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupssis).
8. Open an Admin PowerShell and change to the Infrastructure Scripts folder, and run the following:
   ```PowerShell
   # Exports certificates into a directory VMs\<VMName>. All the certs will be written to the infrastructure\Certs folder.
   .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
   ```
9. Follow the steps in [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupvms)
10. Update Service Fabric to the latest version, before adding the new node. Follow the steps in this document [](/azure/service-fabric/service-fabric-cluster-upgrade-windows-server.md)
11. If this is the first time, you’re adding in a DIXF node, you need to add in the node type to the existing Service Fabric cluster. To do this, on one of the Orchestrator nodes, open an Admin PowerShell prompt and run the following commands:

#Connect to Service Fabric Cluster. Replace 123 with server/star thumbprint and use appropriate IP address
Connect-ServiceFabricCluster 

Get-ServiceFabricClusterConfiguration > C:\Temp\ClusterConfig.json

                Open the config file you just exported above and find the “NodeTypes” section. At the end of the MRType section add in the new SSISNode as follows (highlighted):

                Before:

{
                     "AllowStatefulWorkloads": true,
                     "Name": "MRType",
                     "PlacementProperties": {
                       "IsMREnabled": "True"
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
              }
       ],

                After:

              {
                     "AllowStatefulWorkloads": true,
                     "Name": "MRType",
                     "PlacementProperties": {
                       "IsMREnabled": "True"
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
                     "name":  "SSISNodeType",
                     "clientConnectionEndpointPort":  "19000",
                     "clusterConnectionEndpointPort":  "19001",
                     "leaseDriverEndpointPort":  "19002",
                     "serviceConnectionEndpointPort":  "19003",
                     "httpGatewayEndpointPort":  "19080",
                     "reverseProxyEndpointPort":  "19081",
                     "applicationPorts":  {
                                                         "startPort":  "20001",
                                                         "endPort":  "20031"
                                                  },
                     "ephemeralPorts":  {
                                                       "startPort":  "49152",
                                                       "endPort":  "65535"
                                                },
                     "isPrimary":  false,
                     "placementProperties":  {
                                                              "HasSSIS":  "True"
                                                       }
              }
       ],

                Edit the ClusterConfigurationVersion version in the config to increase the value, example:

                From:

                "ClusterConfigurationVersion": "2.0.10"

                To:

                "ClusterConfigurationVersion": "2.0.11"

Update the Service Fabric cluster to add in the new node type:

Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath C:\Temp\ClusterConfig.json


12.	Add in the new DIXF Node. Follow these steps below:

a)	In Service Fabric Explorer, select Cluster, and make a note of the Microsoft Service Fabric cluster version, e.g. 9.1.XXXX.XXXX
b)	On one of the orchestrator nodes, open File Explorer. On the View tab, in the Show/hide group, make sure that the **File name extensions** and **Hidden items** checkboxes are selected.
c)	Expand drive C, and then drill down into the following folder. (Note that the bold parts of the path will vary, depending on the node name and setup.)
d)	C:\ProgramData\SF\ORCH1\Fabric\work\Applications\__FabricSystem\_App4294967295\work\Store\131811633624852852
e)	In the folder, you should see a list of folders for various versions of Service Fabric.
f)	Open the folder that has the same name as the version of Microsoft Service Fabric cluster that you made a note of earlier.
g)	In the folder, you should see a .cab file.
h)	Copy the .cab file to C:\Temp, and rename the copied file MicrosoftAzureServiceFabric.cab. (If you don't have a Temp folder, create it.)
i)	Open a PowerShell Command Prompt windows as an admin.
j)	Run the following command to connect to your Service Fabric cluster. (Edit the command as you require.)

#Connect to Service Fabric Cluster. Replace 123 with server/star thumbprint and use appropriate IP address
Connect-ServiceFabricCluster 

k)	Run the following command to add the node. Before you run it, make the required edits to the NodeName, IPAddress, UpgradeDomain, and FaultDomain parameters. (If you're replacing an existing server, you should have made a note of the values earlier.)

Add-ServiceFabricNode -NodeName "SSIS1" -NodeType "SSISNodeType" -IpAddressOrFQDN "10.179.108.22" -UpgradeDomain "ud0" -FaultDomain "fd:/fd0" -FabricRuntimePackagePath "C:\Temp\MicrosoftAzureServiceFabric.cab"
Repeat the step above for any additional DIXF Nodes.

13.	Add in the pre-deployment script for enabling the DIXF Service. If you don’t have the base pre-deployment script you’ll need to setup that, and then also enable the script “TSG_EnableGMSAForAOS.ps1”. Also, in the main pre-deployment script, you need to uncomment out the line for the DIXF script, and ensure you have the DIXF share you created in the previous step set. See: https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/onprem-tsg-implementations 
14.	Finally, log into LCS and select the project and environment. From the Maintain menu, select Update Settings. Do not make any changes, and click Prepare. Once the config it downloaded, you can then click Update in LCS to complete the process. 


