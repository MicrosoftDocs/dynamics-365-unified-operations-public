---
title: Enable enhanced user feedback for Copilot and related experiences
description: Learn how administrators can enable user feedback for Copilot and related experiences in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.topic: how-to
ms.date: 12/17/2024
ms.custom:
 - bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# (Preview) Enable enhanced user feedback for Copilot and related experiences

Enhanced *user feedback for the Copilot sidecar and related experiences* enables users to submit detailed written feedback about their experience via the Thumbs up and down buttons, while using Copilot in the sidecar user interface (such as when using [Copilot generative help](../../fin-ops/copilot/copilot-generative-help.md)), summarization experiences, and other experiences. Without this feature, users can only provide feedback on through simple thumbs-up or thumbs-down signals, resulting in less actionable data for enhancing the service.

:::image type="content" source="feedback-thumbs.png" alt-text="Feedback Thumbs up and Down experience.":::

Users are invited to provide a written statement about the experience, wether it is positive or negative.
:::image type="content" source="feedback-survey-popup.png" alt-text="Example for a survey popup with a user provided message.":::

When submitting feedback users can optionally attach additional information. For example, in the Copilot sidecar users can rate the usefulness of Copilot's responses and optionally attach the conversation to provide more context.  Users always can review the information that will be attached before submitting, and can decide to submit the feedback without attachments. Admins can also disable attachments for user feedback tenant wide.

The system automatically categories and translates all feedback. This allows for a comprehensive collection of user insights, supporting ongoing improvements to the Copilot experience.

## Admin control for enhanced user feedback for Copilot and related experiences

The admin has multiple levels of control on whether and to which detail users can send Copilot related product feedback on their experience to Microsoft, and the following settings will be honored by finance and operations apps.

|Level    |Settings  |Details  |
|---------|---------|---------|
|Tenant wide  |*Copilot feedback* |Enabled by default. If this setting is disabled, users can't submit detailed feedback to Microsoft.|
|Tenant wide |*Copilot data collection*  |Enabled by default. If this setting is disabled,  data such as conversation history can't be attached to the user's feedback.|
|Per Dataverse Environment    |*Allow users to provide feedback to improve Copilot experiences*|Enabled by default. If this flag on Dataverse organization is set to *No*, users can't submit detailed feedback to Microsoft.|
|Finance and operations environment |*(Preview) Enable user feedback for Copilot and related experiences*|Enabled by default in finance and operations [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). If disabled users can't submit detailed feedback to Microsoft.|

> [!NOTE]
> If the tenant level setting **Copilot Feedback** or the organizational level setting **Allow users to provide feedback to improve Copilot experiences** are disabled, then the feature **(Preview) Enable user feedback for Copilot and related experiences** in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) will automatically be disabled and marked as **"Feature disabled by Microsoft."** and cannot be enabled.

### Steps to enable or disable enhanced user feedback for Copilot and related experiences
- Enable or disable **Copilot feedback** and **Copilot data collection** on tenant level 
    1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. On the left navigation pane, select **Settings**.
    1. On the **Tenant settings** page, find the row with a **Name** of *Copilot feedback*. This setting controls whether feedback sending is on or off. This setting is on by default. Select this link to open the **Copilot feedback** dialog. Set the option to *On* to enable or *Off* to disable feedback tenant wide across apps and then select **Save**.
    1. On the **Tenant settings** page, find the row with a **Name** of *Copilot data collection*. This setting controls whether users can send conversation metadata as part of the feedback.  This setting is on by default. Select this link to open the **Copilot data collection** dialog. Set the option to *On* to allow and *Off* to prevent users to attach additional data with feedback and then select **Save**.

- Dataverse Organization-level:
    1. Open the [maker experience for Power Apps](https://aka.ms/makepowerapps) for the Dataverse environment.
    1. On the left navigation pane, select **Tables**.
    1. In the list of tables identify the **Organization** table and open it.
    1. In the grid **Organization columns data** use the drop down in the column header. In the popup to *Show existing column* use the search field search to select the column **Allow users to provide feedback to improve Copilot experiences** and press **Save**.
    1. In the grid you can now choose whether users can submit enhanced feedback. This setting is on by default. If you change the value, wait until the change has been saved, indicated by the text *Saving* and then *Data saved*.

- Enable or disable enhanced feedback on finance and operations environment level
    1. Sign in to your finance and operations apps environment.
    1. Use the [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace to turn on or off the feature called **(Preview) Enable user feedback for Copilot and related experiences**. This feature controls within the finance and operations environment whether users can submit enhanced feedback.

