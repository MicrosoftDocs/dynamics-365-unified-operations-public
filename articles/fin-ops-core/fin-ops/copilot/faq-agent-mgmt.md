---
title: Responsible AI FAQ for Agent management in finance and operations apps (preview)
description: Get answers to frequently asked questions about the AI technology used in connection with Agent management. This article includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 04/25/2025
ms.update-cycle: 180-days
ms.collection:
  - bap-ai-copilot
ms.custom:
  - responsible-ai-faqs
  - copilot-learning-hub
ms.topic: article
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
---

# Responsible AI FAQ for Agent management in finance and operations apps (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

An AI system includes not only the technology but also the people who use it, the people who are affected by it, and the environment where it's deployed. This responsible AI FAQ is intended to help you understand how the Agent management feature's AI technology works, and how system owners and users can influence system performance and behavior. In addition, it helps you understand the importance of thinking about the whole system, including the technology, the people, and the environment.

## What is Agent management?

Agent management is a preview feature in Microsoft Dynamics 365 finance and operations apps that enables autonomous AI-powered agents. The feature lets users discover, configure, and manage those agents.

> [!NOTE]
> This feature is a preview feature and is subject to change. It should always be tested in a sandbox environment before it's deployed to production.

## How does Agent management use AI?

Agent management uses AI to create autonomous agents. Those agents use AI to perform the following operational tasks:

- Run predefined business processes, based on configured parameters.
- Complete routine tasks that otherwise require manual intervention.

## What are the capabilities of the system?

The Agent management system lets users complete the following tasks:

- Discover and activate new agents on the **Library** tab.
- Preview agent capabilities before activation.
- Configure agent parameters and task-specific preferences through a wizard.
- Monitor agent activity and task completion.
- Activate or deactivate individual agent tasks.
- Track agent interactions on the **Agent activity** page.

## What data does Agent management access and process?

Agents access and process the business data in finance and operations apps that is relevant to their configured tasks. Activity data is stored in the "Copilot for finance and operations agent activity" (msdyn\_erpagentactivity) Dataverse entity. It includes records of the following information:

- Agent interactions
- Task executions and completions
- Operational decisions that agents made
- Configuration changes

By default, activity data is retained for up to 90 days. After 90 days, a Dataverse system job deletes the data.

## What choices do system owners and users have?

System owners, administrators, and users have several options for controlling the Agent management feature:

- **Organization-wide control** – Administrators can enable or disable the entire Agent management feature through the **Feature management** workspace.
- **Agent-specific control** – Users can activate or deactivate specific agents or individual agent tasks.
- **Configuration options** – Users can customize agent preferences during setup.
- **Activity retention** – Administrators can modify the default 90-day retention period for agent activity records by adjusting the Dataverse system job.
- **Batch job management** – Administrators can monitor and cancel agent actions by deleting associated batch jobs.

## How was Agent management evaluated? What metrics are used to track performance?

Microsoft conducted extensive user research and testing during each phase of the feature development. We have a robust set of metrics that we track to measure the performance of Agent Management and the resulting customer experience.

- We continuously monitor the availability of this feature to ensure that it's accessible when it's needed.
- The system periodically collects feedback from users to gauge satisfaction. We actively track this feedback to ensure that the Agent management feature is compliant and appropriate. This feedback loop is essential for continually improving agent performance and reliability.

## How is agent activity tracked and monitored?

Agent activity is comprehensively logged. It can be monitored through the following mechanisms:

- The **Agent activity** page, which shows all agent interactions and task completions
- The "Copilot for finance and operations agent activity" (msdyn\_erpagentactivity) Dataverse entity
- Batch jobs, which administrators can review to monitor agent actions

By default, activity data is retained for 90 days. However, administrators can customize the retention period in Dataverse.

## What are the limitations and considerations?

The current preview version of Agent management has the following limitations:

- Extensibility of the feature isn't supported.
- There is no direct UI-based administrative override for individual user actions.

## How can administrators control Agent management functionality?

Administrators can control and oversee Agent management through the following mechanisms:

- **Feature management** – Turn off the entire Agent management feature organization-wide.
- **Batch job management** – Delete batch jobs to cancel agent actions for individual users.
- **Credit allocation** – Control agent functionality through credit allocation in the Power Platform admin center.
- **Prerequisite management** – Disable required components, such as the Immersive Home or Copilot features, to prevent this feature from working.
