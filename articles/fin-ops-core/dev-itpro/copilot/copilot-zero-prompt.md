---
title: Customize the Copilot zero prompt experience
description: Learn how to customize the zero prompt experience for Copilot for finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 10/07/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Customize the zero prompt experience (preview)

[!include [banner](../includes/banner.md)]

The zero prompt experience helps makers enhance user engagement and streamline interactions by presenting the user with customized prompt options to select at the start of the Copilot chat session. By presenting a zero prompt experience adaptive card at the beginning of the chat session, the user receives relevant information and options without the need for additional prompts and iterations. The zero prompt experience can be context aware, shown selectively for targeted pages.

The zero prompts are a set of prompts that, when selected will either be submitted automatically as a prompt to the agent, or populate the chat box with the prompt enabling the user to send the prompt to the agent without manually typing the prompt.

> [!IMPORTANT]
> This is a preview feature. Preview features aren't meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2216214), and are available before an official release so customers can get early access and provide feedback.

## Configuring the zero prompt experience
You can configure your custom zero prompt experience in three steps:
1. Create a new topic in the **Copilot for finance and operations apps** agent.
2. Update the trigger node to trigger the topic when the Copilot chat panel is opened in the finance and operations apps client.
3. Create an adaptive card with your zero prompts that will be sent to the user on the triggering event.

### Add a new topic
1. In Copilot Studio, open the **Copilot for finance and operations apps** agent.
2. Select the **Topics** tab.
3. Select **Add a topic** > **From blank**.
4. Change the **Name** of the topic from "Untitled" to something that describes the topic, like "Zero prompt experience".

### Update the trigger
When the **Copilot for finance and operations apps** chat experience is opened in the client starting a new session, the control sends the `Microsoft.PowerApps.Copilot.RequestZeroPrompt` event to the agent. This event is used to trigger the zero prompt experience topic.

1. On the **Trigger** node, select **Change trigger** > **A custom client event occurs**.
2. In the **Event name** field, set the value to `Microsoft.PowerApps.Copilot.RequestZeroPrompt`.
3. If you want this zero prompt experience to be triggered only within a specific application context, you can define the condition using context variables. For example, if you want the zero prompt experience to be specific to the Vendors form, then in the **Condition** section:
   - Set the **Select a variable** field to `Global.PA_Copilot_ServerForm_PageContext.metadataName`.
   - Select **is equal to**.
   - Enter or select a value: **VendTable**.
4. Set the **Priority** value. If you have multiple topics that are triggered by the zero prompt event the Priority set for the trigger node determines the order in which they are executed.

> [!NOTE] You can create multiple topics for zero prompt experiences for the various conditions you want to support. See [Use application context with Copilot](./copilot-application-context.md) for more information on available application context variables.
