---
title: Transparency notes for the Confirmed purchase orders with changes workspace
description: This transparency note provides information about the AI technology that's used in the Confirmed purchase orders with changes workspace in Microsoft Dynamics 365 Supply Chain Management. It includes key considerations and details about how the AI is used, how it was tested and evaluated, and any specific limitations.
ms.date: 06/19/2023
ms.custom: 
  - transparency-note
ms.topic: article
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
---

# Transparency notes for the Confirmed purchase orders with changes workspace

This transparency note describes the AI impact of the **Confirmed purchase orders with changes** workspace in Microsoft Dynamics 365 Supply Chain Management.

## What is the Confirmed purchase orders with changes workspace?

The **Confirmed purchase orders with changes** workspace helps procurement professional quickly and easily assess, manage, and follow up on changes that are made to purchase orders after they're confirmed. It uses [Dynamics 365 Copilot](/power-platform/transparency-note-copilot-data-security-privacy) to generate natural-language change summaries and draft communications for vendors.

This feature is part of the *Procurement with Copilot* feature set, which is a growing collection of features that use AI to help procurement managers with their daily procurement tasks.

## What are the system's capabilities?

The system takes changes to confirmed purchase orders as input and then identifies the downstream orders that are related to those purchase orders. The feature uses Copilot to generate natural-language summaries and draft communications for vendors. Copilot uses the *Text-davinci-003* generative AI model to generate the natural-language content.

## What is the system's intended use?

The **Confirmed purchase orders with changes** workspace is intended to help procurement professional review changes to confirmed purchase orders and mitigate the downstream impacts. It supports a workflow where the purchaser first reviews and reconfirms changed purchase orders that have little or no downstream impact. It then provides tools to help the purchaser assess and mitigate the impact of changes that have significant downstream impact.

Messaging text that Copilot generates isn't intended to be used without manual review or supervision.

## How was the feature evaluated? What metrics are used to measure performance?

The **Confirmed purchase orders with changes** workspace underwent substantial testing before it was released. It relies on user feedback to report inappropriate content.

If you encounter inappropriate generated content, report it to Microsoft by using this feedback form: [Report abuse](https://msrc.microsoft.com/report/abuse?ThreatType=URL&IncidentType=Responsible%20AI&SourceUrl=https://dynamics.microsoft.com/supply-chain-management/overview/). Your feedback helps improve the functionality.

Microsoft might disable the Copilot-driven features for selected customers if abuse of the functionality is detected.

## What are the limitations of the feature? How can users minimize the impact of its limitations when they use the system?

The **Confirmed purchase orders with changes** workspace uses Copilot to generate a summary of impact and proposed communication content.

The generated content should never be used without manual review or supervision.

## What operational factors and settings allow for effective and responsible use of the system?

When you use the feature, follow these recommendations:

- Always review generated summaries, and study the detailed lists of changes and impacts, before you make decisions about reconfirming purchase orders.
- Always review generated communication drafts before you send them by email or post them to a Teams message.

## See also

- [Review and accept changes to confirmed purchase orders](procurement/purchase-order-changes-after-confirmation.md)
- [Transparency note for Copilot data security and privacy in Microsoft Power Platform](/power-platform/transparency-note-copilot-data-security-privacy)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
