---
title: Enable agent management (production ready preview)
description: This article describes the Agent management feature in Microsoft Dynamics 365 finance and operations apps.
author: twheeloc
ms.author: jkhaira
ms.topic: concept-article
ms.date: 03/09/2026
ms.update-cycle: 180-days
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.collection: 
 - bap-ai-copilot
---

# Enable agent management (production ready preview)

[!include [preview-banner](../includes/preview-banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes the agent management feature in Microsoft Dynamics 365 finance and operations apps.

By using the agent management feature in finance and operations apps, you can use autonomous, AI-powered agents to perform predefined tasks in your business ecosystem. Users can discover, configure, and manage agents that automate routine operational tasks.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

## Prerequisites

Before a finance and operations apps administrator can activate the *(Production ready preview) Agent management* feature in the **Feature management** workspace, the administrator must meet the following prerequisites:

- Enable the [*Immersive Home*](../copilot/immersive-home.md) feature in the **Feature management** workspace in your finance and operations environment.

A Power Platform admin center administrator must ensure that the following prerequisites are met:

- Your finance and operations apps must run version 10.0.44 (10.0.2263.30) or later. Install pending updates in Lifecycle Services (LCS).

- You must link a Dataverse environment to your finance and operations apps environment. To verify, open [LCS](https://lcs.dynamics.com/v2), select your project, and open the **Full details** for your finance and operations apps environment. In the **Power Platform Integration** section, look for your Power Platform Environment information. If no environment information is shown, follow the instructions provided to deploy an associated Dataverse environment.

- You must install the **Copilot for Finance and Operations apps** solution (logical name: msdyn\_fnocopilot) in the environment. The minimum accepted version is 1.0.03021.3.
- You must turn on the **Copilot** feature flag in the Power Platform admin center.

    1. In the Power Platform admin center, go to **Environments**.
    1. Select your environment, and then select **Settings**.
    1. Select **Product**, and then select **Features**.
    1. Confirm that the **Copilot** feature flag is turned on.

- You must enable billing.

  1. In the Power Platform admin center, go to **Billing** > **Licenses**.
  1. Select **Copilot Studio**.
  1. Create a new billing plan as necessary.
  1. Assign credits to the relevant environment. To learn more, see [AI Builder licensing and credit management](/ai-builder/credit-management).

After all of the other prerequisites are in place, a finance and operations apps administrator must enable the *(Production ready preview) Agent management* feature in the **Feature management** workspace.

## Navigation options

You can access agent-related pages from the following places:

- **Immersive Home** – The Immersive Home is the primary navigation hub for discovering and managing agents. Use **View Activity** in the upper right of the Immersive Home to go directly to the following agent-related pages:

  - **Agents** – This page includes **Manage** and **Library** tabs.
  - **Agent activity**

- **Search bar** – Quickly access the agent-related pages by entering the following search terms:

  - **Agents**
  - **Agent activity**

## Discover and activate agents

Use the following tabs on the **Agent** page to discover and activate new agents:

- **Library**

  - Browse available agent templates.
  - Preview agent capabilities.
  - Select and configure new agents for deployment.

- **Manage**

  - View agents that are currently active.
  - Edit existing agent configurations.
  - Activate or deactivate individual agent tasks.

> [!NOTE]
> Administrators can turn off relevant agent features through Feature management. This action affects all users. Therefore, it effectively turns off autonomous agents across the entire organization.

## Activate an agent for the first time

When you activate an agent for the first time, you see a configuration wizard. This wizard helps you set agent parameters and define task-specific preferences.

## Track agent activity

The **Agent activity** page provides a comprehensive log of actions that autonomous agents perform.

- The page shows agent interactions and task completions.
- The data is stored in the **Copilot for Finance and Operations Agent Activity** Dataverse entity (logical name: msdyn\_erpagentactivity).
- By default, activity history is retained for up to 90 days. However, administrators can modify the retention period, as described in the next section. After the retention period expires, a Dataverse system job deletes the records.

## Customize activity retention

Administrators can modify the retention period for activity history by adjusting the **Delete Copilot for finance and operations Agent activity records older than 90 days** Dataverse system job. Environment administrators can view all system jobs by using the Power Platform environment settings app.

> [!NOTE]
> The system job is created after records exist in the msdyn\_erpagentactivity Dataverse entity in your environment. In other words, the system job isn't created until there's data to clean up.

## Additional considerations

- **Billing and credits**

  - Your organization is billed for each deployed agent.
  - If your organization exhausts its allocated credits, agents might be temporarily deactivated.
  - Contact your organization's administrator to renew credits and restore agent functionality.

- **Limitations in the current preview**

  - The feature doesn't support extensibility.
  - There's no direct UI-based administrative override for individual user actions.
  - As described in the next section, administrators can use batch jobs to cancel agent actions for individual users.

## Use batch jobs to cancel agent actions

The current UI provides limited administrative oversight. System administrators can use batch jobs to monitor agent activities for all users and cancel individual agent actions that run on behalf of a user.

If you're an administrator, follow these steps to cancel agent actions.

1. Go to **Batch jobs**.
1. Use the **Job description** section to search by agent name or the **Created by** section to search by individual user name.
1. To cancel agent actions, delete batch jobs that are associated with the agent or user that you found in the previous step.

## Support and feedback

Because this release is a preview release, provide your feedback so the product team can improve the agent management feature. Report any issues or suggestions through the standard Dynamics 365 support channels. You might also be prompted to provide in-product feedback.
