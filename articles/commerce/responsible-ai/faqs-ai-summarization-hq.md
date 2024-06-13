---
title: FAQ for Copilot AI summarization in Commerce headquarters
description: This article provides answers to frequently asked questions about the Copilot AI technology used for generating summaries in Microsoft Dynamics 365 Commerce headquarters.
ms.date: 06/13/2024
ms.collection:
  - bap-ai-copilot
ms.custom:
  - responsible-ai-faqs
  - bap-template
ms.topic: faq
author: shajain
ms.author: shajain
ms.reviewer: v-chrgriffin
---

# FAQ for Copilot AI summarization in Commerce headquarters

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Copilot AI technology used for generating summaries in Microsoft Dynamics 365 Commerce headquarters. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is AI summarization in Commerce headquarters?

AI summarization in Commerce headquarters helps business users make better decisions more efficiently by giving them access to summarized information about data and risks.

## What can AI summarization in Commerce headquarters do?

The feature is powered by Azure Open AI's large language model. It uses the information from posted and unposted statements to generate a summary that includes insights such as the count of transactions affected, the total sales amount of these statements, and risks such as transactions with returns without receipts, expense transactions, and price overrides. The AI summary is also displayed for merchandisers, providing insights about product misconfigurations. Copilot uses the *gpt-3.5-turbo* generative AI model to generate natural language content. 

## What is the intended use of AI summarization in Commerce headquarters?

The intended use is for users to have immediate access to a relevant summary of an entity, helping them make faster, better decisions. 

## How was AI summarization evaluated in Commerce headquarters? What metrics are used to measure performance?

The AI-generated summary feature was evaluated manually by comparing the results against the values in current and associated entities. Additional validation was done for scenarios where users are missing privileges to see data to avoid overexposure, and where entities are missing data to avoid hallucination. All calculations are done using traditional coding methods, and only preaggregated data is sent to the large language models (LLM) service Copilot application programming interface (CAPI). They were verified against the same data during the testing process. If you encounter inappropriate generated content, you can report it to Microsoft by using the [Report abuse](https://msrc.microsoft.com/report) feedback form. Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of AI summarization in Commerce headquarters? How can users minimize the impact of limitations when using the system?

For very large documents, only a subset of the most impactful datasets are prefiltered to avoid token size limitation. The generated content should never be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of AI summarization in Commerce headquarters?

When you use the feature, you should follow these recommendations:

- Confirm that your company has sufficient control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- In case of large priority issues, the summarization capability can be turned off from the **Feature management** workspace in headquarters. There are also granular controls to turn off summarization for individual forms based on business need and relevance. 




[!INCLUDE[footer-include](../../includes/footer-banner.md)]

