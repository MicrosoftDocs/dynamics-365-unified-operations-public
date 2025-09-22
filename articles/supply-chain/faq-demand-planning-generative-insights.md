---
title: Responsible AI FAQ for Generative insights for Demand planning (production ready preview)
description: Access answers to frequently asked questions about the AI technology that's used in the "Generative insights for Demand planning" feature.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: article
ms.date: 06/17/2025
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
---

# Responsible AI FAQ for Generative insights for Demand planning (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This FAQ provides answers to frequently asked questions about the AI technology that's used in Generative insights for Demand planning in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

[!INCLUDE [production-ready-preview-dynamics365](~/../shared-content/shared/preview-includes/production-ready-preview-dynamics365.md)]

## What are Generative insights for Demand planning?

Generative insights for Demand planning analyzes your demand plans to detect patterns (such as seasonality and signal correlations) across products and locations. The feature provides answers using natural language and visualizations.

By using Generative insights, you can quickly gain valuable insights across multiple dimensions. You can use these insights to improve operational efficiency, increase profitability, and improve customer satisfaction.

Learn more about this feature in [Generative insights for Demand planning (preview)](demand-planning/generative-insights.md).

## What are the capabilities of Generative insights?

This feature lets you analyze your multidimensional demand plans for patterns such as seasonality and signal correlations. The system queries the data for all dimensions, and returns natural-language summaries, graphs, and other visualizations.

## What is the intended use of Generative insights?

Demand planners spend considerable time analyzing demand plans. This feature helps them gain valuable insights into the patterns that can be found in their data. These insights help planners make informed decisions about when to initiate promotions and also help them to predict the potential impact of those promotions.

## How was Generative insights evaluated? What metrics are used to measure performance?

The system underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [<Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if the abuse of the functionality is detected.

## What are the limitations of Generative insights? How can users minimize the impact of these limitations when they use the system?

A maximum of fifteen seasonal patterns can be detected. Generative insights calculates a confidence score for each seasonal pattern and sorts them according to that score. Results of equal confidence are ordered arbitrarily.

Products with insufficient data are grouped into a system-generated seasonal pattern named *Insufficient data*. This approach ensures that all data is analyzed and assigned a classification.

The AI-generated results are always presented in US English.

AI-generated content should not be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of Generative insights?

When you use this feature, follow these recommendations:

- Make sure that your company has enough control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- Before you make decisions about modifying a demand plan, always review and study the generated response, and compare it with actual demand plan data.

## Related information

- [Generative insights for Demand planning (preview)](demand-planning/generative-insights.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)
