---
title: FAQ for Copilot AI summarization in Commerce headquarters
description: This article provides answers to frequently asked questions about the Microsoft Copilot AI technology that is used to generate summaries in Dynamics 365 Commerce headquarters.
ms.date: 02/06/2026
ms.update-cycle: 180-days
ms.collection:
  - bap-ai-copilot
ms.topic: faq
author: shajain
ms.author: shajain
ms.reviewer: v-griffinc
ms.custom:
  - responsible-ai-faqs
  - bap-template
---

# FAQ for Copilot AI summarization in Commerce headquarters

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Copilot AI technology that generates summaries in Dynamics 365 Commerce headquarters. It includes key considerations and details about how the AI is used, how Microsoft tested and evaluated it, and any specific limitations.

## What is AI summarization in Commerce headquarters?

AI summarization in Commerce headquarters helps business users make better decisions more efficiently by giving them access to summarized information about data and risks.

## What can AI summarization in Commerce headquarters do?

The feature is powered by Azure OpenAI Service's large language model. It uses the information from posted and unposted statements to generate a summary. This summary includes insights such as the number of affected transactions, the total sales amount of those statements, and risks such as transactions that have returns without receipts, expense transactions, and price overrides. The AI summary is also shown for merchandisers, to provide insights about product misconfigurations.

[!INCLUDE[rai-feedback-mechanism.md](../../includes/rai-feedback-mechanism.md)]

## What is the intended use of AI summarization in Commerce headquarters?

The intended use is for users to have immediate access to a relevant summary of an entity, so that they can make faster, better decisions. 

## How was AI summarization in Commerce headquarters evaluated? What metrics measure performance?

The AI-generated summary feature was manually evaluated by comparing the results against the values in current and associated entities. Further validation was done for scenarios where users are missing privileges to view data (to prevent overexposure) and scenarios where entities are missing data (to prevent incorrect information). All calculations are done by using traditional coding methods, and only preaggregated data is sent to the large language models (LLM) service Copilot application programming interface (CAPI). The calculations were verified against the same data during the testing process. If you encounter inappropriate generated content, you can report it to Microsoft by using the [Report abuse](https://msrc.microsoft.com/report) feedback form. Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if it detects abuse of the functionality.

## What are the limitations of AI summarization in Commerce headquarters? How can users minimize the impact of those limitations when they use the system?

For large documents, the system prefilters only a subset of the most impactful datasets to prevent token size limitation. You should always manually review or supervise the generated content.

## What operational factors and settings allow for effective and responsible use of AI summarization in Commerce headquarters?

When you use the feature, follow these recommendations:

- Confirm that your company has enough control over data permissions to ensure that business data can't be manipulated in an undesirable way to influence AI data processing.
- In the event of large priority problems, turn off the summarization capability from the **Feature management** workspace in headquarters. Granular controls also let you turn off summarization for individual pages, based on business need and relevance.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
