---
# required metadata

title: Apply updates to an on-premises deployment
description: This topic explains how to apply updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: manado
manager: AnnBe
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Unified Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12

---
# Apply updates to an on-premises deployment

[!include[banner](../includes/banner.md)]

This topic explains how to apply supported updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. All updates to on-premises environments are done through Microsoft Dynamics Lifecycle Services (LCS).

## Update types
Three types of updates can be applied to an on-premises deployment of Finance and Operations:

- Customizations
- Application X++ hotfixes that are released by Microsoft
- Platform updates

> [!NOTE] 
> At this time, application binary updates can't be applied to an on-premises environment.

## Save your configuration
Before you delete the environment you plan to update, use the following steps to save your configuration. 
1. In LCS, navigate to **Project Settings** > **On-prem Connectors**.
2. Select the connector to your environment, and then click **Edit**.
3. On the **Edit connector** tab, navigate to **Configure Agent** > **Enter Configuration**.
4. Copy the value of the Download Fileshare location in the **Configuration Settings** section. You will need this later.
5. Log in to the on-premises environment file share machine and copy the **\agent\wp<environment name>\StandaloneSetup\config.json**. You can use the configuration settings in this json file to redeploy your environment.

## Apply code customizations
To apply customizations at the same time that you deploy a new on-premises environment, follow the steps in [Develop and deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md). To apply new customizations to an on-premises environment that has already been deployed, follow these steps.

1. In LCS, open the on-premises implementation project.
2. Under **Environments**, select **Delete** to delete the application for the environment. This step cleans up the environment and removes any code that is deployed. **The on-premises agent, the data, and the infrastructure aren't affected when the application is deleted**.

    ![Delete an application](./media/apply-updates-on-prem-env-01.png)

3. Select **Configure** to re-deploy by using a new application and custom code.
4. In the advanced settings of the deployment configuration, select the application deployable package to apply, and then select **Done** to continue with the environment deployment process.

## Find and apply application hotfixes
There are two ways to find application hotfixes that are available:

- **Issue search in Lifecycle Services** – For more information about Issue search, see [Issue search](../lifecycle-services/issue-search-lcs.md).
- **Application X++ hotfix tiles** – For cloud-hosted environments, the **Environment details** page shows all hotfixes that are applicable to the environment, based on the version that is currently deployed. However, the tile functionality isn't available for on-premises environments. Therefore, to see the list of applicable hotfixes, you should maintain a cloud-hosted development environment that is the same version as the on-premises sandbox or production environment. Note that this approach is recommended only for X++ hotfixes, not for any other type of update.

Follow these steps to apply a hotfix.

1. Download the required hotfix to your development environment, and then follow the steps in [Create a deployable package](create-apply-deployable-package.md).
2. In the Asset library in LCS, upload the deployable package to the **Software deployable packages** tab.
3. As when you apply code customizations, you can include the above deployable package as an asset when you deploy an environment. To apply the package to a new environment or an environment that was previously deployed, follow the steps in the "Apply code customizations" section of this topic.

## Re-deploy your environment
The following instructions provide information about how to update or redeploy your environment with a new platform or topology.
1. In LCS, navigate to the **Environments** blade in your on-premises project.
2. Click **Delete** to delete your environment. 

    > [!NOTE]
    > Deleting the environment will not delete the database, infrastructure or Local agent. Only the Service Fabric applications are deleted.

3. Wait for a few minutes and verify that the deployment is deleted. To confirm the deployment is deleted, log in to the on-premises environment and navigate to the Service Fabric Explorer.

    The following applications should be deleted:
    - AXBootstapperAppType
    - AXSFType
    - FinancialReportingType
    - RTGatewayAppType
    - ReportingService
    
    The following on-premises service fabric agent applications should not be deleted:
    - LocalAgentType
    - MonitoringAgentAppType

4. After all of the applications in step 3 are deleted, go back to LCS and click **Configure**.
5. Select the new topology for your platform.
6. Enter the environment name. You can use the same name or enter a new one.
7. Click **Advanced Settings**.
   You can now use the relevant configurations from the .json file that you saved to configure your environment.

## Configuration settings
The following tables provide information about configuration settings. Use the **Configuration setting** value from the .json file that you saved in the previous procedure.

**Active Directory Federation Services settings**

