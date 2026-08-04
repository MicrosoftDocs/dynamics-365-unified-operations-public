---
title: Supplier Engagement deployment overview, prerequisites, and licensing (preview)
description: Plan prerequisites and deployment tasks for Supplier Engagement across Power Platform and Supply Chain Management.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Supplier Engagement deployment overview, prerequisites, and licensing (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Supplier Engagement deployment spans both Power Platform and Supply Chain Management. You install the solution in your Power Platform tenant, enable the related functionality in Supply Chain Management, and then finish the setup tasks that connect both experiences. Planning the prerequisites up front helps you avoid setup delays later in the deployment.

## Deployment process overview

Deploying Supplier Engagement includes the following tasks:

- Confirm the prerequisites.
- Install the Supplier Engagement app on Power Platform.
- Install the supplier portal in Power Pages.
- Turn on the Supplier Engagement feature in Supply Chain Management.

Power Platform hosts the model-driven app, supplier portal, cloud flows, and supporting Dataverse components. Supply Chain Management provides the business processes, shared supplier data, and feature configuration that the solution depends on.

## Prerequisites

Before you start deployment, make sure that your environment and service account meet the following requirements:

- **Dataverse readiness** – Confirm that Microsoft Power Platform is up to date and that the latest release updates are applied.
- **Supply Chain Management version** – Run Microsoft Dynamics 365 Supply Chain Management version 10.0.48 build 10.0.2645.52 or later.
- **Dataverse connection** – Connect your Supply Chain Management environment to Dataverse. Learn more in [Microsoft Power Platform integration with finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/power-platform/overview).
- **Finance and operations virtual entity solutions** – In the [Power Apps maker portal](https://make.powerapps.com/), open your environment, go to **Solutions**, open the **Managed** tab, and confirm that the following solutions are installed:
    - *Dynamics 365 Company*
    - *Dynamics Operations Virtual Entity Support*
    - *Microsoft Operations ERP Catalog*
    - *Dynamics 365 ERP Virtual Entities*

    If one or more solutions are missing, install them as described in [Configure Dataverse virtual entities](/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference).

- **Power Platform Dynamics 365 apps** – Run the latest update of the *Finance and Operations Virtual Entity* app from [Power Platform admin center](https://admin.powerplatform.microsoft.com/). The app must be version 2.20.3385.8 or later. Learn more in [Manage Dynamics 365 apps](/power-platform/admin/manage-apps).
- **Dedicated service account** – Set up a dedicated Microsoft Entra ID service account for installation and configuration in both Dataverse and Supply Chain Management. The account must be a standard user account, not an app registration account, and it must have all required licenses. The service account is used for flows, notifications, and background automation. Grant it the following security privileges:
    - **Dataverse** – *System Administrator* role
    - **Supply Chain Management** – *System Administrator* role
    - **Microsoft Entra ID** – *Power Platform administrator* role

## Supplier Engagement licensing

Supplier Engagement is currently a preview feature that is provided for evaluation and testing. The licensing model for Supplier Engagement features in Dynamics 365 Supply Chain Management and the Supplier Engagement app in Dataverse is still under review. The supplier portal offers a 30-day trial period. Additional information regarding the licensing requirements will be published before the solution is made generally available.

## What to do next

After you confirm the prerequisites, install the Supplier Engagement app and supplier portal in Power Platform. When those components are available, configure Power Platform and Supply Chain Management so that onboarding, notifications, synchronization, and workflows can run correctly.

## Related information

- [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md)
- [Onboard using the onboarding guide](deploy-onboarding-guide.md)
- [Configure Supplier Engagement elements in Power Platform](deploy-configure-power-platform.md)
- [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md)
- [Post-deployment validation checklist](deploy-validation-checklist.md)
- [Deployment FAQs](deploy-questions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
