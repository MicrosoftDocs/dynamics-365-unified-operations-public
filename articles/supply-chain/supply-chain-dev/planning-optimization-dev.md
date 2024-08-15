---
title: Unified developer experience for planning optimization (preview)
description: Access overview of the process for setting up a development environment and testing your extensions for the Planning Optimization Add-in.
author: bahadirbal 
ms.author: bahbal
ms.topic: how-to
ms.date: 01/30/2024
ms.custom: bap-template
ms.reviewer: kamaybac
audience: Developer
ms.search.form:
---

[!include [banner](../includes/banner.md)]

# Unified developer experience for planning optimization (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Microsoft Power Platform provides a unified developer experience that includes tools and environments for writing and debugging extensions for the Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management. This topic provides an overview of the process for setting up a development environment and testing your extensions.

Learn more in [Unified developer experience for finance and operations apps](/power-platform/developer/unified-experience/finance-operations-dev-overview).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Extensibility scenarios

Developers can extend Planning Optimization to add support for scenarios that apply after master planning runs. Developers can test their extensions by connecting the Planning Optimization service to their development environment.

The most common extensibility scenario for Planning Optimization involves the application of custom processing after a plan is updated. Microsoft Power Platform supports low-code development that enables new solutions to be created quickly. At the same time, developers can make sure that their extensions work correctly by using the real-time results that Planning Optimization produces.

## Set up an environment for testing your Planning Optimization extensions

### Provision a new environment

To provision an environment that you can use for Planning Optimization, follow the instructions in [Tutorial: Provision a new environment with an ERP-based template](/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC).

> [!IMPORTANT]
> When you provision the environment, you must set the template ID to *D365\_FinOps\_SCM*.

After you complete the steps in the [Step-by-step provisioning guide](/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC#step-by-step-provisioning-guide), your new environment will be prepared in Power Platform admin center.

### Confirm that the Planning Optimization Add-in is installed

To confirm that you successfully added the Planning Optimization Add-in to your environment, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the navigation pane, select **Environments**, and then open the environment where you installed the add-in.
1. In the **Resources** section, select **Dynamics 365 apps**.
1. In the list, find the row where the **Name** field is set to *Planning optimization add-in for D365 SCM*. Confirm that the **Status** field is set to *Installed*.

### Turn on Planning Optimization for your Supply Chain Management environment

To turn on Planning Optimization for your Supply Chain Management environment, follow these steps.

1. Sign in to your new Supply Chain Management environment. (You can find your Supply Chain Management URL on the environment page in [Power Platform admin center](https://admin.powerplatform.microsoft.com).)
1. Follow the instructions in [Turn on Planning Optimization for your environment](/dynamics365/supply-chain/master-planning/planning-optimization/get-started#turn-on-planning-optimization-for-your-environment).

## Related resources

- [Unified developer experience for finance and operations apps](/power-platform/developer/unified-experience/finance-operations-dev-overview)
- [Unified admin experience for finance and operations apps](/power-platform/admin/unified-experience/finance-operations-apps-overview)
- [Install and configure development tools](/power-platform/developer/unified-experience/finance-operations-install-config-tools)
- [Provision a new environment with an ERP-based template](/power-platform/admin/unified-experience/tutorial-deploy-new-environment-with-erp-template?tabs=PPAC)
- [Write, deploy, and debug X++ code](/power-platform/developer/unified-experience/finance-operations-debug)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
