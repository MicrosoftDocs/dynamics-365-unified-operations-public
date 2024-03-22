---
title: Responsible AI FAQ for suggested questions provided with Copilot
description: This FAQ provides answers to frequently asked questions about the AI technology that's used to suggest next best question in Copilot. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 11/09/2023
ms.collection:
  - bap-ai-copilot
ms.custom:
  - responsible-ai-faqs
ms.topic: article
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
---

# Responsible AI FAQ for Suggested Actions within Copilot

[!include [banner](../includes/banner.md)]
[This article is prerelease documentation and is subject to change.]

This FAQ provides answers to frequently asked questions about the AI technology that's used in *conversational Copilot experiences in finance and operations apps*. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is Suggested Questions?

*Suggested Questions* will give you up to three questions you can ask Copilot once you have started a conversation. The questions are based on the conversation and the answers the system returns.

It appears in [Dynamics 365 Copilot](/power-platform/transparency-note-copilot-data-security-privacy) to offer the user additional information in the context of the current conversation.

## What can Suggested Questions do?

*Suggested Questions* will enable you to quickly ask follow-up questions to get answers from Copilot. It’s designed to provide a diversity of follow-up questions, and to avoid repeating questions you have already asked. The questions are intended to be answered using [Generative Answers](/microsoft-copilot-studio/faqs-generative-answers).

## What is the intended use of Suggested Questions in Copilot?

*Suggested Questions* are intended to be used to save you time compared to typing your next question and help you get answers sooner from Copilot. 

## How was Suggested Questions in Copilot evaluated? What metrics are used to measure performance?

We evaluated the system by testing a variety of starting questions and conversations with copilot to see what questions it suggests. We evaluated if the suggested questions resulted in answers that were useful through manual labeling. Additionally, we tested the system to make sure it does not produce any harmful content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report/abuse?ThreatType=URL&IncidentType=Responsible%20AI&SourceUrl=https://dynamics.microsoft.com/supply-chain-management/overview/). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of Suggested Questions in Copilot? How can users minimize the impact of its limitations when they use it?

*Suggested Questions* will only be based on the conversation, so it is not able to consider other context when making recommendations. You can always ignore the suggestions and type your own prompt to Copilot.

## See also

- [Overview of Copilot capabilities in finance and operations apps](copilot-for-finance-operations.md)
- [Enable Copilot capabilities in finance and operations apps](../../dev-itpro/copilot/enable-copilot.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]