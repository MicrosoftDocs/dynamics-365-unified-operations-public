---
title: Enable enhanced feedback for the Copilot sidecar
description: Learn how administrators can enable basic Copilot capabilities in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 10/25/2024
ms.custom:
 - bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Enable enhanced feedback for the Copilot sidecar

*Enhanced feedback for the Copilot sidecar* enables users to submit detailed written feedback about their experience using Copilot in the sidecar user interface (such as when using [Copilot generative help](../../fin-ops/copilot/copilot-generative-help.md)). Users can rate the usefulness of Copilot's responses and optionally attach the conversation to provide more context.Without this feature, users can only provide feedback on through simple thumbs-up or thumbs-down signals, resulting in less actionable data for enhancing the service.

The system automatically categories and translates all feedback. This allows for a comprehensive collection of user insights, supporting ongoing improvements to the Copilot experience.

## Deploy enhanced feedback for the Copilot sidecar

1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left navigation pane, select **Settings**.
1. On the **Tenant settings** page, find the row with a **Name** of *Copilot feedback*. This setting controls whether feedback sending is on or off. Select this link to open the **Copilot feedback** dialog. Set the option to *On* and then select **Save**.
1. On the **Tenant settings** page, find the row with a **Name** of *Copilot data collection*. This setting controls whether users can send conversation metadata as part of the feedback. Select this link to open the **Copilot data collection** dialog. Set the option to *On* and then select **Save**.
1. Organization-level: "Allow users to provide feedback to improve Copilot experiences" (same as flag 1, can be turned on or off for specific org) <!-- KFM: Where is this? -->
1. Sign in to your finance and operations apps environment.
1. Use the [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on the feature called *(Preview) Enable user feedback in the Copilot sidecar*.
