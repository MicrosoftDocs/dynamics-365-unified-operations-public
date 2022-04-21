---
# required metadata

title: Certificate rotation
description: This topic explains how to place existing certificates and update the references within the environment to use the new certificates.
author: PeterRFriis
ms.date: 04/07/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: peterfriis
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Platform update 25 

---

# Certificate rotation

[!include[banner](../includes/banner.md)]

You may need to rotate the certificates used by your Dynamics 365 Finance + Operations (on-premises) environment as they approach their expiration date. In this topic, you will learn how to replace the existing certificates and update the references within the environment to use the new certificates.

> [!WARNING]
> The certificate rotation process should be initiated well before the certificates expire. This is very important for the Data Encryption certificate, which could cause data loss for encrypted fields. For more information, see [After certificate rotation](#aftercertrotation). 
> 
> Old certificates must remain in place until the certificate rotation process is complete, removing them in advance will cause the rotation process to fail.

> [!WARNING]
> The certificate rotation process should not be carried out on Service Fabric clusters running 7.0.x and 7.1.x. 
>
> Upgrade your Service Fabric cluster to 7.2.x or later before attempting certificate rotation.

## Update your infrastructure scripts 

1. Rename the original **Infrastructure** folder that you created during the process to [Download setup scripts from LCS](setup-deploy-on-premises-pu41.md#downloadscripts). Rename the folder to **InfrastructureOld**.

2. Download the latest setup scripts from [Download setup scripts from LCS](setup-deploy-on-premises-pu41.md#downloadscripts). Unzip the files into a file share that can be accessed by all machines in the cluster. Name the folder **Infrastructure**.

    > [!NOTE]
    > As of version 2.14.0, each version of the scripts will have its own entry in the Shared asset library.

3. Compare the schema version of the **ConfigTemplate.xml** file in the **InfrastructureOld** folder with the schema version of the **ConfigTemplate.xml** file in the **Infrastructure** folder.

    - If the schema versions haven't changed, copy the **ConfigTemplate.xml** file from the **InfrastructureOld** folder to the **Infrastructure** folder.
    - If the schema versions have changed, follow these steps:

        1. Copy the **ConfigTemplate.xml** file from the **InfrastructureOld** folder to the **Infrastructure** folder.
        2. Run the following command.
        
            ```powershell
            .\Update-ConfigTemplate.ps1 -OldConfigTemplate .\ConfigTemplateOld.xml -NewConfigTemplate .\ConfigTemplate.xml
            ```

        > [!NOTE]
        > Newer versions of the scripts (version 2.14.0 and later) that introduce changes to the schema of the configuration file will include logic that migrates the configuration file to the new schema.
        > 
        > The script doesn't currently have logic for updating from schemas that are earlier than version 1.5. In these cases, you must manually migrate the old **ConfigTemplate.xml** file by comparing it with the new **ConfigTemplate.xml** file.

## Preparation steps 

1. In the **ConfigTemplate.xml** file, configure certificates as you require. Follow the steps in [Configure certificates](setup-deploy-on-premises-pu41.md#configurecert). Specifically, follow these steps.

    ```powershell
    # Only run the first command if you have not generated the templates yet.
    .\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -CreateTemplates
    .\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!NOTE]
    > The AD CS scripts need to run on a domain controller, or a Windows Server computer with Remote Server Admin Tools installed.
    > The AD CS functionality is only available with Infrastructure scripts release 2.7.0 and later. 

    Alternatively, if you want to continue to use self-signed certificates, run the following command.

    ```powershell
    # Create self-signed certs
    .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!WARNING]
    > Self-signed certificates should never be used in production environments. If you're using publicly trusted certificates, manually update the values of those certificates in the ConfigTemplate.xml file.

    After you've generated the certificates, run the following command.

    ```powershell
    # Exports .pfx files into a directory VMs\<VMName>. All the certs will be written to the infrastructure\Certs folder.
    .\Export-PfxFiles.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Continue to [set up VMs](setup-deploy-on-premises-pu41.md#setupvms). Here are the specific steps that are required for this process:

    1. Export the scripts that must be run on each VM.
    
        ```powershell
        # Exports the script files to be executed on each VM into a directory VMs\<VMName>.
        .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        ```

    2. Copy the contents of each `infrastructure\VMs<VMName>` folder into the corresponding VM (if remoting scripts are used, they will automatically copy the content to the target VMs), and then run the following scripts, if they exist. Perform these steps as an Administrator.

        ```powershell
        # If remoting, only execute
        # .\Configure-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ForcePushLBDScripts

        .\Configure-PreReqs.ps1
        ```

    3. Run the following scripts, if they exist. Perform these steps as an administrator.

        ```powershell
        # If remoting, only execute
        # .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml 

        .\Complete-PreReqs.ps1
        ```       

    4. Run the following script to validate the VM setup.
    
        ```powershell
        # If remoting, only execute
        # .\Test-D365FOConfiguration-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        .\Test-D365FOConfiguration.ps1
        ```

1. Run the following PowerShell command so that you have values that can be used in LCS later. For more information, see [Deploy your on-premises environment from LCS](setup-deploy-on-premises-pu41.md#deploy).

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

## Activate new certificates within Service Fabric cluster

### <a name="sfcertrotationnotexpired"></a>Service Fabric with certificates that aren't expired

1. Locate the **Clusterconfig.json** file for editing. If you cannot find this file, follow steps 2 and 3, otherwise continue to step 4.
2. Run the following command to connect to the Service Fabric Cluster.

    ```powershell
    #Connect to the Service Fabric Cluster from a node within the cluster
    Connect-ServiceFabricCluster 
    ```

3. Run the following command to save the configuration file to C:\\Temp\\ClusterConfig.json. (Make sure that the C:\\Temp path exists.)

    ```powershell
    Get-ServiceFabricClusterConfiguration > C:\Temp\ClusterConfig.json
    ```

4. Open the **Clusterconfig.json** file for editing and find the following section. If a secondary thumbprint is defined, go to [Clean up old Service Fabric certificates](#cleanupoldsfcerts) before you continue.

    ```json
    "security": {
        "metadata":  "The Credential type X509 indicates this cluster is secured using X509 Certificates. 
        The thumbprint format is - d5 ec 42 3b 79 cb e5 07 fd 83 59 3c 56 b9 d5 31 24 25 42 64.",
        "ClusterCredentialType":  "X509",
        "ServerCredentialType":  "X509",
        "CertificateInformation":  {
            "ClusterCertificate":  {
                                       "X509StoreName":  "My",
                                        "Thumbprint": "*Old server thumbprint(Star/SF)*"
                                   },
            "ServerCertificate":   {
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

5. Replace that section in the file with the following code.

    ```json
    "security":  {
        "metadata":  "The Credential type X509 indicates this cluster is secured using X509 Certificates. 
        The thumbprint format is - d5 ec 42 3b 79 cb e5 07 fd 83 59 3c 56 b9 d5 31 24 25 42 64.",
        "ClusterCredentialType":  "X509",
        "ServerCredentialType":  "X509",
        "CertificateInformation":  {
            "ClusterCertificate":  {
                                       "X509StoreName":  "My",
                                        "Thumbprint": "*New server thumbprint(Star/SF)*",
                                        "ThumbprintSecondary": "Old server thumbprint(Star/SF)"
                                   },
            "ServerCertificate":   {
                                        "X509StoreName":  "My",
                                        "Thumbprint": "*New server thumbprint(Star/SF)*",
                                        "ThumbprintSecondary": "Old server thumbprint(Star/SF)"
                                   },
            "ClientCertificateThumbprints":  [
                                       {
                                            "CertificateThumbprint": "*Old client thumbprint*",
                                            "IsAdmin":  false
                                       },
                                       {
                                            "CertificateThumbprint": "*New client thumbprint*",
                                            "IsAdmin":  true
                                       }
                                             ]
                                   }
                },
    ```

6. Edit the new and old thumbprint values. 

7. Change clusterConfigurationVersion to the new version, for example 2.0.0.

    ```json
    {
    "name": "Dynamics365Operations",
    "clusterConfigurationVersion": "2.0.0",
    "apiVersion": "10-2017",
    ```

8. Save the new ClusterConfig.json file.

9. Run the following PowerShell command.

    ```powershell
    # Connect to the Service Fabric Cluster
    Connect-ServiceFabricCluster

    # Get path of ClusterConfig.json for following command
    # Note that after running the following command, you need to manually cancel using the red button (Stop Operation) in Windows PowerShell ISE or Ctrl+C in Windows PowerShell, otherwise you will receive the following notification, "Start-ServiceFabricClusterConfigurationUpgrade : Operation timed out.". Be aware that the upgrade will proceed.
    Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath ClusterConfig.json

    # If you are using a single Microsoft SQL Server Reporting Services node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will timeout
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    
    # To monitor the status of the upgrade, run the following and note UpgradeState and UpgradeReplicaSetCheckTimeout
    Get-ServiceFabricClusterUpgrade
    
    # While monitoring the status of the upgrade, if UpgradeReplicaSetCheckTimeout was reset to the default (example 49710.06:28:15), run the following command again
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    
    # When UpgradeState shows RollingForwardCompleted, the upgrade is finished
    ```

    > [!NOTE] 
    > You might receive the following error message: "Upgrading from two different certificates to two different certificates is not allowed." This message indicates that you didn't clean up old Service Fabric certificates on the previous certificate rotation exercise. In this case, see the [Clean up old Service Fabric certificates](certificate-rotation-on-prem.md#cleanupoldsfcerts) section later in this topic, and then repeat the steps in this section.  

### Service Fabric with or without expired certificates (cluster not accessible)

Continue this process following the steps in [Troubleshoot on-premises deployments](troubleshoot-on-prem.md#clean-up-an-existing-environment-and-redeploy).

## Update the LocalAgent certificate

You must reinstall the LocalAgent in the following situations:

- You changed the Service Fabric cluster/server certificate.
- You changed the Service Fabric client certificate.
- You changed the LocalAgent certificate.

1. Update your **current localagent-config.json** file by replacing the **serverCertThumbprint** and **clientCertThumbprint** values with the new thumbprints.

    ```json
    {
    "serviceFabric": {
        "connectionEndpoint": "192.168.8.22:19000",
        "clusterId": "Orch",
        "certificateSettings": {
            "serverCertThumbprint": "New server thumbprint(Star/SF)",
            "clientCertThumbprint": "New client thumbprint"
        }
    },
    ```

1. Run the following PowerShell command on one of the Orchestrator nodes.

    ```powershell
    .\LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

1. Run the following PowerShell command and note the new LocalAgent thumbprint.

    ```powershell
    .\Get-AgentConfiguration.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Follow the steps in [Configure LCS connectivity for the tenant](setup-deploy-on-premises-pu41.md#configurelcs).

    > [!NOTE] 
    > If you receive the error **Update to existing credential with KeyId '\<key\>' is not allowed**, follow the instructions in [Error: "Updates to existing credential with KeyId '\<key\>' is not allowed"](troubleshoot-on-prem.md#error-updates-to-existing-credential-with-keyid-key-is-not-allowed).

1. Continue with [Configure a connector and install an on-premises local agent](setup-deploy-on-premises-pu41.md#configureconnector), specifically the following changes:

    - Client certificate thumbprint
    - Server certificate thumbprint
    - Tenant service principle certificate thumbprint

    > [!IMPORTANT]
    > Do **not** create a new connector in LCS. Update the configuration of your existing connector and download the settings again.

## Update your current deployment configuration

Because you've updated your certificates, the configuration file that is present in your environment is outdated and must be manually updated. Otherwise, the clean-up job may fail. This manual update must be done just this one time.

1. Open the configuration file 'config.json' on your agent file share. This will be in a share similar to the following: \\\\fileserver\agent\wp\environmentID\StandaloneSetup-123456. You can find the location of this file by running the following SQL statement on the orchestrator database.

    ```sql
    select Location from DeploymentInstanceArtifact where AssetId='config.json' and DeploymentInstanceId = 'LCSENVIRONMENTID'
    ```

    > [!NOTE]
    > Replace **LCSENVIRONMENTID** with the ID of your environment. You can obtain this ID from the page for your environment in LCS (this is the GUID value associated with your environment).

    The beginning of the file should resemble the following example.

    ```json
    {
    "serviceFabric": {
        "connectionEndpoint": "192.168.8.22:19000",
        "clusterId": "Orch",
        "certificateSettings": {
            "serverCertThumbprint": "Old server thumbprint(Star/SF)",
            "clientCertThumbprint": "Old client thumbprint"
        }
    },
    ```

2. Replace the **serverCertThumprint** and **clientCertThumbprint** values with the new thumbprints.

    ```json
    {
    "serviceFabric": {
        "connectionEndpoint": "192.168.8.22:19000",
        "clusterId": "Orch",
        "certificateSettings": {
            "serverCertThumbprint": "New server thumbprint(Star/SF)",
            "clientCertThumbprint": "New client thumbprint"
        }
    },
    ```

3. Save and close the file. Remember to close any programs that are accessing this network location. Otherwise, the cleanup process might fail.

## Rotate Credentials.json

If you've generated a new **axdataencipherment** certificate, you must re-encrypt the **Credentials.json** file.

```powershell
.\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Rotate
```

Alternatively, if you also want to rotate the existing credentials, follow these steps.

1. Decrypt the **Credentials.json** file.

    ```powershell
    .\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Decrypt
    ```

1. Open the **Credentials.json** file, and update any credentials that you want to update.

1. Re-encrypt the **Credentials.json** file.

    ```powershell
    .\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Encrypt
    ```

> [!NOTE]
> Make sure that you run the script from an Application Object Server (AOS) node.

## Update deployment settings in LCS

> [!NOTE]
> The Client, Data Signing, and Encipherment certificates will only be replaced.
>
> Before you continue, you need to make a backup of the local Dynamics database.

1. In LCS, select the "Full Details" link for the environment where you want to change the certificates.

2. Select **Maintain** and then select **Update Settings**.

    ![Apply update settings.](media/addf4f1d0c0a86d840a6a412f774e474.png)

3. Change the thumbprints to the new thumbprints that you previously configured. You can find them in the ConfigTemplate.xml file in the InfrastructureScripts folder.

    ![Deployment settings thumbprint image 1.](media/07da4d7e02f11878ee91c61b4f561a50.png)

    ![Deployment settings thumbprint image 2.](media/785caaf4ee652d66c0d88cf615a57e26.png)

4. Select **Prepare**.

5. After downloading and preparation is complete, the **Update environment** button will display.

    ![Update environment button.](media/0a9d43044593450f1a828c0dd7698024.png)

6. Select **Update environment** to start updating your environment.

7. During the update, the environment will be unavailable.

8. After the environment is successfully updated with the new certificates, you can view the new thumbprints in Service Fabric Cluster Explorer. The names of the thumbprints in Service Fabric Explorer might differ from the names in LCS. However, the values should be the same.

    Here is an example of how the name of the same thumbprint might differ.

    ![Deployment settings thumbprint example 1.](media/038173714b2fb6cf12acc4bda2a3dde5.png)

    ![Deployment settings thumbprint example 2.](media/642f6434da9cdeac3651b765acca08fa.png)

## Update other certificates as needed

1. Always check if the SQL server certificate has expired. For more information, see [Set up SQL Server](setup-deploy-on-premises-pu41.md#setupsql).

2. Check to be sure that the Active Directory Federation Service (ADFS) certificate has not expired.

## <a name="cleanupoldsfcerts"></a>Clean up old Service Fabric certificates

This procedure should be completed either after a successful certificate rotation or before the next certificate rotation.

1. Remove the old/secondary thumbprints from the cluster configuration. After you've removed them, the appropriate section should resemble the following example.

    ```json
    "security": {
        "metadata":  "The Credential type X509 indicates this is cluster is secured using X509 Certificates.
        The thumbprint format is - d5 ec 42 3b 79 cb e5 07 fd 83 59 3c 56 b9 d5 31 24 25 42 64.",
        "ClusterCredentialType":  "X509",
        "ServerCredentialType":  "X509",
        "CertificateInformation":  {
            "ClusterCertificate":  {
                                       "X509StoreName":  "My",
                                        "Thumbprint": "server thumbprint(Star/SF)"
                                   },
            "ServerCertificate":   {
                                        "X509StoreName":  "My",
                                        "Thumbprint": "server thumbprint(Star/SF)"
                                   },
            "ClientCertificateThumbprints":  [
                                       {
                                            "CertificateThumbprint": "client thumbprint",
                                            "IsAdmin":  true
                                       }
                                             ]
                                   }
                },
    ```

1. Follow steps 4 through 6 in the [Service Fabric with certificates that are not expired](#sfcertrotationnotexpired) section earlier in this topic. 

## <a name="aftercertrotation"></a> After certificate rotation

### Data encryption certificate

This certificate is used to encrypt data stored in the database. By default there are certain fields that are encrypted with this certificate, you can check those fields in [Document the values of encrypted fields](../database/dbmovement-scenario-goldenconfig.md#document-the-values-of-encrypted-fields). However, our API can be used to encrypt other fields that customers deem should be encrypted. 

In Platform update 33 and later, the batch job that is named "Encrypted data rotation system job" will use the newly rotated certificate to re-encrypt data. This batch job crawls through your data to re-encrypt all the encrypted data by using the new certificate. It will run for two hours per day until all of the data has been re-encrypted. In order to enable the batch job, a flight and a configuration key need to be enabled. Execute the following commands against your business database (for example, AXDB).

```sql
IF (EXISTS(SELECT * FROM SYSFLIGHTING WHERE [FLIGHTNAME] = 'EnableEncryptedDataCrawlerRotationTask'))
  UPDATE SYSFLIGHTING SET [ENABLED] = 1 WHERE [FLIGHTNAME] = 'EnableEncryptedDataCrawlerRotationTask'
ELSE
  INSERT INTO SYSFLIGHTING ([FLIGHTNAME],[ENABLED],[FLIGHTSERVICEID]) VALUES ('EnableEncryptedDataCrawlerRotationTask', 1, 0)
 
IF (EXISTS(SELECT * FROM SECURITYCONFIG WHERE [KEY_] = 'EnableEncryptedDataRotation'))
  UPDATE SECURITYCONFIG SET [VALUE] = 'True' WHERE [KEY_] = 'EnableEncryptedDataRotation'
ELSE
  INSERT INTO SECURITYCONFIG ([KEY_], [VALUE]) VALUES ('EnableEncryptedDataRotation', 'True')
```

After the above commands have been executed, restart your AOS nodes from Service Fabric Explorer. The AOS will detect the new configuration and will schedule the batch job to run during off hours. After the batch job has been created, the schedule can be modified from the user interface.

> [!WARNING]
> Make sure that the old Data Encryption certificate is not removed before all encrypted data has been re-encrypted and it has not expired. Otherwise, this could lead to data loss.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
