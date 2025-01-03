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

The *Enhanced user feedback for Copilot and related experiences* feature lets users provide product feedback to Microsoft by selecting thumbs-up or thumbs-down buttons. These buttons are currently available in experiences such as the Copilot sidecar and summary cards.

:::image type="content" source="media/feedback-thumbs.png" alt-text="Screenshot that shows the feedback experience with thumbs-up and thumbs-down buttons.":::

In addition to simple thumbs-up or thumbs-down input, the feature lets users provide detailed written feedback. In this way, Microsoft gains richer insights that can help us improve Copilot responses and user satisfaction. Without enhanced user feedback, users can indicate positive or negative experiences only through a simple signal. The result is limited actionable data that can be used for service enhancements.

> [!NOTE]
> Feedback is captured by using the [in-product feedback system](/microsoft-365/admin/misc/feedback-user-control?view=o365-worldwide) that is common across Microsoft products. This system follows existing data handling and privacy policies.

When enhanced user feedback is turned on, if users select a thumbs-up or thumbs-down button, a dialog box prompts them to provide a written statement that describes their experience.

:::image type="content" source="media/feedback-survey-popup.png" alt-text="Screenshot of a Submit feedback to Microsoft dialog box where a user entered some positive feedback.":::

When users submit feedback, they can choose to attach system-collected information to provide richer context. For example, in the Copilot sidecar, users can attach the conversation history to their feedback. Before users finalize their submission, they have an opportunity to review all attached data and can opt out of including attachments.

Administrators can disable attachments across the tenant as necessary.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use enhanced user feedback, you must be running finance and operations apps version 10.0.43 or later. Learn about release schedules for finance and operations apps in [Service update availability](../get-started/public-preview-releases.md).

## Turn enhanced user feedback on or off

By default, enhanced user feedback is turned on. The feature integrates with existing Microsoft product feedback mechanisms and the standard thumbs-up/thumbs-down interface.

Admins control whether and how users can submit feedback to Microsoft by managing various aspects of the feature at each of several levels: the tenant, the Dataverse organization, and the finance and operations environment. If feedback is disabled at a higher level, it can't be enabled at any lower levels. To make the feature available to users of finance and operations apps, you must enable it at each level, as described in the following procedures.

To turn enhanced user feedback on or off at the tenant level, follow these steps.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. In the left pane, select **Settings**.
1. On the **Tenant settings** page, configure the following settings:

    - **Copilot feedback** – This setting is on by default. It controls the ability of users to submit detailed feedback. Select it to open the **Copilot feedback** dialog box, set the option to *On* or *Off*, and then select **Save**.
    - **Copilot data collection** – This setting is on by default. It controls the ability of users to attach more information (such as a conversation history) to their feedback. Select it to open the **Copilot data collection** dialog box, set the option to *On* or *Off*, and then select **Save**.

To turn enhanced user feedback on or off at the Dataverse organization level, follow these steps.

1. Open the [maker experience for Power Apps](https://aka.ms/makepowerapps) for your Dataverse environment.
1. In the left pane, select **Tables**.
1. Find the **Organization** table, and open it.
1. In the **Organization columns and data** grid, select the **\+\<*number*\> more** column heading to open the **Show existing column** dropdown dialog box. In the dialog box, search for *Allow users to provide feedback to improve Copilot experiences*, select the checkbox for that column, and then select **Save**.
1. The **Allow users to provide feedback to improve Copilot experiences** column now appears in the grid. Set the option in this column to *Yes* to allow user feedback, or set it to *No* to prevent user feedback. By default, the option is set to *Yes*. If you change the setting, don't proceed until a "Data saved" message appears on the header of the grid.

To turn enhanced user feedback on or off at the finance and operations environment level, follow these steps.

1. Sign in to your finance and operations apps environment.
1. Go to **System administration** \> **Workspaces** \> **Feature management**. (Learn more about Feature management in [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Select **Check for updates**.
1. Find and select the feature that is named *(Preview) Enable user feedback for Copilot and related experiences*. Then select **Enable now** to turn it on or **Disable** to turn it off.

    > [!NOTE]
    > If the tenant-level **Copilot feedback** setting and/or the organizational-level **Allow users to provide feedback to improve Copilot experiences** setting is turned off, the *(Preview) Enable user feedback for Copilot and related experiences* feature is automatically disabled and marked as *Feature disabled by Microsoft* in Feature management. You must turn on each of the higher-level settings before you can turn on the feature in Feature management.

## Review and manage feedback

Admins can review and manage user-provided feedback by going to product feedback portal in Microsoft 365 admin center.

1. Open [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. In the left pane, select **Health** \> **Product feedback**.

The portal shows all collected feedback. Admins can filter, review details, and examine attached data as they require.
