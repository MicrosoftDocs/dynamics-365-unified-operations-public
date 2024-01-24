---
title: Regulatory Configuration Service merge to Globalization Studio workspace (preview)
description: This article explains the Regulatory Configuration Service merge to Globalization Studio workspace (preview)
author: filatovm
ms.author: filatovm
ms.topic: conceptual 
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Regulatory Configuration Service merge to Globalization Studio workspace (preview)

[!INCLUDE[banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

The functionality of Regulatory Configuration Service (RCS) is merged to Dynamics 365 Finance Globalization Studio Workspace in 10.0.39.

This merge:

- Simplifies **deployments** (no separate RCS service).
- Simplifies **UX**.
- Simplifies globalization feature setup, validation and deployment.
- Aligns **geo coverage** with Dynamics 365 Finance.
- Aligns with Dynamics 365 Platform capabilities.
- Aligns **Application Lifecycle Management (ALM)** with Power Platform (Dataverse).

Regulatory Configuration Service will be deprecated. All new RCS provisioning is stopped as of 10.0.39 GA. If provisioning is required, please register a support ticket. We will be providing tools and required support for migration from RCS to Globalization Studio workspace. We plan to fully shutdown RCS by Aug 1, 2024.

Application Lifecycle management (ALM) part of RCS and Electronic Reporting (ER), currently leveraging Global repository, will be done via Dataverse solutions. A new type of repository for getting ER configurations in Dynamics 365 Finance is added and is calle the Dataverse configuration repository. With this, Global repository will be deprecated.

The **E-invoicing service** design experience will use Globalization Studio workspace and will align with overall RCS merge timeline.

The RCS merge into Dynamics 365 Finance, Tax calculation Service (TCS) will also be seamlessly incorporated into the ** Globalization Studio** workspace. With this change, installing the TCS add-in is no longer a mandatory step for new environments. In addition, the constraint to have a Teir-2 environment will not apply any longer.

**Migration of Tax Calculation Features and Configurations**: Migration of tax calculation features that were created in RCS and are in-use in Dynamics 365 Finance legal entities in Tax calculation parameters will be provided via a backend job processing. The process will be run automatically once the "Enable Globalization feature setup for Tax Calculation Service" feature in the Feature management workspace is enabled. In the new workspace for Globalization studio, under the Globalization services, the Tax calculation tile will be available to create and maintain tax features in Dynamics 365 Finance. Once the batch job is completed, you will be able to see and update your features migrated from RCS and used in legal entities. Also, you will be able to restore additional feature versions migrated from RCS. Tax calculation configurations will be available in the Globalization studio workspace \> Electronic reporting, under the Tax configurations tile.

**User Experience (UI)**: It's important to note that the user experience (UI) for configuring tax features remains consistent and unaffected by this release.

**Timeline**: Please be aware that we will be enabling TCS in all environments. The activities related to discontinuation of TCS as an add-in will align with the timeline set for RCS.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
