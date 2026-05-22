---
title: Regulatory Configuration Service merge to the Globalization Studio workspace
description: Learn about the Regulatory Configuration Service (RCS) merge to the Globalization Studio workspace, including additional resources.
author: filatovm
ms.author: filatovm
ms.topic: overview
ms.date: 03/19/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Regulatory Configuration Service merge to the Globalization Studio workspace

[!INCLUDE[banner](../../../includes/banner.md)]

[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

Starting with version 10.0.39, Microsoft Dynamics 365 Finance merges the functionality of Regulatory Configuration Service (RCS) into the **Globalization Studio** workspace.

This merge provides the following benefits:

- It simplifies **deployments** because there's no separate RCS service.
- It simplifies the **user experience (UX)**.
- It simplifies the setup, validation, and deployment of Globalization features.
- It aligns **geo coverage** with Dynamics 365 Finance.
- It's aligned with Dynamics 365 platform capabilities.
- It aligns **Application Lifecycle Management (ALM)** with Microsoft Power Platform (Dataverse).

The ALM part of RCS and Electronic reporting (ER) currently uses the Global repository. After the merge, it uses Dataverse solutions. A new type of repository for getting ER configurations in Dynamics 365 Finance is added. This repository is known as the Dataverse configuration repository. The Global repository will be deprecated, and ALM functionality will be available through Dataverse solutions. The Global repository shuts down the day after the end of service of CY24Q3: 10.0.40 Service update, which is planned for February 18, 2025.
If you have any nonobsolete or redundant Electronic Reporting configurations stored in the Global repository and not saved in your Dynamics 365 Finance database, download them before the Global repository shutdown. You can download them by using the steps described in the following article: [Import Electronic reporting (ER) configurations from Global Repository of Configuration service](../../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

The **E-invoicing service** design experience uses the **Globalization Studio** workspace and aligns with the overall RCS merge timeline.

The RCS merge to the Dynamics 365 Finance Tax Calculation service seamlessly incorporates into the **Globalization Studio** workspace. Because of this change, installation of the Tax Calculation service add-in is no longer a mandatory step for new environments. In addition, the constraint to have a Tier-2 environment no longer applies.

**Migration of tax calculation features and configurations**

Back-end job processing provides migration of tax calculation features that you created in RCS and that are used in Dynamics 365 Finance legal entities in Tax calculation parameters. The processing automatically runs after you enable the **Enable Globalization feature setup for Tax Calculation Service** feature in the **Feature management** workspace.

In the **Globalization Studio** workspace, use the **Tax calculation** tile in the **Globalization services** section to create and maintain tax features in Dynamics 365 Finance. After the batch job finishes, you can view and update the features that RCS migrated and used in legal entities. You can also restore additional feature versions that RCS migrated.

You can access tax calculation configurations through the **Tax configurations** tile by selecting **Electronic reporting** in the **Globalization studio** workspace.

**User experience**

The UX for the configuration of tax features remains consistent and is unaffected by this release.

**Timeline**

Microsoft enables the Tax Calculation service in all environments. Activities that are related to the discontinuation of the Tax Calculation service as an add-in align with the timeline that RCS set.

## Additional resources

[Globalization Studio workspace features](gsw-features.md)

[Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
