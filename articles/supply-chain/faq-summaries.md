---
title: Responsible AI FAQ for AI summaries with Copilot
description: Access answers to frequently asked questions about the AI technology that's used in AI summaries with Microsoft Copilot in Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/06/2024
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
---

# Responsible AI FAQ for AI summaries with Copilot

[!include [banner](../includes/banner.md)]

This FAQ provides answers to frequently asked questions about the AI technology that's used in AI summaries with Microsoft Copilot in Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What are AI summaries with Copilot?

AI summaries with Copilot are available on many of the most-used pages in Supply Chain Management. These summaries provide a quick overview of the most important information that's related to the page, personalized for the current user. Summaries can include information such as the number of lines on a purchase order, the number of items in a warehouse, or the number of overdue invoices for a vendor.

The information that Copilot provides depends on the current page and user context. For example, the information can vary based on the other pages that the user works with the most, and it's limited based on the user's security roles and permissions.

## What are the capabilities of AI summaries with Copilot?

AI summaries with Copilot use Copilot to generate natural-language summaries of information that's available on the pages where they appear and other related pages. Copilot uses the *gpt-3.5-turbo* generative AI model to generate the natural-language content. Summaries and content are generated from data records that are stored in the system, including products, purchase orders, and vendors.

## What is the intended use of AI summaries with Copilot?

This section describes the intended use for each of the available summaries.

### Warehouse Management mobile app insights

Warehouse Management mobile app insights give workers information about the number of lines that must be picked as open work, the number of workers who are online at the warehouse, and the type of work that must be picked. Learn more in [Workload insights with Copilot in the Warehouse Management mobile app](warehousing/warehouse-management-mobile-app-insights.md).

### Product hover and released product summaries

Many different people need product information, including sellers, planners, and purchasers. Unlike product information managers, people who work in these roles often lack deep knowledge of each product and where all its information can be found in the system. Product summaries provide high-level information about what each product is, its availability, and its purchase and sale information.

### Purchase order summaries

Each purchase order summary shows an overview of a selected purchase order's status. For example, it can show the number of partially or fully confirmed, received, and invoiced lines. It can also show other selected insights, such as a summary of lines that are overdue or nearly overdue. Each summary helps focus users' attention on the most important or unusual things about an order.

### Sales order summaries

Sales order summaries are similar to purchase order summaries, but for sales orders.

### Vendor summaries

Intelligent vendor summaries include information about vendor on-hold status, active contracts, rebates, open purchase orders, outliers, and risks. Each summary indicates the vendor's account number, vendor currency, and accounting currency. Purchase orders, posted vendor invoices, and payment status information are provided. Overdue vendor invoices, purchasing agreements, and active rebates are also shown. Risks arise from overdue purchase lines, delivery trends, vendor history, and potential foreign exchange losses from outstanding invoices.

## How were AI summaries with Copilot evaluated? What metrics are used to measure performance?

AI summaries with Copilot underwent substantial testing before they were released. They rely on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of AI summaries with Copilot? How can users minimize the impact of these limitations?

AI summaries with Copilot use Copilot to generate summaries of information on the page where they appear and other related pages. Not all pages are used.

The generated content should never be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of AI summaries with Copilot?

When you use the feature, follow these recommendations:

- Make sure that your company has enough control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- Always review the generated summaries before you make decisions based on the information that's provided.

## Related information

- [AI summaries with Copilot](get-started/copilot-summaries-overview.md)
- [Workload insights with Copilot in the Warehouse Management mobile app](warehousing/warehouse-management-mobile-app-insights.md)
- [Responsible AI FAQ for Workload insights with Copilot](faq-wma-copilot.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
