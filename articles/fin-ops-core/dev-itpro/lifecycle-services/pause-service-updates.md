---
# required metadata

title: Pause service updates through Lifecycle Services (LCS)
description: This topic explains how to pause service updates to your environments.
author: laneswenka 
ms.date: 04/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

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
ms.author: laswenka
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# Pause service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This topic explains how to pause updates to your sandbox and production cloud environments by using Microsoft Dynamics Lifecycle Services (LCS). This topic doesn't apply to on-premises environments.

Microsoft updates your configured sandbox and production environments to the latest service update that Microsoft has released. Microsoft notifies you about upcoming updates to your environments via email and through notifications in LCS. At that point, if you can't proceed with the update for some reason, you can pause it through LCS.

For more information about how to change the configured sandbox environment and set the production update cadence, see [Configure service updates through Lifecycle Services (LCS)](configure-service-updates.md).

## Who can pause service updates?

Only users (customers or partners) who are assigned to the **project owner** role in LCS can pause updates. Additionally, updates can be paused only for **implementation projects**.

Staying current with service updates helps guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

You can't use LCS to pause updates if any sandbox and production environments in your project are four updates behind the latest update that Microsoft has released. For example, if the latest update that Microsoft has released is version 10.0.25, customers who have environments that are on version 10.0.22, 10.0.23, or 10.0.24 **can** pause updates. However, customers who have environments on version 10.0.21 **can't** pause updates, because they are four updates behind. If any sandbox or production environment is too far behind, you will receive the following error message if you try to pause updates via LCS: 

> One or more sandbox and/or production environments are not compliant with Microsoft's service update policy. All your environments need to be compliant before you can pause updates.

## What can I pause?

If you decide to pause updates, you have these options:

- Pause updates only to your production environment.
- Pause updates to both your sandbox environment and your production environment.
- Pause updates to additional sandbox environments by pausing updates to your production environment.
- Pause updates in your LCS implementation project by updating the environments to a version within N-3, and then pause the updates from LCS. 

> [!NOTE]
> If updates to the production environment are paused, all updates to additional sandbox environments will be paused too. Note how the versions are referenced:
> 
> - Version N is the latest version, such as 10.0.25
> - Version N-1 is one version older than N, such as 10.0.24
> - Version N-2 is two versions older than N, such as 10.0.23
> - Version N-3 is three versions older than N, such as 10.0.22
> - Version N-4 is four versions older than N, such as 10.0.22 (In this example, customers on version 10.0.22 **can't** pause updates.)

You can pause a maximum of three continuous updates at a time. For example, if you're using version 10.0.22, you can pause updates to version 10.0.23, 10.0.24, and 10.0.25. However, you can't pause the update to version 10.0.26. We require that you take at least two updates in a year.

> [!IMPORTANT]
> There is no way to pause more than three updates, regardless of your industry or business schedule. For example, if you're four updates behind, and you find a critical issue with the Microsoft service update during validations in your sandbox environment after the update, you can contact Microsoft Support to pause the update to your production environment. The issue must be logged as an active bug/regression with Microsoft. This requirement applies only if you're more than three updates behind and can't use the pause updates functionality that is available in LCS to pause the update to your production environment.
>
> If you pause updates to your sandbox environment, updates are automatically paused for your production environment too, because Microsoft always updates configured sandbox environments before production environments.

## Can I pause updates to my additional sandbox environments only?
 
**No**, you can't pause updates to additional sandbox environments only.

## What if the update to the default sandbox environment is paused? 

If the update to the default sandbox environment is paused, the updates to the production environment and all additional sandbox environments will also be paused. 

## How do I pause updates?

To pause updates, follow these steps.

1. In LCS, in your implementation project, open the **Project settings** page.

    This page has a new tab that is named **Update settings**.

2. In the **Pause Updates** section, on the **Update settings** tab, select **Pause upcoming update**.
3. In the dialog box that appears, select whether you want to pause updates to your production environment only, or to both your sandbox environment and your production environment.
4. Select **Next**.
5. Select your reason for pausing updates. If you select **Issue found during validations**, you must enter a valid support ticket number. You can add any additional details that will help Microsoft understand why you want to pause updates.
6. When you've finished, select **Confirm**.

You can also edit an existing pause. You can either extend the pause duration, so that updates are paused for a longer time, or cancel it, so that updates are resumed. To edit a pause, select **Pause upcoming update**. The limitations on the number of updates that you can pause still apply.

Any time that you pause updates or edit an existing pause, a notification appears at the top of the **Update settings** tab. This notification shows what has been paused. An email is also sent to all stakeholders (the project owner and environment manager) to inform them that service updates for the selected environments have been paused. If someone cancels an existing pause and resumes updates, the notification disappears, and an email is sent to inform the stakeholders that updates have resumed.

> [!IMPORTANT]
> You can pause updates through LCS until four hours before the start of the downtime window.
>
> You can cancel a pause and resume updates only seven days or more before the start of the downtime date. If there is less than seven days before your downtime starts, you won't be able to cancel a pause.

## What happens after the pause duration expires?

Cumulative service updates help guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

There are two ways to cancel pauses, so that updates are resumed:

- Someone manually cancels an ongoing pause, as explained in the previous section.
- The duration that was set for the pause expires, and updates to the configured environments are automatically resumed.

In both cases, an email is sent to inform the stakeholders.

For more information about service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
