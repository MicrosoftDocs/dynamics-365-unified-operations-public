---
title: FAQ for Copilot-based insights
description: This article provides answers to frequently asked questions about the Microsoft Copilot AI technology used to generate summaries in the Dynamics 365 Commerce Store Commerce app.
author: ashishmsft
ms.date: 01/22/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
---

# FAQ for Copilot-based insights

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Copilot AI technology that is used to generate summaries in the Dynamics 365 Commerce Store Commerce app. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is Copilot-based insights for Store Commerce?

The Copilot-powered Store Commerce app is designed to streamline retail operations and enhance customer engagement. Its core purpose is to simplify complex data analysis, personalize customer service, and optimize product management through advanced AI-driven summarization features.

## What can Copilot-based insights for Store Commerce do?

This AI feature uses the advanced capabilities of [Azure OpenAI Service](/azure/ai-services/openai/overview) to synthesize summary content that is tailored for various Store Commerce scenarios, including report insights, customer insights, and product insights. It intelligently uses the provided datasets to craft concise, meaningful, and contextual summaries. These summaries serve as valuable references that can help store managers, sales associates, and cashiers make data-driven decisions that drive store sales, enhance operational efficiency, and improve customer service.

## What are the intended uses of Copilot-based insights for Store Commerce?

The intended use is to give users immediate access to a relevant summary of an entity, so that they can make faster, better decisions.

- **Report insights**: Generates narrative summaries for channel reports to provide insights into sales and performance metrics. Enhances accuracy and offers real-time analysis. 
- **Customer insights**: Helps store associates create personalized interactions by summarizing customer transactional activity, interactions, and profile data. Empowers associates through a deeper understanding of customers and enables them to provide personalized recommendations.
- **Product insights**: Helps store associates drive product sales by providing description, top benefits, inventory, and discount information. Helps associates cross-sell related products to deliver on the sales strategy and boost the customer experience.

## How is Copilot-based insights for Store Commerce evaluated? What metrics are used to measure performance?

Features undergo substantial testing before they're made available for customers in production. AI-generated summaries are evaluated by manually comparing the results against the values in the current and associated entities. The feature also relies on user feedback. If an AI-generated summary contains irrelevant or inappropriate responses, report the issue to Microsoft by using the thumbs-down gesture. Microsoft associates each thumbs-up and thumbs-down gesture with the corresponding AI-generated output. Your feedback helps improve the functionality moving forward. Microsoft also tracks the feature's service-level agreement (SLA) to ensure that it's always available.

## What are the limitations of Copilot-based insights for Store Commerce?

- The first release of these features is available only for English. Support for additional languages will be added in future releases.
- There are limitations on the [geographical regions where Copilot is available](/power-platform/admin/geographical-availability-copilot).
- There are no open-ended prompts to allow for modification of the style of summarization that Copilot uses for any insights.
- For performance reasons, Copilot-generated summaries for customer and product insights are cached for 15 minutes at the store level. Therefore, during those 15 minutes, an associate who accesses the same customer or product information on different registers in the same store can view the cached response.
- For customer insights, the **Spark-a-conversation** functionality considers a maximum of 20 transactions from the past year for an individual customer.
- To calculate average customer spending, price range, average items per order, lifetime value, year-to-date spending, and orders placed in the last year, a dataset of previous orders and previous products that a customer purchased is used. However, this dataset uses only the 50 latest order headers and the 50 latest order lines.
- For customer insights, Microsoft doesn't consider cash-and-carry orders because of a current limitation of the API.

## How can users minimize the impact of Copilot-based insights for Store Commerce's limitations when using the system?

- For customers who have a large transaction history, token size limitations cause the summarization for **Spark-a-conversation** functionality to be limited to the most recent 20 transactions in the last 12 months.
- All summarization prompts are system-generated. If you have feedback, contact Microsoft Support.

## What are plug-ins, and how does Copilot-based insights for Store Commerce use them?

No plug-ins or extensibility functionality is currently supported.

## What data can Copilot-based insights for Store Commerce provide to plug-ins? What permissions do Copilot-based insights for Store Commerce plug-ins have? 

No plug-in or extensibility functionality is currently supported.

## What kinds of issues might arise when using Copilot-based insights for Store Commerce enabled with plug-ins?

No plug-in or extensibility functionality is currently supported.

## Additional resources

[Customer insights by Copilot](../copilot-pos-customer-insights.md)

[Store report insights by Copilot](../copilot-pos-report-insights.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
