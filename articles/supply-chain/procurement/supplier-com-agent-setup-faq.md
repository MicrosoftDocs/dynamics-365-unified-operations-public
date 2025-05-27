---
title: FAQ and solving typical issues when setting up and configure the Supplier Communications Agent (production ready preview)
description: Identify and solve typical issues when configure the Supplier Communications Agent in Dynamics 365 Supply Chain Management to streamline vendor communication.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/22/2025
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# FAQ and solving typical issues when setting up and configure the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article helps to system administrators to solve typical issues when configuring the Supplier Communications Agent.

# Trouble shooting the deployment of the Supplier Communications Agent

## Issues and solutions

### Symptom: Missing *Dynamics 365 apps* in the environment details page in [Power Platform admin center](https://aka.ms/ppac)

PPAC environment has been deployed for Finance and Operations but does not show *Dynamics 365 apps* in the environment details page under *Resources*.

**Solution:** Open the *Full details* for your Finance and Operations environment in your [LCS](https://lcs.dynamics.com/V2) project. Under Power Platform Integration see if errors have been reported (such as *"LCS Power Platform Integration provisioning fails with timeout"*) and attempt a retry to complete the deployment.

*Please note:* The Dual-write application is not required for the agent deployment,

### Symptom: In PPAC under Manage / Dynamics 365 Apps it is not possible to install Copilot apps into the environment deployed for Finance and Operations

The Admin navigates to [PPAC](https://aka.ms/ppac)  **Manage** / **Dynamics 365 Apps** and wants to install the applications *Copilot for finance and operations apps* and *Copilot in Microsoft Dynamics 365 Supply Chain Management*, but they cannot find the environment for Finance and Operations in the environment selection.

**Solution:** Open the *Full details* for your Finance and Operations environment in your [LCS](https://lcs.dynamics.com/V2) project. Under Power Platform Integration see if errors have been reported (such as *"LCS Power Platform Integration provisioning fails with timeout"*) and attempt a retry to complete the deployment.

### Symptom: The feature *(Production Ready Preview) Agent Management* in finance and operations cannot not be enabled

When trying to enable feature *(Production Ready Preview) Agent Management* in Feature Management, an error indicates *"You cannot enable this Feature. Environment must be linked to Dataverse for agents to function". And this error appears even though a Dataverse environment has been successfully created in LCS.

**Solution:** Install available feature updates for 10.0.44. After the initial preview release of 10.0.44 changes regarding the Copilot message capacity had been introduced that are required to enable the Agent Management feature.

