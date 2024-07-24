---
title: Generative help and guidance
description: This article describes Copilot features in Business performance analytics.
author: Carylhenry
ms.author: carylhenry
ms.topic: article
ms.date: 07/22/2024
ms.collection: bap-ai-copilot

ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Generative help and guidance

Generative help and guidance is a Microsoft Copilot feature in Business performance analytics. It provides a conversational interface where users can ask Copilot questions about the app. Generative help and guidance is intended to help new users learn how to use the app. It's also intended to help experienced users learn about new app features.

## Access

Generative help and guidance is currently available in the United States in the English language.

If the Copilot icon isn't visible in the upper-right corner of Business performance analytics, an administrator should check the following settings:

1. Confirm that consent was given to the terms of use for copilots and generative AI features in the Power Platform admin center. For more information, see [Turn on copilots and generative AI features](/power-platform/admin/geographical-availability-copilot#turn-on-copilots-and-generative-ai-features-1).

    If only the **Move data across regions** checkbox is selected, not the **Bing search** checkbox, the Copilot sidecar might be visible in Business performance analytics. However, Copilot can't respond to most prompts that a user asks.

1. Confirm that the **Allow users to analyze data using an AI-powered chat experience in canvas and model-driven apps** field is set to either **Default** or **On** for your environment in the Power Platform admin center. For more information, see [Enable Copilot for model-driven apps in your environment](/power-apps/maker/model-driven-apps/add-ai-copilot#enable-copilot-for-model-driven-apps-feature-for-your-environment).
1. Confirm that the **Copilot control** field is set to either **Default** or **On** for the Business performance app in the Maker portal. For more information, see [Disable Copilot for a model-driven app](/power-apps/maker/model-driven-apps/add-ai-copilot#disable-copilot-for-a-model-driven-app).

## Use

After generative help and guidance is turned on as described in the previous section, users can ask questions via the Copilot sidecar in Business performance analytics.

- Users can ask questions in several ways:

    - They can select a prompt from the initial message in the chat.
    - They can select a prompt from the prompt guide near the text box at the bottom of the sidecar.
    - They can enter their own text prompt in the text box at the bottom of the sidecar.

- To form a response, Copilot looks at Business performance analytics documentation, including this article, on Microsoft Learn.
- Prompts that are unrelated to Business performance analytics, or that have severe errors in spelling and grammar, don't receive an answer. Instead, they receive a default, fallback response.
- For each response, users can use the thumbs-up and thumbs-down icons to provide feedback about whether the response is good or bad.
