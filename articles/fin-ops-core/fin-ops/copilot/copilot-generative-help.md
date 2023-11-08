---
# required metadata

title: Copilot for generative help and guidance
description: This article provides information on Copilot for generative help and guidance in the finance and operations platform
author: cabeln
ms.date: 11/07/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EventCreateRule
# ROBOTS:
audience: Application user
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: richdi
ms.search.validFrom: 2023-11-15
ms.dyn365.ops.version: Platform update 62
---

# Microsoft Copilot for Dynamics 365 finance and operations: Overview and Functional Mechanism

> [!IMPORTANT]
> The Microsoft Copilot functionality in this article is available as part of a preview release. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> To learn about the capabilities and limitations of AI-powered and Copilot features see [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md).

## Overview

Microsoft Copilot in Dynamics 365 finance and operations apps provides users with access to AI capabilities augmenting the application experiences and functionality. 

Copilot will bring a growing set of skills that help user in different aspects of there tasks and can appear in different user experiences:

1. **Sidecar**: The Copilot sits alongside the application as a *sidecar* user experience for conversational support to the user. This  is the primary Copilot interface in finance and operations apps. It provides a natural language chat experience throughout finance and operations apps as a helper with the applicatin functionality and data.
1. **Embedded**: These are built into the application as intelligent capabilities on the form, bringing AI to the center of the applicatino experience. For example, the [Confirmed purchase orders with changes](../../../supply-chain/procurement/purchase-order-changes-after-confirmation#the-confirmed-purchase-orders-with-changes-workspace) workspace has AI capabilities built into the page to assist in understanding and reacting to changes in confirmed purchase orders.
1. **Outside**: Agents help orchestrate across apps and tasks. For example, users can ask questions about finance and operations data in Microsoft 365 Copilot. See [FAQ for finance and operations data on Microsoft 365 Copilot (Preview)](../../dev-itpro/m365-copilot/faq-for-chat-with-fno-data-on-m365copilot) for more information.


### Copilot skill for generative help and guidance 

The Copilot skill for in-app help guidance leverages the power of generative AI to provide users with contextual support, directly accessing the breadth of public documentation to offer precise assistance and streamline the navigation of Finance and Operations extensive capabilities.

![Copilot help pane in the user experience](./media/copilot-homepage%20-explain-worflow.png)

### How Copilot works for in-app help and guidance

Copilot transforms the support experience by introducing a conversational Sidecar experience where users can input their questions or express their needs directly within D365 FnO. The system is adept at understanding the context of user queries and provides relevant, tailored information to aid in task completion. Future enhancements are expected to expand their capabilities to include direct navigation and proactive action suggestions.

### Grounding in public documentation

The Copilot skill is deeply rooted in the official public documentation for D365 FnO. This grounding ensures that the AI has a comprehensive understanding of the system and can generate responses that are not only accurate but also aligned with the latest features and best practices established by Microsoft.
Powered by Generative AI
Employing state-of-the-art generative AI, Copilot dynamically interprets user inquiries and crafts responses in real-time. This process involves a sophisticated mechanism where the AI first rephrases the user's question for clarity, searches the indexed public documentation, and then synthesizes the information into a coherent, actionable answer.

### Process for generating guidance with large language models

The workflow of generating a response through Copilot can be broken down as follows:
1.	Query Rewrite: Copilot reformulates the user's initial question to optimize understanding and search efficacy.
1.	Document Search: Leveraging the Bing search index, it locates the most pertinent documents on the learn.microsoft.com domain.
1.	Response Generation: With the relevant documentation at hand, Copilot engages with a large language model to construct a comprehensive answer, including citations from the source material.

## Responsible AI

Microsoft is committed to responsible AI practices with Copilot, ensuring user privacy with stringent data protection measures and overseeing content generation to maintain relevance and safety.


In conclusion, Copilot stands as a pivotal enhancement to the D365 FnO experience, marrying the complexity of supply chain management with the simplicity of AI-powered assistance, ultimately fostering a more productive and cost-efficient environment for users.

## See also
-  [For Adminstrators: How to enable *Copilpot for Dynamics 365 finance and operations*](../../dev-itpro/copilot/enable-copilot.md)
- [Responsible AI FAQ for *Copilpot for Dynamics 365 finance and operations*](copilot-generative-help-rai-faq.md)
