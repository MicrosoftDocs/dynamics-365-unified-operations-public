---
title: Microsoft Copilot for finance and operations apps overview (preview)
description: This article provides information about Microsoft Copilot for finance and operations apps and explains how to use it.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 11/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Microsoft Copilot for finance and operations apps overview (preview)

[!include [banner](../includes/banner.md)]
[This article is prerelease documentation and is subject to change.]

Microsoft Copilot for finance and operations apps gives users access to AI capabilities that augment the application experiences and functionality.

Copilot brings a growing set of skills that help users complete various tasks. It can appear in many different user experiences. Here are some examples:

- **Sidecar** – The Copilot sits alongside the application as a *sidecar* and provides conversational support to the user. The sidecar is the primary Copilot interface in finance and operations apps. It provides a natural language chat experience that helps users work with application functionality and data.
- **Embedded** – These Copilot features add intelligent capabilities to the application itself. In this way, they bring AI to the center of the application experience. For example, in the [Confirmed purchase orders with changes workspace](../../../supply-chain/procurement/purchase-order-changes-after-confirmation.md), AI capabilities that are built into the page help users understand and react to changes in confirmed purchase orders.
- **Outside** – External agents help orchestrate across different apps and tasks. For example, users can use Copilot to ask questions about finance and operations data. For more information, see [FAQ for finance and operations data on Microsoft 365 Copilot (Preview)](../../dev-itpro/m365-copilot/faq-for-chat-with-fno-data-on-m365copilot.md).

> [!IMPORTANT]
>
> - The Microsoft Copilot functionality that's described in this article is a preview feature.
> - Preview features aren't meant for production use and may have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.
> - For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
> - To learn about the capabilities and limitations of AI-powered and Copilot features, see [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md).

## Generative help and guidance

The Copilot skill for in-app help guidance uses the power of generative AI to provide contextual support to users. Copilot accesses the full range of public documentation to offer precise assistance and streamline the navigation though the extensive capabilities of finance and operations apps.

[<img src="media/copilot-homepage-explain-worflow.png" alt="Copilot help pane in the user experience." title="Copilot help pane in the user experience" width="720" />](media/copilot-homepage-explain-worflow.png#lightbox)

## How Copilot works for in-app help and guidance

Copilot transforms the support experience by introducing a conversational sidecar in finance and operations apps. Therefore, users can enter questions or express their needs directly in the app. The system is effective at interpreting the context of user queries, and provides relevant, tailored information to help with task completion. Future enhancements are expected to expand the system's capabilities so that they include direct navigation and proactive action suggestions.

## Grounded in public documentation

Copilot in-app help guidance is deeply grounded in the official public documentation for Microsoft finance and operations apps. This grounding ensures that the AI has a comprehensive understanding of the system and can generate responses that are not only accurate but also aligned with the latest features and best practices that Microsoft has established.

## Powered by generative AI

Copilot uses state-of-the-art generative AI to dynamically interpret user inquiries and compose responses in real time. This process involves a sophisticated mechanism where the AI first rephrases the user's question for clarity, then searches the indexed public documentation, and finally synthesizes the information into a coherent, actionable answer.

## Process for generating guidance with large language models

The workflow for generating a response through Copilot can be broken down into the following steps.

1. **Query rewrite** – Copilot reformulates the initial question to optimize understanding and search efficacy.
1. **Document search** – Copilot uses the Bing search index to find the most relevant documents in the learn.microsoft.com domain.
1. **Response generation** – After it has the relevant documentation, Copilot uses a large language model to construct a comprehensive answer that includes citations from the source material.

## Responsible AI

Microsoft is committed to applying [responsible AI practices](../../dev-itpro/responsible-ai/responsible-ai-overview.md) with Copilot. We ensure user privacy through stringent data protection measures and oversee content generation to maintain relevance and safety.

## See also

- For administrators: [Enable Microsoft Copilot for finance and operations apps](../../dev-itpro/copilot/enable-copilot.md)
- [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md)
