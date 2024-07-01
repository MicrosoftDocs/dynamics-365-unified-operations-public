---
title: Secure one-box development environments
description: Learn about how to help secure one-box developer environments, including outlines on default congigurations and how to deploy to a custom virtual network.
author: mnordick
ms.author: mnordick
ms.date: 07/01/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2022-09-13
---

# Secure one-box development environments

[!include [banner](../includes/banner.md)]

This article describes how to help secure one-box developer environments.

One-box developer environments consist of Microsoft Azure resources that are deployed in your own Azure subscription.

When you deploy a one-box developer environment, you can expect the following Azure resources to be deployed:

- 1 virtual machine (VM)
- 5 disks
- 1 load balancer
- 1 regular network interface
- 1 network security group
- 1 virtual network
- 1 public IP address
- 1 storage account
- 1 or more other storage accounts that are prefixed with "dyn," for the storage of product binaries

Because these Azure resources are under your own management, you might have to comply with security and compliance requirements that are specific to your organization. In addition, recommendations from sources such as Microsoft Defender or Azure Well-Architected security assessments might apply to your one-box developer environment. This article outlines some of these recommendations to help you make decisions that best secure your one-box environments.

## Default configuration

Out of the box, your one-box developer environment has the following basic security configuration:

- Management ports on your VM are restricted to Microsoft Dynamics Lifecycle Services IP addresses. You can view these restrictions in the network security group in the resource group for your environment. Lifecycle Services uses the Windows Remote Management (WinRM) management port (5986) to do the initial configuration of your environment and to enable operations such as package deployments from Lifecycle Services.
- Remote Desktop Protocol (RDP) is one of the primary ways that one-box environments are accessed. Therefore, the RDP port (3389) is allowed by default. RDP access can be limited to your own client IP address in the network security group. As a best practice, you should limit RDP access to clients that require access after deployment. Customers can also consider using other Azure technologies, such as Azure Bastion, to securely obtain RDP access.
- On port 443, the one-box environment has a public endpoint that's exposed for HTTPS traffic. This endpoint is used by the environment URL and provides access to the product itself, which runs on the VM. By default, the endpoint is exposed to the internet. Although authorization is required for any sign-in to the site, as a best practice, you should still restrict port 443 access to clients that require it. This configuration is specific to your organization, and you must define it after the environment is deployed.
- A storage account is associated with the environment for the storage of non-SQL data, such as document attachments. The configuration file on your VM contains a storage key in an encrypted field to enable your environment to access the storage account. The storage account has a publicly accessible IP address, because some product features require that the storage account be externally accessible.
- Another storage account (prefixed with "dyn") in your subscription is used to host finance and operations code packages. This storage account is also publicly addressable and is required for Lifecycle Services to access code packages for deployment.

## Deploy to a custom virtual network

Lifecycle Services lets you select a custom virtual network at the time of deployment. In this way, you can deploy the one-box environment's VM directly to a preconfigured virtual network. However, when you use a custom virtual network, you must consider several points to ensure that Lifecycle Services capabilities continue to function, so that environment deployment can succeed.

- IP addresses from Lifecycle Services must be allowed to access port 5986 on the VM. This port is required to both deploy and manage the environment from Lifecycle Services.

### Lifecycle Services regional instances and IPs

The following table shows the regional instances of Lifecycle Services.

> [!IMPORTANT]
> These regional instances correspond to the Lifecycle Services portal where you sign in to manage your project and environments. A portal's location can differ from the region where you intend to deploy your development environment.

| Geography | Lifecycle Services URL | Lifecycle Services IP addresses |
|---|---|---|
| United States/Public | lcs.dynamics.com | 191.239.20.104<br>40.76.5.241<br>40.112.209.123<br>40.121.208.21<br>40.118.145.241 |
| Azure Government/GCC | gov.lcs.microsoftdynamics.us | 20.141.106.7<br>20.141.192.69 |
| Azure Government/GCC High | high.lcs.microsoftdynamics.us | 52.245.167.30<br>20.141.241.11 |
| China | lcs.dynamics.cn | 40.73.5.94<br>40.73.64.218<br>40.112.209.123<br>40.121.208.21 |
| Europe | eu.lcs.dynamics.com | 40.114.140.114<br>40.115.104.173 |
| France | fr.lcs.dynamics.com | 40.89.132.81<br>40.89.155.166<br>40.89.130.72<br>52.136.130.60<br>52.136.130.76 |
| South Africa | sa.lcs.dynamics.com | 102.133.165.35<br>102.133.67.149<br>40.127.1.92<br>102.133.67.146<br>40.127.4.34 |
| Switzerland | ch.lcs.dynamics.com | 51.103.133.142<br>51.103.146.43<br>51.103.138.255<br>51.107.226.123<br>51.107.224.152<br>51.107.224.175 |
| United Arab Emirates | uae.lcs.dynamics.com | 20.45.79.158<br>40.123.207.67<br>20.45.64.174<br>40.123.217.56<br>20.45.79.195 |

