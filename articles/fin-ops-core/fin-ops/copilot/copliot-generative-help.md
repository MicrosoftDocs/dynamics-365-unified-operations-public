---
title: Generative help and guidance with Copilot (preview)
description: Copilot provides in-app help and guidance that uses the power of generative AI to give contextual support to users. This article provides information about this feature, its prerequisites, and how it works.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 12/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Generative help and guidance with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

Copilot provides in-app help and guidance that uses the power of generative AI to give contextual support to users. Copilot accesses the full range of public documentation to offer precise assistance and streamline the navigation though the extensive capabilities of finance and operations apps.

[<img src="media/copilot-homepage-explain-worflow.png" alt="Screenshot of the Copilot help pane in the user experience." title="Screenshot of the Copilot help pane in the user experience" width="720" />](media/copilot-homepage-explain-worflow.png#lightbox)

[!INCLUDE [preview-note](../../../supply-chain/includes/preview-note.md)]

## Prerequisites

Before you can use generative help and guidance with Copilot in finance and operations apps, the feature and its prerequisites must be installed and enabled on your system, as described in [Enable generative help and guidance with Copilot](../../dev-itpro/copilot/enable-copliot-generative-help.md).

## How Copilot works for in-app help and guidance

Copilot transforms the support experience by introducing a conversational sidecar in finance and operations apps. Therefore, users can enter questions or express their needs directly in the app. The system is effective at interpreting the context of user queries, and provides relevant, tailored information to help with task completion. Future enhancements are expected to expand the system's capabilities so that they include direct navigation and proactive action suggestions.

## Grounded in public documentation

Copilot in-app help and guidance is deeply grounded in the official public documentation for Microsoft finance and operations apps. This grounding ensures that the AI has a comprehensive understanding of the system and can generate responses that are not only accurate but also aligned with the latest features and best practices that Microsoft has established.

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

- For administrators: [Enable generative help and guidance with Copilot](../../dev-itpro/copilot/enable-copliot-generative-help.md)
- [Responsible AI FAQ for Generative help and guidance with Copilot](faq-copilot-generative-help.md)
