---
title: Secure one-box development environments
description: This article describes security considerations of your one-box developer environment.
author: mnordick
ms.date: 09/13/2022
ms.topic: article
audience: Developer
ms.reviewer: 
ms.search.region: Global
ms.author: 
ms.search.validFrom: 2022-09-13
ms.dyn365.ops.version: AX 7.0.0
ms.custom:
ms.assetid:
---

# Securing one-box development environments

[!include [banner](../includes/banner.md)]

This article describes security considerations of your one-box developer environment.

## Overview

One-box developer environments are comprised of Azure resources which are deployed into your own Azure subscription.

> When you deploy a one-box developer environment, you can expect the following Azure resources to be deployed:
> + 1 Virtual machine
> + 5 Disks
> + 1 Load balancer
> + 1 Regular network interface
> + 1 Network security group
> + 1 Virtual network
> + 1 Public IP address
> + 1 Storage account
> + 1 or more additional storage accounts prefixed with “dyn” for storage of product binaries>

Because these resources will be under your own management, you may have security and compliance requirements which are specific to your organization for which you want to adhere. Additionally, there may also be many recommendations coming from various sources such as Microsoft Defender or Azure Well-Architected Security Assessments which apply to your one-box developer environment. This article will discuss some of these common recommendations to help you to make decisions on best securing your one-box environments.

## Default configuration

By default, your one-box developer environment is configured out of the box with a basic security configuration as follows:

1. Management ports on your Virtual Machine are restricted to only Life-Cycle Services (LCS) IP addresses. You can see these restrictions in the Network Security Group within the Resource Group for your environment.
The WinRM management port (5986) is utilized by Life-Cycle Services to both initially configure your environment, as well as to enable operations like package deployments from LCS.

2. Remote Desktop (RDP) is one of the primary ways one-box environments are accessed and so RDP port 3389 is allowed by default. RDP access can be limited in the Network Security Group to your own client IP address. It is a best practice to limit RDP access to only clients that require access after deployment. Additionally, customers can consider using other Azure technologies like Bastian to obtain RDP access securely.
3. The one-box environment has a public endpoint exposed for Https traffic on port 443. This is the endpoint used by the environment url and provides access the product itself, running on the Virtual Machine. By default, this endpoint is exposed to the Internet. Authorization is required for any login to the site, however, it would still be a best practice to restrict the access to this port to only the clients requiring it. This configuration would be specific to your organization and something you would need to configure after the environment is deployed.

4. There is a storage account associated with the enviornment for the storage of non-SQL data, such as document attachements. The configuration file on your Virtual Machine contains a the storage key in an encrypted field which allows your environment access this storage account. The storage account has a publicly accessible IP address because certain product features require the storage account to be externally accessible.

5. There is an additional storage account (prefixed dyn) in your subscription that is used for hosting the Finance and Operations code package. This storage account is also publicly addressable and is required for LCS to access for copying code packages for deployment.

## Deploying to a custom virtual network
Life-Cycle Services allows a custom virtual network to be chosen at deployment time. This capability makes it possible to deploy the one-box environment's Virtual Machine directly into a pre-configured virtual network. However, several considerations must be taken when using a custom virtual network to ensure Life-Cycle Services capabilities continue to function and environment deployment can succeed.

1. IP addresses from Life-Cycle Services must be allowed to access port 5986 on the Virtual Machine. These ports are required to both deploy and management the environment from LCS. The latest list of IPs allowed for port 5986 can be found in the default configured Network Security Group when using a non-custom vNet.
> If you are using a higher-level firewall, outside of the vNet's Network Security Group, you will need to allow a broader range of in-bound ports from the LCS source IP addresses. This is because the Load-Balancer is configured to map a randomized port in the range of 50,000-65535 to the well-known ports (such as WinRM and RDP). Deployment from LCS will require these port ranges to be accessible.

2. Port 443 (Https) is not required to be exposed externally and is not used during deployment or management operations.

3. Outbound internet access must remain open from the virtual network. The Finance and Operations product requires internet access for various product functionalities, including access to Azure Active Directory for authentication.

Deploying to a custom virtual network is an advanced configuration. The guidance above is provided to outline the requirements for you to be successful in using a custom virtual network. An incorrect virtual network conifguration can prevent deployment or management operations from LCS and care must be taken to understand how the customizations may impact external integrations.

>Note:  Microsoft Support is unable to trouble-shoot problems with custom configurations due to the wide variety of possible customizations. The recommendation for troubleshooting is to leverage the default configuration as a known-good configuration and apply your additional restrictions incrementally to narrow down problems with the desired custom configuration.

## Security architecture recommendations

Microsoft Defender and Azure Well-Architected Security Assessments provide general security guidance which apply to any Azure resources you provision in your subscription, including your one-box development environment resources.

When considering if these recommendations are right for you and your organization's policies, it is important that the above guidance be taken into consideration. For example, Management Ports are required to be accessible for LCS to manage your environment, even though security assessments recommend closing access to these ports. As another example, recommendations may include restricting network access to the environment's storage account, however this will break some integration scenarios like Export to Excel which rely on the file being accessible externally for download. Lastly, some recommendations around diagnostic and telemetry logging may incur additional costs that the resource owner will need to consider if is applicable to their needs.


# Frequently asked questions

##  Why does my newly provisioned One-Box Developer Environment have security recommendations from Microsoft Defender and other security assessments?
Many of the recommendations from these assessments require engagement from the resource owner to fully implement or to consider if they will incur any additional costs. The guidance in this document should be taken into consideration when evaluating the implementation of any security recommendations.

## I want network access restricted to my one-box developer environment to limit my security exposure. How can I block network access? 
* Virtual Machine access can be restricted using the Network Security Group in the environment's resource group. The WinRM management port (5986) is already restricted to only be accessible my Microsoft Life-Cycle Services. The Network Security Group rules for RDP (3389) and Https (443) ports are not limited by default, but can be restricted down to the client IPs of your choosing.
    * Outbound internet access must remain available for the Finance and Operations product to function.
* The environment's Azure Storage Account can have access restricted but must remain accessible by the Virtual Machine's public IP and the IP(s) of any authorized client. Failure to properly allow this access will result in failure of Finance and Operations features that rely on the storage functionality.

## My deployment is failing when I tried to provision with my custom vNet. Can Microsoft tell me what is wrong?
This document lists out the network access requirements for the Azure resources for your environment. Please refer to the section titled Deploying to a custom vitual network. Unfortunately, due to the wide variety of possible configurations, Microsoft Support cannot help troubleshoot custom networking configurations. The recommendation for troubleshooting is to leverage the default configuration as a known-good configuration and apply your additional restrictions incrementally to narrow down problems with the desired custom configuration.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]