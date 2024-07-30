---
title: Streamline your Merchandising Process with Copilot based insights
description: This article explains how to use Copilot proactively provides a comprehensive summary of insights for your merchandising configurations for your retail channels simplifying your merchandising workflows
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

# Streamline your Merchandising Process with Copilot based insights
This article explains how to Copilot proactively provides a comprehensive summary of insights for your merchandising configurations for your retail channels simplifying your merchandising workflows. The summary enables you to understand the status and performance of your products across different channels, as well as identify and resolve any issues related to your product, category and catalog data.

## Prerequisites

To be able to streamline your merchandising processes with Copilot, your Dynamics 365 Commerce system must meet the following requirements:

- Commerce version 10.0.38 with proactive quality update 5 (PQU-5) or later
- Commerce version 10.0.39 with PQU-3 or later
- Any build of Commerce version 10.0.40 or later

In addition, Copilot capabilities should be enabled in finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).

## Enable Copilot based summary and insights for merchandising data

Copilot based summary and insights for merchandising data are viewable on **Channel categories and product attributes** form and to view that, enable the **Enable Copilot based summary and insights for merchandising data** feature in the **Feature management** workspace in Commerce headquarters.

> [!NOTE]
> The **Enable Copilot based summary and insights for merchandising data** features are not on by default in headquarters.
>
> And upon enabling this feature, it would take a while before these insights would become available, as it will activate batch jobs recurring every 24-hours detecting risks across product, category and catalog data for a given channel.
>
> You can view these details of each automated run by navigating to **Channel merchandising configuration validator**. [Learn more](./articles/commerce/dev-itpro/channel-merch-config-validator.md).

## Overview 

Merchandising is a complex and time-consuming process that involves configuring various aspects of products, categories, catalogs, and attributes for each channel. Merchandisers need to ensure that their products are displayed correctly and accurately on the online store, and that they comply with the business rules and policies of each channel. However, manual validation of these configurations is prone to human errors, and can result in misconfigured products that affect customer experience and sales. Moreover, manual validation is not scalable for large-scale businesses that have millions of products, thousands of attributes, and hundreds of categories and catalogs across hundreds of stores.

With Copilot, you can enhance your merchandiser efficiency by streamlining your merchandising workflows. Copilot can offer a clear summary of your product settings, such as variant groups, dimension groups, attribute groups, and category hierarchies. Copilot can also automate data validation, by checking for errors, inconsistencies, and duplicates in your product data. Copilot can also provide a Risk Preview, by showing you the potential issues that might arise from your product configuration, such as out-of-stock, price misconfigurations, and catalog mismatches.

By using the summary of merchandising configuration risks, you can significantly reduce the number of clicks and searches needed to access and update your product data. Copilot provides you with a proactive insightful summary that shows you the most important and relevant information at a glance. You can easily navigate to the list of issues and take action, without losing context. Compared to the traditional way of managing your product data, which would require over numerous clicks and multiple searches across various forms, Copilot offers you a "One-Click" experience that elevates your productivity and efficiency. By resolving the risks, you can optimize your merchandising configuration and improve your product performance across your retail channels.

# What do the Copilot-generated summaries and insights reveal about Merchandising data?

The summary provided by Copilot enables you to understand the status of your products and other merchandising configurations across different channels, as well as identify and guide you to resolve any issues related to your product, category and catalog data. To access the summary, navigate to the Channel Categories and Product Attributes dialog and select a channel from the list. You will see a Copilot panel, which will display the summary of insights for the selected channel.

The summary consists of four sections:
- **Channel overview**: This section displays the total number of products, categories and catalogs in the channel.
- **Product risks**: This section displays the number and percentage of products that have some issues or risks, such as missing or inaccurate data. You can click on each risk to see the list of affected products and their details.
- **Category risks**: This section displays the number and percentage of categories that have some issues or risks, such as missing or inaccurate data. You can click on each risk to see the list of affected products and their details.
- **Catalog risks**: This section displays the number and percentage of catalogs that have some issues or risks, such as missing or inaccurate data. You can click on each risk to see the list of affected products and their details.

Click on "Review all" to be directed to detailed view of each issue and learn about individual records that are having issue with a deep-link to fix those issues to specific record, ensuring you never lose context and it guides you to resolve the issue in every step. Learn more about what kind of rules being validated for your merchandising data for physical stores and online channels by [Channel merchandising configuration validator](./articles/commerce/dev-itpro/channel-merch-config-validator.md)

> [!Note] 
> AI-generated maybe incorrect. [Learn more](https://aka.ms/BusinessApplicationLegal)
>
> View [Responsible AI FAQ](./articles/commerce/responsible-ai/faqs-ai-summarization-hq.md)
>
>Enabling this feature will activate batch jobs that detect risks across your product, category and catalog data for all physical stores and online channels. These jobs run every 24 hours and update the summary with the latest insights. You can also manually trigger the jobs from the **Channel merchandising configuration validator** if you want to refresh the summary at any time. [Learn more ](./articles/commerce/dev-itpro/channel-merch-config-validator.md)
>



