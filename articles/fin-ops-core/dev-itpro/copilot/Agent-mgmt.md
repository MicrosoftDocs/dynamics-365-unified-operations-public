---
title: Set up Agent management (preview)
description: Learn about how to set up Agent management.
author: jaredha
ms.author: jaredha
ms.topic: overview
ms.date: 11/25/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

# Overview 

The Agent management feature in Dynamics 365 Finance and Operations enables autonomous agents to perform predefined tasks within your business ecosystem. Here, users can discover, configure, and manage AI-powered
agents that can automate routine operational tasks. 

## Prerequisites 

Before using Agent Management, a Power Platform Admin Center (PPAC) administrator must ensure the following prerequisites are met: 

The environment must have a Dataverse instance linked. 

The environment must have the "Copilot for Finance and Operations apps" solution (logical name: msdyn_fnocopilot) installed. Minimum accepted version is 1.0.03006.1. 

The Copilot feature flag must be turned on in PPAC. Navigate to PPAC, then “Environments”, then select your environment, click the “Settings” page. On this page, select “Product” and click “Features”. Find 
the “Copilot” feature flag and ensure it is turned on.  

Billing must be enabled. In PPAC, head to “Billing”, then “Licenses”, select “Copilot Studio” and create a new billing plan if necessary. Then, assign credits to the relevant environment. Find more details here. 

A Dynamics 365 Finance and Operations administrator must ensure the following additional prerequisites are met: 
 - The "Immersive Home" feature must be enabled in the “Feature Management” workspace in your Dynamics 365 Finance and Operations environment.
 - The "Agent Management" feature must be activated in the Feature Management workspace
 - Each user who needs to view agent activity or configure agents must be assigned the Dataverse security role "Finance and Operations Agent Configuration Manager". To assign this role: 

Go to the Power Platform Admin Center (PPAC) 
Select "Users" 
Select the user and click the three dots (ellipsis) menu 
Choose "Manage Security Roles" 
Assign the "Finance and Operations Agent Configuration Manager" role 

Without this security role, users will not have proper access to agent configuration or agent activity pages, even if other prerequisites are met. 

### Navigation options 

Users can access Agent-related pages through: 

 - Immersive Home  
     - The Immersive home is the primary navigation hub for discovering and managing agents. It provides direct access to:
     - Agent Activity page using the “View Activity” button on the top right of the Immersive Home.
     - Agents page with Manage and Library tabs using the “View Agents” button on the top right of the Immersive Home. 

 - Search Bar  
Quick access by searching for:  
"Agents" 
"Agent Activity" 

### Configuring Agents 

Agent discovery and activation 

Users can discover and activate new agents through: 
 - Library tab
     - Browse available agent templates
     - Preview agent capabilities
     - Select and configure new agents for deployment 
 - Manage Tab 
     - View currently active agents
     - Edit existing agent configurations
     - Activate or deactivate individual agent tasks 

>[!Note]
> Admins can turn off relevant agent features using feature management for an org-wide control that affects all users, effectively turning off autonomous agents across the entire organization. 

### Set up an agent the first time  

When setting up an agent for the first time, users are automatically guided through a configuration wizard. This wizard helps you set agent parameters and define task-specific preferences. 

### Agent activity tracking 

Activity Monitoring 

The Agent Activity page provides a comprehensive log of actions performed by autonomous agents: 
 - Displays agent interactions and task completions
 - This data is stored in the Dataverse entity “Copilot for Finance and Operations Agent Activity” with logical name msdyn_erpagentactivity
 - Retains activity history for up to 90 days by default. After 90 days, a Dataverse system job deletes these records 

Customizing Activity Retention 

Administrators can modify the activity history retention period by adjusting the Dataverse system job titled "Delete Copilot for Finance and Operations Agent Activity records older than 90 days". Environment
administrators can see all system jobs by using the Power Platform Environment Settings app. 

Note: The system job is created once any records exist in your environment within the msdyn_erpagentactivity Dataverse entity. meaning the system job is not created until there is data to clean up. 

### Important considerations 

Limitations in current preview 
 - Extensibility of the feature is not currently supported
 - No direct UI-based administrative override for individual user actions
 - Admins can use batch jobs to cancel agent actions for individual users 

### Using batch jobs to cancel agent actions  

While the current UI provides limited administrative oversight, system administrators can delete batch jobs to monitor agent activities for all users and cancel individual agent actions run on behalf of a user.  
 - Navigate to “Batch Jobs”
 - Search by “Job Description” to search by the Agent name or the “Created By” section to search by individual usernames.
 - Admins can choose to delete batch jobs associated with an Agent or user to cancel Agent actions 

### Support and feedback 

As this is a preview release, we welcome your feedback to improve the Agent Management feature. Report any issues or suggestions through the standard Dynamics 365 support channels. You may also be prompted to 
provide in-product feedback.  

 

 

 

 
