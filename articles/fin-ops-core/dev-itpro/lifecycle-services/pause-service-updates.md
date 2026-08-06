---
title: Pause service updates through Lifecycle Services
description: Learn about how to pause service updates to your environments, including overviews on who can pause and what parts of the service get paused.
author: ttreen
ms.author: ttreen
ms.topic: how-to
ms.date: 08/04/2026
ms.custom:
ms.reviewer: twheeloc  
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-03-31
ms.search.form:
ms.dyn365.ops.version: Platform update 24 
---

# Pause service updates through Lifecycle Services

[!include [banner](../includes/banner.md)]
[!include [LCS freeze](../../../includes/lcs-freeze-banner.md)]

This article explains how to pause updates to your sandbox and production cloud environments by using Microsoft Dynamics Lifecycle Services. This article doesn't apply to on-premises environments.

Microsoft updates your configured sandbox and production environments to the latest service update that Microsoft releases. Microsoft notifies you about upcoming updates to your environments via email and through notifications in Lifecycle Services. At that point, if you can't proceed with the update for some reason, you can pause it through Lifecycle Services.

> [!IMPORTANT]
> As of February 19, 2024, the maximum number of consecutive updates that you can pause is reduced from three to one. However, because the service update cadence is also reduced, from seven to four releases, the same minimum of two service updates per year is maintained. For more information, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md). For information about how to change the configured sandbox environment and set the production update cadence, see [Configure service updates through Lifecycle Services](configure-service-updates.md).
>
> Microsoft is giving customers more flexibility in their update schedules. Beginning with the 10.0.39 release, customers can choose from two auto-update windows that are four weeks apart for each service update. Organizations can select the update window that better accommodates their validation process and operational schedules. For more information about how this change affects pause policy, see the **Who can pause service updates** section later in this article.

## Who can pause service updates?

Only users (customers or partners) assigned the **project owner** role in Lifecycle Services can pause updates. You can pause updates only for **implementation projects**.

Staying current with service updates helps guarantee that customers always run on the latest set of fixes that Microsoft releases, so they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

Starting February 19, 2024, the maximum number of consecutive updates that you can pause is reduced from three to one. Therefore, customers must take a minimum of two service updates annually.

You can't use Lifecycle Services to pause a release if any sandbox and production environments in your project are more than two updates behind the latest release. This rule applies even in the case of two autoupdate windows now available with 10.0.39 release. For example, if Microsoft's latest released version is 10.0.39, customers with version 10.0.38 can pause one or both autoupdate windows to completely pause the 10.0.39 release. Customers with version 10.0.37 can pause only the first autoupdate window and must take the 10.0.39 release in the second update window. If environments are two releases behind the latest release (older than 10.0.37 in this example), none of the autoupdate windows are applicable as no pause is allowed. 

If any sandbox or production environment is too far behind, you receive the following error message if you try to pause updates in Lifecycle Services:

> One or more sandbox and/or production environment isn't compliant with Microsoft's service update policy. All your environments need to be compliant before you can pause updates.

> [!IMPORTANT]
> To pause a release, customers must pause both autoupdate windows if they're eligible to do so, based on the pause policy. Pausing the first autoupdate window doesn't automatically pause the second window.

## What updates can I pause?

If you decide to pause updates, you have these options:

- Pause updates only to your production environment.
- Pause updates to both your sandbox environment and your production environment.
- Pause updates to other sandbox environments by pausing updates to your production environment.

> [!NOTE]
> If you pause updates to the production environment, all updates to other sandbox environments are paused too.

You can pause a maximum of one consecutive update at a time. For example, if you're using version 10.0.39, you can pause the update to version 10.0.40. However, you can't pause the update to version 10.0.41. You must take at least two updates per year.

> [!IMPORTANT]
> There's no way to pause more than one consecutive service update by using Lifecycle Services. Microsoft grants additional pauses beyond the standard pause allowance only when it confirms an update-blocking Microsoft product bug or regression and no viable workaround exists.
>
> Customers are expected to test service updates in sandbox environments as early as possible and report potential Microsoft issues immediately to support. Microsoft must have sufficient time to investigate and validate the issue before an exception can be considered. Requests submitted too close to a scheduled or mandatory update date are rejected if there's insufficient time to complete the investigation.
>
> An open support request alone doesn't qualify for an additional pause. If Microsoft determines that a viable workaround is available, the update isn't paused.
>
> Issues in third-party solutions, ISV applications, partner customizations, or other non-Microsoft components aren't eligible for additional pause approvals. Customers are responsible for working with the applicable solution provider to obtain a fix and validate compatibility before the scheduled update date.
>
> If you pause updates to a sandbox environment, updates are automatically paused for the corresponding production environment because Microsoft always updates configured sandbox environments before production environments.

## Can I pause updates to my additional sandbox environments only?

**No**, you can't pause updates to additional sandbox environments only.

## What if the update to the default sandbox environment is paused?

If you pause the update to the default sandbox environment, the updates to the production environment and all additional sandbox environments are also paused.

## How do I pause updates?

To pause updates, follow these steps:

1. In Lifecycle Services, in your implementation project, open the **Project settings** page.

    This page has a new tab named **Update settings**.

1. In the **Pause Updates** section, on the **Update settings** tab, select **Pause upcoming update**.
1. In the dialog box that appears, select whether you want to pause updates to your production environment only, or to both your sandbox environment and your production environment.
1. Select **Next**.
1. Select your reason for pausing updates. If you select **Issue found during validations**, enter a valid support ticket number. You can add any other details that help Microsoft understand why you want to pause updates.
1. When you finish, select **Confirm**.

You can also edit an existing pause to cancel it so that updates resume. To edit a pause, select **Pause upcoming update**. The maximum of one update pause still applies. Therefore, you can't edit the pause to extend its duration past one update.

Whenever you pause an update or edit an existing pause, a notification appears at the top of the **Update settings** tab. This notification shows what version was paused. All stakeholders (the project owner and environment manager) also receive an email to inform them that a service update for the selected environments was paused. If someone cancels an existing pause and resumes updates, the notification disappears, and an email is sent to inform the stakeholders the paused update resumed.

> [!IMPORTANT]
> You can pause an update through Lifecycle Services up to four hours before the start of the downtime window.
>
> You can cancel a pause and resume updates up to seven days before the start of the downtime date. If there are fewer than seven days before your downtime starts, you can't cancel a pause.

## What happens after the pause duration expires?

Cumulative service updates help guarantee that customers always run on the latest set of fixes that Microsoft releases, so they get the best service experience. Therefore, you can't pause updates indefinitely.

You can cancel a pause and resume updates in two ways:

- Someone manually cancels a pause, as explained in the previous section.
- The duration that you set for the pause expires, and updates to the configured environments automatically resume.

In both cases, the system sends an email to inform the stakeholders.

For more information about service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
