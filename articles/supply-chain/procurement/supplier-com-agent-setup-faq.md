---
title: FAQ and solving typical issues when setting up and configure the Supplier Communications Agent (production ready preview)
description: Identify and solve typical issues when configuring the Supplier Communications Agent in Dynamics 365 Supply Chain Management to streamline vendor communication.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/28/2025
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# Solve common problems when setting up the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article helps system administrators to solve typical issues when configuring the Supplier Communications Agent.

## The *Dynamics 365 apps* link isn't shown for my environment in the Power Platform admin center

### Symptoms

In the [Power Platform admin center](https://aka.ms/ppac), the environment is deployed for finance and operations apps, but it doesn't show **Dynamics 365 apps** under **Resources** on the environment details page.

### Solution

Open your project in [Lifecycle Services (LCS)](https://lcs.dynamics.com/V2) and then open the **Full details** for your finance and operations apps environment. Under **Power Platform Integration**, check whether any errors are reported (such as "LCS Power Platform Integration provisioning fails with timeout"). Then attempt a retry to complete the deployment.

> [!NOTE]
> Dual write isn't required for agent deployment.

## It isn't possible to install the Copilot apps on my environment in the Power Platform admin center

### Symptoms

In the [Power Platform admin center](https://aka.ms/ppac), you go to **Manage** \> **Dynamics 365 Apps** and try to install the applications *Copilot for finance and operations apps* and *Copilot in Microsoft Dynamics 365 Supply Chain Management*, but your finance and operations apps environment isn't shown in the **Select an environment** drop-down list in the install dialog.

### Solution

Open your project in [Lifecycle Services (LCS)](https://lcs.dynamics.com/V2) and then open the **Full details** for your finance and operations apps environment. Under **Power Platform Integration**, check whether any errors are reported (such as "LCS Power Platform Integration provisioning fails with timeout"). Then attempt a retry to complete the deployment.

## I can't enable the *(Production ready preview) Agent management* feature in feature management

### Symptoms

In the **Feature management** workspace for your finance and operations apps environment, when you try to enable the *(Production Ready Preview) Agent Management* feature, you receive the following error message:

> You cannot enable this Feature. Environment must be linked to Dataverse for agents to function

The error appears even though a Dataverse environment was successfully created in LCS.

### Solution

If you're running version 10.0.44 of finance and operations apps, then install the latest quality update for that version. This is required because the initial preview release of version 10.0.44 didn't include important changes to the Copilot message capacity, and these changes are required to enable the agent management feature.

## The Supplier Communications Agent shows error "Exception has been thrown by target of invocation"

### Symptoms

When you're configuring the Supplier Communications Agent, and specifying the conditions in which the agent should operate, the following error is shown when you press the **Activate** button:

> Exception has been thrown by target of invocation

### Solution 1

It could be that, when you installed or updated the *Copilot for finance and operations app* Dynamics 365 app in the Power Platform admin center, the included cloud flows weren't turned on automatically. To resolve the issue, open your [Power App maker environment](https://make.powerapps.com/), select the Dataverse environment associated with your finance and operations app, and select **Solutions**. Under **Managed**, find *Copilot for finance and operations apps*, open the ellipsis (**...**) menu and select **Edit**. Select the object category **Cloud flows** and make sure that each of the two cloud flows is turned on.

### Solution 2

Make sure that the mailbox email address is always identified using lower case only.

1. In [Power Platform admin center](https://aka.ms/PPAC), open your environment details and then select **Settings** from the top navigation bar.
1. Expand the **Email** heading and select **Mailboxes**. Identify the mailbox that you configured in Dataverse for the Supplier Communication Agent and open the details. In the field **Email Address**, make sure that the email is written in lower case.
1. Back on the **Settings** page, expand the **Business** heading and select **Queues**. Identify the queue you created for your team and open it. In the field **Incoming Email**, make sure that the email is written in lower caps.
