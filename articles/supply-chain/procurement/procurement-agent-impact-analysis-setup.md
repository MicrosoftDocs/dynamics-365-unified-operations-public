---
title: procurement-agent-impact-analysis-setup
description: "Impact analysis setup: Learn how to configure and test Procurement Agent impact analysis in Dynamics 365 to assess purchase order changes automatically and manually."
#customer intent: As a system administrator, I want to set up and configure Procurement Agent impact analysis so that I can automatically and manually analyze the downstream impact of purchase order changes.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: lisascholz
ms.date: 04/01/2026
ms.topic: install-set-up-deploy
---

# Set up, configure, and test impact analysis

[This article is prerelease documentation and is subject to change.]

This article explains how system administrators can set up and configure the Procurement Agent impact analysis to automatically and manually analyze the downstream impact of purchase order changes.

## Prerequisites

In addition to the prerequisites detailed in [Set up the Procurement Agent](procurement-agent-setup.md), to use impact analysis you must turn on the following feature in feature management:

- *(Production-ready preview) Impact analysis*

Enabling this feature will allow manual simulations without additional configuration.

## Set up sources that automatically trigger impact analysis

If impact analysis is to be used on incoming change requests received through emails or the Vendor Collaboration Module, then these must be enabled first.

See [Procurement Agent - Supplier communications](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/procurement-agent-supplier-com-overview) and [Vendor Collaboration Module](https://learn.microsoft.com/en-us/dynamics365/supply-chain/procurement/vendor-collaboration-work-external-vendors).

To enable the impact analysis to run based on change requests coming through one or both sources, follow these steps:

1. Sign in to the Microsoft Dynamics 365 Supply Chain Management environment as a user who has permissions to manage the agent configuration.
2. Go to **Agents** > **Agents**.
3. On the **Library** tab, look for *(Production-ready preview) Impact analysis - Procurement Agent*, select **Select**.
4. Select *Source* to enable *vendor emails* if using supplier communications and/or the *Vendor Collaboration Module*.
5. Select **Activate**.

## Test Impact Analysis

We recommend testing out impact analysis using the simulation feature. This can be done as soon as the *(Production-ready preview) Impact analysis* feature has been enabled in feature management.
See [Simulate if purchase order changes have impact](procurement-agent-impact-analysis-simulation.md).
