---
# required metadata

title: Dynamics 365 Finance and Dynamics 365 Supply Chain Management in US Government Community Cloud (GCC)
description: Select Dynamics 365 US Government products are available to qualified government and private entities, limited to (i) United States (US) federal, state, local, tribal, and territorial government entities; (ii) private entities using Dynamics 365 US Government to provide solutions to a government entities or a qualified member of the cloud community; and (iii) private entities with customer data subject to government regulations for which the use of Dynamics 365 US Government is the appropriate service to meet the regulatory requirements.
author: hasaid
ms.date: 11/09/2021
ms.topic: article
audience: Application User
ms.reviewer: sericks
ms.search.region: Global
ms.author: hasaid
ms.search.validFrom: 2021-11-09
---

# Dynamics 365 Finance and Dynamics 365 Supply Chain Management in US Government Community Cloud (GCC)

[!include [banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Select Dynamics 365 US Government products are available to qualified government and private entities, limited to (i) United States (US) federal, state, local, tribal, and territorial government entities; (ii) private entities using Dynamics 365 US Government to provide solutions to a government entities or a qualified member of the cloud community; and (iii) private entities with customer data subject to government regulations for which the use of Dynamics 365 US Government is the appropriate service to meet the regulatory requirements.
For information , see [Dynamics 365 US Government](/power-platform/admin/microsoft-dynamics-365-government).

## Onboarding

To perform initial onboarding steps for an implementation project in Lifecycle Services (LCS), follow the instructions detailed at [Onboard an implementation project](../../../fin-ops-core/fin-ops/imp-lifecycle/onboard.md). However, please note the following URL should be used in place of the Lifecycle Services specified there.

 > [!NOTE]
    > The URL to access Lifecycle Services (LCS) for the US Government Community Cloud is [Dynamics Lifecycle Services GCC](https://gov.lcs.microsoftdynamics.us)

Once the initial onboarding steps are complete in Lifecycle Services (LCS), proceed to follow the instructions at [Project onboarding](../lifecycle-services/project-onboarding.md). Again, be sure to substitute the URL above for LCS.

## Environment Deployment

After completing project onboarding as described above you may review additional capabilities of LCS at [Lifecycle Services (LCS) for Finance and Operations apps customers](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs.md) and then proceed to environment deployment. 

- For deployment of Microsoft managed environments via LCS, follow the instructions at [Lifecycle Services (LCS) for Finance and Operations apps customers](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-works-lcs.md#new-deployment-experience)  

- **For Cloud hosted environment**, see [Deploy and access development environments](../../../fin-ops-core/dev-itpro/dev-tools/access-instances.md). You must also complete the Resource Manager onboarding process for your connectors, see [Complete the Azure Resource Manager onboarding process for US government Lifecycle Services projects](arm-onbarding-us-goverment.md).

> [!NOTE]
> For US government Microsoft Dynamics Lifecycle Services (LCS) projects, only Azure US government–specific Azure subscriptions are supported.
  
## Features not available

The following features listed will not be available for general availability of the Dynamics 365 Services in GCC. For information about feature availability, see [Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).

-   **Azure DevOps Services** will be unavailable in **Government cloud**. However, use of Azure DevOps on-premises or public Azure DevOps services will be available.


## Frequently asked questions

## Is Dynamics 365 Finance and Dynamics 365 Supply Chain Management supported in GCC-High ?
No, Dynamics 365 Finance and Dynamics 365 Supply Chain Management is only supported in GCC

## Can I use public Azure DevOps with Finance and Supply Chain in GCC?
Yes, you can use public Azure DevOps services if you don't have requirements for a FEDRAMP certified solution or you can use Azure DevOps Server.


## Can I deploy a Cloud Hosted Environment Tier-1 development box on an Azure commercial subscription ?
No, in Lifecycle Services (LCS) for the US Government Community Cloud [Dynamics Lifecycle Services GCC](https://gov.lcs.microsoftdynamics.us), you must use an Azure Government subscription to deploy a cloud hosted environment.

## What can I do if I need a package from the shared asset library that is not available in Lifecycle Services (LCS) for the US Government Community Cloud?
You can download the same package from the public [Dynamics Lifecycle Services](https://lcs.dynamics.com) shared asset library or your partner can help you download the package.

## Is Code upgrade tool available In GCC?
No. Not at this time, however you can create a prospect project in public [Dynamics Lifecycle Services](https://lcs.dynamics.com) and use the code upgrade tool. Please note that you will not be able to deploy environments in prospect projects. 

## Can my partner open a support ticket on my behalf?
Yes, but be aware that if your partner uses a non GCC identity the support ticket will be directed to the public support queue. We do recommend opening support tickets using customer GCC entitlement in LCS.


## See also

- 	[Dynamics 365 US Government](/power-platform/admin/microsoft-dynamics-365-government)
- 	[Business Applications US Government Feature Availability](https://aka.ms/BAPFunctionalParity).
- 	[Lifecycle Services (LCS) User guide](../../../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md)  
-  [Cloud deployment overview](../../../fin-ops-core/dev-itpro/deployment/cloud-deployment-overview.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
