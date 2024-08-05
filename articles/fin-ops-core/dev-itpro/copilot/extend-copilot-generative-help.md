---
title: Add knowledge to generative help and guidance with Copilotwith Copilot
description: Learn about how to add custom knowledge to generative help and guidance to support users with additional information.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/07/2024
ms.custom: 
  - bap-template
ms.collection:
  - bap-ai-copilot
---

# Add knowledge to generative help and guidance with Copilot

Copilot uses *knowledge sources* as the basis of the information it provides to users. Copilot capabilities in finance and operations apps come with the out-of-the-box *conversational boosting* topic, which uses [Generative answers in Microsoft Copilot Studio](/microsoft-copilot-studio/nlu-boost-conversations) to answer user questions based on information provided by the knowledge sources it has been given.

> [!NOTE]
> By default, Copilot knowledge is limited to the published product documentation for finance and operations apps, and considers the language preferences selected by each user.
>
> The out-of-the-box *conversational boosting* topic assumes that all information in its knowledge sources relates to using product functionality. If you add unrelated knowledge, Copilot might generate responses that imply that the added knowledge is related to the use of finance and operations apps.  

You can extend Copilot's knowledge by adding new knowledge to it in Copilot Studio. For example, you can add individual document files (using file formats such as PDF, RTF, or Microsoft Word) or link to other information sources (such as SharePoint).

## Add specific knowledge

To add custom knowledge sources to generative help and guidance with Copilot, use [AI general knowledge](/microsoft-copilot-studio/nlu-ai-general-knowledge).

> [!IMPORTANT]
> Dataverse virtual entities published from finance and operations apps aren't currently supported as knowledge sources.

Follow these steps:

1. Open [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and select the Dataverse environment associated with your finance and operations apps environment.
1. Select **Copilots** on the navigation pane on the left.
1. Open the Copilot named **Copilot for finance and operations apps**.
1. Open the **Knowledge** tab.
1. Select the **Add knowledge** button and then choose the type of knowledge source you want to add. For example, select **Files** to [upload files](https://learn.microsoft.com/microsoft-copilot-studio/nlu-documents) from your local computer as additional knowledge.
1. Your new knowledge source is added to grid. It might take a few minutes before the new knowledge is available to answer questions. You can follow its progress in the **Status** column. When the system is finished processing your new knowledge source, you can test it. From the toolbar, select the **Test** button and then enter some test questions to see whether your new knowledge source is working as expected.
1. On the toolbar, select **Publish**  to roll out the changes and make the new knowledge available to users in finance and operations apps.

> [!NOTE]
> The amount of content you can add Copilot is [limited](/microsoft-copilot-studio/nlu-boost-node#information-sources) based on the type of the information source.

> [!TIP]
> After adding and publishing new knowledge, you should close any open Copilot sessions and start a new session to ensure that the new knowledge is available.

## Include general knowledge

You can add the ability for Copilot to use [AI general knowledge](https://learn.microsoft.com/microsoft-copilot-studio/nlu-ai-general-knowledge) to answer general questions. This content incudes information that's part of the used language model, Web content identified through Bing Search, and other sources. Copilot will use this information after it has exhausted the information from your specific knowledge sources. This option is enabled by default, but you can enable it if you want.

> [!WARNING]
> Enabling general knowledge can increase the richness of Copilot responses, but it can also increases the risk that answers might include incorrect content.
>
> Before you publish AI general knowledge into your production system, be sure apply careful consideration and testing.

To add AI general knowledge to Copilot, follow these steps:

1. Open [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and select the Data Verse environment associated to your finance and operations apps environment.
1. Select **Copilots** on the navigation pane on the left.
1. Open the Copilot named **Copilot for finance and operations apps**.
1. On the **Overview** tab, in the **Knowledge** section, set **Allow the AI to use its own general knowledge** to *Enabled*. It's usually ready after just a few seconds.
1. From the toolbar, select the **Test** button and then enter some test questions to see whether general knowledge is working as expected.
1. On the toolbar, select **Publish**  to roll out the changes and make the new knowledge available to users in finance and operations apps.

## See also

- [Generative help and guidance with Copilot](../../fin-ops/copilot/copliot-generative-help.md)
- [Responsible AI FAQ for Generative help and guidance with Copilot in finance and operations apps](../../fin-ops/copilot/faq-copilot-generative-help.md)
- [Responsible AI FAQ for Suggested questions within Copilot](../../fin-ops/copilot/faq-copilot-suggested-questions.md)