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

# (Preview) Enable Enhanced User Feedback for Copilot and Related Experiences

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
>
> - *Enhanced user feedback for Copilot and related experiences* is available in finance and operations version 10.0.43 and later. For information about release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).
> - This feature is a preview feature. It's subject to the [preview supplemental terms of use](https://go.microsoft.com/fwlink/?linkid=2105274). Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).


> [!NOTE]
> Feedback is captured using the [in-product feedback system](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/feedback-user-control?view=o365-worldwide) common across Microsoft products. This system follows existing data handling and privacy policies.

Users can provide product feedback to Microsoft by selecting the Thumbs Up or Thumbs Down buttons. Currently, these options are available in experiences like the Copilot sidecar and summary cards, and will be extended to more scenarios over time.

:::image type="content" source="feedback-thumbs.png" alt-text="Feedback experience with Thumbs up and Down buttons.":::

Enhanced *user feedback for  Copilot and related experiences* allows users to provide more detailed, written feedback in addition to simple thumbs-up or thumbs-down inputs. By enabling this feature, Microsoft gains richer insights to help improve Copilot responses and user satisfaction. Without enhanced feedback, users can only indicate positive or negative experiences with a simple signal, resulting in limited actionable data for service enhancements.

When a user selects thumbs up or thumbs down, they’re prompted to provide a written statement describing their experience—positive or negative.
:::image type="content" source="feedback-survey-popup.png" alt-text="Example for a survey popup with a user provided message.":::

When submitting feedback, users can choose to include additional system-collected information to provide richer context. For example, in the Copilot sidecar, users may attach the conversation history along with their feedback. Before finalizing, users review all attached data and can opt out of including any attachments. Administrators have the option to disable attachments across the tenant if necessary.

## Admin Review and Management of Feedback

Administrators can review and manage user-provided feedback in the Microsoft 365 admin center’s product feedback portal.

1. Open the admin center at [admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the left navigation pane, select **Health > Product feedback**.

The portal displays all collected feedback. Admins can filter, review details, and examine attached data as needed.

## Admin Controls for Enhanced User Feedback

By default, enhanced user feedback for Copilot and related experiences is turned on. These features integrate with existing Microsoft product feedback mechanisms and the standard thumbs-up/down interface. 

Administrators have multiple layers of control, enabling them to manage whether and how users submit product feedback to Microsoft. Disabling feedback at a higher level prevents it from being enabled at lower levels.

The following settings apply to finance and operations apps:

|Level    |Settings  |Details  |
|---------|---------|---------|
|Tenant wide  |*Copilot feedback* |On by default. If disabled, users cannot submit detailed feedback.|
|Tenant wide |*Copilot data collection*  |On by default. If disabled, users cannot attach additional data (such as conversation history) to their feedback.|
|Dataverse organization level |*Allow users to provide feedback to improve Copilot experiences*|On by default. If set to No, users cannot submit detailed feedback to Microsoft.|
|Finance and operations environment level|*(Preview) Enable user feedback for Copilot and related experiences*|On by default through [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). If disabled, users cannot submit detailed feedback.|

> [!NOTE]
> If the tenant level setting **Copilot Feedback** or the organizational level setting **Allow users to provide feedback to improve Copilot experiences** is disabled, then the feature **(Preview) Enable user feedback for Copilot and related experiences** in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) is automatically disabled and marked as **"Feature disabled by Microsoft."**. It cannot be re-enabled unless those higher-level settings are turned back on.

### Steps to Enable or Disable Enhanced User Feedback

- Enable or disable **Copilot feedback** at the tenant level 
    1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. Select **Settings** from the left navigation pane.
    1. On the **Tenant settings** page, locate the setting *Copilot feedback*. This setting is on by default. Select it, and in the **Copilot feedback** dialog toggle it to On or Off and choose **Save**.

- Enable or disable **Copilot data collection** at the tenant level
    1. Open [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    1. Select **Settings** from the left navigation pane.
    1. On the **Tenant settings** page, locate the setting *Copilot data collection*. Select it, and in the **Copilot data collection** dialog toggle it to On or Off and choose **Save**.

- Enable or disable **Copilot feedback** at the Dataverse organization level:
    1. Open the [maker experience for Power Apps](https://aka.ms/makepowerapps) for the Dataverse environment.
    1. From the left navigation pane, select **Tables**.
    1. Find the **Organization** table and open it.
    1. In the **Organization columns data** grid use the drop down in the column header to *Show existing column*. Search for **Allow users to provide feedback to improve Copilot experiences** and select the column to be added and press **Save**.
    1. Back in the gris, select this column to edit, then toggle the value. It’s on by default. After changing it, wait until you see Data saved before proceeding.

- Enable or disable enhanced feedback at the finance and operations environment level:
    1. Sign in to your finance and operations apps environment.
    1. Use the [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace to enable or disable **(Preview) Enable user feedback for Copilot and related experiences**. If disabled, users cannot submit detailed feedback within this environment.
