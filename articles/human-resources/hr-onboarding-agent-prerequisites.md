---
# required metadata

title: Prerequisites for the Dynamics 365 Human Resources Onboarding agent (preview)
description: This article lists the prerequisites to complete before installing the Onboarding agent in Microsoft Dynamics 365 Human Resources.
author: Pranjal-Sinha
ms.date: 06/22/2026
ms.reviewer: twheeloc
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: pranjalsinha
ms.search.validFrom: 2026-06-15
ms.dyn365.ops.version: Human Resources

---

# Prerequisites for the Dynamics 365 Human Resources Onboarding agent (preview)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Before you install the Dynamics 365 Human Resources Onboarding agent (preview), make sure that the following prerequisites are met.

## Environment

Deploy a new sandbox environment, or upgrade an existing sandbox environment, to Dynamics 365 Human Resources version 10.0.48 or later with the latest quality update. For more information, see [Deploy a new environment](../fin-ops-core/dev-itpro/deployment/deployenvironment-newinfrastructure.md).

## Microsoft Dataverse

The sandbox environment must be linked to a Microsoft Dataverse environment. If it isn't linked yet, follow one of these articles:

- To connect to a new Dataverse environment, see [Connect finance and operations apps with a new Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md).
- To connect to an existing Dataverse environment, see [Connect finance and operations apps with an existing Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md).

## Microsoft Copilot Studio license

You must have a Microsoft Copilot Studio license. For more information, see [Copilot Studio licensing](/microsoft-copilot-studio/requirements-licensing-subscriptions).

## Related information

- [Set up the onboarding agent for HR and new hires](hr-onboarding-agent-setup.md)
