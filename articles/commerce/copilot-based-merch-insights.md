---
title: Streamline your merchandising process with Copilot-based insights
description: This article explains how to use Microsoft Copilot to proactively provide a comprehensive summary of insights for the merchandising configurations of your retail channels to simplify your merchandising workflows in Dynamics 365 Commerce.
author: ashishmsft
ms.date: 08/01/2024
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

This article explains how to use Microsoft Copilot to proactively get a comprehensive summary of insights for the merchandising configurations of your retail channels. You can use this summary of insights to simplify your merchandising workflows in Dynamics 365 Commerce. The summary helps you understand the status and performance of your products across different channels. It also helps you identify and fix any issues that are related to your product, category, and catalog data.


## Enhance merchandiser efficiency by streamlining merchandising workflows

Merchandising is a complex and time-consuming process that involves configuring various aspects of products, categories, catalogs, and attributes for each channel. Merchandisers must ensure that their products are shown correctly and accurately in the online store, and that they comply with the business rules and policies of each channel. However, manual validation of these configurations is prone to human error and can result in misconfigured products that affect the customer experience and sales. In addition, manual validation isn't scalable for large-scale businesses that have millions of products, thousands of attributes, and hundreds of categories and catalogs across hundreds of stores.

With Copilot, you can enhance your merchandiser efficiency by streamlining your merchandising workflows. Copilot can offer a clear summary of your product settings, such as variant groups, dimension groups, attribute groups, and category hierarchies. It can also automate data validation by checking for errors, inconsistencies, and duplicates in your product data. In addition, Copilot can provide a risk preview by showing potential issues that might arise from your product configuration, such as out-of-stock issues, price misconfigurations, and catalog mismatches.

By using the summary of merchandising configuration risks, you can significantly reduce the number of clicks and searches that are needed to access and update your product data. Copilot provides a proactive insightful summary that shows the most important and relevant information at a glance. You can easily go to the list of issues and take action without losing context. Unlike the traditional method of product data management, which requires numerous clicks and multiple searches across various forms, Copilot offers a "one-click" experience that can increase your productivity and efficiency. By resolving the risks, you can optimize your merchandising configuration and improve product performance across your retail channels.

## Prerequisites

Before you can streamline your merchandising processes by using Copilot, your Commerce system must meet the following requirements:

- Commerce version 10.0.38 with proactive quality update 5 (PQU-5) or later
- Commerce version 10.0.39 with PQU-3 or later
- Any build of Commerce version 10.0.40 or later

In addition, Copilot capabilities should be enabled in finance and operations apps. Learn more in [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).

## Enable Copilot-based summary and insights for merchandising data

You can view Copilot-based summary and insights for merchandising data in Commerce headquarters on the **Channel categories and product attributes** page. Before you can view the insights, you must enable the **Enable Copilot based summary and insights for merchandising data** feature in the **Feature management** workspace (**Systems administration** \> **Workspaces** \> **Feature management**).

> [!NOTE]
> - The **Enable Copilot based summary and insights for merchandising data** feature isn't turned on by default in headquarters. You must manually enable it.
> - When the feature is enabled, it activates batch jobs that detect risks across product, category, and catalog data for a given channel. These jobs recur every 24 hours. Therefore, after you enable the feature, there is a delay before the insights become available.
> - To view the details of each automated run in headquarters, go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Channel merchandising configuration validator**. Learn more in [Channel merchandising configuration validator](dev-itpro/channel-merch-config-validator.md).

## What Copilot-generated summaries and insights reveal about merchandising data

The summary that Copilot provides helps you understand the status of your products and other merchandising configurations across different channels. They also identify and guide you to resolve any issues that are related to your product, category, and catalog data. To access the summary in headquarters, go to **Retail and Commerce** \> **Channel setup** \> **Channel categories and product attributes**, and select a channel in the list. A Copilot panel appears and shows the summary of insights for the selected channel.

The summary consists of four sections:

- **Channel overview**: This section shows the total number of products, categories, and catalogs in the channel.
- **Product risks**: This section shows the number and percentage of products that have some issues or risks, such as missing or inaccurate data. You can select each risk to view the list of affected products and their details.
- **Category risks**: This section shows the number and percentage of categories that have some issues or risks, such as missing or inaccurate data. You can select each risk to view the list of affected products and their details.
- **Catalog risks**: This section shows the number and percentage of catalogs that have some issues or risks, such as missing or inaccurate data. You can select each risk to view the list of affected products and their details.

Select **Review all** to go to a detailed view of each issue and learn about individual records that have issues. A link is provided that you can use to fix issues for specific records. This functionality ensures that you never lose context as you're guided step by step to fix the issue. Learn more about the types of rules that are validated for your physical store and online channel merchandising data in [Channel merchandising configuration validator](dev-itpro/channel-merch-config-validator.md).

> [!NOTE]
> - AI-generated content might be incorrect. Learn more in [Service Agreement & Microsoft Products and Services Data Protection Addendum](https://aka.ms/BusinessApplicationLegal).
> - When the feature is enabled, it activates batch jobs that detect risks across your product, category, and catalog data for all physical stores and online channels. These jobs recur every 24 hours and update the summary with the latest insights. You can also manually trigger the jobs from the **channel merchandising configuration validator** at any time if you want to update the summary. [Learn more](dev-itpro/channel-merch-config-validator.md).

## Additional resources

[FAQ for Copilot AI summarization in Commerce headquarters](responsible-ai/faqs-ai-summarization-hq.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