| **Field**                                                                                                                                                | **Configuration setting**                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| The email address of the user who will be the initial administrator (such as, adminuser@yourdomain.com)                                                  | components.(AOS).parameters.provisioning.adminPrincipleName.value                        |
| ADFS OpenID metadata endpoint for the Dynamics 365 Application group. (such as, https://[federation-service-name]/adfs/.well-known/openid-configuration) | components.(AOS).parameters.activeDirectory.adfsMetadata.value                           |
| ADFS OpenID Connect client ID for the AOS application group                                                                                          | components.(AOS).parameters.activeDirectory.adfsClientId.value                           |
| ADFS OpenID Connect client ID for the Financial Reporting application group                                                                          | components.(FinancialReporting).parameters.aad.nativeClientAuthentication.clientId.value |

**SQL database configuration**

| **Field**                        | **Configuration setting**                                                              |
|------------------------------|------------------------------------------------------------------------------------|
| SQL SERVER                   | components.(AOS).parameters.database.dbServer.value          |
| AX DATABASE                  | components.(AOS).parameters.database.dbName.value            |
| FINANCIAL REPORTING DATABASE | components.(FinancialReporting).parameters.mrdb.dbName.value |
 
**File share settings**

| **Field**                                                                                                                              | **Configuration setting**                                                                  |
|------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| The file share path for the Microsoft Dynamics 365 instance. This share is used as the document store for files uploaded by users. | components.(AOS).parameters.storage.fileSharePath.value          |
| The File share certificate thumbprint for the Microsoft Dynamics 365 instance.                                                      | components.(AOS).parameters.storage.sharedAccessThumbprint.value |

   > [!NOTE]
   > When you copy the file path configuration value from .json file to LCS UI, make sure to remove the extra backslashes. For example, configuration value **\\\\DC1\\D365FFOStorage** from the .json file should be **\\DC1\D365FFOStorage** in the LCS UI.
    
**SSRS configuration settings**

| **Field**                                                                      | **Configuration setting**                                                                                      |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| The IP Address of the SSRS instance.                                        | components.(AOS).parameters.biReporting.persistentVirtualMachineIPAddressSSRS.value  |
| The thumbprint used by the SSRS application to communicate with AX Service. | components.(ReportingServices).parameters.reportingClientCertificateThumbprint.value |
 
**Configure service settings**

| **Field**                                                                                                                                      | **Configuration setting**                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| DYNAMICS 365 DNS INFORMATION - The DNS host name of the Microsoft Dynamics 365 instance, such as ax.d365ffo.onprem.contoso.com.           | components.(AOS).parameters.infrastructure.hostName                                            |
| AOS SERVICE PRINCIPAL USER SETTINGS - The domain user account to run the AX service, such as yourdomain\axserviceuser.                         | components.(AOS).parameters.infrastructure.principalUserAccountName *                          |
| MR SERVICE PRINCIPAL USER SETTINGS - The group managed service account (gMSA) to run the MR application service, such as yourdomain\Svc-FRAS$. | components.(FinancialReporting).parameters.ApplicationServicePrincipalUser.accountName.value * |
| The group managed service account (gMSA) to run the MR process service, such as yourdomain\Svc-FRPS$.                                          | components.(FinancialReporting).parameters.ProcessServicePrincipalUser.accountName.value *     |
| The group managed service account (gMSA) to run the MR click-once service, such as yourdomain\Svc-FRCO$.                                       | components.(FinancialReporting).parameters.ClickOnceServicePrincipalUser.accountName.value *   |
 
> [!NOTE]
> Remove the extra backslash from the Principal username cofiguration value in the .json file before entering in the LCS UI. For example, contoso\\AXServiceUser should be entered as contoso\AXServiceUser in LCS.
 
**Application certificate settings**

| **Field**                                                                         | **Configuration setting**                                                                                             |
|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| The thumbprint of the Data Encryption certificate.                             | components.(AOS).parameters.database.dataEncryptionCertificateThumbprint.value              |
| The thumbprint of the Data Signing certificate.                                | components.(AOS).parameters.database.dataSigningCertificateThumbprint.value                 |
| The thumbprint of the Session Authentication certificate.                      | components.(FinancialReporting).parameters.sessionAuthenticationCertificateThumbprint.value |
| The thumbprint of the SSL vertificate used for WCF/SOAP support.               | components.(AOS).parameters.infrastructure.sslCertificateThumbprint.value                   |
| The thumbprint used by the Management Reporter to communicate with AX service. | components.(FinancialReporting).parameters.tokenSpec.certThumbprint.value                   |



