---
title: Responsible AI FAQ for generative help and guidance
description: Learn how Microsoft has minimized the potential harm related to AI features in Business performance analytics.
author: Carylhenry
ms.author: carylhenry
ms.topic: article 
ms.date: 07/22/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.collection: bap-ai-copilot
---

# Responsible AI FAQ for generative help and guidance

## What is generative help and guidance?

Generative help and guidance is a feature in Business performance analytics. It provides a chat interface where users can ask Microsoft Copilot questions about the app.

## What can generative help and guidance do?

Generative help and guidance scans Business performance analytics documentation to search for an answer to a user's prompt. If an answer is found, generative help and guidance summarizes the documentation. It also provides links to the documentation pages that were used to generate the response. If no answer is found, Copilot encourages the user to try to change their question.

## What are generative help and guidance's intended uses?

This feature is intended to help new users of Business performance analytics learn how to use the app. It's also intended to help experienced users learn how to use newly released features.

## How was generative help and guidance evaluated? What metrics are used to measure performance?

Security, legal, and responsible AI professionals reviewed the purpose, user interaction, and implementation of generative help and guidance, and have approved of its release. Additionally, the feature was rigorously tested before the release to ensure that responses were clear and accurate when prompts were clear, well-formed, and relevant to Business performance analytics.

## What are the limitations of generative help and guidance? How can users minimize the impact of the feature? What are the limitations when the system is used?

Because generative help and guidance searches only Business performance analytics documentation to form a response, it can't answer prompts that are unrelated to Business performance analytics or that aren't covered by that documentation.

Additionally, this Copilot feature was validated only for the [English language](https://go.microsoft.com/fwlink/?linkid=2270154). Although it can be used in other languages, it might not work as intended. The user's interactions or system settings might affect language quality. Language quality, in turn, might affect accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of generative help and guidance?

- Users should have clear guidelines about the types of queries that are suitable for generative help and guidance. They should also understand the importance of critical assessment of the AI-generated guidance. Both this documentation and the interface of the feature provide those guidelines.
- Two mechanisms are in place to help users understand that generative help and guidance can answer questions only about Business performance analytics. When users open the Copilot sidecar, the default message that appears informs them that Business performance analytics documentation is used as the source for answers. If Copilot can't find an answer to the user's prompt, the fallback response reinforces that message.
- Users should always be skeptical of AI-generated content, because there's always a chance that it's inaccurate. Every response contains an **AI-generated content** label and links to sources that were used to form the response.
- This feature relies on Azure OpenAI Service's abuse monitoring service. To opt out of this service, see [How can customers get an exemption from abuse monitoring and human review?](/legal/cognitive-services/openai/data-privacy#how-can-customers-get-an-exemption-from-abuse-monitoring-and-human-review)
