---
title: Agent management (preview)
description: This article describes the Agent management feature in Dynamics 365 finance and operations.
author: jinniew
ms.author: jiwo
ms.topic: conceptual
ms.date: 03/27/2025

ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Agent management (preview)

[!include [preview-banner](../includes/preview-banner.md)]

This article describes the Agent management feature in Dynamics 365 finance and operations.

## Overview 

The Agent management feature in Dynamics 365 Finance and Operations enables autonomous agents to perform predefined tasks within your business ecosystem. Here, users can discover, configure, and manage AI-powered
agents that can automate routine operational tasks. 

### Prerequisites 

Before using Agent management, a Power Platform Admin Center (PPAC) administrator must ensure the following prerequisites are met: 
 - The environment must have a Dataverse instance linked.
 - The environment must have the "Copilot for Finance and Operations apps" solution (logical name: msdyn_fnocopilot) installed. Minimum accepted version is 1.0.03006.1.
 - The Copilot feature flag must be turned on in the Power Platform Admin Center.
   - Go to the Power Platform admin center > **Environments**.
   - Select your environment, click **Settings**.
   - On this page, select **Product**, click **Features**.
   - Confirm **Copilot** feature flag is turned on.  
 - Billing must be enabled. In Power Platform admin center, go to **Billing** > **Licenses**. Select **Copilot Studio** and create a new billing plan if necessary.
Then, assign credits to the relevant environment. Find more details here. 

A Dynamics 365 Finance and Operations administrator must ensure the following additional prerequisites are met: 
 - The **Immersive Home** feature must be enabled in the **Feature management** workspace in your Dynamics 365 finance and operations environment.
 - The **Agent Management** feature must be activated in the **Feature management** workspace. 

### Navigation options 

Users can access Agent-related pages through: 
 - Immersive Home - The Immersive home is the primary navigation hub for discovering and managing agents.

It provides direct access to:  
 - **Agent activity** page using the **View Activity** on the top right of the Immersive Home.
 - **Agents** page with **Manage** and **Library** tabs using **View agents** on the top right of the Immersive Home. 

 - Search bar - provides quick access by searching for:  
**Agents**
**Agent activity**


### Configuring agents 

Users can discover and activate new agents using the 
 - **Library** tab
     - Browse available agent templates
     - Preview agent capabilities
     - Select and configure new agents for deployment 
 - **Manage** tab
    - View currently active agents
    - Edit existing agent configurations
    - Activate or deactivate individual agent tasks 

>[!Note]
> Administrators can turn off relevant agent features using feature management that affects all users, effectively turning off autonomous agents across the entire organization. 

### Set up agents the first time  

When setting up an agent for the first time, users are automatically guided through a configuration wizard. This wizard helps you set agent parameters and define task-specific preferences. 

### Track agent activity 

The **Agent activity** page provides a comprehensive log of actions performed by autonomous agents: 
 - Displays agent interactions and task completions.
 - This data is stored in the **Copilot for Finance and Operations Agent Activity** Dataverse entity with logical name msdyn_erpagentactivity.
 - Retains activity history for up to 90 days by default. After 90 days, a Dataverse system job deletes these records. 

### Customizing activity retention 

Administrators can modify the activity history retention period by adjusting the **Delete Copilot for finance and operations Agent activity records older than 90 days** Dataverse system job. Environment administrators can see all system jobs by using the Power Platform environment settings app. 

>[Note]
> The system job is created after any records exist in your environment in the msdyn_erpagentactivity Dataverse entity. The system job isn't created until there is data to clean up. 

#### Additional considerations 
 - Billing and credits
     - Your organization is billed for each deployed agent.
     - If your organization exhausts its allocated credits, agents may be temporarily deactivated.
     - Contact your organization's administrator to renew credits and restore agent functionality. 

 - Limitations in current preview 
    - Extensibility of the feature isn't supported
    - No direct UI-based administrative override for individual user actions
    - Administrators can use batch jobs to cancel agent actions for individual users
      
#### Using batch jobs to cancel agent actions  
The current UI provides limited administrative oversight, system administrators can use batch jobs to monitor agent activities for all users and cancel individual agent actions run on behalf of a user.  
To cancel agents actions using a batch, follow these steps:
1. Go to **Batch jobs**.
2. Search by **Job description** to search by the Agent name or the **Created by** section to search by individual usernames.
3. Administrators can choose to delete batch jobs associated with an Agent or user to cancel Agent actions. 

#### Support and feedback 
As this is a preview release, we welcome your feedback to improve the **Agent management** feature. Report any issues or suggestions through the standard Dynamics 365 support channels. You may also be prompted to provide in-product feedback.  

 
