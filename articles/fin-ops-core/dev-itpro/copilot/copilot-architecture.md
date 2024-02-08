---
title: Copilot architecture
description: This article describes the architecture of Copilot for finance and operations.
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: conceptual
ms.date: 02/08/2024
audience: Developer
ms.search.region: Global
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---

# Architecture of Copilot in finance and operations

[!include [banner](../includes/banner.md)]

Copilot in finance and operations apps builds on [Microsoft Copilot Studio](/microsoft-copilot-studio/fundamentals-what-is-copilot-studio), which provides the central AI orchestration of the Copilot capabilities. This framework enables you to extend the capabilities, creating powerful AI-powered experiences in finance and operations apps. 

<img alt="Create an action using a flow to get the course description" src="../media/Copilot-architecture.png">

## Copilot interface
The Copilot interface for the chat experience in finance and operations apps uses the same [AI Copilot](/power-apps/maker/canvas-apps/ai-overview) control that is used in [canvas apps](/power-apps/maker/canvas-apps/add-ai-copilot) and [model-driven apps](/power-apps/maker/model-driven-apps/add-ai-copilot), including other Dynamics 365 applications. The control is embedded in the finance and operations client, hosted in the **SysCopilotChatPanel** form. It manages the communication between the finance and operations client and Microsoft Copilot Studio, and acts as the executor for client actions.

## Orchestration with Microsoft Copilot Studio
[Microsoft Copilot Studio](/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) provides the central AI orchestration of the capabilities in finance and operations apps. When a prompt is entered in the Copilot chat panel, it's sent to Copilot Studio, which then determines the intent of the prompt and which topics or plugins should be invoked to provide a response. Copilot Studio executes plugins, gets the required data, and provides an output in natural language that is returned back to the user in the Copilot interface. For more information about the architecture and execution of plugins in Copilot Studio, see [Microsoft Copilot Studio plugin architecture](/microsoft-copilot-studio/copilot-plugins-architecture).

Copilot in finance and operations apps is bound to a single chatbot in Copilot Studio, called **Copilot in Finance and Operation**. The chatbot is deployed as part of the Copilot in the finance and operations (msdyn_FnoCopilot) solution. For guidance on installing the solution and chatbot in your environment, see [Step 4: Install the Copilot application in your finance and operations apps environment](enable-copilot.md#step-4-install-the-copilot-application-in-your-finance-and-operations-apps-environment).

## Plugins
Capabilities are added to Copilot in finance and operations apps by adding plugins to the Copilot in finance and operations chatbot. A **plugin** is a reusable piece of code that can perform a specific task or provide specific functionality for Copilot. The plugin provides the definition of the capability, including the data to retrieve, queries to execute, workflows to run, external systems to connect to, or any other instructions needed to construct the response to the prompt that invokes the plugin. 

Conceptually, a plugin is something Copilot knows how to do. For example, if you want Copilot to be able to get customer balances, you create a plugin that describes the capability, and knows which API to call to get the information to be returned to the user.

When designing your Copilot experiences, consider the types of questions or actions that the application user would expect to ask/prompt Copilot to answer or perform. Plugins themselves shouldn't be thought of as an end-to-end scenario. A plugin should be thought of as an individual skill that the user can prompt in Copilot in various scenarios and sequences as part of the natural language conversation. The plugins can be chained together by the Copilot Studio orchestration to create an end-to-end conversational experience, but won't necessarily be the same sequence each time. The conversation of chained-together plugins becomes the end-to-end business scenario.

### Plugin context
When developing your plugins for Copilot in finance and operations apps, consider the user context in which the plugin will be executed. Some plugins enable prompts that can be applicable in multiple user interfaces, while others are ideal for use cases only within the context of a flow in finance and operations apps.

**Headless plugins:** Headless plugins are ideal for scenarios where there isn't a specific user interface for the scenario. If the plugin is querying general information that is applicable in any UI, then it should be engineered as a headless plugin. For example, you might want to check a customer balance or on-hand inventory from data in finance and operations apps while in a Teams conversation. This information doesn't necessarily require application context to understand and receive value from the data. In these cases, using a headless plugin enables making the plugin available to any user interface connected to the [Power Platform plugin registry](/microsoft-copilot-studio/copilot-plugins-architecture#business-applications-and-power-platform-plugin-registry).

If a headless plugin is the right approach for your business scenario, you can create your plugin in Copilot Studio as a Copilot plugin that connects data across multiple sources, and allows the plugin to be used across any Copilot interface connected to the Power Platform plugin registry, such as [Copilot for Microsoft 365](https://www.microsoft.com/microsoft-365/copilot-for-work) and Copilot in finance and operations apps. For more information, see [Create and configure copilot plugins](/microsoft-copilot-studio/copilot-plugins-overview).

**Client plugins:** Client plugins are ideal for use cases that are applicable only in the currently connected/running conversation and application context. If it's a skill that only makes sense within the flow of an in-app business process, or requires client action, then you would likely want to develop this as a client plugin. For example, a plugin that uses AI to calculate alternate production plans for a production schedule may make sense when in the application context of the production schedule, but wouldn't be helpful in other interfaces outside finance and operations apps.

> [!NOTE]
> Client plugins involve invoking client code in the finance and operations client. Capabilities for creating client plugins in finance and operations client code are planned for version 10.0.40. Additional guidance on creating client plugins will be available when the release is in public preview.
