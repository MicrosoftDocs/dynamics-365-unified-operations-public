---
title: Regulatory Configuration Service merge to the Globalization Studio workspace
description: Learn about the Regulatory Configuration Service (RCS) merge to the Globalization Studio workspace, including additional resources.
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Regulatory Configuration Service merge to the Globalization Studio workspace

[!INCLUDE[banner](../../../includes/banner.md)]

[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

In version 10.0.39, the functionality of Regulatory Configuration Service (RCS) is merged to the Microsoft Dynamics 365 Finance **Globalization Studio** workspace.

This merge has the following benefits:

- It simplifies **deployments**, because there's no separate RCS service.
- It simplifies the **user experience (UX)**.
- It simplifies the setup, validation, and deployment of Globalization features.
- It aligns **geo coverage** with Dynamics 365 Finance.
- It's aligned with Dynamics 365 platform capabilities.
- It aligns **Application Lifecycle Management (ALM)** with Microsoft Power Platform (Dataverse).

The ALM part of RCS and Electronic reporting (ER) currently uses the Global repository. After the merge, it will be done via Dataverse solutions. A new type of repository for getting ER configurations in Dynamics 365 Finance is added. This repository is known as the Dataverse configuration repository. The Global repository will be deprecated and ALM functionality will be available via Dataverse solutions. Global repo will be shutdown the next day after the end of service of CY24Q3: 10.0.40 Service update which is planned for February 18, 2025.
If you have any non-obsolete or redundant Electronic Reporting configurations stored in Global repository and not saved in your Dynamics 365 Finance Database, please download them before Global repository shutdown. You can download them using the steps described in the following article: [Import Electronic reporting (ER) configurations from Global Repository of Configuration service](../../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md)

The **E-invoicing service** design experience will use the **Globalization Studio** workspace and will be aligned with the overall RCS merge timeline.

The RCS merge to the Dynamics 365 Finance Tax Calculation service will be seamlessly incorporated into the **Globalization Studio** workspace. Because of this change, installation of the Tax Calculation service add-in is no longer a mandatory step for new environments. In addition, the constraint to have a Tier-2 environment no longer applies.

**Migration of tax calculation features and configurations**

Back-end job processing provides migration of tax calculation features that were created in RCS and that are used in Dynamics 365 Finance legal entities in Tax calculation parameters. The processing is automatically run after the **Enable Globalization feature setup for Tax Calculation Service** feature is enabled in the **Feature management** workspace.

In the **Globalization Studio** workspace, you can use the **Tax calculation** tile in the **Globalization services** section to create and maintain tax features in Dynamics 365 Finance. After the batch job is completed, you can view and update the features that were migrated from RCS and used in legal entities. You can also restore additional feature versions that were migrated from RCS.

Tax calculation configurations will be available through the **Tax configurations** tile that you can access by selecting **Electronic reporting** in the **Globalization studio** workspace.

**User experience**

The UX for the configuration of tax features remains consistent and is unaffected by this release.

**Timeline**

Be aware that Microsoft will enable the Tax Calculation service in all environments. Activities that are related to the discontinuation of the Tax Calculation service as an add-in will be aligned with the timeline that has been set for RCS.

## Additional resources
- [Globalization Studio workspace features](gsw-features.md)
- [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
