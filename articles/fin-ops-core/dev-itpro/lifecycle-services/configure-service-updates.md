---
# required metadata

title: Configure service updates through Lifecycle Services (LCS)
description: This article explains how to specify how and when you receive service updates for your environments.
author: angelmarshall
ms.date: 03/02/2023
ms.topic: article
ms.prod: 
ms.technology: 
ms.custom: bap-template
# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# Configure service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics Lifecycle Services (LCS), you can specify how and when you receive service updates from Microsoft for your environments.

> [!IMPORTANT]
> This feature is available only to customers who are using **version 8.1 and later** or are using **version 7.3**, and who are **not** part of the [First release](../../fin-ops/get-started/public-preview-releases.md#release-processes) program. Microsoft is working to make the feature available to First release customers. For customers who are on version 7.1, 7.2, or 8.0, you can take the update manually using the regular servicing flows.

Only users (customers or partners) who are assigned to the **Project owner** role in LCS can configure updates. Additionally, updates can be configured only for **implementation projects**.

Follow these steps to change your update settings.

> [!NOTE]
> These settings apply only to service updates. They have no effect on the operating system–level security updates that are applied to your environments every month.

1. In LCS, in your implementation project, open the **Project settings** page.

    This page has a new tab that is named **Update settings**.

2. On the **Update settings** tab, set the following configuration options as you require:

    - **Default Sandbox Update environment** – Select an alternate sandbox environment that should be updated before the production update.

        By default, Microsoft first updates the Tier 2 Standard Acceptance Test (sandbox) environment that is included in the base offer. It then applies the update to the production environment. If you've purchased Tier 2 and higher sandbox add-on environments and want a different sandbox to be updated, you can use this field to change the default environment to an alternate environment.

        > [!IMPORTANT]
        > The environment that you select here will be updated seven calendar days before the update cadence that is selected for the production environment.

    - **Production environment update cadence** – Select a recurring cadence for updates to your production environment. The sandbox environment that is selected in the **Default Sandbox Update environment** field will be updated seven calendar days before the selected cadence. The remaining additional sandboxes will be updated on the same cadence as the production environment. The following options are available:

        - **Select the cadence** – Select whether to receive updates in the first, second, or third week of the month.
        - **Select one of the three time-zones** – Select the time zone that the production environment should be updated in: Eastern Time (UTC – 5), Hong Kong Time (UTC + 8), or Greenwich Mean Time (UTC + 0).
        - **Select a day of the week:** Select the day in the week when you want to receive updates.
        - **Select a time slot:** Select the time slot when you want to receive updates.

        > [!IMPORTANT]
        > Currently, only a few options are available for the day of the week and time slot options. Microsoft will add more options soon, such as weekdays for customers.
        
        > If the above time slots do not meet your needs, you always have the option to do a self-update at a time that is convinient to you by taking the update and applying it to your environments using the regular servicing flows.

 3. When you've finished setting the configuration options, select **Save**.
 
After you set the update environment and update cadence, Microsoft generates an update calendar for the next six months. This calendar shows exactly when the configured sandbox and production environments will be updated. Therefore, you'll know when to expect each update. To view the calendar, select **View the update calendar**.

> [!IMPORTANT]
> After the settings are saved, you can change them at any time. However, if there is an ongoing rollout, the new settings won't be used to update the existing rollout timings. Instead, they'll start to be used in the next rollout. An ongoing rollout is defined by the 14-day period between the date when the email notification about the update of the sandbox environment is sent and the date when the production environment is updated.

For more information about how to pause updates to configured sandbox and production environments, see [Pause service updates through Lifecycle Services (LCS)](pause-service-updates.md).

For more information about One Version and Microsoft-managed service updates, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).

## Canceled updates
A scheduled update could be canceled for various reasons. Here are some of the common reasons that could cause a scheduled update to be canceled by Microsoft. 
- An error was found during update preparation. The update preparation starts approximately 4 hours before the update to ensure that the environment is in a healthy state. If the environment was in a failed state or maintenance mode, the scheduled update will be canceled before it starts.    
- An error was found while updating the environment. If there were issues during the update, the scheduled update will be canceled and the environment is rolled back to the previous state.  
- The environment is already running on the latest version.  There's no need to apply the update again, the scheduled update will be canceled before it starts. 
- The target environment isn't found. If the designated sandbox was deleted or the production environment hasn't been deployed, the scheduled update will be canceled before it starts.
- You’re enrolled in the [First Release program](https://aka.ms/FirstReleaseFnO).  The First Release program has different release cadence so the previously scheduled updates will be canceled. 

You can find the canceled updates via the **View recent canceled updates** in the update settings. It will show all canceled updates, if any, within the last 2 scheduled updates.

## Additional sandbox environments
In addition to the default sandbox environment and the production environment, if you have additional sandbox environments deployed in your LCS implementation project, the additional sandbox environments will also be auto-updated with the One Version service update. 

### Update additional sandbox environments
The additional sandbox environments will be updated on the same cadence as your production environment, based on your update settings. If you have additional sandbox environments, they'll be scheduled for update together.

If you haven't deployed the production environment, none of the additional sandbox environments will be auto-updated.

If the production environment is updated **before** the email about the production update is sent, then the production environment, as well as all additional sandbox environments, **will not** get updated. If the production environment is updated **after** the email about the production update is sent, then the production environment update **will** be canceled, but additional sandbox environments will get updated.

If there’s any update failure on the production environment or any of the additional sandbox environments, it will not interfere with the remaining updates. That is, if the production update failed, the additional sandbox update will continue. Similarly, if you have additional sandbox environments and one of them failed during the update, the others will continue.

You can self-update any of your environments prior to the scheduled service update. If you have self-updated to the latest version on an environment, then the scheduled service update will not apply an update on that environment again.

### Change the default sandbox environment
If you already have selected a default sandbox environment, and want to change it with one of the additional sandbox environments, the change will take effect in the next scheduled service update.

### Pause service updates
Additional sandbox environments can't be paused independently. However, if you pause the default sandbox environment, then both the production environment and additional sandbox environments will be paused automatically. If you pause the production environment, then additional sandbox environments will also be paused.

The current [pause service updates](pause-service-updates.md) policy still applies.

### Email notifications 
If your additional sandbox environments are scheduled for an update, you'll receive reminder email notifications 6 days prior to the scheduled service update.
After the update completes, you'll also receive email notification regarding the update result for each environment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
