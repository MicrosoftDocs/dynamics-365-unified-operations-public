---
title: Copilot in Business performance analytics
description: This article describes Copilot features within Business performance analytics
author: Caryl Henry
ms.author: carylhenry
ms.topic: application
ms.date: 07/22/2024

ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Generative help and guidance

Generative help and guidance is a Copilot feature within Business performance analytics that is currently in public preview. This feature uses a conversational interface within Business performance analytics to help new users learn how to use the app for the first time and veteran users learn about new features for the app.

## Access

Generative help and guidance is currently in public preview, and its availability is limited to the United States in English language at this time. If this describes you but the Copilot icon is still not visible in the upper righthand corner of Business performance analytics, an admin should check the following settings to turn generative help and guidance on:
1.	Consent to Generative AI features in the Power Platform admin center according to [Turn on copilots and generative AI features
](https://learn.microsoft.com/en-us/power-platform/admin/geographical-availability-copilot#turn-on-copilots-and-generative-ai-features-1)
    1.	If only the “Move data across regions” setting is checked and not the “Bing Search” setting, the Copilot sidecar may be visible in Business performance analytics but will not be able to respond to most prompts a user asks Copilot. 
3.	Ensure Copilot is set as “Default” or “On” for your environment in the Power Platform admin center according to [Add Copilot for app users in model-driven apps
](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/add-ai-copilot#enable-copilot-for-model-driven-apps-feature-for-your-environment)
4.	Ensure the Copilot control is set as “Default” or “On” for the Business performance app in the Maker portal according to [Add Copilot for app users in model-driven apps
](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/add-ai-copilot#disable-copilot-for-a-model-driven-app)

## Usage
Once an admin has turned on generative help and guidance using the steps detailed above, generative help and guidance can be asked via the Copilot sidecar in Business performance analytics. Users can select a prompt from initial message in the chat, the Prompt Guide near the textbox at the bottom of the sidecar, or enter their own text prompts. Copilot will then look at Business performance analytics’ documentation on MS Learn, including this page, to form a response. Prompts unrelated to Business performance analytics or those with severe spelling and grammar errors won’t get an answer. Instead, these prompts will receive a default, fallback response instead. If a response is particularly good or bad, users can choose to provide feedback using the thumbs up and down icons located on each response.   
