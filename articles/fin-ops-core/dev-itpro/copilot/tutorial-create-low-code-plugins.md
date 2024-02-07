---
title: Extending Copilot capabilities with low-code plugins
description: This article provides a tutorial on creating low-code plugins for Copilot for Finance and Operations using Microsoft Copilot Studio
author: jaredha
ms.author: jaredha
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 2/6/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extending Copilot capabilities with low-code plugins

[!include [banner](../includes/banner.md)]

Microsoft Copilot Studio provides the orchestration of AI capabilities for Copilot in Finance and Operations, which enables a low-code maker experience for customizing the Copilot capabilities. This tutorial walks through an example of adding a plugin to the Copilot in Finance and Operation chatbot in Copilot Studio to add new capabilities to Copilot.

## Scenario
In this scenario we will add the Copilot capability to translate a course description into another language by entering a prompt in the Copilot panel like "Translate the course description into French." The steps provide guidance on creating low-code plugins in Microsoft Copilot Studio and AI translation capabilities of AI Builder.

The following is an overview of the steps of the tutorial:
1. Create a new topic in Microsoft Copilot Studio triggered by a prompt to translate the course description.
2. Create an action that uses a Power Automate flow to get the course description.
3. Create an acton that uses Power Automate and AI Builder to translate the course description text.
4. Create a message response to send the translated text back to the user in the Copilot pane.

### Prerequisites
For this tutorial you must first have enabled Copilot in Finance and Operations in your environment by following the steps outlined in [Enable Copilot capabilities in finance and operations apps](enable-copilot.md).

## Step 1: Create a new topic
In this step you will create a new topic in the **Copilot for finance and oerations apps** chatbot.

1. Open [Microsoft Copilot Studio](https://web.powerva.microsoft.com) in the environment linked to your finance and operations apps.
2. Open the **Copilot for finance and operations apps** Copilot chatbot.
3. On the **Topics & Plugins** tab, select the **Add** drop-down list, and select **Topic** >> **From blank**.
4. On the **Trigger** node, select **Edit** on the **Phrases** card.
5. In the **Enter text** box on the **Phrases** pane, enter "Translate the course description" and hit Enter.

## Step 2: Add questions to determine the course ID and language
In the new topic, add questions Copilot will ask the user to determine the course ID of the course description to translate, and the language into which it will be translated.

> [!NOTE] In a coming release, the current record viewed by the user in finance and operations apps will be available as a variable in Microsoft Copilot Studio, similar to other contextual variables highlighted in [Using application context with Copilot](copilot-application-context.md). Having this available will enable having Copilot know the current record rather than requiring a question to the user to provide the course ID.

1. Select the (+) icon below the **Trigger** node, and select **Ask a question**.
2. On the **Question** node, enter the following:
   - **Enter a message**: "What is the course ID for the course description you want to translate?"
   - **Identify**: User's entire response
   - **Save response as**: Select the variable and change the **Variable name** to "CourseID".
3. Below the **Question** node, select the (+) icon and select **Ask a question** to create a second **Question** node.
   - **Enter a message**: "Into what language do you want the description translated?"
   - **Idenfity**: Language
   - **Save response as**: Select the variable and change the **Variable name** to "LanguageChoice".
4. Select **(+)** >> **Variable management** >> **Set a variable value** to create a new node.
   - **Set variable**: Create a new variable with the name **LanguageCode**.
   - **To value**: Select the **Formula** tab and enter the following Power Fx:
     ```powerapps-dot
      Switch(Topic.LanguageChoice,
	      "Italian", "it",
	      "French", "fr",
	      "Spanish", "es",
	      "Russian", "ru",
	      "German", "de",
	      "Latin", "la")
     ```
