---
title: Copilot based insights for Store Commerce - Responsible AI FAQ
description: This article provides answers to frequently asked questions about the Microsoft Copilot AI technology that is used to generate summaries in Store Commerce app of Dynamics 365 Commerce.
author: ashishmsft
ms.date: 07/30/2024
ms.topic: how-to
audience: Application user
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: v-chrgriffin
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
---

# Copilot based insights for Store Commerce - Responsible AI FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions about the Microsoft Copilot AI technology that is used to generate summaries in the Store Commerce app. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

### What is Copilot based insights for Store Commerce?

The Store Commerce app, powered by Copilot, is designed to streamline retail operations, and enhance customer engagement. Its core purpose is to simplify complex data analysis, personalize customer service, and optimize product management through advanced AI-driven summarization features

### What can Copilot based insights for Store Commerce do? 

Using the advanced capabilities of [Azure Open AI](/azure/ai-services/openai/overview), this AI feature is engineered to synthesize summary content tailored for various Store Commerce Scenarios, including Report Insights, Customer Insights, Product Insights, and others. It intelligently uses the provided datasets to craft concise, meaningful, and contextual summaries. These summaries serve as valuable references for store managers, sales associates, and cashiers, enabling them to make data-driven decisions that drive store sales, enhance operational efficiency, and improve customer service.

### What are the intended uses of Copilot-based insights for Store Commerce?

The intended use is for the users to have immediate access to relevant summary of an entity, helping them make faster, better decisions.  
- **Report Insights**: Generates narrative summaries for channel reports, providing insights into sales and performance metrics. Enhances accuracy and offers real-time analysis, with customizable prompts for tailored report generation.
- **Customer Insights**: Assists store associates in creating personalized interactions by summarizing customer transactional activity, interactions, and profile data. Empowers store associates with a deeper understanding of customers, enabling them to provide personalized recommendations.
- **Product Insights**: Helps store associates drive product sales by providing description, top benefits, inventory, and discount information. Also helps cross-selling other related products to deliver on sales strategy and to boost customer experience

### How were Copilot based insights for Store Commerce evaluated? What metrics are used to measure performance?

The features underwent substantial testing before they were being made available for customers in production. AI-generated summaries were evaluated by manually comparing the results against the values in the current and associated entities. The feature also relies on user feedback. If the AI-generated summary contains irrelevant or inappropriate responses, report it to Microsoft using the thumbs down gesture. Microsoft associates each thumbs up and thumbs down gesture with the associated AI-generated output. Your feedback helps improve the functionality moving forward. Microsoft also tracks the feature's service-level agreement (SLA) to ensure that it's always available.

### What are the limitations of Copilot based insights for Store Commerce?

- First release of these features is available for English only. Support for additional languages will be added in future releases.
- See the [availability of Copilot in your geographical region](/power-platform/admin/geographical-availability-copilot).
- There are no open-ended prompts to allow further modification to style of summarization by Copilot for any of insights.
- For performance reasons, caching of 15 minutes for Copilot-generated summaries is introduced for Customer and Product insights at a store level, that way if any associate is accessing same customer or product information on different registers in same store they're allowed to view the cached response for those 15 minutes. 
- With regard to Customer insights, the 'Spark-a-conversation' section considers a maximum of 20 transactions from the past year for an individual customer.
- The dataset of previous orders and products a customer has purchased that is used for calculating avg customer spending, price range, Avg items per order, lifetime value, year to date spending, orders places in last year – we use 50 latest order headers and 50 latest order lines.
- For customer insights, Microsoft doesn't consider cash and carry orders due to a current limitation of the API.

### How can users minimize the impact of Copilot based insights for Store Commerce’s limitations when using the system?

- For customers with large transaction history, due to token size limitations, summarization for ‘spark-a-conversation’ is limited to recent 20 transactions in last 12 months.
- All the summarization prompts are system-generated. If you have feedback, reach out to Microsoft support 

### What are plug-ins and how does Copilot based insights for Store Commerce use them?  
- N/A – no plug-ins or extensibility are supported as of this release.
- 
### What data can Copilot based insights for Store Commerce provide to plug-ins? What permissions do Copilot based insights for Store Commerce plug-ins have? 
- N/A – no plug-ins or extensibility are supported as of this release.
- 
### What kinds of issues may arise when using Copilot based insights for Store Commerce enabled with plug-ins?  
- N/A – no plug-ins or extensibility are supported as of this release.

