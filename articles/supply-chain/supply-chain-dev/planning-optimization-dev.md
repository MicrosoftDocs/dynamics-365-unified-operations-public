---
# required metadata

title: Unified developer experience for planning optimization (preview)
description: This article provides information about the development experience for planning optimization. 
author: bahbal
ms.date: 01/02/2024
ms.topic: article
ms.prod: 
ms.technology: 

---

[!include [banner](../includes/banner.md)]

[This article is pre-release documentation and is subject to change.]

Recently, the unified developer experience is introduced by Power Platform that you can use the same tools and environments for writing and debugging your extensions for Planning optimization. 
For more information, please visit: [Unified developer experience for finance and operations apps](https://learn.microsoft.com/en-us/power-platform/developer/unified-experience/finance-operations-dev-overview).

> [!Important]
> This is a preview feature.
> Preview features aren't meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

## Scenario

Planning optimization provides extensibility scenarios when master planning is completed. These extensibilities can be implemented by developer and also can be tested with Planning optimization service connected unified development environments.
The most common extensibility scenario for Planning optimization is to apply custom processing after the plan has been updated. Power Platform brings the ability to author solutions quickly and seamlessly using low-code development and being sure their extensibilities will react correctly with real-time results of Planning optimization.

## Step-by-step provision a new environment
1. Please follow up the tutorial for creating environments can be used for development [Provision a new environment with an ERP-based template](https://learn.microsoft.com/en-us/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC)
1.1. Note that the template ID should be **D365_FinOps_SCM** for Planning optimization. 
2. After completed the steps in [Step-by-step provisioning guide](https://learn.microsoft.com/en-us/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC#step-by-step-provisioning-guide), the environment will be prepared in Power platform admin center.
3. In order to check Planning optimization add-in, go to "Dynamics 365 Apps" on Environment's page and check whether "Planning optimization add-in for D365 SCM" is installed or not.
4. Connect to Finance and Operations environment (Finance and Operations URL can be found on Environment page in PPAC) and check Planning optimization parameters that service is connected or not. 
4.1. See [Turn on Planning Optimization for your environment](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/get-started#turn-on-planning-optimization-for-your-environment).
5. After Planning optimization is connected to the environment, please follow up [Unified developer experience for finance and operations apps](https://learn.microsoft.com/en-us/power-platform/developer/unified-experience/finance-operations-dev-overview)

## Related resources
- [Unified developer experience for finance and operations apps](https://learn.microsoft.com/en-us/power-platform/developer/unified-experience/finance-operations-dev-overview)
- [Unified admin experience for finance and operations apps](https://learn.microsoft.com/en-us/power-platform/admin/unified-experience/finance-operations-apps-overview)
- [Install and configure development tools](https://learn.microsoft.com/en-us/power-platform/developer/unified-experience/finance-operations-install-config-tools)
- [Provision a new environment with an ERP-based template](https://learn.microsoft.com/en-us/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC)
- [Write, deploy, and debug X++ code](https://learn.microsoft.com/en-us/power-platform/developer/unified-experience/finance-operations-debug)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
