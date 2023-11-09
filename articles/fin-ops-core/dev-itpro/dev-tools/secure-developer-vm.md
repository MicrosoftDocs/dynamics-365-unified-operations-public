---
title: Secure one-box development environments
description: This article describes how to help secure one-box developer environments.
author: mnordick
ms.date: 09/15/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mnordick
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
- 1 or more additional storage accounts that are prefixed with "dyn," for the storage of product binaries

Because these Azure resources will be under your own management, you might have to comply with security and compliance requirements that are specific to your organization. In addition, recommendations from sources such as Microsoft Defender or Azure Well-Architected security assessments might apply to your one-box developer environment. This article outlines some of these recommendations to help you make decisions that will best secure your one-box environments.

## Default configuration

Out of the box, your one-box developer environment has the following basic security configuration:

- Management ports on your VM are restricted to Microsoft Dynamics Lifecycle Services IP addresses. You can view these restrictions in the network security group in the resource group for your environment. Lifecycle Services uses the Windows Remote Management (WinRM) management port (5986) to do the initial configuration of your environment and to enable operations such as package deployments from Lifecycle Services.
- Remote Desktop Protocol (RDP) is one of the primary that ways one-box environments are accessed. Therefore, the RDP port (3389) is allowed by default. RDP access can be limited to your own client IP address in the network security group. As a best practice, you should limit RDP access to clients that require access after deployment. Customers can also consider using other Azure technologies, such as Azure Bastion, to securely obtain RDP access.
- On port 443, the one-box environment has a public endpoint that is exposed for HTTPS traffic. This endpoint is used by the environment URL and provides access to the product itself, which runs on the VM. By default, the endpoint is exposed to the internet. Although authorization is required for any sign-in to the site, as a best practice, you should still restrict port 443 access to clients that require it. This configuration will be specific to your organization, and you must define it after the environment is deployed.
- A storage account is associated with the environment for the storage of non-SQL data, such as document attachments. The configuration file on your VM contains a storage key in an encrypted field to enable your environment to access the storage account. The storage account has a publicly accessible IP address, because some product features require that the storage account be externally accessible.
- An additional storage account (prefixed with "dyn") in your subscription is used to host finance and operations code packages. This storage account is also publicly addressable and is required for Lifecycle Services to access code packages for deployment.

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
| Azure Government | gov.lcs.microsoftdynamics.us | 52.227.70.23<br>13.72.15.62<br>23.97.12.187<br>13.72.20.213 |
| China | lcs.dynamics.cn | 40.73.5.94<br>40.73.64.218<br>40.112.209.123<br>40.121.208.21 |
| Europe | eu.lcs.dynamics.com | 40.114.140.114<br>40.115.104.173 |
| France | fr.lcs.dynamics.com | 40.89.132.81<br>40.89.155.166<br>40.89.130.72<br>52.136.130.60<br>52.136.130.76 |
| South Africa | sa.lcs.dynamics.com | 102.133.165.35<br>102.133.67.149<br>40.127.1.92<br>102.133.67.146<br>40.127.4.34 |
| Switzerland | ch.lcs.dynamics.com | 51.103.133.142<br>51.103.146.43<br>51.103.138.255<br>51.107.226.123<br>51.107.224.152<br>51.107.224.175 |
| United Arab Emirates | uae.lcs.dynamics.com | 20.45.79.158<br>40.123.207.67<br>20.45.64.174<br>40.123.217.56<br>20.45.79.195 |

- If you're using a higher-level firewall outside the virtual network's network security group, you must allow a broader range of inbound ports from the Lifecycle Services source IP addresses. This requirement exists because the load balancer is configured to map a randomized port in the range 50000–65535 to well-known ports, such as the ports for WinRM and RDP. Deployment from Lifecycle Services requires that ports in this range be accessible.
- The HTTPS port (443) doesn't have to be exposed externally, and it isn't used during deployment or management operations.
- Outbound internet access must remain open from the virtual network. Finance and operations apps require internet access for various product functionalities. For example, access to Microsoft Entra is required for authentication.

Deployment to a custom virtual network is an advanced configuration. The preceding guidance is provided as an outline of the requirements that will help you successfully use a custom virtual network. An incorrect virtual network configuration can prevent deployment or management operations from Lifecycle Services. Therefore, make sure that you understand how the customizations might affect external integrations.

> [!NOTE]
> Because of the wide variety of possible customizations, Microsoft Support can't troubleshoot issues with custom configurations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration. Then incrementally apply your additional restrictions to isolate issues with the desired custom configuration.

## Security architecture recommendations

Microsoft Defender and Azure Well-Architected security assessments provide general security guidance that applies to any Azure resources that you provision in your subscription, including your one-box development environment resources.

When you're considering whether the recommendations are appropriate for you and your organization's policies, it's important that you follow the preceding guidance. For example, management ports must be accessible for Lifecycle Services to manage your environment, even though security assessments recommend that you close access to those ports. As another example, the guidance might recommend that you restrict network access to the environment's storage account. However, such restrictions will break some integration scenarios, such as export to Excel, that require that files be externally accessible for download. Finally, some recommendations about diagnostic and telemetry logging might incur additional costs that the resource owner will have to consider if those recommendations are applicable to their needs.

## Frequently asked questions

### Why does my newly provisioned one-box developer environment have security recommendations from Microsoft Defender and other security assessments?

Many recommendations from such assessments require engagement from the resource owner to determine whether they will incur any additional costs. You should consider the guidance in this article when you evaluate the implementation of any security recommendations.

### I want to restrict network access to my one-box developer environment, to help limit my security exposure. How can I block network access? 

- VM access can be restricted by using the network security group in the environment's resource group. The WinRM management port (5986) is already restricted so that it's accessible only by Lifecycle Services. The network security group rules for the RDP port (3389) and the HTTPS port (443) aren't limited by default. However, they can be restricted down to the client IPs of your choice.
- Outbound internet access must remain available for finance and operations apps to work.
- The environment's Azure storage account can have access restricted, but it must remain accessible by the VM's public IP address and the IP addresses of any authorized client. If you don't correctly allow access, finance and operations features that rely on the storage functionality will fail.

### My deployment fails when I try to provision with my custom virtual network. Can Microsoft tell me what is wrong?

The [Deploy to a custom virtual network](#deploy-to-a-custom-virtual-network) section of this article lists the network access requirements for the Azure resources for your environment. Unfortunately, because of the wide variety of possible configurations, Microsoft Support can't help troubleshoot custom networking configurations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration. Then incrementally apply your additional restrictions to isolate issues with the desired custom configuration.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]