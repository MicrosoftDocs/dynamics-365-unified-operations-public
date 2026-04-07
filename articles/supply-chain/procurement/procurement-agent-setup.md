---
title: procurement-agent-setup.md
description: Learn how to set up Procurement Agent in Dynamics 365 Supply Chain Management. Follow prerequisites and enable key features for streamlined procurement.
#customer intent: As a supply chain admin, I want to set up the Procurement Agent so that I can manage supplier communications in Dynamics 365 Supply Chain Management.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: lisascholz
ms.date: 04/01/2026
ms.topic: install-set-up-deploy
---

# Set up the Procurement Agent

## Prerequisites

Before you can use Procurement Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later, with all available quality updates.
- The following features must be turned on in feature management. Select Check for updates if the features aren't shown on your system.
 - [*Agent management*](../../fin-ops-core/fin-ops/copilot/agent-mgmt.md)

> [!TIP]
> Optional information to help a user be more successful
If you can't enable the Agent management features, make sure that all of the prerequisites are fulfilled, such as version requirements and Copilot Studio billing enablement.

The feature [*Immersive Home*](../../fin-ops-core/fin-ops/copilot/immersive-home.md) is not mandatory for the Procurement Agent capabilities to work, but it is highly recommended to enable.

In the Power Platform admin center, make sure you're running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:

- First, install Copilot for finance and operations apps version 1.0.3048.2 or later. If it's already installed, update it to the latest version.
- Then, install Copilot in Microsoft Dynamics 365 Supply Chain Management version 1.1.03071.1 or later. If it's already installed, update it to the latest version.

## Enable supplier communications and impact analysis features

The following features in feature management are part of the Procurement Agent:
    - *Procurement Agent - Supplier communications*
    - *(Production-ready preview) Procurement Agent - Impact analysis*

They can be used together or in isolation. This means that you can use supplier communications without the automatic analysis of downstream impact, and you can use impact analysis on sources other and emails through supplier communications.

For more information on setting up supplier communications, refer to: [Set up and configure supplier communications](procurement-agent-supplier-com-setup.md)

For more information on setting up impact analysis, refer to: [Set up, configure and test impact analysis](procurement-agent-impact-analysis-setup.md)