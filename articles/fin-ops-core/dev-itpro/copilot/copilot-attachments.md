---
title: Use file attachments in Copilot for finance and operations apps
description: Learn how to use file attachments with Copilot for finance and operations apps
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 06/03/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Use file attachments in Copilot for finance and operations apps

[!include [banner](../includes/banner.md)]

The chat experience for Copilot for finance and operations apps allows you to attach files, including a screenshot of the current browser window for your finance and oeprations apps client session. The file becomes part of your chat session, which you can then work with by adding extended topics or tools to Copilot providing custom experiences for your environment.

[!NOTE] By default the chat experience for Copilot for finance and operations apps doesn't use the files or screenshots that are attached to the chat session. To use the attached files, you must extend Copilot for finance and operations apps with topics or tools needed for your user experiences that use the attached files.

## Prerequisites
The following prerequisites must be in place to use attachments with Copilot for finance and operations apps:
- Finance and operations apps must be on a minimum version of 10.0.45.
- The following solutions must be installed in the Power Platform environment. If they aren't already installed, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps) for information about how to install Dynamics 365 solution packages in Dataverse.

    - The Copilot for finance and operations package, which includes the following solutions:

        - Copilot for finance and operations apps
        - Copilot for finance and operations generation solution
        - Copilot for finance and operations anchor solution

    - Finance and Operations Virtual Entity

- The **Enable user attachments in Copilot sidecar** feature must be enabled in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

## Attaching files to a chat session
The attachments feature enables you to upload a file to your chat session, or take a screenshot of the current browser window for your finance and operations apps client session to attach to the chat session.

To add a file attachment to the chat session:
1. Select the **Attach** button in the chat window.
2. Select **Browse...**.
3. Browse to the file location and select the file you want to attach.
4. Select **Open**.

To add a screenshot attachment to your chat session with Copilot for finance and operations apps:
1. Select the **Attach** button in the chat window.
2. Select **Add screenshot**.
3. When prompted to allow the client to see the tab, select **Allow**.

## Extending Copilot for finance and operations apps to use the attachment files
By default the chat experience for Copilot for finance and operations apps doesn't use the files or screenshots that are attached to the chat session. The files are added to a system variable that can be accessed by Copilot, but you must create custom topics or tools in Copilot for finance and operations apps to provide Copilot with the skills you want it to have for users in your environment.

### Handling attachments
When a file is attached to the chat session it is added to the `System.Activity.Attachments` object in Copilot Studio, which contains the table of file attachments. You can create a topic or tool that uses the file attachments, accessing the attached files in the table, to provide Copilot with additional capabilities.

### Example extending Copilot with attachments
