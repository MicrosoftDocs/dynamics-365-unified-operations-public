---
title: Responsible AI FAQ
description: Understand how Microsoft has minimized the potential harms related to AI features within Business performance analytics 
author: Carylhenry
ms.author: carylhenry
ms.topic: article 
ms.date: 07/22/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
---

# Generative help and guidance FAQ

## What is generative help and guidance?
Generative help and guidance is a feature within Business performance analytics providing users with a chat interface to ask Copilot questions about the app.

## What can generative help and guidance do? 
Generative help and guidance scans Business performance analytics’ documentation to search for an answer to the user’s prompt. If an answer is found, it summarizes the documentation and provide a link to the documentation pages that were used to generate the response. Otherwise, Copilot encourages the user to try changing their question.

## Who are generative help and guidance’s intended uses?
This feature is intended to help new users of Business performance analytics onboard the app and to help veteran users learn how to use newly released features.

## How was generative help and guidance? evaluated? What metrics are used to measure performance?
Security, legal, and responsible AI professionals reviewed the purpose, user interaction, and implementation of generative help and guidance and have approved of its release. Additionally, it was rigorously tested beforehand to ensure that responses were clear and accurate when prompts were clear, well-formed, and relevant to Business performance analytics. 

## What are the limitations of generative help and guidance? How can users minimize the impact of generative help and guidance? What are the limitations when using the system?
Because generative help and guidance only search this documentation to form a response, prompts that are unrelated to Business performance analytics this or prompts that aren't covered by this documentation can’t be answered by this feature. Additionally, this Copilot feature was validated for the [English language](https://go.microsoft.com/fwlink/?linkid=2270154). While it can be used in other languages, it may not function as intended. Language quality may vary based on the user’s interaction or system settings, which may impact accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of generative help and guidance?
- Users should have clear guidelines on the types of queries suitable for generative help and guidance and understand the importance of critical assessment of the AI-generated guidance. Not only does this documentation contain those guidelines, but the interface of the feature itself contains them. 
- Users are made aware that generative help and guidance can only answer questions about Business performance analytics in two ways. The default message that appears when the Copilot sidecar is opened informs the user that this documentation is being used to source answers. That message is also reinforced in the fallback response when Copilot can’t find an answer to the user’s prompt.
- Users should also apply skepticism to AI-generated content since there is always a chance for it to be inaccurate. Every response contains an **AI-generated content** label and links to sources that were used to form the response.
- This feature relies on Azure Open AI’s abuse monitoring service. To opt out of this, see [Data, privacy, and security for Azure OpenAI Service](/legal/cognitive-services/openai/data-privacy#how-can-customers-get-an-exemption-from-abuse-monitoring-and-human-review).
