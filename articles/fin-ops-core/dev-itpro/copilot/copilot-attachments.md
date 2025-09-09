---
title: Use file attachments in Copilot for finance and operations apps
description: Learn how to use file attachments with Copilot for finance and operations apps
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 09/09/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Use file attachments in Copilot for finance and operations apps

[!include [banner](../includes/banner.md)]

The chat experience for Copilot for finance and operations apps lets you attach files, like a screenshot of the current browser window for your finance and operations apps client session. The file is part of your chat session, and you work with it by adding extended topics or tools to Copilot to create custom experiences for your environment.

[!NOTE] By default, the chat experience for Copilot for finance and operations apps doesn't use the files or screenshots attached to the chat session. To use the attached files, extend Copilot for finance and operations apps with topics or tools needed for user experiences that use the attached files.

## Prerequisites

To use attachments with Copilot for finance and operations apps, make sure you meet these requirements:
- Finance and operations apps must be version 10.0.45 or later.
- Install these solutions in the Power Platform environment. If they're not installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) to learn how to install Dynamics 365 solution packages in Dataverse.

        - The Copilot for finance and operations package, which includes:

        - Copilot for finance and operations apps
        - Copilot for finance and operations generation solution
        - Copilot for finance and operations anchor solution

    - Finance and Operations Virtual Entity

- Turn on the **Enable user attachments in Copilot sidecar** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Attaching files to a chat session

The attachments feature supports uploading a file to your chat session or taking a screenshot of the current browser window in your finance and operations apps client session to attach to the chat session.

To add a file attachment to the chat session, follow these steps.

1. Select the **Attach** button in the chat window.
1. Select **Browse...**.
1. Go to the file location, and select the file you want to attach.
1. Select **Open**.

To add a screenshot attachment to your chat session with Copilot for finance and operations apps, follow these steps.

1. Select the **Attach** button in the chat window.
1. Select **Add screenshot**.
1. When prompted to let the client see the tab, select **Allow**.

## Extending Copilot for finance and operations apps to use attachment files

By default, the chat experience for Copilot for finance and operations apps doesn't use files or screenshots attached to the chat session. Copilot adds the files to a system variable, but you need to create custom topics or tools in Copilot for finance and operations apps to give Copilot the skills you want for users in your environment.

When you attach a file to the chat session, Copilot Studio adds it to the `System.Activity.Attachments` object, which has the table of file attachments. Use the file here, working with it like other files in Copilot Studio. To give Copilot more capabilities, create a topic or tool that uses file attachments and access the attached files in the table.

## Example extending Copilot with attachments

This example shows how to extend Copilot for finance and operations apps with a custom topic that uses attachment files from the chat session to give the user more capabilities. In this scenario, you add a topic that reviews an attached screenshot of an error from Copilot for finance and operations apps, and Copilot gives guidance to the user to fix the error.

[!NOTE] This example assumes [generative AI orchestration](/microsoft-copilot-studio/advanced-generative-actions) is enabled for the agent.

### Create a new topic

To create a new topic, follow these steps.

1. In Copilot Studio, open the **Copilot for finance and operations apps** agent.
1. Select the **Topics** tab, and select **Add a topic >> From blank**.
1. On the **Trigger** node, enter a description like: "This topic troubleshoots errors based on an attached screenshot. It helps with inputs such as 'Help me troubleshoot this error.'"

### Get the attachment file

To get the attachment file, follow these steps.

1. In the new topic, select **Add node** >> **Variable management** >> **Set a variable value** to add a new **Set variable value** node.
1. Create a new local variable in the **Set variable** field called `attachment_data`.
1. In the **To value** field, enter the formula `First(System.Activity.Attachments).Value`.

### Create a prompt that analyzes the error screenshot

To create a prompt that analyzes the error screenshot, follow these steps.

1. After the **Set variable value** node, select **Add node** >> **Add tool** >> **New prompt**.
1. Change the prompt title to **Troubleshoot FinOps errors**.
1. In the **Model** selector, select a model that supports documents and images, like GPT-4.1 or GPT-5.0.
1. In the **Instructions**, select **Add content** >> **Image or document**. Set the **Name** to **FinOpsScreenshot**.
1. In the **Instructions**, after the document input, enter a prompt indicating what you want the LLM to do with the screenshot. For example: "Analyze this image to determine what error messages are displayed. Then provide step-by-step instructions for troubleshooting the error."
1. Save and close the prompt.
1. In the Copilot Studio topic, in the **Input** field of the prompt action, select the `Topic.attachment_data` variable created in the previous step.
1. In the **Output** field, create a new local variable called `troubleshooting_output`.

### Return the response to the user

To return the response to the user, follow these steps.

1. After the **Prompt** node, select **Add node** >> **Send a message**.
1. On the **Message** node, select the **Insert PowerFx expression** button.
1. Enter the formula and insert into the message: `Topic.troubleshooting_output.text`.

### Test the attachments

After saving the topic, and publishing the changes to the agent, you can now try out the new attachments feature. In the finance and operations apps client, perform an operation that returns an error message. With the error message displayed on screen:

To test the attachments, follow these steps.

1. Open the Copilot sidecar chat panel.
1. Select the **Attach** button, then **Add screenshot**.
1. Select **Allow**.
1. In the Copilot chat, with the screenshot attached, type: "Help me troubleshoot this error."

The topic then uses the prompt action to analyze the screenshot and returns guidance to the user for troubleshooting the error.

:::image type="content" source="media/copilot-attachments-demo.png" alt-text="Screenshot of troubleshooting error messages with prompts viewing screenshot attachments in Copilot.":::
