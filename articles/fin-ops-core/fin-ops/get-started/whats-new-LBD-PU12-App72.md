---
title: What's new or changed in on-premises deployments of Dynamics 365 Finance and Operations, Enterprise edition 7.2 with platform update 12 (March 2018)
description: This article describes features that are either new or changed in on-premises deployments of Microsoft Dynamics 365 Finance and Operations, Enterprise edition 7.2 with platform update 12. This deployment option became available in March 2018.
author: sericks007
ms.date: 03/14/2018
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2017-11-30
ms.dyn365.ops.version: Platform update 12
ms.custom: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# What's new or changed in on-premises deployments of Dynamics 365 Finance and Operations, Enterprise edition 7.2 with platform update 12 (March 2018)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in on-premises deployments of Microsoft Dynamics 365 Finance and Operations, Enterprise edition 7.2 with platform update 12. This deployment option became available in March 2018.

For more information about platform update 12, see [What's new or changed in Dynamics 365 Finance and Operations, Enterprise edition platform update 12 (November 2017)](whats-new-platform-update-12.md).

For more resources about on-premises deployments, see [On-premises deployment home page](../../dev-itpro/deployment/on-premises-deployment-landing-page.md).

## Setup and deployment

Improvements have been made to the setup and deployment process. These improvements significantly reduce the time that is required for deployment. Increased automation and multiple prerequisite validations have also been added to improve reliability. For more information, see [Set up and deploy on-premises environments](../../dev-itpro/deployment/setup-deploy-on-premises-latest.md).

## Servicing

After your on-premises environment is deployed, you can now use Microsoft Dynamics Lifecycle Services (LCS) to apply platform and application updates that Microsoft releases. You can also apply code customizations. Therefore, customers can stay current with the latest set of fixes and take up new customizations without having to reconfigure an existing environment or redeploy the on-premises environment. Additionally, you can now roll back code changes if packages aren't successfully applied. For more information, see [Apply updates to on-premises deployments](../../dev-itpro/deployment/apply-updates-on-premises.md).

Note that the [Reconfigure environments to take a new platform or topology](../../dev-itpro/lifecycle-services/reconfigure-environment.md) will remain available for environments that were deployed with platform update versions that are earlier than Platform update 12.

## Hotfixes

Hotfixes that you can download from LCS provide additional features for your on-premises deployments of Platform update 12. Be sure to apply the following hotfixes:

- **[KB 4091763 - Admin toggles for Client connectivity and Skype presence](https://fix.lcs.dynamics.com/Issue/Details?kb=4091763&bugId=3934773&qc=fd949f8a204ceeedaa0a586ca8a1bfdbd6535b35225da98506d688e093d086f6):** This hotfix enables administrators to disable experiences that depend on internet connectivity on client machines. For more information, see [Client internet connectivity](../../dev-itpro/user-interface/client-disconnected.md).
- **[KB 4093454 - ISV license support for on-premises](https://fix.lcs.dynamics.com/Issue/Details?kb=4093454&bugId=3936799&qc=766427475435463a174e287b531401ab8cc8f1aeedf12bf2c2d4f8d1a1774592):** When deploying an on-premises environment starting from platform update 12, the tenant GUID is automatically populated from LCS to the on-prem environment. Licensing validation can read this value and successfully validate the licenses. For more information, see [Independent software vendor (ISV) licensing (on-premises)](../../dev-itpro/dev-tools/isv-licensing-on-prem.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

