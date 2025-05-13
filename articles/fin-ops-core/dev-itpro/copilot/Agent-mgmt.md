---
title: Set up Agent management (preview)
description: Learn about how to set up Agent management.
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

# Overview 

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Agent management feature in Dynamics 365 Finance and Operations enables autonomous agents to perform predefined tasks within your business ecosystem. Here, users can discover, configure, and manage AI-powered
agents that can automate routine operational tasks. 

## Prerequisites 

Before using Agent management, a Power Platform admin center administrator must ensure the following prerequisites are met: 
 - The environment must have a Dataverse instance linked.
 - The environment must have the "Copilot for Finance and Operations apps" solution (logical name: msdyn_fnocopilot) installed. Minimum accepted version is 1.0.03006.1.
 - The **Copilot feature** flag must be turned on in Power Platform admin center. Go to Power Platform admin center, select **Environments**. Select your environment, click **Settings**. On this page, select **Product** and click **Features**. Find the **Copilot feature** flag and ensure it is turned on.  

A Dynamics 365 finance and operations administrator must ensure the following additional prerequisites are met: 
In the **Feature Management** workspace in your Dynamics 365 finance and operations environment, enable the following features:
 - **Immersive home** 
 - **Agent management** 
Each user who needs to view agent activity or configure agents must be assigned the Dataverse security role **Finance and operations agent configuration manager**.

To assign this role: 
1. Go to the Power Platform admin center.
2. Select **Users**.
3. Select the user and click the three dots (ellipsis) menu.
4. Choose **Manage security roles**.
5. Assign the **Finance and operations agent configuration manager** role.
Without this security role, users won't have proper access to agent configuration or agent activity pages. 

### Navigation options 
To access agent related page, users can go to: 
- **Immersive home** - the primary navigation hub for discovering and managing agents. It provides access to:
     - **Agent activity** page using **View activity**.
     - **Agents** page with **Manage** and **Library** tabs using **View agents**.
 - Search bar provides quick access by searching for **Agents** or **Agent activity**. 


### Configuring agents 
To discover and activate new agents, follow these steps:
 - Go to the **Library** tab to:
     - Browse available agent templates
     - Preview agent capabilities
     - Select and configure new agents for deployment 
 - To to the **Manage** tab to: 
     - View currently active agents
     - Edit existing agent configurations
     - Activate or deactivate individual agent tasks 

>[!Note]
> Administrators can turn off relevant agent features using feature management for organization wide control that affects all users across the entire organization. 

### Set up an agent the first time  

When setting up an agent for the first time, users are automatically guided through a configuration wizard. This wizard helps you set agent parameters and define task specific preferences. 

### Agent activity tracking 

The **Agent activity** page provides a comprehensive log of actions performed by autonomous agents: 
 - Displays agent interactions and task completions.
 - This data is stored in the Dataverse entity **Copilot for finance and operations agent activity** with logical name msdyn_erpagentactivity.
 - Retains activity history for up to 90 days by default. After 90 days, a Dataverse system job deletes these records. 

### Customizing activity retention 

Administrators can modify the activity history retention period by adjusting the **Delete Copilot for finance and operations agent activity records older than 90 days** Dataverse system job. Environment
administrators can see all system jobs by using the Power Platform environment settings app. 

>[!Note]
> The system job is created after records are created in your environment in the msdyn_erpagentactivity Dataverse entity.  

### Important considerations 

Limitations in current preview 
 - Extensibility of the feature isn't supported
 - No direct UI-based administrative override for individual user actions
 - Administrators can use batch jobs to cancel agent actions for individual users 

### Using batch jobs to cancel agent actions  

To create a batch job to delete agent activities for all users and cancel individual agent actions, follow these steps:   
1. Go to **Batch jobs**
2. In the **Job description**, search by the **Agent name** or the **Created by** section to search by individual usernames.
3. Administrators can choose to delete batch jobs associated with an Agent or user to cancel Agent actions. 

### Support and feedback 

This is a preview release, we welcome your feedback to improve the Agent management feature. Report any issues or suggestions through the standard Dynamics 365 support channels. You may also be prompted to 
provide in-product feedback.  

 

 

 

 
