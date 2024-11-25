---
title: Pause service updates through Lifecycle Services (LCS)
description: Learn about how to pause service updates to your environments, including overviews on who can pause and what parts of the service get paused.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/20/2024
ms.custom:
ms.reviewer: johnmichalak  
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-03-31
ms.search.form:
ms.dyn365.ops.version: Platform update 24 
---

# Pause service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article explains how to pause updates to your sandbox and production cloud environments by using Microsoft Dynamics Lifecycle Services. This article doesn't apply to on-premises environments.

Microsoft updates your configured sandbox and production environments to the latest service update that Microsoft has released. Microsoft notifies you about upcoming updates to your environments via email and through notifications in Lifecycle Services. At that point, if you can't proceed with the update for some reason, you can pause it through Lifecycle Services.

> [!IMPORTANT]
> As of February 19, 2024, the maximum number of consecutive updates that can be paused is being reduced from three to one. However, because the service update cadence is also being reduced, from seven to four releases, the same minimum of two service updates per year is maintained. For more information, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md). For information about how to change the configured sandbox environment and set the production update cadence, see [Configure service updates through Lifecycle Services (LCS)](configure-service-updates.md).
>
> We are giving customers more flexibility in their update schedules. Beginning with the 10.0.39 release, customers can choose from two auto-update windows that are four weeks apart for each service update. Organizations can select the update window that better accommodates their validation process and operational schedules. For more information about how this affects pause policy, see the **Who can pause service updates** section later in this article.

## Who can pause service updates?

Only users (customers or partners) who are assigned to the **project owner** role in Lifecycle Services can pause updates. Updates can be paused only for **implementation projects**.

Staying current with service updates helps guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

As of February 19, 2024, the maximum number of consecutive updates that can be paused is being reduced from three to one. Therefore, customers are required to take a minimum of two service updates annually.

You can't use Lifecycle Services to pause a release if any sandbox and production environments in your project are more than two updates behind the latest release. This is applicable even in the case of two autoupdate windows now available with 10.0.39 release. For instance, if Microsoft's latest released version is 10.0.39, customers with version 10.0.38 can pause one or both autoupdate windows to completely pause the 10.0.39 release. Customers with version 10.0.37 can pause only the first autoupdate window and must take the 10.0.39 release in the second update window. If environments are two releases behind the latest release (older than 10.0.37 in this example), none of the autoupdate windows are applicable as no pause is allowed. 

If any sandbox or production environment is too far behind, you receive the following error message if you try to pause updates in Lifecycle Services:

> One or more sandbox and/or production environment isn't compliant with Microsoft's service update policy. All your environments need to be compliant before you can pause updates.

> [!IMPORTANT]
> Customers are explicitly required to pause both autoupdate windows to pause a release if they are eligible to do so, based on the pause policy. Pausing the first autoupdate window doesn't automatically pause the second window.

## What can I pause?

If you decide to pause updates, you have these options:

- Pause updates only to your production environment.
- Pause updates to both your sandbox environment and your production environment.
- Pause updates to other sandbox environments by pausing updates to your production environment.

> [!NOTE]
> If you pause updates to the production environment, all updates to other sandbox environments are paused too.

You can pause a maximum of one consecutive update at a time. For example, if you're using version 10.0.39, you can pause the update to version 10.0.40. However, you can't pause the update to version 10.0.41. We require that you take at least two updates per year.

> [!IMPORTANT]
> There's no way to pause more than one consecutive update, regardless of your industry or business schedule. For example, if you're two updates behind, and you find a critical issue with the Microsoft service update during validation in your sandbox environment after the update, you can contact Microsoft Support to pause the update to your production environment. The issue must be logged with Microsoft as an active bug/regression. This requirement applies only if you're more than two updates behind and can't pause updates to your production environment by using the functionality that's available in Lifecycle Services.
>
> If you pause updates to your sandbox environment, updates are automatically paused for your production environment too, because Microsoft always updates configured sandbox environments before production environments.

## Can I pause updates to my additional sandbox environments only?

**No**, you can't pause updates to additional sandbox environments only.

## What if the update to the default sandbox environment is paused?

If the update to the default sandbox environment is paused, the updates to the production environment and all additional sandbox environments are also paused.

## How do I pause updates?

To pause updates, follow these steps.

1. In Lifecycle Services, in your implementation project, open the **Project settings** page.

    This page has a new tab that's named **Update settings**.

2. In the **Pause Updates** section, on the **Update settings** tab, select **Pause upcoming update**.
3. In the dialog box that appears, select whether you want to pause updates to your production environment only, or to both your sandbox environment and your production environment.
4. Select **Next**.
5. Select your reason for pausing updates. If you select **Issue found during validations**, you must enter a valid support ticket number. You can add any other details that help Microsoft understand why you want to pause updates.
6. When you've finished, select **Confirm**.

You can also edit an existing pause to cancel it so that updates are resumed. To edit a pause, select **Pause upcoming update**. The maximum of one update pause still applies. Therefore, you can't edit the pause to extend its duration past one update.

Whenever you pause an update or edit an existing pause, a notification appears at the top of the **Update settings** tab. This notification shows what version was paused. All stakeholders (the project owner and environment manager) also receive an email to inform them that a service update for the selected environments was paused. If someone cancels an existing pause and resumes updates, the notification disappears, and an email is sent to inform the stakeholders the paused update resumed.

> [!IMPORTANT]
> You can pause an update through Lifecycle Services up to four hours before the start of the downtime window.
>
> You can cancel a pause and resume updates up to seven days before the start of the downtime date. If there are fewer than seven days before your downtime starts, you won't be able to cancel a pause.

## What happens after the pause duration expires?

Cumulative service updates help guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

There are two ways to cancel a pause, so that updates are resumed:

- Someone manually cancels a pause, as explained in the previous section.
- The duration that was set for the pause expires, and updates to the configured environments are automatically resumed.

In both cases, an email is sent to inform the stakeholders.

For more information about service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
