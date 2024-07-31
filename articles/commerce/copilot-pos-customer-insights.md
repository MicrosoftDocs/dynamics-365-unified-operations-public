---
title: Customer insights by Copilot
description: This article describes how store associates can use Copilot to enhance customer interactions and create personalized shopping experiences in Microsoft Dynamics 365 Commerce.
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

# Customer insights by Copilot

[!include [banner](includes/banner.md)]

This article describes how store associates can use Copilot to enhance customer interactions and create personalized shopping experiences in Microsoft Dynamics 365 Commerce.

Customer insights by Copilot is a feature in the Dynamics 365 Commerce Store Commerce app that uses artificial intelligence to transform customer service and create individualized shopping experiences. Customer insights by Copilot connects relevant data points from Commerce and presents them to store associates in an intuitive and actionable way. By using Customer insights by Copilot, store associates can:
- Access comprehensive and in-depth profiles of each customer, including:
    - Preferred product categories.
    - Price ranges.
    - Recency, frequency, monetary (RFM) analysis.
    - Lifetime value.
- View a summarized timeline of each customer's activity such as store visits, notes, events, and previous interactions to easily pick up the conversation where it left off or provide a custom follow-up.
- Spark a conversation with personalized icebreaker questions based on a customer's recent purchases within the last year.
- Offer relevant and customized recommendations based on a customer's purchase history, interests, and budget.
  
![Customer insights using Copilot](./media/CustomerInsightsUsingCopilot.png)

## Benefits of Customer insights by Copilot 

Customer expectations are increasing, with a growing desire for individualized experiences when entering a store. Store staff is presented with the considerable task of manually scrutinizing customer behavior, an approach that is both inefficient and daunting, ultimately obstructing the provision of effective personalized encounters. 

Harnessing the power of Copilot simplifies the process of understanding your clientele. Monitoring each customer's timeline of activities such as store visits, notes, and events can be challenging. Copilot efficiently summarizes each customer's engagement timeline and updates you on their previous interactions, which simplifies the process of picking up conversations where they were left off or providing custom follow-up suggestions.

Customer insights by Copilot empowers store associates to excel in service delivery, turning transactions into lasting customer relationships. It also benefits customers by providing them with a personalized and memorable shopping experience that meets their needs and expectations. Customer insights by Copilot is the ultimate tool for clienteling in retail, as it shifts the focus from sales to crafting individual experiences, and creates loyal customers through exceptional service.

## Enable Customer insights by Copilot in the Store Commerce app

To enable Customer insights by Copilot in the Store Commerce app, follow these steps.

1. In Commerce headquarters, go to the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**) and enable the temporary **Enable Copilot in Store Commerce** feature flag. Enabling this feature gives governing control to your organization's administrators to control the rollout of Copilot features in the Store Commerce app. This flag will eventually be retired in the future.
1. Go to **Commerce shared parameters** (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**) and enable the **Enable Copilot in Store Commerce** flag to give additional governing control to your organization's administrators to manage the availability of Copilot features in the Store Commerce app. This flag is automatically enabled when you enable the temporary flag, and will continue to be available after temporary flag is retired. 
1. Go to your POS functionality profile (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**). On the **Copilot** FastTab, enable **Customer insights** to get Customer insights by Copilot reports in the Store Commerce app.
1. Run the **1070 (Channel configuration)** job to sync these updated settings to the channel database.

This capability is available for customers using the following English language Commerce versions:

- Commerce version 10.0.39, PQU-4 onwards (Commerce Scale Unit: 9.49.24184.3, Store Commerce app version 9.49.24193.1)
- Commerce version 10.0.40, PQU-1 onwards (Commerce Scale Unit: 9.50.24184.2, Store Commerce app version 9.50.24189.1)

> [!NOTE]
> - AI-generated content may be incorrect. For more information, see [Service Agreement & Microsoft Products and Services Data Protection Addendum](https://aka.ms/BusinessApplicationLegal).
> - For performance reasons, Customer insights by Copilot results are cached for 15 minutes at the store level so that if any associate is accessing same customer information on different registers they can view the cached response. 
> - For Copilot experiences in the Store Commerce app, your Dataverse instance must be linked to your environment by enabling Copilot capabilities in your finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).
> - If your hosting environment is in one of the regions where Azure Open AI isn't currently available, consider enabling the **Move data across regions** capability in the Power Platform Admin Center (PPAC). If your Dynamics 365 Commerce environments are hosted in the EU Data Boundary, you use an Azure OpenAI endpoint in the same boundary. If the required AI services are already available in your Dataverse region, you don't have to set up support for cross-region calls. If cross-region data movement is required but is disabled, users aren't able to view Copilot-generated summaries in the Store Commerce app. [Learn more](/power-platform/admin/geographical-availability-copilot).


[!INCLUDE[footer-include](../includes/footer-banner.md)]
