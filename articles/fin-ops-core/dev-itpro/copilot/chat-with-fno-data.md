---
title: Chat with finance and operations data (preview)
description: Learn how to configure finance and operations data as knowledge sources to enable chat experiences with your enterprise data
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/24/2024

---

# Chat with finance and operations data (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Microsoft copilot platform enables you to chat with your finance and operations data, enabling users to ask questions of copilot that are answered by the structured finance and operations data to which the user has access. This is done in Copilot Studio by adding finance and operations data as knowledge sources to your copilots, giving you the flexibility to add the right knowledge for your desired copilot experiences. See [Knowledge sources overview](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-copilot-studio) for more information

## Adding knowledge sources to your copilots
You can add your finance and operations structured data as a knowledge source in many different copilot experiences. For example, a Dataverse table can be configured as a knowledge source for a copilot to provide relevant information and insights to the end user in the targeted copilot experience. You can synchronize your finance and operations data to Dataverse using a data sync utility like [dual-write](../data-entities/dual-write/dual-write-overview.md), and have the data available for Q&A as a knowledge source from the Dataverse table. The table can be added to Copilot for finance and operations apps, custom agents, Microsoft 365 copilot, or other copilots that support knowledge sources.

> [!NOTE]
> [Virtual entities for finance and operations apps](../power-platform/virtual-entities-overview.md) are not currently supported for configuration as knowledge sources in Copilot Studio. 

### Add knowledge to Copilot for finance and operations apps or custom agents
Extending Copilot for finance and operations apps with knowledge sources enables users of the in-app sidecar chat to ask questions about the structured data within the context of the application. You can add this same experience to your custom agents by adding the finance and operations data as a knowledge source to the agent in Copilot Studio. See [Add a Dataverse knowledge source](https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-dataverse) for more information on how to add the knowledge source to these agents.

### Extend Microsoft 365 Copilot with finance and operations data
Microsoft 365 Copilot is the default experience for engaging with content and resources across your organization. You can extend this experience by adding finance and operations data as a knowledge source, enabling users to ask questions about the ERP data directly from Microsoft 365 Copilot. This is done by adding a creating a new declarative agent. In this agent you add all the actions and knowledge you want to have available to users of the agent, and publish the agent to Microsoft 365 Copilot.

See [Extend Microsoft 365 Copilot with Copilot agents](https://learn.microsoft.com/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extension) for more information on creating and publishing declarative agents to extend Microsoft 365 Copilot, including [adding knowledge to the agent](https://learn.microsoft.com/microsoft-copilot-studio/microsoft-copilot-extend-copilot-extensions#add-knowledge-to-a-copilot-agent).
