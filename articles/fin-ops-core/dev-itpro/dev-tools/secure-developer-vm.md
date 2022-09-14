---
title: Secure one-box development environments
description: This article describes how to secure one-box developer environments.
author: mnordick
ms.date: 09/14/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mnordick
ms.search.validFrom: 2022-09-13

---

# Secure one-box development environments

[!include [banner](../includes/banner.md)]

This article describes how to secure one-box developer environments.

One-box developer environments are composed of Microsoft Azure resources that are deployed into your own Azure subscription.

When you deploy a one-box developer environment, you can expect the following Azure resources to be deployed:
- 1 virtual machine (VM)
- 5 disks
- 1 load balancer
- 1 regular network interface
- 1 network security group
- 1 virtual network
- 1 public IP address
- 1 storage account
- 1 or more additional storage accounts prefixed with "dyn" for storage of product binaries.

Because these Azure resources will be under your own management, you may have security and compliance requirements specific to your organization to which you want to comply. There may also be recommendations coming from sources such as Microsoft Defender or Azure Well-Architected security assessments that apply to your one-box developer environment. This article outlines some of these common recommendations to help you to make decisions to best secure your one-box environments.

## Default configuration

By default, your one-box developer environment is configured out of the box with the following basic security configuration:

- Management ports on your VM are restricted to only Microsoft Dynamics Lifecycle Services (LCS) IP addresses. You can see these restrictions in the network security group within the resource group for your environment.
The WinRM management port (5986) is used by LCS to initially configure your environment, and also to enable operations like package deployments from LCS.
- Remote Desktop Protocol (RDP) is one of the primary ways one-box environments are accessed, so RDP port 3389 is allowed by default. RDP access can be limited to your own client IP address in the network security group. It's a best practice to limit RDP access only to clients who require access after deployment. Customers can also consider using other Azure technologies like Azure Bastion to securely obtain RDP access.
- The one-box environment has a public endpoint exposed for https traffic on port 443. This is the endpoint used by the environment URL and provides access to the product itself, running on the VM. The endpoint is exposed to the internet by default. Authorization is required for any sign-in to the site, however it would still be a best practice to restrict port 443 access to only clients that require it. This configuration would be specific to your organization and is something you would need to configure after the environment is deployed.
- There's a storage account associated with the environment for the storage of non-SQL data such as document attachments. The configuration file on your VM contains a storage key in an encrypted field that allows your environment to access the storage account. The storage account has a publicly accessible IP address because certain product features require the storage account to be externally accessible.
- There's an additional storage account (prefixed with "dyn") in your subscription that is used for hosting finance and operations code packages. This storage account is also publicly addressable and is required for LCS to access code packages for deployment.

## Deploy to a custom virtual network

LCS allows you to select a custom virtual network at the time of deployment. This capability makes it possible to deploy the one-box environment's VM directly into a preconfigured virtual network. However, several considerations must be taken when using a custom virtual network to ensure that LCS capabilities continue to function so that environment deployment can succeed.

- IP addresses from LCS must be allowed to access port 5986 on the VM. This port is required to both deploy and manage the environment from LCS. 

### LCS regional instances and IPs

> [!IMPORTANT] 
> The regional instances of LCS shown in the following table correspond to the LCS portal where you sign in to manage your project and environments. A portal's location can differ from the region where you intend to deploy your development environment.

