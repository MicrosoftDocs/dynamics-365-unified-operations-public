---
title: Responsible AI FAQ for Analyze demand plans with Copilot (preview)
description: This FAQ provides answers to frequently asked questions about the AI technology that's used in the "Analyze demand plans with Copilot" feature in Demand planning app for Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.date: 04/01/2024
ms.collection:
  - bap-ai-copilot
ms.custom: 
  - responsible-ai-faqs
ms.topic: article
---

# Responsible AI FAQ for Analyze demand plans with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](includes/preview-banner.md)]

This FAQ provides answers to frequently asked questions about the AI technology that's used in the *Analyze demand plans with Copilot* feature in Demand planning app for Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [preview-note](includes/preview-note.md)]

## What is Analyze demand plans with Copilot?

The Demand planning app for Dynamics 365 Supply Chain Management lets you use Copilot to analyze your demand plans. It lets you choose from a set of pre-defined questions and provides answers in real time using natural language.

Using Copilot, you can quickly gain valuable insights across multiple dimensions. Using these insights, you can improve operational efficiency, increase profitability, and improve customer satisfaction.

For example, a demand planner might be interested in tracking down the most significant factors that contributed to a notable shift between two consecutive periods. The planner opens the relevant worksheet, chooses a point of interest on the graph, and then selects a predefined question to ask Copilot. Copilot's response could resemble the following answer:

> The top 10 most significant changes contributing to the change in demand are:<br><br>1. Car Audio Unit-500 in Distribution center increased by 31% or 208 units.<br>2. Car Audio Unit-65-Black in Distribution center increased by 31% or 173 units.<br>3. Car Audio Unit-65-Silver in Store 2 increased by 29% or 574 units.<br>4. Mid-Range Speaker in Store 1 increased by 29% or 509 units.<br>5. High End Speaker in Store 4 increased by 28% or 298 units.<br>6. High End Speaker in Store 1 increased by 28% or 351 units.<br>7. Car Audio Unit-65-Silver in Store 1 increased by 28% or 405 units.<br>8. High End Cabinet-Oak in Distribution center increased by 28% or 190 units.<br>9. Car Audio Unit-500 in Store 4 increased by 28% or 123 units.<br>10. Car Audio Unit-200 in Store 1 increased by 27% or 240 units.<br><br>AI-generated content may be incorrect.

## What are capabilities of Analyze demand plans with Copilot?

This feature allows users to select from a set of predefined questions to analyze their multi-dimensional demand plans. The system queries the data in each dimension and for all dimensions. The results are delivered using natural written language that highlights the dimension values that shifted significantly between the two selected time periods. Both increasing and decreasing shifts are highlighted.

## What is the intended use of Analyze demand plans with Copilot?

Demand planners spend a considerable amount of time analyzing demand plans. This feature helps these users gain valuable insights into demand plans and make informed decisions based on a single result that summarizes the most significant shifts that occurred across several dimensions. Adjustments to plans can easily be made based on the detected shifts.

## How was Analyze demand plans with Copilot evaluated? What metrics are used to measure performance?

The system underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of the Analyze demand plans with Copilot? How can users minimize the impact of these limitations when using the system?

The AI-generated result will always be in US English.

AI-generated content shouldn't be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of the Analyze demand plans with Copilot?

When you use the feature, follow these recommendations:

- Make sure that your company has sufficient control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- Always review and study the generated response, and compare with actual demand plan data, before you make decisions about modifications to the demand plan.

### See also

- [Analyze demand plans with Copilot (Preview)](demand-planning/demand-planning-copilot.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)
