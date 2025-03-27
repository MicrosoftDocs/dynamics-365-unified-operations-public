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

Agent Discovery and Activation 

Users can discover and activate new agents through: 

Library Tab 

Browse available agent templates 

Preview agent capabilities 

Select and configure new agents for deployment 

Manage Tab 

View currently active agents 

Edit existing agent configurations 

Activate or deactivate individual agent tasks 

Note: Admins can turn off relevant agent features using feature management for an org-wide control that affects all users, effectively turning off autonomous agents across the entire organization. 

First-Time Agent Setup 

When setting up an agent for the first time, users will be automatically guided through a configuration wizard. This wizard helps you set agent parameters and define task-specific preferences. 

Agent Activity Tracking 

Activity Monitoring 

The Agent Activity page provides a comprehensive log of actions performed by autonomous agents: 

Displays agent interactions and task completions 

This data is stored in the Dataverse entity “Copilot for Finance and Operations Agent Activity” with logical name msdyn_erpagentactivity 

Retains activity history for up to 90 days by default. After 90 days, a Dataverse system job deletes these records 

Customizing Activity Retention 

Administrators can modify the activity history retention period by adjusting the Dataverse system job titled "Delete Copilot for Finance and Operations Agent Activity records older than 90 days". Environment administrators can see all system jobs by using the Power Platform Environment Settings app. 

Note: The system job is created once any records exist in your environment within the msdyn_erpagentactivity Dataverse entity. meaning the system job is not created until there is data to clean up. 

Important Considerations 

Billing and Credits 

Your organization is billed for each deployed agent 

If your organization exhausts its allocated credits, agents may be temporarily deactivated 

Contact your organization's administrator to renew credits and restore agent functionality 

Limitations in Current Preview 

Extensibility of the feature is not currently supported 

No direct UI-based administrative override for individual user actions 

Admins can use batch jobs to cancel agent actions for individual users 

Using Batch Jobs to Cancel Agent Actions  

While the current UI provides limited administrative oversight, system administrators can delete batch jobs to monitor agent activities for all users and cancel individual agent actions run on behalf of a user.  

Navigate to “Batch Jobs” 

Search by “Job Description” to search by the Agent name or the “Created By” section to search by individual usernames. 

Admins can choose to delete batch jobs associated with an Agent or user to cancel Agent actions 

Support and Feedback 

As this is a preview release, we welcome your feedback to improve the Agent Management feature. Please report any issues or suggestions through the standard Dynamics 365 support channels. You may also be prompted to provide in-product feedback.  

 
