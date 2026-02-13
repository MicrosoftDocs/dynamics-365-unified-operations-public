---
title: Immersive Home overview (production ready preview)
description: Learn about Immersive Home, how it helps you work hand-in-hand with AI agents and stay focused on your most important work items.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.topic: overview
ms.date: 05/28/2025
ms.update-cycle: 180-days
audience: Application User
ms.search.region: Global
ms.search.form: ImmersiveHome, DefaultDashboard, SysUserSetup, AppCopilotAgentActivity, AppCopilotAgentLifecycle
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---

# Immersive Home overview (production ready preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes Immersive Home, how it helps you work hand in hand with AI agents and focus on the most important work items assigned to you.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

Immersive Home is a modern, AI-first landing page that adapts to your most important work, aids decision making, and reduces the need to navigate elsewhere to complete common tasks. It's a modern option for the [initial page](../get-started/set-users-initial-page.md) in finance and operations apps and links to tools for enabling, monitoring, teaching, and interacting with AI agents.

:::image type="content" source="media/immersive-home.png" alt-text="Screenshot of the Immersive Home experience." lightbox="media/immersive-home.png":::

## Prerequisites

### System requirements

To use Immersive Home, your system must meet the following requirements:

- You must be running version 10.0.44 or later of your Microsoft finance and operations apps.
- The feature that is named *(production ready preview) Immersive Home* must be turned on in [feature management](../get-started/feature-management/feature-management-overview.md).

### Required user privileges

Each user that requires access to Immersive Home must be assigned the *View immersive home* privilege, which is typically assigned through the duty with the same name. By default, this duty is assigned to the *System User* security role.

## The components of Immersive Home

Immersive Home consists of a new library of controls for adaptive experiences in Microsoft business applications following the Fluent design patterns. Adaptive experiences aim not only to modernize user experiences but also to bring dynamic approaches that move away from static forms toward experiences that bring relevant work directly to your attention.

Immersive Home features a greeting and work summary, suggestions related to AI agents, and a central focus on work items. It also includes agent activity overviews and a ranked view of spaces, including the classic workspaces in finance and operations apps.

## Greeting and summary

The greeting at the top of the page welcomes you by name and provides a concise summary of relevant work items and suggestions for what to address. This provides a quick overview of the immediate tasks at hand.  

## Suggestions area

The suggestion area presents relevant callouts, such as to suggest that you enroll an agent skill into service for a specific task or provide additional instructions to make an agent's service in a task more beneficial.

Each suggestion typically provides an action that guides you to follow the suggestion and take the necessary steps.

## The work items area

The **Work items** area hosts a list of priority-ranked activity cards. Each card reflects a step that is part of an action plan to complete a task. Multiple similar work items can be collapsed into one activity card, allowing you to move the action plan forward for multiple tasks of the same kind. Examples include expense approvals, catalog requests that need approval, cash forward requests awaiting approval, and other workflow-generated work items.

Other examples include activities from agent-generated action plans, such as when an agent prepares a reminder email for a vendor (asking them to confirm purchase orders) that you need to review it before sending. The **Work items** area might also announce that an agent identified a vendor email that references a purchase order, and prepares a resulting confirmation or change request ready for your review.

In most cases, the activity card allows you to complete an action without navigating away from Immersive Home. To achieve this, action cards show relevant information that allows you to take action, which you can expand as needed. Alternatively, you can navigate to the activity-specific experience for more complex tasks.  

If you have activities that you need to work on for some time and track until completion, you can add them to the **Pinned items** list.

Once you complete an activity, it disappears from Immersive Home.

Activity cards show:

- The type of activity as the title
- A description summary with relevant information
- Action buttons to complete the activity
- A navigation link to the activity-related task or workspace

> [!NOTE]
> Activity cards include a feedback mechanism. You can use it to share feedback about your experience using Immersive Home directly with Microsoft (provided an administrator enables user feedback for Copilot and related experiences). 
>
> Learn more about how the Microsoft in-product feedback system works in [Learn about Microsoft feedback for your organization](/microsoft-365/admin/misc/feedback-user-control).
>
> Learn more about how to enable user feedback for Copilot and related experiences in finance and operations apps in [Enable enhanced user feedback for Copilot and related experiences](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot-feedback).
  
## The agent activity area

The **Agent activity** area is only shown when AI agents are enabled in your environment. For each activated agent, this area shows a section where the agent presents its key activity metrics. This could be the number of cases processed, number of emails sent, or metrics such as estimated time saved.

Typically, agents provide a dedicated task space where you can go into more detail on what the agent has been doing, work hand in hand with the agent, and configure or teach the agent. The chevron at the top right of each agent activity card navigates to the specific agent task space.

At the bottom of the **Agent activity** area, you can navigate to agent lifecycle management-related views. The **View activity** button opens a holistic tracing list of all agent activities. The **View agents** button opens a repository of all currently running agents and the library of all agents available for activation.

## The workspaces area

The **Workspaces** area shows a list of ranked tiles for each workspace. The ranking considers how recently you last used a workspace. Favorite workspaces rank at the top.  

Workspace tiles highlight information that you pin to the dashboard. To pin information to the dashboard, open the relevant workspace, right-click on a tile in the workspace, select **Personalize: &lt;tile name&gt;** and then select the **Pin to dashboard** checkbox (clear this checkbox to remove the information from your Immersive Home).

## Related information

[Responsible AI FAQ for Immersive Home in finance and operations apps (production ready preview)](faq-immersive-home.md)