| Geography | LCS URL | LCS IP addresses
|---|---|---|
| United States / Public | lcs.dynamics.com | 191.239.20.104<br/>40.76.5.241<br/>40.112.209.123<br/>40.121.208.21<br/>40.118.145.241 |
| Azure Government | gov.lcs.microsoftdynamics.us | 52.227.70.23<br/>13.72.15.62<br/>23.97.12.187<br/>13.72.20.213 |
| China | lcs.dynamics.cn | 40.73.5.94<br/>40.73.64.218<br/>40.112.209.123<br/>40.121.208.21 |
| Europe | eu.lcs.dynamics.com | 40.114.140.114<br/>40.115.104.173 |
| France | fr.lcs.dynamics.com | 40.89.132.81<br/>40.89.155.166<br/>40.89.130.72<br/>52.136.130.60<br/>52.136.130.76 |
| South Africa | sa.lcs.dynamics.com | 102.133.165.35<br/>102.133.67.149<br/>40.127.1.92<br/>102.133.67.146<br/>40.127.4.34 |
| Switzerland | ch.lcs.dynamics.com | 51.103.133.142<br/>51.103.146.43<br/>51.103.138.255<br/>51.107.226.123<br/>51.107.224.152<br/>51.107.224.175 |
| United Arab Emirates | uae.lcs.dynamics.com | 20.45.79.158<br/>40.123.207.67<br/>20.45.64.174<br/>40.123.217.56<br/>20.45.79.195 |

- If you're using a higher-level firewall outside of the virtual network's network security group, you'll need to allow a broader range of inbound ports from the LCS source IP addresses. This is because the load balancer is configured to map a randomized port in the range of 50,000-65535 to well-known ports such as those for Windows Remote Management (WinRM) and RDP. Deployment from LCS will require ports in this range to be accessible.
- Port 443 (https) isn't required to be exposed externally and isn't used during deployment or management operations.
- Outbound internet access must remain open from the virtual network. Finance and operations apps require internet access for various product functionalities, including access to Azure Active Directory (Azure AD) for authentication.

Deploying to a custom virtual network is an advanced configuration. The guidance above is provided to outline the requirements for you to be successful in using a custom virtual network. An incorrect virtual network configuration can prevent deployment or management operations from LCS, so care must be taken to understand how the customizations may impact external integrations.

> [!NOTE]
> Microsoft Support is unable to troubleshoot problems with custom configurations due to the wide variety of possible customizations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration and then incrementally apply your additional restrictions to isolate issues with the desired custom configuration.

## Security architecture recommendations

Microsoft Defender and Azure Well-Architected security assessments provide general security guidance that applies to any Azure resources you provision in your subscription, including your one-box development environment resources.

When considering if such recommendations are right for you and your organization's policies, it is important to follow the guidance above. For example, management ports are required to be accessible for LCS to manage your environment, even though security assessments recommend closing access to these ports. In another example, recommendations may include restricting network access to the environment's storage account, even though such restrictions would break some integration scenarios like exporting to Microsoft Excel that rely on files being externally accessible for download. Lastly, some recommendations around diagnostic and telemetry logging may incur additional costs that the resource owner will need to consider if applicable to their needs.

## Frequently asked questions

####  Why does my newly provisioned one-box developer environment have security recommendations from Microsoft Defender and other security assessments?

Many recommendations from such assessments require engagement from the resource owner to determine if they will incur any additional costs. The guidance in this article should be taken into consideration when evaluating the implementation of any security recommendations.

#### I want network access restricted to my one-box developer environment to limit my security exposure. How can I block network access? 

- VM access can be restricted using the network security group in the environment's resource group. The WinRM management port (5986) is already restricted to only be accessible by LCS. The network security group rules for RDP (3389) and https (443) ports are not limited by default, but can be restricted down to the client IPs of your choosing.
- Outbound internet access must remain available for finance and operations apps to function.
- The environment's Azure storage account can have access restricted but must remain accessible by the VM's public IP address and the IP address(es) of any authorized client. Failure to properly allow access will result in the failure of finance and operations features that rely on the storage functionality.

#### My deployment fails when I try to provision with my custom virtual network. Can Microsoft tell me what is wrong?

This document lists out the network access requirements for the Azure resources for your environment in the [Deploy to a custom virtual network](#deploy-to-a-custom-virtual-network) section. Unfortunately, Microsoft Support cannot help troubleshoot custom networking configurations due to the wide variety of possible configurations. The recommendation for troubleshooting is to use the default configuration as a known-good configuration and then incrementally apply your additional restrictions to isolate issues with the desired custom configuration.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
