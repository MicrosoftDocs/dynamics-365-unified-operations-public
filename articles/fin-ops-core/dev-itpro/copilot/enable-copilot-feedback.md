---
title: Enable enhanced user feedback for Copilot and related experiences (preview)
description: Learn how administrators can enable and review user feedback for Copilot and related experiences in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/27/2025
ms.custom: 
  - bap-template
---

# Enable enhanced user feedback for Copilot and related experiences (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

*Enhanced user feedback for Copilot and related experiences* lets users provide product feedback to Microsoft by selecting the thumbs-up or thumbs-down buttons. These options are currently available in experiences like the Copilot sidecar and summary cards.

:::image type="content" source="media/feedback-thumbs.png" alt-text="Feedback experience with thumbs-up and thumbs-down buttons.":::

Enhanced user feedback allows users to provide detailed, written feedback in addition to simple thumbs-up or thumbs-down inputs. This feature enables Microsoft to gain richer insights to help improve Copilot responses and user satisfaction. Without enhanced feedback, users can only indicate positive or negative experiences with a simple signal, resulting in limited actionable data for service enhancements.

> [!NOTE]
> Feedback is captured using the [in-product feedback system](/microsoft-365/admin/misc/feedback-user-control?view=o365-worldwide) common across Microsoft products. This system follows existing data handling and privacy policies.

With enhanced user feedback turned on, when a user selects thumbs up or thumbs down, the system prompts them to provide a written statement describing their experience.

:::image type="content" source="media/feedback-survey-popup.png" alt-text="Example for a survey pop-up dialog with a user provided message.":::

When users submit feedback, they can choose to attach system-collected information to provide richer context. For example, in the Copilot sidecar, users can attach the conversation history along with their feedback. Users get a chance to review all attached data and can opt out of including attachments before finalizing their submission. Administrators can choose to disable attachments across the tenant if necessary.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use enhanced user feedback, you must be running finance and operations apps version 10.0.43 or later. For information about release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).

## Turn enhanced user feedback on or off

By default, enhanced user feedback is turned on. The feature integrates with existing Microsoft product feedback mechanisms and the standard thumbs-up/down interface.

Admins can control whether and how users submit feedback to Microsoft by managing various aspects of the feature at each of several levels (tenant level, Dataverse organization level, and finance and operations environment level). Disabling feedback at a higher level prevents it from being enabled at lower levels. To make the feature available to users of finance and operations apps, you must enable it at each level, as described in the following procedures.

To turn enhanced user feedback on or off at the tenant level, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left navigation pane, select **Settings**.
1. On the **Tenant settings** page, make the following settings:
    - **Copilot feedback** – This setting is on by default. It controls users' ability to submit detailed feedback. Select it to open the **Copilot feedback** dialog, set the slider to *On* or *Off*, and then select **Save**.
    - **Copilot data collection** – This setting is on by default. It controls users' ability to attach more information (such as a conversation history) to their feedback. Select it to open the **Copilot data collection** dialog, set the slider to *On* or *Off*, and then select **Save**.

To turn enhanced user feedback on or off at the Dataverse organization level, follow these steps.

1. Open the [maker experience for Power Apps](https://aka.ms/makepowerapps) for your Dataverse environment.
1. On the left navigation pane, select **Tables**.
1. Find the **Organization** table and open it.
1. In the **Organization columns data** grid, select the **more** column heading to open the **Show existing column** drop-down dialog. Use the dialog to search for the *Allow users to provide feedback to improve Copilot experiences* column, select the column, and then select **Save**.
1. The **Allow users to provide feedback to improve Copilot experiences** column is now shown in the grid and displays a slider. Set the slider to *Yes* to allow user feedback or to *No* to turn it off. It's on by default. After changing it, wait until you see the *Data saved* message in the **Organization columns data** grid header before proceeding.

To turn enhanced user feedback on or off at the finance and operations environment level, follow these steps.

1. Sign in to your finance and operations apps environment.
1. Go to **System administration** \> **Workspaces** \> **Feature management**. (Learn more about feature management in [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Select **Check for updates**.
1. Find and select the feature called *(Preview) Enable user feedback for Copilot and related experiences*. Then select **Enable now** to turn it on or **Disable** to turn it off.

    > [!NOTE]
    > If the tenant-level **Copilot Feedback** and/or organizational-level **Allow users to provide feedback to improve Copilot experiences** settings are turned off, then the feature *(Preview) Enable user feedback for Copilot and related experiences* is automatically disabled and marked as *Feature disabled by Microsoft* in feature management. You must turn on each of those higher-level settings before you can turn on the feature in feature management.

## Review and manage feedback

Administrators can review and manage user-provided feedback by going to the Microsoft 365 admin center's product feedback portal.

1. Open the admin center at [admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the left navigation pane, select **Health** \> **Product feedback**.

The portal displays all collected feedback. Admins can filter, review details, and examine attached data as needed.
