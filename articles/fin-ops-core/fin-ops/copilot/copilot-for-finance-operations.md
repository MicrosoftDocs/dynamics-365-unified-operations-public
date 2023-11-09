---
title: Microsoft Copilot for finance and operations apps (Preview)
description: This article provides information about Microsoft Copilot for finance and operations apps and how to use it.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Microsoft Copilot for finance and operations apps (Preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

> [!IMPORTANT]
> The Microsoft Copilot functionality in this article is available as part of a preview release. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> To learn about the capabilities and limitations of AI-powered and Copilot features see [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md).

Microsoft Copilot in Dynamics 365 finance and operations apps provides users with access to AI capabilities that augment the application experiences and functionality.

Copilot brings a growing set of skills that help users complete various tasks. It can appear in many different user experiences, including:

1. **Sidecar** – The Copilot sits alongside the application as a *sidecar*, providing conversational support to the user. This is the primary Copilot interface in finance and operations apps. It provides a natural language chat experience that helps users work with application functionality and data.
1. **Embedded** – These Copilot features add intelligent capabilities to the application itself, bringing AI to the center of the application experience. An example of this type of functionality is the [Confirmed purchase orders with changes workspace](../../../supply-chain/procurement/purchase-order-changes-after-confirmation.md), which has AI capabilities built into the page to assist in understanding and reacting to changes in confirmed purchase orders.
1. **Outside** – External agents help orchestrate across various different apps and tasks. For example, users can use Copilot to ask questions about finance and operations data. see also [FAQ for finance and operations data on Microsoft 365 Copilot (Preview)](../../dev-itpro/m365-copilot/faq-for-chat-with-fno-data-on-m365copilot.md).

## Generative help and guidance

The Copilot skill for in-app help guidance leverages the power of generative AI to provide users with contextual support. Copilot accesses the full breadth of public documentation to offer precise assistance and streamline the navigation though the extensive capabilities of finance and operations apps.

![<img src="media/copilot-homepage-explain-worflow.png" alt="Copilot help pane in the user experience." title="Copilot help pane in the user experience" width="720" />](media/copilot-homepage-explain-worflow.png#lightbox "Copilot help pane in the user experience")

## How Copilot works for in-app help and guidance

Copilot transforms the support experience by introducing a conversational *sidecar*, where users can enter questions or express their needs directly within a finance and operations app. The system is adept at understanding the context of user queries and provides relevant, tailored information to aid in task completion. Future enhancements are expected to expand the system's capabilities to include direct navigation and proactive action suggestions.

## Grounded in public documentation

Copilot in-app help guidance is deeply rooted in the official public documentation for Microsoft finance and operations apps. This grounding ensures that the AI has a comprehensive understanding of the system and can generate responses that are not only accurate but also aligned with the latest features and best practices established by Microsoft.

## Powered by generative AI

Employing state-of-the-art generative AI, Copilot dynamically interprets user inquiries and crafts responses in real-time. This process involves a sophisticated mechanism where the AI first rephrases the user's question for clarity, then searches the indexed public documentation, and finally synthesizes the information into a coherent, actionable answer.

## Process for generating guidance with large language models

The workflow of generating a response through Copilot can be broken down as follows:

1. **Query Rewrite** – Copilot reformulates the initial question to optimize understanding and search efficacy.
1. **Document Search** – Copilot leverages the Bing search index to locate the most pertinent documents on the learn.microsoft.com domain.
1. **Response Generation** – With the relevant documentation at hand, Copilot engages with a large language model to construct a comprehensive answer, including citations from the source material.

## Responsible AI

Microsoft is committed to applying [responsible AI practices](../../dev-itpro/responsible-ai/responsible-ai-overview.md) with Copilot, ensuring user privacy with stringent data protection measures and overseeing content generation to maintain relevance and safety.

## See also

- For Administrators: [Enable Microsoft Copilot for finance and operations apps](../../dev-itpro/copilot/enable-copilot.md)
- [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md)
