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

# Microsoft Copilot for Dynamics 365 Finance and Operations: Overview and Functional Mechanism

## Overview

Microsoft Copilot revolutionizes the user experience within Dynamics 365 Finance and Operations (FnO) by integrating an in-app help guidance feature that leverages the power of generative AI. This intelligent functionality is designed to provide users with contextual support, directly accessing the breadth of public documentation to offer precise assistance and streamline the navigation of Finance and Operations extensive capabilities.

## How Copilot Works for In-App Help Guidance

Copilot transforms the support experience by introducing a conversational Sidecar experience where users can input their questions or express their needs directly within D365 FnO. The system is adept at understanding the context of user queries and provides relevant, tailored information to aid in task completion. Future enhancements are expected to expand their capabilities to include direct navigation and proactive action suggestions.

## Grounding in Public Documentation

The Copilot skill is deeply rooted in the official public documentation for D365 FnO. This grounding ensures that the AI has a comprehensive understanding of the system and can generate responses that are not only accurate but also aligned with the latest features and best practices established by Microsoft.
Powered by Generative AI
Employing state-of-the-art generative AI, Copilot dynamically interprets user inquiries and crafts responses in real-time. This process involves a sophisticated mechanism where the AI first rephrases the user's question for clarity, searches the indexed public documentation, and then synthesizes the information into a coherent, actionable answer.

## Technical Process Details

The workflow of generating a response through Copilot can be broken down as follows:
1.	Query Rewrite: Copilot reformulates the user's initial question to optimize understanding and search efficacy.
1.	Document Search: Leveraging the Bing search index, it locates the most pertinent documents on the learn.microsoft.com domain.
1.	Response Generation: With the relevant documentation at hand, Copilot engages with GPT to construct a comprehensive answer, including citations from the source material.

## Responsible AI

Microsoft is committed to responsible AI practices with Copilot, ensuring user privacy with stringent data protection measures and overseeing content generation to maintain relevance and safety.


In conclusion, Copilot stands as a pivotal enhancement to the D365 FnO experience, marrying the complexity of supply chain management with the simplicity of AI-powered assistance, ultimately fostering a more productive and cost-efficient environment for users.

## See also

- [Responsible AI FAQ for the Confirmed purchase orders with changes workspace](copilot-generative-help-rai-faq.md)
