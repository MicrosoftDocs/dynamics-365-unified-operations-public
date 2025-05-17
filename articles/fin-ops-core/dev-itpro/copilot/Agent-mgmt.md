---
title: Set up Agent management (preview)
description: Learn how to set up Agent management.
author: jaredha
ms.author: jkhaira
ms.topic: overview
ms.date: 05/13/2025
ms.custom: bap-template
ms.reviewer: twheeloc
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Set up Agent management (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Agent management feature in Microsoft Dynamics 365 finance and operations apps enables autonomous agents to perform predefined tasks in your business ecosystem. Users can discover, configure, and manage AI-powered agents that can automate routine operational tasks.

## Prerequisites

Before you can use Agent management, a Power Platform admin center administrator must ensure that the following prerequisites are met:

- A Dataverse instance must be linked to the environment.
- The **Copilot for Finance and Operations apps** solution (logical name: msdyn_fnocopilot) must be installed in the environment. The minimum accepted version is 1.0.03006.1.
- The **Copilot feature** flag must be turned on in the Power Platform admin center.

    To turn on the feature flag, follow these steps:

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. Select **Environments**, and select your environment.
    1. Select **Settings**.
    1. Select **Product**, and then select **Features**. 
    1. Find the **Copilot feature** flag, and ensure that it's turned on.

In addition, a finance and operations apps administrator must ensure that the following prerequisites are met:

- In your finance and operations apps environment, the following features must be enabled in the **Feature Management** workspace:

    - Immersive home
    - Agent management

- The **Finance and operations agent configuration manager** Dataverse security role must be assigned to each user who has to view agent activity or configure agents. Without this security role, users don't have proper access to agent configuration or agent activity pages.

    To assign the role, follow these steps:

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. Select **Users**, and select the user who must have the role.
    1. Select the ellipsis (**&hellip;**), and then select **Manage security roles** on the menu.
    1. Assign the **Finance and operations agent configuration manager** role.

## Navigation options

Users can access agent-related pages from the following places:

- **Immersive Home** — Immersive Home is the primary navigation hub for discovering and managing agents.

    - To open the **Agent activity** page, select **View activity**.
    - To open the **Agents** page, which has **Manage** and **Library** tabs, select **View agents**.

- **Search bar** — You can quickly access agent-related pages by entering **Agents** or **Agent activity** in the search bar.

## Configure agents

Use the **Agents** page to discover and activate new agents.

- On the **Library** tab, you can complete the following tasks:

    - Browse available agent templates.
    - Preview agent capabilities.
    - Select and configure new agents for deployment.

- On the **Manage** tab, you can complete the following tasks:

    - View agents that are currently active.
    - Edit existing agent configurations.
    - Activate or deactivate individual agent tasks.

> [!NOTE]
> For organization-wide control that affects all users across the whole organization, administrators can turn off relevant agent features by using Feature management.

## Set up an agent for the first time

When users set up an agent for the first time, they are automatically guided through a configuration wizard. This wizard helps set agent parameters and define task-specific preferences.

## Track agent activity

The **Agent activity** page provides a comprehensive log of actions that autonomous agents perform. It shows all agent interactions and task completions.

Agent activity data is stored in the **Copilot for finance and operations agent activity** Dataverse entity (logical name: msdyn_erpagentactivity).

By default, the **Agent activity** page retains activity history for up to 90 days. After 90 days, a Dataverse system job deletes the records.

## Customize activity retention

Administrators can modify the retention period for activity history by adjusting the **Delete Copilot for finance and operations agent activity records older than 90 days** Dataverse system job. Environment administrators can view all system jobs by using the Power Platform environment settings app.

> [!NOTE]
> The Dataverse system job is created after records are created in the msdyn_erpagentactivity Dataverse entity in your environment.

## Important considerations

The current preview has the following limitations:

- Extensibility of the feature isn't supported.
- There is no direct, UI-based administrative override for individual user actions.
- Administrators can use batch jobs to cancel agent actions for individual users.

## Use batch jobs to cancel agent actions

To create a batch job to delete agent activities for all users and cancel individual agent actions, follow these steps.
  
1. Go to **Batch jobs**.
1. Use the **Job description** section to search by agent name or the **Created by** section to search by individual user name.
1. Administrators can cancel agent actions by deleting batch jobs that are associated with an agent or user.

## Support and feedback

This release is a preview release. We welcome your feedback, because it helps us improve the Agent management feature. Report any issues or suggestions through the standard Dynamics 365 support channels. You might also be prompted to provide in-product feedback.
