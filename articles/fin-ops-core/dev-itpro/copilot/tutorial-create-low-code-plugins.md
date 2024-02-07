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
In this step you will create a new topic in the **Copilot in Finance and Operation** chatbot.

1. Open Microsoft Copilot Studio
