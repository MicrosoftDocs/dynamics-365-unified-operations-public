---
title: Add knowledge to Copilot generative help and guidance with Copilot
description: Learn about how to add knowledge to generative help and guidance to support users with additional information.
author: cabeln
ms.author: cabeln
ms.topic: overview
ms.date: 08/02/2024
ms.custom: bap-template
ms.reviewer: 
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Adding knowledge to Generative Help and Guidance with Copilot

Copilot grounds it's information in knowledge sources. The bot Copilot in finance and operations apps comes with the out-of-the-box topic "Conversational Boosting" that uses [Generative Answers](https://learn.microsoft.com/microsoft-copilot-studio/nlu-boost-conversations) to answer user questions from the knowledge sources it has been given.

> [!NOTE]
> By default the Copilot knowledge is limited to the product documentation for Dynamic 365 Apps, and takes into account the currently selected user interface language in the finance and operations app.
>
> The out-of-the-box Copilot topic assumes furthermore that all knowledge is related to in using product functionality in finance and operations apps. If you add add unrelated knowledge, Copilot for generative help and guidance may generate responses that imply that the knowledge is related to the use of finance and operations apps.  

To extend the Copilot knowledge you will need to add knowledge in the bot in Copilot Studio. For example you can add individual document files (such as PDF, RTF, Word documents and other formats), or provide other sources of information such as SharePoint and more.

## Adding specific knowledge

To expand to [General Knowledge](https://learn.microsoft.com/microsoft-copilot-studio/nlu-ai-general-knowledge) for Generative Help and Guidance and allow Copilot to find answers from those knowledge sources you need to add those sources using the following steps.  

> [!TIP]
> After adding new knowledge and publishing the bot you should close and reopen conversational Copilot experiences, to start a new conversational session that includes the knowledge changes.

1) Open [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and select the Dataverse environment associated to your finance and operations apps environment.
1) Click on 'Copilots' and select the bot 'Copilot for finance and operations apps', then navigate to the 'Knowledge' tab
1) Use the '+Add knowledge' button to select additional knowledge sources. For example use the 'Files' option to [upload files](https://learn.microsoft.com/microsoft-copilot-studio/nlu-documents) from your local computer as additional knowledge. It might take a moment until the new knowledge is available to answer questions.
1) Use the 'Test' button in Copilot studio to try out your Copilot with the expanded knowledge in Copilot Studio.
1) Click on 'Publish'  to roll out the knowledge changes to Copilot users in finance and operations apps.

> [!NOTE]
> There are [limitations](https://learn.microsoft.com/microsoft-copilot-studio/nlu-boost-node#information-sources) on the amount of content you may add Copilot, that depending on the type of the information source.  

## Including general knowledge to answer questions

You can allow Copilot to  also use [general knowledge](https://learn.microsoft.com/microsoft-copilot-studio/nlu-ai-general-knowledge) to answer questions. This incudes inherent information from within the used language model as well as and Web content identified through Bing Search and other sources. This information will be used if the information from the specific knowledge has been exhausted.

By default this option is disabled for Copilot in finance and operations apps, but can be enabled by customers.

> [!WARNING]
> By enabling general knowledge, the richness of the responses my increase, but also the risk for answers that may include incorrect content will increase.
>
> Careful consideration and testing is advised when enabling this capability, before publishing the update into the Copilot bot in production.

1) Open [Microsoft Copilot Studio](https://copilotstudio.microsoft.com/) and select the Data Verse environment associated to your finance and operations apps environment.
1) Click on 'Copilots' and select the bot 'Copilot for finance and operations apps' to open the copilot details.
1) Enable the setting 'Allow the AI to use its own general knowledge (preview)'. It might take a moment until the new knowledge is available to answer questions.
1) Use the 'Test' button in Copilot studio to try out your Copilot with the expanded knowledge in Copilot Studio.
1) Click on 'Publish' to roll the knowledge changes out to Copilot users in finance and operations apps.
