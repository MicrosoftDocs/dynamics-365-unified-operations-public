---
title: Responsible AI FAQ for the Confirmed purchase orders with changes workspace
description: Access answers to frequently asked questions about the AI technology that's used in the Confirmed purchase orders with changes workspace.
author: cabeln
ms.author: cabeln
ms.topic: article
ms.date: 11/16/2023
ms.custom:
  - responsible-ai-faqs
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
---

# Responsible AI FAQ for the Confirmed purchase orders with changes workspace

[!include [banner](../includes/banner.md)]

This Responsible AI FAQ provides answers to frequently asked questions about the AI technology that's used in the **Confirmed purchase orders with changes** workspace in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.

## What is the Confirmed purchase orders with changes workspace?

The **Confirmed purchase orders with changes** workspace helps procurement professional quickly and easily assess, manage, and follow up on changes that are made to purchase orders after they're confirmed. It uses [Copilot](/power-platform/transparency-note-copilot-data-security-privacy) to generate natural-language change summaries and draft communications for vendors.

## What are capabilities of the Confirmed purchase orders with changes workspace?

The feature takes changes to confirmed purchase orders as input and then identifies the downstream orders that are related to those purchase orders. The feature uses Copilot to generate natural-language summaries and draft communications for vendors. Copilot uses the *gpt-3.5-turbo* generative AI model to generate the natural-language content. Summaries and content are generated from data records stored in the system, including products, purchase orders, and vendors.

## What is the intended use of the Confirmed purchase orders with changes workspace?

The **Confirmed purchase orders with changes** workspace is intended to help procurement professional review changes to confirmed purchase orders and mitigate the downstream impacts. It supports a workflow where the purchaser first reviews and reconfirms changed purchase orders that have little or no downstream impact. It then provides tools to help the purchaser assess and mitigate the impact of changes that have significant downstream impact.

Messaging text that Copilot generates isn't intended to be used without manual review or supervision.

## How was the Confirmed purchase orders with changes workspace evaluated? What metrics are used to measure performance?

The **Confirmed purchase orders with changes** workspace underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report). Your feedback helps improve the functionality.

Microsoft might disable the Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of the Confirmed purchase orders with changes workspace? How can users minimize the impact of its limitations when they use it?

The **Confirmed purchase orders with changes** workspace uses Copilot to generate a summary of impact and proposed communication content.

The generated content should never be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of the Confirmed purchase orders with changes workspace?

When you use the feature, follow these recommendations:

- Make sure that your company has sufficient control over data permissions to ensure that business data can't be manipulated to influence AI data processing in an undesirable way.
- Always review generated summaries, and study the detailed lists of changes and impacts, before you make decisions about reconfirming purchase orders.
- Always review generated communication drafts before you send them by email or post them to a Teams message.

## Related information

- [Review and accept changes to confirmed purchase orders](procurement/purchase-order-changes-after-confirmation.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
