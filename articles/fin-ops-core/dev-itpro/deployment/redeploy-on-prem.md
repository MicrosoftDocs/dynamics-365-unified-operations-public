---
title: Redeploy on-premises environments
description: Learn about redeploying an on-premises environment, including overviews on how to save and redeploy your configurations.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12
ms.service: dynamics-365-op
---
# Redeploy on-premises environments

[!include [banner](../includes/banner.md)]

At some point, you might need to redeploy your on-premises environment. This need might arise when you want to apply a new platform update or because of changes or problems in your implementation. Before you delete the environment you're currently working with, save your configuration settings so you can use them when you redeploy. This article describes how to save configuration settings and how to redeploy your environment.

## Save your configuration

Before you delete the environment you plan to update, use the following steps to save your configuration.

1. In Microsoft Dynamics Lifecycle Services, go to **Project Settings** > **On-prem Connectors**.
1. Select the connector to your environment, and then select **Edit**.
1. On **Edit connector**, go to **Configure Agent** > **Enter Configuration**.
1. Copy the value of the **Download Fileshare location** in the **Configuration Settings** section. You need this value later.
1. Sign in to the on-premises environment file share machine and copy the `\agent\wp<environment name>\StandaloneSetup\config.json`. You can use the configuration settings in this JSON file to redeploy your environment.

### Configuration settings

The following tables provide information about configuration settings. Use the **Configuration setting** value from the .json file that you saved in the previous procedure.

#### Active Directory Federation Services settings

|                                                                  <strong>Field</strong>                                                                  |                          <strong>Configuration setting</strong>                          |
|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
|                         The email address of the user who is the initial administrator (such as, `adminuser@yourdomain.com`)                          |            components.(AOS).parameters.provisioning.adminPrincipleName.value             |
| ADFS OpenID metadata endpoint for the Dynamics 365 Application group. (such as, https://[federation-service-name]/adfs/.well-known/openid-configuration) |              components.(AOS).parameters.activeDirectory.adfsMetadata.value              |
|                                               ADFS OpenID Connect client ID for the AOS application group                                                |              components.(AOS).parameters.activeDirectory.adfsClientId.value              |
|                                       ADFS OpenID Connect client ID for the Financial Reporting application group                                        | components.(FinancialReporting).parameters.aad.nativeClientAuthentication.clientId.value |

#### SQL database configuration

| **Field**                        | **Configuration setting**                                                              |
|------------------------------|------------------------------------------------------------------------------------|
| SQL SERVER                   | components.(AOS).parameters.database.dbServer.value          |
| AX DATABASE                  | components.(AOS).parameters.database.dbName.value            |
| FINANCIAL REPORTING DATABASE | components.(FinancialReporting).parameters.mrdb.dbName.value |

#### ile share settings

| **Field**                                                                                                                              | **Configuration setting**                                                                  |
|------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| The file share path for the Microsoft Dynamics 365 instance. This share is used as the document store for files uploaded by users. | components.(AOS).parameters.storage.fileSharePath.value          |
| The File share certificate thumbprint for the Microsoft Dynamics 365 instance.                                                      | components.(AOS).parameters.storage.sharedAccessThumbprint.value |

   > [!NOTE]
   > When you copy the file path configuration value from the .json file to the Lifecycle Services UI, make sure to remove the extra backslashes. For example, configuration value **\\\\DC1\\D365FFOStorage** from the .json file should be **\\DC1\D365FFOStorage** in the Lifecycle Services UI.

#### SSRS configuration settings

| **Field**                                                                      | **Configuration setting**                                                                                      |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| The IP Address of the SSRS instance.                                        | components.(AOS).parameters.biReporting.persistentVirtualMachineIPAddressSSRS.value  |
| The thumbprint used by the SSRS application to communicate with AX Service. | components.(ReportingServices).parameters.reportingClientCertificateThumbprint.value |

#### Configure service settings

| **Field**                                                                                                                                      | **Configuration setting**                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| DYNAMICS 365 DNS INFORMATION - The DNS host name of the Microsoft Dynamics 365 instance, such as ax.d365ffo.onprem.contoso.com.           | components.(AOS).parameters.infrastructure.hostName                                            |
| AOS SERVICE PRINCIPAL USER SETTINGS - The domain user account to run the AX service, such as yourdomain\axserviceuser.                         | components.(AOS).parameters.infrastructure.principalUserAccountName *                          |
| MR SERVICE PRINCIPAL USER SETTINGS - The group managed service account (gMSA) to run the MR application service, such as yourdomain\Svc-FRAS$. | components.(FinancialReporting).parameters.ApplicationServicePrincipalUser.accountName.value * |
| The group managed service account (gMSA) to run the MR process service, such as yourdomain\Svc-FRPS$.                                          | components.(FinancialReporting).parameters.ProcessServicePrincipalUser.accountName.value *     |
| The group managed service account (gMSA) to run the MR click-once service, such as yourdomain\Svc-FRCO$.                                       | components.(FinancialReporting).parameters.ClickOnceServicePrincipalUser.accountName.value *   |

> [!NOTE]
> Remove the extra backslash from the Principal username configuration value in the .json file before entering in the Lifecycle Services UI. For example, contoso\\\\AXServiceUser should be entered as contoso\AXServiceUser in Lifecycle Services.

#### pplication certificate settings

| **Field**                                                                         | **Configuration setting**                                                                                             |
|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| The thumbprint of the Data Encryption certificate.                             | components.(AOS).parameters.database.dataEncryptionCertificateThumbprint.value              |
| The thumbprint of the Data Signing certificate.                                | components.(AOS).parameters.database.dataSigningCertificateThumbprint.value                 |
| The thumbprint of the Session Authentication certificate.                      | components.(FinancialReporting).parameters.sessionAuthenticationCertificateThumbprint.value |
| The thumbprint of the SSL certificate used for WCF/SOAP support.               | components.(AOS).parameters.infrastructure.sslCertificateThumbprint.value                   |
| The thumbprint used by the Management Reporter to communicate with AX service. | components.(FinancialReporting).parameters.tokenSpec.certThumbprint.value                   |

## Redeploy your environment

The following instructions explain how to update or redeploy your environment with a new platform or topology.

1. In Lifecycle Services, go to the **Environments** section in your on-premises project.
1. Select **Delete** to delete your environment.

    > [!NOTE]
    > Deleting the environment doesn't delete the database, infrastructure, or local agent. Only the Service Fabric applications are deleted.

1. Wait a few minutes and verify that the deployment is deleted. To confirm the deployment is deleted, sign in to the on-premises environment and go to the Service Fabric Explorer.

    The following applications should be deleted:
   - AXBootstapperAppType
   - AXSFType
   - FinancialReportingType
   - RTGatewayAppType
   - ReportingService

     The following on-premises service fabric agent applications shouldn't be deleted:
   - LocalAgentType
   - MonitoringAgentAppType

1. After all of the applications in step 3 are deleted, go back to Lifecycle Services and select **Configure**.
1. Select the new topology for your platform.
1. Enter the environment name. You can use the same name or enter a new one.
1. Select **Advanced Settings**.
   You can now use the relevant configurations from the .json file that you saved to configure your environment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
