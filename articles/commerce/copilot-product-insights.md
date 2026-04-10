---
title: Product insights by Copilot
description: Learn how store associates can use Microsoft Copilot-generated product insights to quickly understand product information and deliver informed shopping assistance 
author: ashishmsft
ms.date: 04/08/2026
ms.update-cycle: 180-days
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
ms.custom: sfi-image-nochange
---


# Product insights by Copilot
[!include [banner](includes/banner.md)]

This article describes how store associates can use Microsoft Copilot generated product insights to quickly understand product information and deliver informed shopping assistance in the Microsoft Dynamics 365 Commerce Store Commerce app.

## Overview
Product insights by Copilot is a feature in the Dynamics 365 Commerce Store Commerce app that uses AI to generate natural language summaries of product information for store associates.

Store associates frequently interact with customers who want to understand:

- The benefits of a product
- Its availability
- Current offers or applicable discounts
- Navigate complementary items categories based on upsell/cross-sell product configurations

:::image type="content" source="./media/CopilotProductInsights.png" alt-text="Screenshot of Product insights by Copilot features in the Store Commerce app.":::

However, modern retail environments often contain a large assortment of dynamically changing products. Learning and remembering detailed product specifications, pricing, and promotional information can be difficult—particularly for new associates.
Product insights by Copilot connects relevant product data from Dynamics 365 Commerce and presents it to store associates in an intuitive and actionable way directly within the point‑of‑sale (POS) experience.

By using Product insights by Copilot, store associates can:

- View summarized product highlights and benefits
- Understand inventory availability in real time
- Identify applicable discounts and promotions
- Discover complementary or related products

Store associates can use these insights during customer conversations to:

- Explain the value of a product
- Communicate fulfillment expectations accurately
- Offer eligible discounts
- Suggest additional products that enhance the purchase

## Enable Product insights by Copilot in the Store Commerce app

To enable Product insights by Copilot in the Store Commerce app, follow these steps:
1. In Commerce headquarters, go to **Feature management** (**Systems administration \> Workspaces \> Feature management**), and enable the **Enable Copilot in Store Commerce** feature flag.
2. Go to **Commerce shared parameters** (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**), and enable the **Enable Copilot in Store Commerce** parameter.
3. Go to your POS functionality profile (**Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**).
4. On the **Copilot** FastTab, enable **Product insights**.
5. Run the **1070 (Channel configuration)** job to sync the updated settings to the channel database.

This capability is available to customers who use the following English-language Commerce versions:

- Commerce version 10.0.39, proactive quality update 4 (PQU-4) and later (Commerce Scale Unit: 9.49.24184.3, Store Commerce app: 9.49.24193.1)
- Commerce version 10.0.40, PQU-1 and later (Commerce Scale Unit: 9.50.24184.2, Store Commerce app: 9.50.24189.1)

> [!NOTE]
> - AI-generated content might be incorrect. Learn more in [Service Agreement & Microsoft Products and Services Data Protection Addendum](https://aka.ms/BusinessApplicationLegal).
> - For performance reasons, Customer insights by Copilot results are cached for 15 minutes at the store level. Therefore, an associate who accesses the same customer information on different registers can view the cached response.
> - For Copilot experiences in the Store Commerce app, you must link your Dataverse instance to your environment by enabling Copilot capabilities in your finance and operations apps. Learn more in [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).
> - If your hosting environment is in one of the regions where Azure OpenAI Service isn't currently available, consider enabling the **Move data across regions** capability in the Power Platform admin center. If your Commerce environments are hosted in the EU Data Boundary, you use an Azure OpenAI endpoint in the same boundary. If the required AI services are already available in your Dataverse region, you don't have to set up support for cross-region calls. If cross-region data movement is required but disabled, users can't view Copilot-generated summaries in the Store Commerce app. [Learn more](/power-platform/admin/geographical-availability-copilot).

## Additional resources

[FAQ for Copilot-based insights](responsible-ai/faqs-ai-copilot-store-comm-summaries.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
