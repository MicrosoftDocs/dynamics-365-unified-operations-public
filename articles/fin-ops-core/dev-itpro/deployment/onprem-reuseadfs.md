---
# required metadata

title: Reuse the same AD FS instance for multiple environments
description: This topic explains how to use the same instance of Active Directory Federation Services (AD FS) in multiple Dynamics 365 Finance + Operations (on-premises) environments.
author: faix
manager: AnnBe
ms.date: 03/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2020-03-01 
ms.dyn365.ops.version: Platform update 33 

---

# Reuse the same AD FS instance for multiple environments

[!include [banner](../includes/banner.md)]

This topic explains how to use the same instance of Active Directory Federation Services (AD FS) in multiple Dynamics 365 Finance + Operations (on-premises) environments.

>[!IMPORTANT]
> This guide assumes that you have previosuly configured Active Directory Federation Services (AD FS) for one environment using the steps detailed in the setup guide and that environment is running without any problems.

## Setup

1.  In AD FS Manager, go to AD FS > Application groups, and open Microsoft Dynamics 365 for Operations On-premises.
2.  Under the Native application section:
    1.  Open the Microsoft Dynamics 365 for Operations On-premises - Native application. Add the redirect URI of the new environment (https://ax.contoso.com/namespaces/AXSF).
    2.  Open the Microsoft Dynamics 365 for Operations On-premises - Financial Reporting - Native application. Add the redirect URI of the new environment (https://ax.contoso.com/FinancialReporting/ApplicationService/soap/).
3.  Under the Web API section:
    1.	Open the Microsoft Dynamics 365 for Operations On-premises - Web API. Add the two entries of the redirect URI of the new environment (https://ax.contoso.com/namespaces/AXSF and https://ax.contoso.com).
    2.  Open the Microsoft Dynamics 365 for Operations On-premises - Financial Reporting Web API. Add the redirect URI of the new environment (https://ax.contoso.com/FinancialReporting).
4.  Under the Server section:
    1.  (Optional) Open the Microsoft Dynamics 365 for Operations On-premises - Retail. Add the redirect URI of the new environment (https://ax.contoso.com/namespaces/AXSF/).
5.  Optional: Configure the warehouse mobile app for the new environment by following [Configure the Warehousing app for on-premises deployments](./warehousing-for-on-premise-deployments.md) again. Remember to use the new environment URL (https://ax.contoso.com) as the Resource URL.

    >[!Note]
    > No additional configuration is required for the workflow and retail designer applications.

6.  Check that you're able to reach the OpenID metadata endpoint (https://<adfs-dns-name>/adfs/.well-known/openid-configuration) from the AOS and MR nodes in your new environment. If you're using self-signed certificates, you may need to import the AD FS SSL certificate to the Trusted Root Certification Authorities store of each node. 
7.  When deploying the new environment from LCS and specifying the deployment configuration, ensure that you use the same AD FS OpenID metadata endpoint and AD FS OpenID connect client IDs that you specified for the previous environment. 

