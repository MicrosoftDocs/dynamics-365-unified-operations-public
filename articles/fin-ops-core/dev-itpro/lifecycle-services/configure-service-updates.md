---
title: Configure service updates through Lifecycle Services
description: Learn about how to specify how and when you receive service updates for your environments, including an outline on canceled updates.
author: angelmarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.custom: bap-template
ms.reviewer: johnmichalak 
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-3-31
ms.search.form:
ms.dyn365.ops.version: Platform update 24 
---

# Configure service updates through Lifecycle Services

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics Lifecycle Services, you can specify how and when you receive service updates from Microsoft for your environments.

> [!IMPORTANT]
> This feature is available only to customers who are using **version 8.1 and later** or are using **version 7.3**, and who are **not** part of the [First release](../../fin-ops/get-started/public-preview-releases.md#release-processes) program. Microsoft is working to make the feature available to First release customers. For customers who are on versions 7.1, 7.2, or 8.0, you can take the update manually by using the regular servicing flows.

Only users (customers or partners) assigned to the **Project owner** role in Lifecycle Services can configure updates. Additionally, you can configure updates only for **implementation projects**.

Follow these steps to change your update settings.

> [!NOTE]
> These settings apply only to service updates. They have no effect on the operating system–level security updates that are applied to your environments every month.

1. In Lifecycle Services, in your implementation project, open the **Project settings** page.

    This page has a new tab named **Update settings**.

1. On the **Update settings** tab, set the following configuration options as you require:

    - **Default Sandbox Update environment** – Select an alternate sandbox environment that should be updated before the production update.

        By default, Microsoft first updates the Tier 2 Standard Acceptance Test (sandbox) environment that is included in the base offer. It then applies the update to the production environment. If you purchased Tier 2 and higher sandbox add-on environments and want a different sandbox to be updated, use this field to change the default environment to an alternate environment.

        > [!IMPORTANT]
        > The environment that you select here's updated seven calendar days before the update cadence that you select for the production environment.

    - **Production environment update cadence** – Select a recurring cadence for updates to your production environment. The sandbox environment that you select in the **Default Sandbox Update environment** field is updated seven calendar days before the selected cadence. The remaining additional sandboxes are updated on the same cadence as the production environment. The following options are available:

        - **Select the cadence** – Select whether to receive updates in the first, second, or third week of the month.
        - **Select one of the three time-zones** – Select the time zone that the production environment should be updated in: Eastern Time (UTC – 5), Hong Kong Time (UTC + 8), or Greenwich Mean Time (UTC + 0).
        - **Select a day of the week:** Select the day in the week when you want to receive updates.
        - **Select a time slot:** Select the time slot when you want to receive updates.

        > [!IMPORTANT]
        > Currently, only a few options are available for the day of the week and time slot options. Microsoft adds more options soon, such as weekdays for customers.

        > If the above time slots don't meet your needs, you always have the option to do a self-update at a time that is convenient to you by taking the update and applying it to your environments by using the regular servicing flows.

1. When you finish setting the configuration options, select **Save**.

After you set the update environment and update cadence, Microsoft generates an update calendar for the next six months. This calendar shows exactly when the configured sandbox and production environments are updated. Therefore, you know when to expect each update. To view the calendar, select **View the update calendar**.

> [!IMPORTANT]
> After you save the settings, you can change them at any time. However, if there's an ongoing rollout, the new settings aren't used to update the existing rollout timings. Instead, they start to be used in the next rollout. An ongoing rollout is defined by the 14-day period between the date when the email notification about the update of the sandbox environment is sent and the date when the production environment is updated.

For more information about how to pause updates to configured sandbox and production environments, see [Pause service updates through Lifecycle Services](pause-service-updates.md).

For more information about One Version and Microsoft-managed service updates, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

## Canceled updates

A scheduled update can be canceled for various reasons. Here are some common reasons that cause Microsoft to cancel a scheduled update.

- An error is found during update preparation. The update preparation process starts approximately four hours before the update to ensure that the environment is in a healthy state. If the environment is in a failed state or maintenance mode, the scheduled update is canceled before it starts.
- An error is found while updating the environment. If there are problems during the update, the scheduled update is canceled and the environment rolls back to the previous state.  
- The environment is already running on the latest version.  There's no need to apply the update again, so the scheduled update is canceled before it starts.
- The target environment isn't found. If the designated sandbox is deleted or the production environment isn't deployed, the scheduled update is canceled before it starts.
- You're enrolled in the [First Release program](https://aka.ms/FirstReleaseFnO).  The First Release program has a different release cadence, so previously scheduled updates are canceled.

You can find the canceled updates through the **View recent canceled updates** in the update settings. It shows all canceled updates, if any, within the last two scheduled updates.

## Additional sandbox environments

In addition to the default sandbox environment and the production environment, if you deploy additional sandbox environments in your Lifecycle Services implementation project, the One Version service update also auto-updates the additional sandbox environments.

### Update additional sandbox environments

You update the additional sandbox environments on the same cadence as your production environment, based on your update settings. If you have additional sandbox environments, you schedule them for update together.

If you don't deploy the production environment, none of the additional sandbox environments are auto-updated.

If you update the production environment **before** you send the email about the production update, the production environment and all additional sandbox environments **aren't** updated. If you update the production environment **after** you send the email about the production update, the production environment update **is** canceled, but additional sandbox environments are updated.

If there's any update failure on the production environment or any of the additional sandbox environments, it doesn't interfere with the remaining updates. That is, if the production update fails, the additional sandbox update continues. Similarly, if you have additional sandbox environments and one of them fails during the update, the others continue.

You can self-update any of your environments prior to the scheduled service update. If you self-update to the latest version on an environment, the scheduled service update doesn't apply an update on that environment again.

### Change the default sandbox environment

If you already have selected a default sandbox environment, and want to change it with one of the additional sandbox environments, the change will take effect in the next scheduled service update.

### Pause service updates

Additional sandbox environments can't be paused independently. However, if you pause the default sandbox environment, then both the production environment and additional sandbox environments will be paused automatically. If you pause the production environment, then additional sandbox environments will also be paused.

The current [pause service updates](pause-service-updates.md) policy still applies.

### Email notifications

If your additional sandbox environments are scheduled for an update, you'll receive reminder email notifications 6 days prior to the scheduled service update.
After the update completes, you'll also receive email notification regarding the update result for each environment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
