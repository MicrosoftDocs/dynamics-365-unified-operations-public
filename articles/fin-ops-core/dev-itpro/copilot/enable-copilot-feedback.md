---
title: Enhanced user feedback for Copilot and related experiences (preview)
description: Learn how administrators can enable user feedback for Copilot and related experiences in finance and operations apps.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/27/2025
ms.custom: 
  - bap-template
---

# Enhanced user feedback for Copilot and related experiences (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

*Enhanced user feedback for Copilot and related experiences* lets users provide product feedback to Microsoft by selecting the thumbs-up or thumbs-down buttons. These options are currently available in experiences like the Copilot sidecar and summary cards.

:::image type="content" source="media/feedback-thumbs.png" alt-text="Feedback experience with Thumbs up and Down buttons.":::

Enhanced *user feedback for  Copilot and related experiences* allows users to provide more detailed, written feedback in addition to simple thumbs-up or thumbs-down inputs. By enabling this feature, Microsoft gains richer insights to help improve Copilot responses and user satisfaction. Without enhanced feedback, users can only indicate positive or negative experiences with a simple signal, resulting in limited actionable data for service enhancements.

When a user selects thumbs up or thumbs down, they’re prompted to provide a written statement describing their experience—positive or negative.

:::image type="content" source="media/feedback-survey-popup.png" alt-text="Example for a survey popup with a user provided message.":::

When submitting feedback, users can choose to include additional system-collected information to provide richer context. For example, in the Copilot sidecar, users may attach the conversation history along with their feedback. Before finalizing, users review all attached data and can opt out of including any attachments. Administrators have the option to disable attachments across the tenant if necessary.

> [!NOTE]
> Feedback is captured using the [in-product feedback system](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/feedback-user-control?view=o365-worldwide) common across Microsoft products. This system follows existing data handling and privacy policies.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use enhanced user feedback, your system must meet the following requirements:

- You must be running finance and operations apps version 10.0.43 or later. For information about release schedules for finance and operations apps, see [Service update availability](../get-started/public-preview-releases.md).
- The feature that is named *(Preview) Enable user feedback for Copilot and related experiences* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of version 10.0.43, this feature is turned on by default.

## Review and manage feedback

Administrators can review and manage user-provided feedback in the Microsoft 365 admin center's product feedback portal.

1. Open the admin center at [admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339).
2. In the left navigation pane, select **Health** \> **Product feedback**.

The portal displays all collected feedback. Admins can filter, review details, and examine attached data as needed.

## Turn enhanced user feedback on or off

By default, enhanced user feedback is turned on. The feature integrates with existing Microsoft product feedback mechanisms and the standard thumbs-up/down interface.

Enhanced user feedback can be managed on several levels (tenant level, Dataverse organization level, and finance and operations environment level), which enables admins to control whether and how users submit product feedback to Microsoft. Disabling feedback at a higher level prevents it from being enabled at lower levels.



To turn enhanced user feedback on or off at the tenant level, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select **Settings** from the left navigation pane.
1. On the **Tenant settings** page, make the following settings:
    - **Copilot feedback** – This setting is on by default. It enables users to submit detailed feedback. Select it to open the **Copilot feedback** dialog and then set it to *On* or *Off* and select **Save**.
    - **Copilot data collection** – This setting is on by default. It enables users to attach additional data (such as conversation history) to their feedback. Select it to open the **Copilot data collection** dialog and then set it to *On* or *Off* and select **Save**.

To turn enhanced user feedback on or off at the Dataverse organization level, follow these steps.

1. Open the [maker experience for Power Apps](https://aka.ms/makepowerapps) for the Dataverse environment.
1. From the left navigation pane, select **Tables**.
1. Find the **Organization** table and open it.
1. In the **Organization columns data** grid use the drop down in the column header to *Show existing column*. Search for **Allow users to provide feedback to improve Copilot experiences** and select the column to be added and press **Save**.
1. Back in the gris, select this column to edit, then toggle the value. It’s on by default. After changing it, wait until you see Data saved before proceeding.

To turn enhanced user feedback on or off at the finance and operations environment level, follow these steps.

1. Sign in to your finance and operations apps environment.
1. Go to **System administration** \> **Workspaces** \> **Feature management**. (To learn more about feature mangement, go to [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Select **Check for updates**.
1. Find and select the feature called *(Preview) Enable user feedback for Copilot and related experiences*. If disabled, users cannot submit detailed feedback within this environment.

    > [!NOTE]
    > If the tenant-level **Copilot Feedback** and/or organizational-level **Allow users to provide feedback to improve Copilot experiences** settings are turned off, then the feature *(Preview) Enable user feedback for Copilot and related experiences*  is automatically disabled and marked as **Feature disabled by Microsoft** in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). You must turn on those higher-level settings before you can turn on the feature in feature management.
