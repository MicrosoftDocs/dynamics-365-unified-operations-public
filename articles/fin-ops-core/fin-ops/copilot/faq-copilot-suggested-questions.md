---
title: Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)
description: This FAQ provides answers to frequently asked questions about the AI technology that's used to generate follow-up questions in the Copilot sidecar in finance and operations apps. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 10/29/2024
ms.collection:
  - bap-ai-copilot
ms.custom:
  - responsible-ai-faqs
ms.topic: article
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
---

# Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This FAQ provides answers to frequently asked questions about the *Follow-up questions in the Copilot sidecar* AI feature. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## What is Follow-up questions in the Copilot sidecar?

*Follow-up questions in the Copilot sidecar* is an AI technology that's used in the [Copilot side car experience](copilot-for-finance-operations.md), which provides conversational Copilot experiences in finance and operations apps.

*Follow-up questions in the Copilot sidecar* generates and displays up to three questions that you can choose from to ask Copilot to keep the conversation going. Each question is generated based on the existing conversation so far and represents something that Copilot thinks you're likely to want to ask next.

The feature is powered by [Dynamics 365 Copilot](/power-platform/transparency-note-copilot-data-security-privacy) and helps guide you to additional information in the context of the current conversation.

## What can Follow-up questions in the Copilot sidecar do?

The *Follow-up questions in the Copilot sidecar* feature makes it fast and easy to post follow-up questions and get answers from Copilot. It's designed to provide a diversity of follow-up questions, and avoids repeating questions you have already asked. The suggested questions are answered using [Generative Answers](/microsoft-copilot-studio/faqs-generative-answers), which is the foundation for the [Generative help and guidance with Copilot](copilot-generative-help.md) feature in finance and operation apps.

## What is the intended use of Follow-up questions in the Copilot sidecar?

The *Follow-up questions in the Copilot sidecar* feature is intended to save you time compared to typing your next question so you can get answers sooner from Copilot.

## How was Follow-up questions in the Copilot sidecar evaluated? What metrics are used to measure performance?

We evaluated the system by testing a variety of starting questions and conversations with copilot to see what questions it suggests. We evaluated whether the suggested questions resulted in answers that were useful through manual labeling. Additionally, we tested the system to make sure it doesn't produce any harmful content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report/). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of Follow-up questions in the Copilot sidecar? How can users minimize the impact of its limitations when they use it?

*Follow-up questions in the Copilot sidecar* only generates questions based on the current conversation, so it can't consider other contexts when making recommendations. You can always ignore the suggestions and type your own prompt to Copilot if needed.

## See also

- [Generative help and guidance with Copilot](copilot-generative-help.md)
- [Enable generative help and guidance with Copilot](../../dev-itpro/copilot/enable-copilot-generative-help.md)
- [Add knowledge to generative help and guidance with Copilot](../../dev-itpro/copilot/extend-copilot-generative-help.md)
- [Responsible AI FAQ for Generative help and guidance with Copilot in finance and operations apps](faq-copilot-generative-help.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
