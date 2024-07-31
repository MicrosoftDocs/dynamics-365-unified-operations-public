---
title: Streamline your merchandising process with Copilot-based insights
description: This article explains how to use Copilot to proactively provide a comprehensive summary of insights for the merchandising configurations of your retail channels to simplify your merchandising workflows in Microsoft Dynamics 365 Commerce.
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

# Streamline your merchandising process with Copilot-based insights

[!include [banner](includes/banner.md)]

This article explains how to use Copilot to proactively provide a comprehensive summary of insights for the merchandising configurations of your retail channels to simplify your merchandising workflows in Microsoft Dynamics 365 Commerce. The summary of insights enables you to understand the status and performance of your products across different channels, as well as identify and resolve any issues that are related to your product, category, and catalog data.

## Enhance merchandiser efficiency by streamlining merchandising workflows

Merchandising is a complex and time-consuming process that involves configuring various aspects of products, categories, catalogs, and attributes for each channel. Merchandisers need to ensure that their products are displayed correctly and accurately on the online store, and that they comply with the business rules and policies of each channel. However, manual validation of these configurations is prone to human errors, and can result in misconfigured products that affect customer experience and sales. Moreover, manual validation isn't scalable for large-scale businesses that have millions of products, thousands of attributes, and hundreds of categories and catalogs across hundreds of stores.

With Copilot, you can enhance your merchandiser efficiency by streamlining your merchandising workflows. Copilot can offer a clear summary of your product settings, such as variant groups, dimension groups, attribute groups, and category hierarchies. Copilot can also automate data validation by checking for errors, inconsistencies, and duplicates in your product data. Copilot can also provide a risk preview by showing you the potential issues that might arise from your product configuration, such as out-of-stock issues, price misconfigurations, and catalog mismatches.

By using the summary of merchandising configuration risks, you can significantly reduce the number of clicks and searches needed to access and update your product data. Copilot provides you with a proactive insightful summary that shows you the most important and relevant information at a glance. You can easily navigate to the list of issues and take action without losing context. Compared to the traditional way of managing your product data that requires numerous clicks and multiple searches across various forms, Copilot offers you a "one-click" experience that can increase your productivity and efficiency. By resolving the risks, you can optimize your merchandising configuration and improve your product performance across your retail channels.

## Prerequisites

To be able to streamline your merchandising processes with Copilot, your Commerce system must meet the following requirements:

- Commerce version 10.0.38 with proactive quality update 5 (PQU-5) or later.
- Commerce version 10.0.39 with PQU-3 or later.
- Any build of Commerce version 10.0.40 or later.

In addition, Copilot capabilities should be enabled in finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).

## Enable Copilot-based summary and insights for merchandising data

Copilot-based summary and insights for merchandising data are viewable in Commerce headquarters on the **Channel categories and product attributes** form. To view the insights, you must first enable the **Enable Copilot based summary and insights for merchandising data** feature in the **Feature management** workspace (**Systems administration \> Workspaces \> Feature management**).

> [!NOTE]
> - The **Enable Copilot based summary and insights for merchandising data** feature isn't turned on by default in headquarters. You must enable it manually.
> - After enabling the feature, there is a delay before these insights become available because the feature activates batch jobs that recur every 24 hours that detect risks across product, category, and catalog data for a given channel.
> - To view the details of each automated run in headquarters, go to **Retail and Commerce \> Retail and Commerce IT \> Channel merchandising configuration validator**. For more information, see [Channel merchandising configuration validator](dev-itpro/channel-merch-config-validator.md).

## What Copilot-generated summaries and insights reveal about merchandising data

The summary Copilot provides enables you to understand the status of your products and other merchandising configurations across different channels, and identify and guide you to resolve any issues related to your product, category, and catalog data. To access the summary in headquarters, go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes** and select a channel from the list. A Copilot panel appears that displays the summary of insights for the selected channel.

The summary consists of four sections:
- **Channel overview**: This section displays the total number of products, categories, and catalogs in the channel.
- **Product risks**: This section displays the number and percentage of products that have some issues or risks, such as missing or inaccurate data. You can select each risk to see the list of affected products and their details.
- **Category risks**: This section displays the number and percentage of categories that have some issues or risks, such as missing or inaccurate data. You can select each risk to see the list of affected products and their details.
- **Catalog risks**: This section displays the number and percentage of catalogs that have some issues or risks, such as missing or inaccurate data. You can select each risk to see the list of affected products and their details.

Select **Review all** to be directed to a detailed view of each issue and learn about individual records that are having issues. A link is provided to fix issues for specific records, ensuring that you never lose context as you're guided to resolve the issue step-by-step. For more information about what kind of rules are being validated for your physical store and online channel merchandising data, see [Channel merchandising configuration validator](dev-itpro/channel-merch-config-validator.md).

> [!NOTE] 
> - AI-generated content may be incorrect. For more information, see [Service Agreement & Microsoft Products and Services Data Protection Addendum](https://aka.ms/BusinessApplicationLegal).
> - Enabling this feature will activate batch jobs that detect risks across your product, category and catalog data for all physical stores and online channels. These jobs run every 24 hours and update the summary with the latest insights. You can also manually trigger the jobs from the **Channel merchandising configuration validator** if you want to refresh the summary at any time. [Learn more ](dev-itpro/channel-merch-config-validator.md)

## Additional resources

[Responsible AI FAQ](responsible-ai/faqs-ai-summarization-hq.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
