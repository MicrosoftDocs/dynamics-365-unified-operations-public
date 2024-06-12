---
title: Responsible AI FAQ for AI summarization in Commerce headquarters
description: This FAQ provides answers to frequently asked questions about the AI technology that is used for generating summaries in Commerce headquarters. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 06/12/2024
ms.collection:
  - bap-ai-copilot
ms.custom:
  - responsible-ai-faqs
ms.topic: article
author: shajain
ms.author: shajain
ms.reviewer: v-chrgriffin
---

# Responsible AI FAQ for AI summarization in Commerce headquarters

[!include [banner](../includes/banner.md)]

This Responsible AI FAQ provides answers to frequently asked questions about the AI technology that's used in generating the summaries in the headquarter application within Microsoft Dynamics 365 Commerce. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is AI summarization in Commerce headquarters?

**AI summarization in Commerce headquarters** helps business users make better decisions more efficiently, by giving them access to summarized information about the data and risks, among other things.

## What can AI summarization in Commerce headquarters do? 
The feature is powered by Azure Open AI's large language model. It uses the information from the posted and unposted statements to generate a summary that includes insights like the count of transactions affected, total sales amount of these statements and risks such as transactions with returns without receipts, expense transactions, and price overrides and more. AI summary is also displayed for Merchandizers, providing insights about product misconfigurations. Copilot uses the *gpt-3.5-turbo* generative AI model to generate the natural-language content. 

## What is/are AI summarization in Commerce headquarters’s intended use(s)??

The intended use is for the users to have immediate access to relevant summary of an entity, helping them make faster, better decisions. 

## How was AI summarization in Commerce headquarters? What metrics are used to measure performance?

he AI-generated summary was evaluated manually by comparing the results against the values in the current and associated entities. Additional validation was done for scenarios where the user is missing privileges to see data, to avoid over-exposure and entities with missing data to avoid hallucination. All calculations are done using traditional coding methods, and only pre-aggregated data is sent to the LLM service (CAPI). They were verified against the same data during the testing process. If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable the Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of AI summarization in Commerce headquarters? How can users minimize the impact of AI summarization in Commerce headquarters limitations when using the system?

For very large documents, only a subset of the most impactful dataset and pre-filtered due to avoid token size limitation. The generated content should never be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of AI summarization in Commerce headquarters?

When you use the feature, follow these recommendations:

- Make sure that your company has sufficient control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- In case of hig priority issues, the summarization capability can be turned off from the Feature Management workspace. There are granular controls to turn off summarization for individual forms based on business need and relevance. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]