- If you're using a higher-level firewall outside the virtual network's network security group, you must allow a broader range of inbound ports from the Lifecycle Services source IP addresses. This requirement exists because the load balancer is configured to map a randomized port in the range 50000–65535 to well-known ports, such as the ports for WinRM and RDP. Deployment from Lifecycle Services requires that ports in this range be accessible.
- The HTTPS port (443) doesn't have to be exposed externally, and it isn't used during deployment or management operations.
- Outbound internet access must remain open from the virtual network. Finance and operations apps require internet access for various product functionalities. For example, access to Microsoft Entra is required for authentication.

Deployment to a custom virtual network is an advanced configuration. The preceding guidance is provided as an outline of the requirements that help you successfully use a custom virtual network. An incorrect virtual network configuration can prevent deployment or management operations from Lifecycle Services. Therefore, make sure that you understand how the customizations might affect external integrations.

> [!NOTE]
> Because of the wide variety of possible customizations, Microsoft Support can't troubleshoot issues with custom configurations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration. Then incrementally apply your other restrictions to isolate issues with the desired custom configuration.

## Security architecture recommendations

Microsoft Defender and Azure Well-Architected security assessments provide general security guidance that applies to any Azure resources that you provision in your subscription, including your one-box development environment resources.

When you're considering whether the recommendations are appropriate for you and your organization's policies, it's important that you follow the preceding guidance. For example, management ports must be accessible for Lifecycle Services to manage your environment, even though security assessments recommend that you close access to those ports. As another example, the guidance might recommend that you restrict network access to the environment's storage account. However, these restrictions break some integration scenarios, such as export to Microsoft Excel, that requires that files are externally accessible for download. Finally, some recommendations about diagnostic and telemetry logging might incur more costs that the resource owner must consider if those recommendations are applicable to their needs.

## External integrations

Your one-box development environment can integrate with your Microsoft Entra tenant for added capabilities. Here are some of these capabilities:

- Import users.
- Import Microsoft Entra ID groups.
- Import Electronic reporting (ER) configurations. For more information about how to import ER configurations, see [Dynamics 365 Finance + Operations (on-premises) environments and enable the functionality](../analytics/electronic-reporting-import-ger-configurations.md).
- Report execution using WCF service.
- Data Task Automation.

To use these capabilities, you must configure certificate access to your tenant.

> [!NOTE]
> You should be careful about granting access to your Microsoft Entra tenant. Unless these capabilities are required for development, Microsoft recommends that you restrict certificate access to your tenant.
>
> As of November 15, 2023, certificates in your Microsoft Entra tenant are no longer installed in new one-box development environments by default. This change affects the external integrations that are mentioned in this section. To reenable this capability, use the instructions that follow.
>
> This change doesn't affect development environments that were deployed before November 15, 2023. These certificates can optionally be removed. For instruction, see the [Frequently asked questions](#frequently-asked-questions) section of this article.

If you must use the previously mentioned capabilities in your one-box development environment, follow the steps in the next section to set up a new application and tenant certificate.

### Set up a new application and certificate registration

