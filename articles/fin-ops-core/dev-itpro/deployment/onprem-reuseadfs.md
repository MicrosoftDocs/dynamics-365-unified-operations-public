---
# required metadata

title: Reuse the same AD FS instance for multiple environments
description: This article explains how to use the same instance of Active Directory Federation Services (AD FS) in multiple Microsoft Dynamics 365 Finance + Operations (on-premises) environments.
author: faix
ms.date: 03/03/2020
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2020-03-31 
ms.dyn365.ops.version: Platform update 33 
search.app:
  - financeandoperationsonprem-docs
---

# Reuse the same AD FS instance for multiple environments

[!include [banner](../includes/banner.md)]

This article explains how to use the same instance of Active Directory Federation Services (AD FS) in multiple Microsoft Dynamics 365 Finance + Operations (on-premises) environments.

## Setup

> [!IMPORTANT]
> This procedure assumes that you've previously configured AD FS for one environment by following the instructions in the [Set up and deploy on-premises environments](./setup-deploy-on-premises-environments.md) content. It also assumes that that environment is running without any issues.

1. In AD FS Manager, go to **AD FS** \> **Application groups**, and open **Microsoft Dynamics 365 for Operations On-premises**.
2. In the **Native application** section, follow these steps:

    1. Open **Microsoft Dynamics 365 for Operations On-premises - Native application**, and add the redirect URI of the new environment (`https://ax.contoso.com/namespaces/AXSF`).
    2. Open **Microsoft Dynamics 365 for Operations On-premises - Financial Reporting - Native application**, and add the redirect URI of the new environment (`https://ax.contoso.com/FinancialReporting/ApplicationService/soap/`).

3. In the **Web API** section, follow these steps:

    1. Open **Microsoft Dynamics 365 for Operations On-premises - Web API**, and add two entries for the redirect URI of the new environment (`https://ax.contoso.com/namespaces/AXSF` and `https://ax.contoso.com`).
    2. Open **Microsoft Dynamics 365 for Operations On-premises - Financial Reporting Web API**, and add the redirect URI of the new environment (`https://ax.contoso.com/FinancialReporting`).

4. Optional: In the **Server** section, open **Microsoft Dynamics 365 for Operations On-premises - Retail**, and add the redirect URI of the new environment (`https://ax.contoso.com/namespaces/AXSF/`).
5. Optional: Configure the warehouse mobile app for the new environment by following the instructions in [Configure the Warehousing app for on-premises deployments](./warehousing-for-on-premise-deployments.md) again. Remember to use the URI of the new environment (`https://ax.contoso.com`) as the **Resource URL** value.

    > [!NOTE]
    > No additional configuration is required for the workflow and retail designer applications.

6. Verify that you can reach the OpenID metadata endpoint (`https://<adfs-dns-name>/adfs/.well-known/openid-configuration`) from the **AOS** and **MR** nodes in your new environment. If you're using self-signed certificates, you might have to import the AD FS Secure Sockets Layer (SSL) certificate into the Trusted Root Certification Authorities store of each node.
7. When you deploy the new environment from Microsoft Dynamics Lifecycle Services (LCS) and are specifying the deployment configuration, make sure that you use the same AD FS OpenID metadata endpoint and AD FS OpenID connect client IDs that you specified for the previous environment.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
