---
title: Add knowledge to generative help and guidance with Copilot
description: Learn how to add custom knowledge to generative help and guidance with Copilot to support users through additional information.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.reviewer: kamaybac
ms.search.form:
ms.date: 08/06/2024
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# Add knowledge to generative help and guidance with Copilot

Microsoft Copilot uses *knowledge sources* as the basis for the information that it provides to users. Copilot capabilities in finance and operations apps include the out-of-box *conversational boosting* topic. This topic uses [generative answers in Copilot Studio](/microsoft-copilot-studio/nlu-boost-conversations) to answer user questions based on information from the knowledge sources that were added to it.

You can extend Copilot's knowledge by adding new knowledge to it in Copilot Studio. For example, you can add individual document files (in file formats such as PDF, RTF, or Word) or link to other information sources (such as SharePoint).

> [!NOTE]
> By default, Copilot knowledge is limited to the published product documentation for finance and operations apps. It also considers the language preferences that each user selected.
>
> The out-of-box *conversational boosting* topic assumes that all information in its knowledge sources is related to the use of product functionality. If you add unrelated knowledge, the responses that Copilot generates might imply that the added knowledge is related to the use of finance and operations apps.

## Add specific knowledge

You can add specific knowledge by using [AI general knowledge](/microsoft-copilot-studio/nlu-ai-general-knowledge) to add custom knowledge sources to generative help and guidance with Copilot.

> [!IMPORTANT]
> Dataverse virtual entities that are published from finance and operations apps aren't currently supported as knowledge sources.

To add specific knowledge to Copilot, follow these steps.

1. Open [Copilot Studio](https://copilotstudio.microsoft.com/), and select the Dataverse environment that is associated with your finance and operations apps environment.
1. On the navigation pane on the left, select **Copilots**.
1. Open the copilot that is named *Copilot for finance and operations apps*.
1. On the **Knowledge** tab, select **Add knowledge**, and then select the type of knowledge source that you want to add. For example, select **Files** to [upload files](/microsoft-copilot-studio/nlu-documents) from your local computer as additional knowledge.
1. The new knowledge source is added to the grid. The new knowledge might take a few minutes to become available for answering questions. You can follow the progress in the **Status** column.
1. When the system finishes processing the new knowledge source, you can test it. On the toolbar, select **Test**. Then enter some test questions to determine whether the new knowledge source works as you expect.
1. On the toolbar, select **Publish** to roll out the changes and make the new knowledge available to users in finance and operations apps.

> [!NOTE]
> The amount of content that you can add to Copilot is [limited](/microsoft-copilot-studio/nlu-boost-node#information-sources) based on the type of the knowledge source.

> [!TIP]
> To ensure that new knowledge is available after you add and publish it, close any open Copilot sessions, and then start a new session.

## Include general knowledge

You can add the capability for Copilot to use [AI general knowledge](/microsoft-copilot-studio/nlu-ai-general-knowledge) to answer general questions. This content includes information that is part of the language model that is used, web content that is identified through Bing Search, and information from other sources. Copilot uses this information after it exhausts the information from your custom knowledge sources.

This capability is disabled by default, but you can enable it if you want to use it.

> [!WARNING]
> When the use of general knowledge is enabled, it can increase the richness of Copilot responses. However, it also increases the risk that answers might include incorrect content.
>
> Before you publish AI general knowledge to your production system, be sure to carefully consider and test it.

To add AI general knowledge to Copilot, follow these steps.

1. Open [Copilot Studio](https://copilotstudio.microsoft.com/), and select the Dataverse environment that is associated with your finance and operations apps environment.
1. On the navigation pane on the left, select **Copilots**.
1. Open the copilot that is named *Copilot for finance and operations apps*.
1. On the **Overview** tab, in the **Knowledge** section, set the **Allow the AI to use its own general knowledge** option to *Enabled*. The use of general knowledge is usually ready in just a few seconds.
1. On the toolbar, select **Test**. Then enter some test questions to determine whether general knowledge works as you expect.
1. On the toolbar, select **Publish** to roll out the changes and make the new knowledge available to users in finance and operations apps.

## Related information

- [Generative help and guidance with Copilot](../../fin-ops/copilot/copilot-generative-help.md)
- [Enable generative help and guidance with Copilot](enable-copilot-generative-help.md)
- [Responsible AI FAQ for Generative help and guidance with Copilot in finance and operations apps](../../fin-ops/copilot/faq-copilot-generative-help.md)
- [Responsible AI FAQ for Follow-up questions in the Copilot sidecar (preview)](../../fin-ops/copilot/faq-copilot-suggested-questions.md)