1. Create an application. For more information, see [Register an application with the Microsoft identity platform](/entra/identity-platform/quickstart-register-app#register-an-application).
2. [Create a certificate](/azure/key-vault/certificates/create-certificate#partnered-ca-providers), and [add it to your service principal](/entra/identity-platform/quickstart-register-app#add-a-certificate).
3. Install the certificate on the cloud-hosted environment virtual machine (VM).
4. In the **web.config** file under **K:\\AosService\\webroot\\**, replace the value of the `Aad.Realm` key with the application ID/client ID. Replace the value of the `Infrastructure.S2SCertThumbprint` key and the `GraphApi.GraphAPIServicePrincipalCert` key with the value of the installed certificate's thumbprint.

    ```
    <add key="Aad.Realm" value="spn:<your application ID>" />
    <add key="Infrastructure.S2SCertThumbprint" value="<certificate thumbprint>" />
    <add key="GraphApi.GraphAPIServicePrincipalCert" value="<certificate thumbprint>" />
    ```

5. In the **wif.config** file under **K:\\AosService\\webroot\\**, Add a new entry under `audienceUris` below the existing value for the customer's Entra AppId. Do not remove the spn:00000015-0000-0000-c000-000000000000 entry.
    ```
    <securityTokenHandlerConfiguration>
    <audienceUris>
    <add value="spn:00000015-0000-0000-c000-000000000000" />
    <add value="spn:<your application ID>" />
    </audienceUris>
    ```
6. Add the environment URL as a redirect URI for the application under **Web App** platform. For more information, see [Add a redirect URI](/entra/identity-platform/quickstart-register-app#add-a-redirect-uri).
7. Add the environment OAUTH URL (EnvironmentURL/oauth) as a redirect URI for the application under **Web App** platform.
8. Assign the API permissions for the application:

    1. Go to **API Permissions**, select **Add a Permission**, and add the following permissions:

        - **Dynamics ERP** – This permission is required to access finance and operations environments.
        - **Microsoft Graph** (**User.Read.All** and **Group.Read.All** permissions of the **Application** type)
        - **Dynamics Lifecycle service** (permission of type **Delegated**)

    2. In the cloud-hosted environment, grant **Read** access to the network service for the newly installed certificate.
9. Clear any cached configurations for LCS access using the SQL query on AX DB:
     ```
     DELETE FROM SYSOAUTHCONFIGURATION where SECURERESOURCE = 'https://lcsapi.lcs.dynamics.com'
  
     DELETE FROM  SYSOAUTHUSERTOKENS where SECURERESOURCE = 'https://lcsapi.lcs.dynamics.com'
     ```
10. Perform IISRESET from administrator command prompt.    

## Frequently asked questions

### Why does my newly provisioned one-box developer environment have security recommendations from Microsoft Defender and other security assessments?

Many recommendations from such assessments require engagement from the resource owner to determine whether they incur any more costs. You should consider the guidance in this article when you evaluate the implementation of any security recommendations.

### I want to restrict network access to my one-box developer environment, to help limit my security exposure. How can I block network access? 

- VM access can be restricted by using the network security group in the environment's resource group. The WinRM management port (5986) is already restricted so that it's accessible only by Lifecycle Services. The network security group rules for the RDP port (3389) and the HTTPS port (443) aren't limited by default. However, they can be restricted down to the client IPs of your choice.
- Outbound internet access must remain available for finance and operations apps to work.
- The environment's Azure storage account can have access restricted, but it must remain accessible by the VM's public IP address and the IP addresses of any authorized client. If you don't correctly allow access, finance and operations features that rely on the storage functionality fail.

### My deployment fails when I try to provision with my custom virtual network. Can Microsoft tell me what's wrong?

The [Deploy to a custom virtual network](#deploy-to-a-custom-virtual-network) section of this article lists the network access requirements for the Azure resources for your environment. Unfortunately, because of the wide variety of possible configurations, Microsoft Support can't help troubleshoot custom networking configurations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration. Then incrementally apply your other restrictions to isolate issues with the desired custom configuration.

### I have a development environment that I deployed before November 15, 2023. Do I have to take any action?

No action is required for your development environment to continue to function as is. However, Microsoft encourages customers to limit their tenant's security exposure and recommends that they remove this certificate if it isn't required. For information about the feature areas that require this certificate, see the [External integrations](#external-integrations) section.

To optionally remove the Dynamics ERP application certificate from your tenant's service principal, follow these steps from any one of your one-box development VMs.

1. In Lifecycle Services, download version 2.19.1 or later of the infrastructure scripts for on-premises deployments from the Shared asset library. This asset is available in the global and EU Lifecycle Services regions. For more information, see [Obtain the infrastructure scripts for your Finance + Operations (on-premises) deployment](../deployment/obtain-infrascripts-onprem.md#download-the-infrastructure-scripts).
2. Find the thumbprint of your S2S certificate. You must specify this thumbprint when you run the script in the next step. To find it, open the **web.config** file under **K:\\AosService\\webroot\\**, and look for the `Infrastructure.S2SCertThumbprint` key.
3. Run the following PowerShell script to remove the certificate from your service principal.

    ``` PowerShell
    .\Remove-CertFromServicePrincipal.ps1 -CertificateThumbprint <thumbprint of your S2S certificate>
    ```

    If you're unsure whether a certificate is registered against your service principal, you can run the following PowerShell script to validate this fact.

    ``` PowerShell
    .\Remove-CertFromServicePrincipal.ps1 -CertificateThumbprint <thumbprint of your S2S certificate> -Test
    ```

    If your account has access to multiple tenants, you can run the following PowerShell script to specify the tenant where you want to perform the operation.

    ``` PowerShell
    .\Remove-CertFromServicePrincipal.ps1 -CertificateThumbprint <thumbprint of your S2S certificate> -Tenant <your tenant ID>
    ```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
