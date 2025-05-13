---
title: Responsible AI FAQ for Agent management in finance and operations apps (preview)
description: This FAQ provides answers to frequently asked questions about the AI technology that's used in connection to Agent management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 04/25/2025
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

An AI system includes not only the technology, but also the people who use it, the people affected by it, and the environment in which it's deployed. This responsible AI FAQ is intended to help you understand 
how the Agent management feature's AI technology works, the choices system owners and users can make that influence system performance and behavior, and the importance of thinking about the whole system, 
including the technology, the people, and the environment. 

## What is Agent management (Preview)? 

Agent management is a preview feature in Dynamics 365 finance and operations that enables autonomous AI-powered agents. The feature allows users to discover, configure, and manage these agents.  

>[!NOTE]
> This a preview feature, it's subject to change and should always be tested in a sandbox environment before deployment to production. 

## How does Agent management use AI? 

Agent management leverages artificial intelligence to create autonomous agents that can perform operational tasks. These agents use AI to: 
 - Execute predefined business processes based on configured parameters
 - Complete routine tasks that would otherwise require manual intervention 
 
## What are the capabilities of the system? 

The Agent management system allows users to: 
 - Discover and activate new agents using the **Library** tab
 - Preview agent capabilities before activation
 - Configure agent parameters and task-specific preferences through a guided wizard
 - Monitor agent activity and task completions
 - Activate or deactivate individual agent tasks
 - Track agent interactions through the **Agent activity** page 

## What data does Agent management access and process? 

Agents access and process business data within Dynamics 365 finance and operations relevant to their configured tasks. Activity data is stored in the Dataverse entity "Copilot for finance and operations agent 
activity" (msdyn_erpagentactivity) and includes records of: 
 - Agent interactions
 - Task executions and completions
 - Operational decisions made by agents
 - Configuration changes 

This activity data is retained for up to 90 days by default, after which it is deleted by a Dataverse system job. 

## What choices do system owners and users have? 

System owners and administrators have several controls over the Agent management feature: 
 - Organization-wide control: Administrators can enable or disable the entire Agent management feature through the **Feature management** workspace.
 - Agent-specific control: Users can activate or deactivate specific agents or individual agent tasks.
 - Configuration options: Users can customize agent preferences during setup.
 - Activity retention: Administrators can modify the default 90-day retention period for agent activity records by adjusting the Dataverse system job.
 - Batch job management: Administrators can monitor and cancel agent actions by deleting associated batch jobs. 

## How was Agent management evaluated? What metrics are used to track performance?  

We conducted extensive user research and testing during each phase of the feature development. We have a robust set of metrics we track to measure the performance of Agent Management and the resulting customer 
experience: 
 - We continuously monitor the availability of this feature to ensure it is accessible when needed
 - The system periodically collects feedback from users to gauge satisfaction. We actively track this feedback to ensure Agent management feature is compliant and appropriate. This feedback loop is essential for
   continually improving agent performance and reliability. 

## How is agent activity tracked and monitored? 
Agent activity is comprehensively logged and can be monitored through: 
 - The **Agent activity** page, which displays all agent interactions and task completions
 - The Dataverse entity "Copilot for Finance and Operations Agent Activity" (msdyn_erpagentactivity)
 - Batch jobs, which can be reviewed by administrators to monitor agent actions 

Activity data is retained for 90 days by default but can be customized by administrators in Dataverse. 

## What are the limitations and considerations? 
The current preview version of Agent management has several limitations: 
 - Extensibility of the feature isn't currently supported
 - There is no direct UI-based administrative override for individual user actions 

## How can administrators control Agent functionality? 
Administrators have several mechanisms to control and oversee Agent management: 
 - **Feature Management** - Turn off the entire Agent management feature organization-wide
 - Batch job management - Delete batch jobs to cancel agent actions for individual users
 - Credit allocation - Control agent functionality through credit allocation in the Power Platform Admin Center
 - Prerequisites management - Disabling required components like the **Immersive home** or the **Copilot** features prevent this feature from working 

