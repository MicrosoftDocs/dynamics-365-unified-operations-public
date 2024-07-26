---
title: Customer insights using Copilot - Transforming Clienteling in Retail
description: This article describes how Store associates can leverage Copilot to enhance customer interactions and create personalized shopping experiences.
author: ashishmsft
ms.date: 07/19/2024
ms.topic: article
audience: Application user
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
---

# Customer insights using Copilot: Transforming Clienteling in Retail

Imagine a store where every associate knows their customers by name, their preferences, their budget, and their shopping behavior. A store where associates can engage customers with personalized ice-breakers, recommend products that match their interests and price sensitivity, and follow up with them after every purchase. A store where customers feel valued, understood, and loyal.
That store is possible with Customer insights by Copilot, a new feature in Store Commerce app of Dynamics 365 Commerce that leverages artificial intelligence to transform customer service and create individualized shopping experiences. Customer insights by Copilot connects relevant data points from Dynamics 365 Commerce and presents them to store associates in an intuitive and actionable way. By using Customer insights by Copilot, store associates can:
- Access comprehensive and in-depth profiles of each customer, including their preferred product categories, price ranges, RFM analysis, and lifetime value.
- View a summarized timeline of each customer's activity, such as store visits, notes, events, and previous interactions, and easily pick up the conversation where it left off or provide a tailored follow-up.
- Spark a conversation with personalized ice-breaker questions based on the customer's recent purchases within the last year.
- Offer relevant and customized recommendations based on the customer's purchase history, interests, and budget.
  
![Customer insights using Copilot](./media/CustomerInsightsUsingCopilot.png)

## Why use Customer insights by Copilot? 

The expectations of customers are increasing, with a growing desire for individualized experiences upon entering a store. Store staff is presented with the considerable task of manually scrutinizing customer behavior, an approach that is both inefficient and daunting, ultimately obstructing the provision of effective personalized encounters. 
Harnessing the power of Copilot simplifies the process of understanding your clientele. Monitoring each customer's timeline of activities such as store visits, notes, events, etc., can prove to be a hefty chore. Copilot efficiently summarizes each customer’s engagement timeline. In just a brief look, you are updated on their previous interactions, which simplifies the process of picking up conversations where they were left or giving tailor-made follow-ups.
Customer insights by Copilot empowers store associates to excel in service delivery, turning transactions into lasting customer relationships. It also benefits customers by providing them with a personalized and memorable shopping experience that meets their needs and expectations. Customer insights by Copilot is the ultimate tool for clienteling in retail, as it shifts the focus from sales to crafting individual experiences, and creates loyal customers through exceptional service.

## How to enable Customer insights by Copilot?
To use Customer insights by Copilot in Store Commerce app, you need to follow these three steps:
1.	From feature management workspace, enable the temporary flag "Enable Copilot in Store Commerce" giving governing control to your organization's administrators to control the roll-out of Copilot features in Store Commerce app. This flag will eventually be retired in future, as with any other feature management workspace based feature flags. These settings are off by default and can be turned on or off as per your business needs.
2.	From Commerce shared parameters, enable the permanent flag "Enable Copilot in Store Commerce" giving additional governing control to your organization's administrators to control the availability of Copilot features in Store Commerce app. This flag will get automatically enabled once you enable the temporary flag, and shall continue to be available even after temporary flag is retired. 
3.	From POS functionality profile, you would notice new fast-tab for "Copilot" settings, enable "Customer insights" to get Store reports insights by Copilot in Store Commerce app and run CDX jobs for these updated settings to be synced to Channel database for it to take effect.

This capability is available for Dynamics 365 Commerce customers on following versions for stores using English languages - 

- 10.0.39, PQU-4 onwards (CSU : 9.49.24184.3, Store Comm. App 9.49.24193.1)
- 10.0.40, PQU-1 onwards (CSU : 9.50.24184.2, Store Comm. App 9.50.24189.1)


> [!Note]
> AI-generated maybe incorrect. [Learn more](https://aka.ms/BusinessApplicationLegal)
>
> For performance reasons, Customer insights by Copilot are cached for 15 mins at a Store-level, that way if any associate is accessing same customer information on different registers they will get to view the cached response. 
>
> For Copilot experiences in Store Commerce app, it depends on your Dataverse instance being linked to your environment. For this, Copilot capabilities should be enabled in your finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).
> 
> Lastly, if your hosting environment is in one of the regions where Azure Open AI is currently not available, then through Power Platform Admin Center (PPAC) consider enabling "Move data across regions". If your Dynamics 365 environments are hosted in the EU Data Boundary, we use an Azure OpenAI endpoint in the same boundary.If the required AI services are already available in your Dataverse region, you don't have to set up support for cross-region calls. If cross-region data movement is required but is disabled, users won't be able to view Copilot generated summaries in Store Commerce app. [Learn more](/power-platform/admin/geographical-availability-copilot)
