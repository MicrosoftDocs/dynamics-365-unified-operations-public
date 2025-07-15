---
title: Generative help and guidance in Business performance planning 
description: Learn about Copilot features in Business performance planning.
author: twheeloc
ms.author: romainpham
ms.topic: article
ms.date: 04/23/2025
ms.update-cycle: 180-days
ms.collection: bap-ai-copilot

ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Generative help and guidance in Business performance planning

Generative help and guidance is a Microsoft Copilot feature in Business performance planning. It provides a conversational interface where users can ask Copilot questions about the app. This feature is designed to help new users learn how to navigate the app. In addition, it helps experienced users stay up to date about new features.

The assistance that Copilot provides is based on the public documentation for Business performance planning that is available on Microsoft Learn. This documentation includes comprehensive details about the app, Business performance planning in general, Power BI visuals, the Excel add-in, and more. It's important to note the Copilot knowledge base is limited to the official public documentation on Microsoft Learn. It can't search the entire internet.

## Access generative help and guidance

Generative help and guidance is currently available in the United States in the English language.

If the Copilot icon isn't visible in the upper-right corner of Business performance planning, an administrator should review the following settings:

1. In the Power Platform admin center, confirm that consent was given to the terms of use for agents and generative AI features. Learn more in [Turn on data movement, Bing search, and Microsoft 365 services for Copilots and generative AI features](/power-platform/admin/geographical-availability-copilot#turn-on-data-movement-bing-search-and-microsoft-365-services-for-copilots-and-generative-ai-features).
1. In the Power Platform admin center, confirm that the **Move data across regions** checkbox is selected in addition to the **Bing search** checkbox.

    > [!NOTE]
    > If the **Move data across regions** checkbox is selected, but the **Bing search** checkbox is cleared, the Copilot sidecar might be visible in Business performance planning. However, Copilot can't respond to most prompts that a user enters.

1. In the Power Platform admin center, confirm that the **Allow users to analyze data using an AI-powered chat experience in canvas and model-driven apps** field is set to either **Default** or **On** for your environment. Learn more in [Enable Copilot for model-driven apps in your environment](/power-apps/maker/model-driven-apps/add-ai-copilot#enable-copilot-for-model-driven-apps-feature-for-your-environment).
1. In the Power Apps maker portal, confirm that the **Copilot control** field is set to either **Default** or **On** for the Business performance app. Learn more in [Disable Copilot chat for a model-driven app](/power-apps/maker/model-driven-apps/add-ai-copilot#disable-copilot-chat-for-a-model-driven-app).

## Use generative help and guidance

After generative help and guidance is turned on as described in the previous section, users can ask questions via the Copilot sidecar in Business performance planning.

- Users can ask questions in several ways:

    - Select a prompt from the initial message in the chat.
    - Select a prompt from the prompt guide near the text box at the bottom of the sidecar.
    - Enter a text prompt in the text box at the bottom of the sidecar.

- To form a response, Copilot looks at Business performance planning documentation, including this article, on Microsoft Learn.
- Prompts that are unrelated to Business performance planning, or that have severe errors in spelling and grammar, don't receive an answer. Instead, they receive a default, fallback response.
- For each response, users can use the thumbs-up and thumbs-down buttons to provide feedback about whether the response is good or bad.
