---
# required metadata

title: FAQ for Copilot in site builder
description: This FAQ provides information about the AI technology that's used in Copilot in site builder for product enrichment, along with key considerations and details about how AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 03/29/2024
ms.custom: 
  - responsible-ai-faqs
ms.collection:
  - bap-ai-copilot
ms.topic: article
author: ashishmsft
ms.author: asharchw
ms.reviewer: v-chrgriffin
---

# FAQ for Copilot in site builder

These frequently asked questions (FAQ) describe the AI impact of the Copilot in site builder feature for product enrichment in Microsoft Dynamics 365 Commerce.

## What is Copilot in site builder?

Copilot in site builder works seamlessly with Dynamics 365 Commerce site builder to help you quickly create product enrichment and marketing content that's customized for your target audience and brand tone. Site builder offers a range of templates, features, and tools to help you customize your website to meet your needs and preferences. By using Copilot in site builder, you can quickly and efficiently generate persuasive, compelling, and engaging product enrichment and marketing content for your e-commerce websites.

## What are the capabilities of Copilot in site builder?

Copilot in site builder uses [Microsoft's Azure OpenAI Service](/azure/ai-services/openai/overview) to access powerful language models that analyze and generate natural language. These models are trained on a wide body of text datasets. 

Copilot in site builder offers the following capabilities:

- **Initiate the creative process** – Copilot generates content based on basic product information such as the name, description, attributes, and dimensions. You can then use the generated content to spark further ideas.
- **Optimize for search engines** – Optimize your product marketing content for search engines to help rank your e-commerce site higher in internet search results and drive up sales.
- **Choose the messaging tone** – You can select the voice that best fits your brand and audience, and you can specify a unique tone for each product. For example, the tone of the messaging for a product might be adventurous, casual, luxurious, formal, informational, or educational.
- **Create custom messages for specific buyers** – Select the intended audience to create custom messages for specific buyers, such as new parents, graduates, older adults, and health care workers.
- **Amplify with key highlights** – Use natural language to augment your content with key highlights that are specific to a product, and generate engaging text snippets that help amplify key highlights for your product.
- **Make basic modifications** – Easily make basic text modifications, either by using an inline rich text editor or by using natural language to provide key prompts to format text.

## What is the intended use of Copilot in site builder?

Creating marketing and storytelling content for a specific product for e-commerce sites is key for driving customer engagement and sales, but it can be a time-consuming and challenging process for retailers. With the new Copilot capability in Commerce that is built for site builder's product enrichment workflow, you can generate persuasive, compelling, and engaging product enrichment and marketing content for your e-commerce websites. Your content is optimized for search engines to help increase customer loyalty and boost your sales conversions.

## How was Copilot in site builder evaluated, and what metrics are used to measure performance?

- Copilot in site builder underwent extensive testing where language experts evaluated numerous texts in different languages against various criteria. Testing was based on fictitious product catalogs that are part of the demonstration data.
- Copilot in site builder is built in accordance with Microsoft's Responsible AI Standard. For more information, see [Empowering responsible AI practices](https://aka.ms/RAI).

## How does Microsoft monitor the quality of generated content?

Microsoft has various systems in place to ensure that Copilot capabilities remain operational and generate content of the highest quality.

- Users have the opportunity to provide feedback to report inappropriate content and improve the functionality.
- If users encounter inappropriate generated content, they can report it to Microsoft via the [Microsoft Security Response Center reporting portal](https://go.microsoft.com/fwlink/?linkid=2249810). 

  Microsoft might disable the Copilot-driven features for selected customers if abuse of the functionality is detected. 

 - Microsoft tracks user feedback to help improve suggestions. When users interact with Copilot in site builder, they can provide feedback by using the like (thumbs up) or dislike (thumbs down) symbols. Microsoft gathers the telemetry of these gestures for each AI output for which users submit feedback.
- The Azure OpenAI Service stores prompts and completions from the service to monitor for abusive use and to develop and improve the quality of Azure OpenAI's content management systems. Your company data isn't used to train AI models in the Azure OpenAI service. For information about content management and filtering, see [Content filtering](/azure/cognitive-services/openai/concepts/content-filter). 

Authorized Microsoft employees can access prompt and completion data that triggers automated systems for the purposes of investigating and verifying potential abuse. This data may be used to improve content management systems. In the event of a confirmed policy violation, Microsoft may ask you to take immediate action to remediate the issue and to prevent further abuse. Failure to address an issue may result in suspension or termination of Azure OpenAI resource access.

For more information, see [Data, privacy, and security for Azure OpenAI Service](/legal/cognitive-services/openai/data-privacy#abuse-and-harmful-content-generation).

## What are the limitations of Copilot in site builder, and how can users minimize the impact of the Copilot in site builder limitations when using the system?

The underlying technology behind Copilot in site builder uses AI that is trained on a wide range of sources, but the generated content isn't always factual or suitable. Some suggestions may even include questionable or inappropriate content. It's your responsibility to review and edit generated suggestions to ensure accuracy and appropriateness.

Inaccurate responses might be returned when users interact with the system in languages other than the supported languages. For information about supported languages, see [Copilot international availability](https://go.microsoft.com/fwlink/?linkid=2263265) 

## What operational factors and settings allow for effective and responsible use of Copilot in site builder?

There are a few things you can do to get the most out of Copilot in site builder:

- Add more attributes to an item to promote the specific features and characteristics you're interested in.
- Change the options for tone of voice and emphasis of quality to match your personal preferences.
- Change the options for the audience for whom you want to tailor the message. 
- Improve the item's description.
- Use descriptive prompts so that Copilot can revise the content meaningfully. 

## See also

- [Use Copilot in site builder to enrich product detail pages](../copilot-site-builder.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
