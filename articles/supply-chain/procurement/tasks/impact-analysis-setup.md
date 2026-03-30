# Set up, configure, and test impact analysis #

[This article is prerelease documentation and is subject to change.]

This article explains how system administrators can set up and configure the Procurement Agent impact analysis to automatically and manually analyze the downstream impact of purchase order changes.

## Prerequisites ## 
Before you can use impact analysis, your system must meet the following requirements:
- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later, with all available quality updates.
- The following features must be turned on in feature management. Select Check for updates if the features aren't shown on your system.
 - Immersive Home
 - Agent management
 - (Production-ready preview) Impact analysis

Enabling the (Production-ready preview) Impact analysis will allow manual simulations without additional configuration.

Tip
If you can't enable the Agent management features, make sure that all of the prerequisites are fulfilled, such as version requirements and Copilot Studio billing enablement.

In the Power Platform admin center, make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
- First, install Copilot for finance and operations apps version 1.0.3048.2 or later. If it's already installed, update it to the latest version.
- Then, install Copilot in Microsoft Dynamics 365 Supply Chain Management version 1.1.03071.1 or later. If it's already installed, update it to the latest version.

## Set up sources that automatically trigger impact analysis ##

If impact analysis is to be used on incoming emails or the Vendor Collaboration Module, then these must be enabled first. 

See [Procurement Agent - Supplier communications](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/supplier-com-agent-overview) and [Vendor Collaboration Module ](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/vendor-collaboration-work-external-vendors).

To enable the impact analysis to run based on change requests coming through one or both sources, follow these steps:
1.	Sign in to the Microsoft Dynamics 365 Supply Chain Management environment as a user who has permissions to manage the agent configuration.
2.	Go to Agents > Agents (Preview).
3.	On the Library tab, for (Production-ready preview) Impact analysis - Procurement Agent, select Select.
4.	Select Source to enable vendor emails if using supplier communications and/or the Vendor Collaboration Module. 
5.	Select Activate.

## Test Impact Analysis ##

Learn how to test impact analysis in Microsoft Dynamics 365 Supply Chain Management.

Impact analysis can either run automatically based on configured sources or be initated manually as part of the simulation capability. We recommend testing out impact analysis using the simulation feature. This can be done as soon as the (Production-ready preview) Impact analysis feature has been enabled in feature management. See <Simulate if purchase order changes have impact>.
