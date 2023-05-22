---
title: Redeploy on-premises environments
description: This article provides information about redeploying an on-premises environment.
author: faix
ms.date: 10/14/2020
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12
ms.custom: 
ms.assetid: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---
# Redeploy on-premises environments

[!include [banner](../includes/banner.md)]

At some point, you might have to redeploy your on-premises environment. This could be to apply a new platform update or because of changes or issues in your implementation. Before you delete the environment you are currently working with, you should save your configuration setting information to use when you redeploy. This article describes how to save configuration settings and how to redeploy your environment. 

## Save your configuration
Before you delete the environment you plan to update, use the following steps to save your configuration. 
1. In LCS, navigate to **Project Settings** > **On-prem Connectors**.
2. Select the connector to your environment, and then click **Edit**.
3. On the **Edit connector** tab, navigate to **Configure Agent** > **Enter Configuration**.
4. Copy the value of the Download Fileshare location in the **Configuration Settings** section. You will need this later.
5. Log in to the on-premises environment file share machine and copy the `\agent\wp<environment name>\StandaloneSetup\config.json`. You can use the configuration settings in this json file to redeploy your environment.

### Configuration settings
The following tables provide information about configuration settings. Use the **Configuration setting** value from the .json file that you saved in the previous procedure.

**Active Directory Federation Services settings**


|                                                                  <strong>Field</strong>                                                                  |                          <strong>Configuration setting</strong>                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
|                         The email address of the user who will be the initial administrator (such as, `adminuser@yourdomain.com`)                          |            components.(AOS).parameters.provisioning.adminPrincipleName.value             |
| ADFS OpenID metadata endpoint for the Dynamics 365 Application group. (such as, https://[federation-service-name]/adfs/.well-known/openid-configuration) |              components.(AOS).parameters.activeDirectory.adfsMetadata.value              |
|                                               ADFS OpenID Connect client ID for the AOS application group                                                |              components.(AOS).parameters.activeDirectory.adfsClientId.value              |
|                                       ADFS OpenID Connect client ID for the Financial Reporting application group                                        | components.(FinancialReporting).parameters.aad.nativeClientAuthentication.clientId.value |

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
> Remove the extra backslash from the Principal username cofiguration value in the .json file before entering in the LCS UI. For example, contoso\\\\AXServiceUser should be entered as contoso\AXServiceUser in LCS.

**Application certificate settings**

| **Field**                                                                         | **Configuration setting**                                                                                             |
|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| The thumbprint of the Data Encryption certificate.                             | components.(AOS).parameters.database.dataEncryptionCertificateThumbprint.value              |
| The thumbprint of the Data Signing certificate.                                | components.(AOS).parameters.database.dataSigningCertificateThumbprint.value                 |
| The thumbprint of the Session Authentication certificate.                      | components.(FinancialReporting).parameters.sessionAuthenticationCertificateThumbprint.value |
| The thumbprint of the SSL certificate used for WCF/SOAP support.               | components.(AOS).parameters.infrastructure.sslCertificateThumbprint.value                   |
| The thumbprint used by the Management Reporter to communicate with AX service. | components.(FinancialReporting).parameters.tokenSpec.certThumbprint.value                   |



## Redeploy your environment
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





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
