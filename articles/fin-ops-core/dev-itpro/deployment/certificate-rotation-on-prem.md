---
title: Certificate rotation
description: Learn how to place existing certificates and update the references within the environment to use the new certificates.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.date: 02/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global 
ms.search.validFrom: 2019-04-30
ms.dyn365.ops.version: Platform update 25 
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Certificate rotation

[!include[banner](../includes/banner.md)]

You might need to rotate the certificates used by your Dynamics 365 Finance + Operations (on-premises) environment as they approach their expiration date. This article shows you how to replace the existing certificates and update the references within the environment to use the new certificates.

> [!WARNING]
> Initiate the certificate rotation process well before the certificates expire. This timing is very important for the Data Encryption certificate, which could cause data loss for encrypted fields if it expires. For more information, see [After certificate rotation](#aftercertrotation). 
> 
> Keep the old certificates in place until the certificate rotation process is complete. Removing them in advance causes the rotation process to fail.
>
> Don't carry out the certificate rotation process on Service Fabric clusters running 7.0.x and 7.1.x. 
>
> Upgrade your Service Fabric cluster to 7.2.x or later before attempting certificate rotation.

## Preparation steps 

1. Update your infrastructure scripts by following the steps in [Update your Infrastructure Scripts](obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).

1. In the **ConfigTemplate.xml** file, configure certificates as you require. Follow the steps in [Configure certificates](setup-deploy-on-premises-latest.md#configurecert). Specifically, follow these steps:

    ```powershell
    # Only run the first command if you have not generated the templates yet.
    .\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -CreateTemplates
    .\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!NOTE]
    > The AD CS scripts need to run on a domain controller, or a Windows Server computer with Remote Server Admin Tools installed.
    >
    > The AD CS functionality is only available with Infrastructure scripts release 2.7.0 and later. 

    Alternatively, if you want to continue to use self-signed certificates, run the following command.

    ```powershell
    # Create self-signed certs
    .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    > [!WARNING]
    > Never use self-signed certificates in production environments. If you're using publicly trusted certificates, manually update the values of those certificates in the `ConfigTemplate.xml` file.

    After you generate the certificates, run the following command.

    ```powershell
    # Exports certificates into a directory VMs\<VMName>. All certs are written to the infrastructure\Certs folder.
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Continue to [set up VMs](setup-deploy-on-premises-latest.md#setupvms). Here are the specific steps that are required for this process:

    1. Export the scripts that you must run on each VM.

        ```powershell
        # Exports the script files to be executed on each VM into a directory VMs\<VMName>.
        .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        ```

    1. Copy the contents of each `infrastructure\VMs<VMName>` folder into the corresponding VM. If you use remoting scripts, they automatically copy the content to the target VMs. Then, run the following script. Perform this step as an administrator.

        ```powershell
        # If remoting, only execute
        # .\Configure-PreReqs-AllVMs.ps1 -MSIFilePath <share folder path of the MSIs> -ConfigurationFilePath .\ConfigTemplate.xml -ForcePushLBDScripts

        .\Configure-PreReqs.ps1 -MSIFilePath <path of the MSIs>
        ```

    1. Run the following script to ensure that all prerequisites are completed. Perform this step as an administrator.

        ```powershell
        # If remoting, only execute
        # .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml 

        .\Complete-PreReqs.ps1
        ```

    1. Run the following script to validate the VM setup.

        ```powershell
        # If remoting, only execute
        # .\Test-D365FOConfiguration-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
        .\Test-D365FOConfiguration.ps1
        ```

1. Run the following PowerShell command so that you have values that you can use in Lifecycle Services later. For more information, see [Deploy your on-premises environment from Lifecycle Services](setup-deploy-on-premises-latest.md#deploy).

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

## Activate new certificates within Service Fabric cluster

To simplify the certificate rotation process, use certificate common names (subject name) instead of thumbprints for your Service Fabric standalone cluster configuration. If you have an existing cluster and want to migrate from using thumbprints to using certificate common names, follow the steps in [Appendix A](#appendix-a) later in this article.

### <a name=""></a>Service Fabric cluster with certificate common names

#### Service Fabric with certificates that aren't expired

No further action is required on the Service Fabric cluster. Service Fabric automatically detects the new certificates. Proceed with [Update the LocalAgent certificates](#update-the-localagent-certificates). 

If you change the certificate common name, you must upgrade your Service Fabric cluster configuration.

1. Run the following script to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateCommonNames
    ```

    > [!NOTE]
    > If the issuers also change, use the following command instead.
    >
    > ```powershell
    > .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateCommonNames -UpdateIssuers
    > ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

#### Service Fabric with certificates that are expired

If the cluster isn't available after 10 minutes from when you finished provisioning the new certificates to all nodes, consider restarting the nodes where the Service Fabric service isn't started.

If you change the certificate common name (subject name), the Service Fabric cluster won't start up. If you can't generate new certificates with the previous common name, you need to clean up and recreate the cluster.

#### Service Fabric with restricted certificate issuers

If the following sections are defined for your cluster configuration, the allowed certificate issuers are restricted. 

```json
"ClusterCertificateIssuerStores": [
    {
        "IssuerCommonName": "sample-ca",
        "X509StoreNames": "Root"
    }
],
"ServerCertificateIssuerStores": [
    {
        "IssuerCommonName": "sample-ca",
        "X509StoreNames": "Root"
    }
],
"ClientCertificateIssuerStores": [
    {
        "IssuerCommonName": "sample-ca",
        "X509StoreNames": "Root"
    }
],
```

If the issuer of your new certificates differs from what is defined in these configurations, you must go through a cluster configuration upgrade to add the new issuers.

If you need to update the list of issuers, make the update while the existing certificates are still valid.

1. Run the following script to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateIssuers
    ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

### <a name=""></a>Service Fabric cluster defined with certificate thumbprints

#### <a name="sfcertrotationnotexpired"></a>Service Fabric with certificates that aren't expired

1. Run the following script from a node that belongs to the Service Fabric cluster to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateThumbprints
    ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

#### Service Fabric with or without expired certificates (cluster not accessible)

If the cluster isn't accessible, continue this process by following the steps in [Troubleshoot on-premises deployments](troubleshoot-on-prem.md#clean-up-an-existing-environment-and-redeploy).

## Update the LocalAgent certificates

Reinstall the LocalAgent in the following situations:

- You change the Service Fabric cluster/server certificate.
- You change the Service Fabric client certificate.
- You change the LocalAgent certificate.

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

1. Follow the steps in [Configure Lifecycle Services connectivity for the tenant](setup-deploy-on-premises-latest.md#configurelcs).

    > [!NOTE] 
    > If you receive the error **Update to existing credential with KeyId '\<key\>' is not allowed**, follow the instructions in [Error: "Updates to existing credential with KeyId '\<key\>' is not allowed"](troubleshoot-on-prem.md#error-updates-to-existing-credential-with-keyid-key-is-not-allowed).

1. Continue with [Configure a connector and install an on-premises local agent](setup-deploy-on-premises-latest.md#configureconnector), specifically the following changes:

    - Client certificate thumbprint
    - Server certificate thumbprint
    - Tenant service principle certificate thumbprint

    > [!IMPORTANT]
    > Do **not** create a new connector in Lifecycle Services. Update the configuration of your existing connector and download the settings file again.

## Update your current deployment configuration

> [!NOTE]
> This step is necessary only for local agent versions 3.2.2 and older. If you're using local agent version 3.2.3 or later, you can skip this step.

Because you updated your certificates, you must manually update the configuration file in your environment. If you don't update the configuration file, the clean-up job might fail. You only need to perform this manual update once.

1. Open the configuration file `config.json` on your agent file share. This file is in a share similar to the following path: `\\fileserver\agent\wp\environmentID\StandaloneSetup-123456`. Run the following SQL statement on the orchestrator database to find the location of this file.

    ```sql
    select Location from DeploymentInstanceArtifact where AssetId='config.json' and DeploymentInstanceId = 'LCSENVIRONMENTID'
    ```

    > [!NOTE]
    > Replace **LCSENVIRONMENTID** with the ID of your environment. You can get this ID from the page for your environment in Lifecycle Services. This ID is the GUID value associated with your environment.

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

1. Replace the **serverCertThumprint** and **clientCertThumbprint** values with the new thumbprints.

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

1. Save and close the file. Close any programs that are accessing this network location. Otherwise, the cleanup process might fail.

## Rotate Credentials.json

If you generate a new **axdataencipherment** certificate, re-encrypt the **Credentials.json** file.

> [!NOTE]
> Make sure that you run the script from an Application Object Server (AOS) node.

```powershell
.\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Rotate
```

Alternatively, if you also want to rotate the existing credentials, follow these steps:

1. Decrypt the **Credentials.json** file.

    ```powershell
    .\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Decrypt
    ```

1. Open the **Credentials.json** file, and update any credentials that you want to update.

1. Re-encrypt the **Credentials.json** file.

    ```powershell
    .\Configure-CredentialsJson.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Action Encrypt
    ```

## Update deployment settings in Lifecycle Services

> [!NOTE]
> The process replaces only the Client, Data Signing, and Encipherment certificates.
>
> Before you continue, back up the local Dynamics database.

1. In Lifecycle Services, select the **Full Details** link for the environment where you want to change the certificates.

1. Select **Maintain** and then select **Update Settings**.

:::image type="content" source="media/addf4f1d0c0a86d840a6a412f774e474.png" alt-text="Screenshot of Apply update settings in Lifecycle Services. ":::

1. Change the thumbprints to the new thumbprints that you previously configured. You can find them in the `ConfigTemplate.xml` file in the `InfrastructureScripts` folder.

:::image type="content" source="media/07da4d7e02f11878ee91c61b4f561a50.png" alt-text="Screenshot of deployment settings thumbprint example 1. ":::

:::image type="content" source="media/785caaf4ee652d66c0d88cf615a57e26.png" alt-text="Screenshot of deployment settings thumbprint example 2. ":::

1. Select **Prepare**.

1. After the preparation finishes, the **Update environment** button displays.

:::image type="content" source="media/0a9d43044593450f1a828c0dd7698024.png" alt-text="Screenshot of Update environment button. ":::

1. Select **Update environment** to start updating your environment.

1. During the update, the environment is unavailable.

1. After the environment is successfully updated with the new certificates, you can view the new thumbprints in Service Fabric Cluster Explorer. The names of the thumbprints in Service Fabric Explorer might differ from the names in Lifecycle Services. However, the values should be the same.

    Here's an example of how the name of the same thumbprint might differ.

:::image type="content" source="media/038173714b2fb6cf12acc4bda2a3dde5.png" alt-text="Screenshot of thumbprint name example 1 in Service Fabric Explorer. ":::

:::image type="content" source="media/642f6434da9cdeac3651b765acca08fa.png" alt-text="Screenshot of thumbprint name example 2. ":::

## Update other certificates as needed

1. Always check if the SQL server certificate is expired. For more information, see [Set up SQL Server](setup-deploy-on-premises-latest.md#setupsql).

1. Check to be sure that the Active Directory Federation Service (ADFS) certificate isn't expired.

## <a name="cleanupoldsfcerts"></a>Clean up old Service Fabric certificates thumbprints

> [!NOTE]
>
> Run the following steps only if you're using a Service Fabric cluster defined with certificate thumbprints. If you're using common names, you can skip this step. 

Complete this procedure after a successful certificate rotation or before the next certificate rotation.

1. Run the following script to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -RemoveOldThumbprints
    ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

## <a name="aftercertrotation"></a>After certificate rotation

### Data encryption certificate

Use this certificate to encrypt data that you store in the database. By default, specific fields are encrypted by using this certificate. You can check those fields in [Document the values of encrypted fields](../database/dbmovement-scenario-goldenconfig.md#document-the-values-of-encrypted-fields). However, you can use the API to encrypt other fields as you require. 

In Platform update 33 and later, the **Encrypted data rotation system job** batch job uses the newly rotated certificate to re-encrypt data. This batch job crawls through your data to re-encrypt all the encrypted data by using the new certificate. The job runs for two hours each day until all the data is re-encrypted. To enable the batch job, you must enable a flight and a configuration key. Run the following commands against your business database (for example, AXDB).

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

After you run the commands, restart your AOS nodes from Service Fabric Explorer. AOS detects the new configuration and schedules the batch job to run during off hours. After the batch job is created, you can modify the schedule from the user interface.

> [!WARNING]
> Make sure that you don't remove the old data encryption certificate before all encrypted data is re-encrypted, and that it isn't expired. Otherwise, data might be lost.

## <a name="appendix-a"></a>Appendix A

Using certificate common names instead of thumbprints to describe your Service Fabric cluster configuration eases future certificate rotation operations as the Service Fabric cluster automatically switches to using new certificates once they're available in the machine. Service Fabric doesn't accept any certificate. However, the certificate that you provide must match the subject name that you define in the Service Fabric cluster. Additionally, the issuer of the certificate must match the issuer that you also specify in the configuration. For more information on how Service Fabric uses common names, see [Common name-based certificate validation declarations](/azure/service-fabric/cluster-security-certificates#common-name-based-certificate-validation-declarations). For more information on how to secure standalone Service Fabric clusters, see [Secure a standalone cluster on Windows by using X.509 certificates](/azure/service-fabric/service-fabric-windows-cluster-x509-security).

1. Run the following script to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpgradeToCommonNames
    ```

    > [!NOTE]
    > In some cases, you might choose to not restrict the issuer of the certificates in the Service Fabric cluster configuration. While this choice isn't recommended, you can achieve it by using the following command.
    >
    > ```powershell
    > .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpgradeToCommonNames -DoNotRestrictCertificateIssuers
    > ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
