---
# required metadata

title: Certificate rotation
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: PeterRFriis
manager: AnnBe
ms.date: 05/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: perahlff
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Platform update 25 

---

# Certificate rotation

[!include[banner](../includes/banner.md)]

You may need to rotate the certificates used by your Finance and Operations on-premises environment, as they approach their expiry date. In this article you can understand how to replace the existing certificates with new ones and update the references within the environment to use the new certificates.

> [!NOTE]
> Old certificates must remain in place until the certificate rotation process is complete, removing them beforehand will cause the rotation process to fail.

## Preparation steps 

1. Rename the original **Infrastructure** folder you created during **Set up and deploy on-premises environments** [on-premises setup scripts from LCS](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#downloadscripts) to **InfrastructureOld**

2. Download the latest [on-premises setup scripts from LCS](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#downloadscripts). Unzip the files into a folder that is named **Infrastructure**.

3. Copy **ConfigTemplate.xml** and **ClusterConfig.json** from **InfrastructureOld** to **Infrastructure**

4. Configure certificates as needed in **ConfigTemplate.xml**. For more information, see [Configure certificates](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#configurecert)
    ```powershell
    # Create self-signed certs
    .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    
    # Exports Pfx files into a directory VMs\<VMName>, all the certs will be written to infrastructure\Certs folder.
    .\Export-PfxFiles.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

5. Proceed with [Setup VMs](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#setupvms). Specific steps that are needed are:

    1. Export the scripts that must be run on each VM.
        ```powershell
        # Exports the script files to be execute on each VM into a directory VMs\<VMName>.
        .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        ```

    2. Copy the contents of each infrastructure\\VMs<VMName> folder into the corresponding VM (if remoting scripts are used, they will automatically copy the content to the target VMs), and then run the following scripts, if they exist, as an Administrator.
        ```powershell
        # If Remoting, only execute
        # .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        # .\Test-D365FOConfiguration-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml

        .\Add-GMSAOnVM.ps1
        .\Import-PfxFiles.ps1
        .\Set-CertificateAcls.ps1
        ```
        
    3. Run the following script to validate the VM setup.
        ```powershell
        .\Test-D365FOConfiguration.ps1
        ```

6. If axdataenciphermentcert certificates is rotated, you need to regenerate credentials.json file. For more information, see [Encrypt credentials](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#encryptcred)

7. Run following PowerShell command to have values to be used in LCS later. For more information, see [Deploy your Finance and Operations (on-premises) environment from LCS](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#deploy)
    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    `````


## Activation of New Certificates within Service Fabric Cluster

### Service fabric with not expired Certificates

1. Edit the Clusterconfig.json file. Find the Part:  
    ```
                       "security":  {
                                        "metadata":  "The Credential type X509 indicates this is cluster is secured using X509 Certificates. The thumbprint format is - d5 ec 42 3b 79 cb e5 07 fd 83 59 3c 56 b9 d5 31 24 25 42 64.",
                                        "ClusterCredentialType":  "X509",
                                        "ServerCredentialType":  "X509",
                                        "CertificateInformation":  {
                                                                       "ClusterCertificate":  {
                                                                                                  "X509StoreName":  "My",
                                                                                                  "Thumbprint": "*Old server thumbprint(Star/SF)*"
                                                                                              },
                                                                       "ServerCertificate":  {
                                                                                                 "X509StoreName":  "My",
												 "Thumbprint": "*Old server thumbprint(Star/SF)*"
                                                                                             },
                                                                       "ClientCertificateThumbprints":  [
                                                                                                            {
                                                                                                                "CertificateThumbprint": "*Old client thumbprint*",
                                                                                                                "IsAdmin":  true
                                                                                                            }
                                                                                                        ]
                                                                   }
                                    },
    ```

2. Replace section with following
    ```
                       "security":  {
                                        "metadata":  "The Credential type X509 indicates this is cluster is secured using X509 Certificates. The thumbprint format is - d5 ec 42 3b 79 cb e5 07 fd 83 59 3c 56 b9 d5 31 24 25 42 64.",
                                        "ClusterCredentialType":  "X509",
                                        "ServerCredentialType":  "X509",
                                        "CertificateInformation":  {
                                                                       "ClusterCertificate":  {
                                                                                                  "X509StoreName":  "My",
                                                                                                  "Thumbprint":  "New Server humbprint(Star/SF)"
												 ,"ThumbprintSecondary": "Old Server humbprint(Star/SF)"
                                                                                              },
                                                                       "ServerCertificate":  {
                                                                                                 "X509StoreName":  "My",
                                                                                                 "Thumbprint":  "New Server humbprint(Star/SF)"
												 ,"ThumbprintSecondary":"Old Server humbprint(Star/SF)"
                                                                                             },
                                                                       "ClientCertificateThumbprints":  [
                                                                                                            {
                                                                                                                "CertificateThumbprint":  "Old Client Thumbprint",
                                                                                                                "IsAdmin":  false
                                                                                                            },
                                                                                                            {
                                                                                                                "CertificateThumbprint":  "New Client Thumbprint",
                                                                                                                "IsAdmin":  true
                                                                                                            }
                                                                                                        ]
                                                                   }
                                    },
    ```

3. Edit new and old thumbprint values. 

4. Change clusterConfigurationVersion in the top to new version, example 2.0.0.
    ```
    {
    "name": "Dynamics365Operations",
    "clusterConfigurationVersion": "2.0.0",
    "apiVersion": "10-2017",
    ```
5. Save the new ClusterConfig.json

6. Run following PowerShell command
    ```powershell
    Connect-ServiceFabricCluster

    # If using a single Microsoft SQL Server Reporting Services node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check.
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath ClusterConfig.json
    ```

> [!NOTE] If you have a Service Fabric JSON file format issue, please add required comma as below

![C:\\Users\\laionel\\AppData\\Local\\Microsoft\\Windows\\INetCache\\Content.MSO\\14673ECF.tmp](media/7c1a988596e5f59244c2ea1fa04835d1.png)

### Service fabric with or without expired Certificates (cluster not accessible)

1. Download PowerShell script ChangeCert.ps1.
2. Change the first section so that it fits the environment:
    ```
    Param(
    [Parameter(Mandatory=\$false)]
    [ValidateNotNullOrEmpty()]
    [string] \$clusterDataRootPath="C:\\ProgramData\\SF", (Service Fabric installation folder)
    [Parameter(Mandatory=\$false)] \#\$true
    [ValidateNotNullOrEmpty()]
    [string]\$oldThumbprintServer="Old Server Thumbprint(Star/SF)",
    [Parameter(Mandatory=\$false)] \#\$true
    [ValidateNotNullOrEmpty()]
    [string]\$newThumbprintServer="New Server Thumbprint(Star/SF)",
    [Parameter(Mandatory=\$false)] \#\$true
    [ValidateNotNullOrEmpty()]
    [string]\$oldThumbprintClient="Old Client Thumbprint",
    [Parameter(Mandatory=\$false)] \#\$true
    [ValidateNotNullOrEmpty()]
    [string]\$newThumbprintClient="New Client Thumbprint",
    [Parameter(Mandatory=\$false)]
    [ValidateNotNullOrEmpty()]
    [string]\$certStoreLocation='Cert:\\LocalMachine\\My\\',
    [Parameter(Mandatory=\$false)] \#\$true
    [ValidateNotNullOrEmpty()]
    [string[]]\$nodeIpArray=\@("10.0.0.11", "10.0.0.12", "10.0.0.13") (Add all IPs from all member server of the SF cluster)
    )
    ```
3.  Save the changes.

4. Run following PowerShell command on one of the Cluster members 
    ChangeCert.ps1

5. A login screen will popup. Use an admin user that is present on all Nodes.

6. Script will run on all nodes remotely and makes the necessary changes to get the cluster up and running again.

## LocalAgent Certificate update (if needed)

1. Run following PowerShell command on one of the Orchestrator nodes
    ```powershell
    .\LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

2. Run following PowerShell command to note new LocalAgent thumbprint
    ```powershell
    .\Get-AgentConfiguration.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

3. Proceed with [Configure LCS connectivity for the tenant](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#configurelcs)

> [!NOTE] If receive error **Update to existing credential with KeyId '\<key\>' is not allowed.**, follow [Error: "Updates to existing credential with KeyId '<key>' is not allowed"](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/troubleshoot-on-prem#error-updates-to-existing-credential-with-keyid-key-is-not-allowed)

4. Proceed with [Configure a connector and install an on-premises local agent](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#configureconnector), specifically following changes. 
**Client certificate thumbprint**
**Server Certificate thumbprint**
**Tenant service principle certificate thumbprint**

## Update deployment settings in LCS:
> [!NOTE] Make a backup of local Dynamics database

1. In LCS, click on the "Full Details" link of the environment where you want to change the certificates.

2. Click **Maintain** button and select **Update Settings**.

![](media/addf4f1d0c0a86d840a6a412f774e474.png)

3. Change the thumbprints with the new ones that you have previously configured (you can find these in the ConfigTemplate.xml in the InfrastructureScripts folder).

![](media/07da4d7e02f11878ee91c61b4f561a50.png)

![](media/785caaf4ee652d66c0d88cf615a57e26.png)

4. Click “Prepare”.

5. After downloading and preparing is complete, the "Update environment" button will show up.

![](media/0a9d43044593450f1a828c0dd7698024.png)

6. Click "Update environment" to start updating you environment.

7. During this period the environment will be unavailable.

![](media/bbc38a913888afa5b0410d05af38216e.png)

8. After the environment is successfully updated with the new certificates, you can check the new thumbprints in Service Fabric Cluster Explorer. Please note that the name of the thumbprint name from SF Explorer might differ from the names of the thumbprints you see in the LCS page. However, their values should be the same.

Here is an example of how the name of the same thumbprint might differ.

![](media/038173714b2fb6cf12acc4bda2a3dde5.png)

![](media/642f6434da9cdeac3651b765acca08fa.png)

## Update other certificates as needed

1. SQL server. For more information, see []Set up SQL Server](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/setup-deploy-on-premises-pu12#setupsql)

2. AD FS
