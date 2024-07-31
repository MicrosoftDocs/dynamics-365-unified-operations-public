---
title: FAQ for Copilot-based insights
description: This article provides answers to frequently asked questions about the Microsoft Copilot AI technology used to generate summaries in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: ashishmsft
ms.date: 07/31/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
---

# FAQ for Copilot-based insights

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Copilot artificial intelligence (AI) technology used to generate summaries in the Microsoft Dynamics 365 Commerce Store Commerce app. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is Copilot-based insights for Store Commerce?

The Copilot-powered Store Commerce app is designed to streamline retail operations and enhance customer engagement. Its core purpose is to simplify complex data analysis, personalize customer service, and optimize product management through advanced AI-driven summarization features.

## What can Copilot-based insights for Store Commerce do? 

Using the advanced capabilities of [Azure Open AI](/azure/ai-services/openai/overview), this AI feature is engineered to synthesize summary content that is tailored for various Store Commerce scenarios including report insights, customer insights, and product insights. It intelligently uses the provided datasets to craft concise, meaningful, and contextual summaries. These summaries serve as valuable references for store managers, sales associates, and cashiers, enabling them to make data-driven decisions that drive store sales, enhance operational efficiency, and improve customer service.

## What are the intended uses of Copilot-based insights for Store Commerce?

The intended use is for the users to have immediate access to relevant summary of an entity, helping them make faster, better decisions.  
- **Report Insights**: Generates narrative summaries for channel reports, providing insights into sales and performance metrics. Enhances accuracy and offers real-time analysis, with customizable prompts for tailored report generation.
- **Customer Insights**: Assists store associates in creating personalized interactions by summarizing customer transactional activity, interactions, and profile data. Empowers store associates with a deeper understanding of customers, enabling them to provide personalized recommendations.
- **Product Insights**: Helps store associates drive product sales by providing description, top benefits, inventory, and discount information. It also helps with cross-selling other related products to deliver on sales strategy and to boost customer experience.

## How is Copilot-based insights for Store Commerce evaluated? What metrics are used to measure performance?

The features undergo substantial testing before they're made available for customers in production. AI-generated summaries are evaluated by manually comparing the results against the values in the current and associated entities. The feature also relies on user feedback. If the AI-generated summary contains irrelevant or inappropriate responses, report it to Microsoft using the thumbs down gesture. Microsoft associates each thumbs up and thumbs down gesture with the corresponding AI-generated output. Your feedback helps improve the functionality moving forward. Microsoft also tracks the feature's service-level agreement (SLA) to ensure that it's always available.

## What are the limitations of Copilot-based insights for Store Commerce?

- The first release of these features is available only for English. Support for additional languages will be added in future releases.
- The [Availability of Copilot in your geographical region](/power-platform/admin/geographical-availability-copilot).
- There are no open-ended prompts to allow further modification to the style of summarization by Copilot for any insights.
- For performance reasons, caching of 15 minutes for Copilot-generated summaries is implemented for customer and product insights at a store level so that if any associate is accessing the same customer or product information on different registers in same store, they're allowed to view the cached response for those 15 minutes. 
- For Customer insights, the **Spark-a-conversation** section considers a maximum of 20 transactions from the past year for an individual customer.
- The dataset of previous orders and products a customer has purchased that's used for calculating average customer spending, price range, average items per order, lifetime value, year-to-date spending, and orders places in last year uses the 50 latest order headers and the 50 latest order lines.
- For customer insights, Microsoft doesn't consider cash and carry orders due to a current limitation of the API.

## How can users minimize the impact of Copilot-based insights for Store Commerce’s limitations when using the system?

- For customers with a large transaction history, due to token size limitations the summarization for **spark-a-conversation** functionality is limited to the most recent 20 transactions in last 12 months.
- All summarization prompts are system-generated. If you have feedback, reach out to Microsoft support. 

## What are plug-ins and how does Copilot based insights for Store Commerce use them?  

No plug-ins or extensibility functionality is currently supported.

## What data can Copilot based insights for Store Commerce provide to plug-ins? What permissions do Copilot based insights for Store Commerce plug-ins have? 

No plug-in or extensibility functionality is currently supported.
  
## What kinds of issues may arise when using Copilot based insights for Store Commerce enabled with plug-ins?  

No plug-in or extensibility functionality is currently supported.

## See also

[Customer insights by Copilot](../copilot-pos-customer-insights.md)

[Store report insights by Copilot](../copilot-pos-report-insights.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
