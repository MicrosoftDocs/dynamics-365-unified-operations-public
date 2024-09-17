---
title: Responsible AI FAQ for Analyze demand plans with Copilot (preview)
description: Access answers to frequently asked questions about the AI technology that's used in the "Analyze demand plans with Copilot" feature for Demand planning.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 04/01/2024
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
---

# Responsible AI FAQ for Analyze demand plans with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This FAQ provides answers to frequently asked questions about the AI technology that's used in the *Analyze demand plans with Copilot* feature for Demand planning in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## What is Analyze demand plans with Copilot?

Demand planning in Supply Chain Management lets you use Copilot to analyze your demand plans. You can select from a set of predefined questions. The app then provides answers in real time by using natural language.

By using Copilot, you can quickly gain valuable insights across multiple dimensions. You can use these insights to improve operational efficiency, increase profitability, and improve customer satisfaction.

For example, a demand planner is interested in learning the most significant factors that contributed to a notable shift between two consecutive periods. The planner opens the relevant worksheet, selects a point of interest on the chart, and then selects a predefined question to ask Copilot. Copilot's response might resemble the following example:

> The top 10 most significant changes contributing to the change in demand are:
>
> 1. Car Audio Unit-500 in Distribution center increased by 31% or 208 units.
> 1. Car Audio Unit-65-Black in Distribution center increased by 31% or 173 units.
> 1. Car Audio Unit-65-Silver in Store 2 increased by 29% or 574 units.
> 1. Mid-Range Speaker in Store 1 increased by 29% or 509 units.
> 1. High End Speaker in Store 4 increased by 28% or 298 units.
> 1. High End Speaker in Store 1 increased by 28% or 351 units.
> 1. Car Audio Unit-65-Silver in Store 1 increased by 28% or 405 units.
> 1. High End Cabinet-Oak in Distribution center increased by 28% or 190 units.
> 1. Car Audio Unit-500 in Store 4 increased by 28% or 123 units.
> 1. Car Audio Unit-200 in Store 1 increased by 27% or 240 units.
>
> AI-generated content may be incorrect.

## What are the capabilities of Analyze demand plans with Copilot?

This feature lets users select from a set of predefined questions to analyze their multidimensional demand plans. The system queries the data in each dimension and for all dimensions. The results are delivered in natural written language and highlight the dimension values that shifted significantly between the two selected periods. Both increasing and decreasing shifts are highlighted.

## What is the intended use of Analyze demand plans with Copilot?

Demand planners spend considerable time analyzing demand plans. This feature helps these users gain valuable insights into demand plans. It helps them make informed decisions by providing a single result that summarizes the most significant shifts that occurred across several dimensions. Plans can then easily be adjusted based on the detected shifts.

## How was Analyze demand plans with Copilot evaluated? What metrics are used to measure performance?

The system underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of Analyze demand plans with Copilot? How can users minimize the impact of these limitations when they use the system?

Copilot shows a maximum of ten results. These results are ordered by significance. Results of equal significance are ordered arbitrarily. Although there might be additional results that have the same significance as the tenth result, Copilot doesn't indicate that those results exist.

The AI-generated results are always presented in US English.

AI-generated content should not be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of Analyze demand plans with Copilot?

When you use this feature, follow these recommendations:

- Make sure that your company has enough control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- Before you make decisions about modifications to the demand plan, always review and study the generated response, and compare it with actual demand plan data.

### Related information

- [Analyze demand plans with Copilot (Preview)](demand-planning/demand-planning-copilot.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)
