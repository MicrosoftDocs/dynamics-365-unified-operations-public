---
# required metadata

title: Pause service updates through Lifecycle Services (LCS)
description: This article explains how to pause service updates to your environments.
author: laneswenka 
ms.date: 09/29/2023
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

This article explains how to pause updates to your sandbox and production cloud environments by using Microsoft Dynamics Lifecycle Services (LCS). This article doesn't apply to on-premises environments.

Microsoft updates your configured sandbox and production environments to the latest service update that Microsoft has released. Microsoft notifies you about upcoming updates to your environments via email and through notifications in LCS. At that point, if you can't proceed with the update for some reason, you can pause it through LCS.

> [!Important]
> Beginning February 19, 2024, the number of maximum consecutive pauses to update allowed will be reduced from three to one. This change along with the service update cadence from 7 to 4 releases maintains the same minimum two service updates annually as before. See [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

For more information about how to change the configured sandbox environment and set the production update cadence, see [Configure service updates through Lifecycle Services (LCS)](configure-service-updates.md).

## Who can pause service updates?

Only users (customers or partners) who are assigned to the **project owner** role in LCS can pause updates. Additionally, updates can be paused only for **implementation projects**.

Staying current with service updates helps guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

Beginning February 19, 2024, the number of maximum consecutive pauses to update allowed will be reduced from three to one. This means customers are required to take a minimum of two service updates annually.

You can't use LCS to pause updates if any sandbox and production environments in your project are two updates behind the latest update that Microsoft has released. For example, if the latest update that Microsoft has released is version 10.0.41, customers who have environments that are on version 10.0.40 **can** pause updates. However, customers who have environments on version 10.0.39 **can't** pause updates, because they are two updates behind. If any sandbox or production environment is too far behind, you will receive the following error message if you try to pause updates via LCS:

> One or more sandbox and/or production environments are not compliant with Microsoft's service update policy. All your environments need to be compliant before you can pause updates.

## What can I pause?

If you decide to pause updates, you have these options:

- Pause updates only to your production environment.
- Pause updates to both your sandbox environment and your production environment.
- Pause updates to additional sandbox environments by pausing updates to your production environment.

> [!NOTE]
> If updates to the production environment are paused, all updates to additional sandbox environments will be paused too.

You can pause a maximum of one consecutive update at a time. For example, if you're using version 10.0.39, you can pause the 10.0.40 update. However, you can't pause the update to version 10.0.41. We require that you take at least two updates in a year.

> [!IMPORTANT]
> There is no way to pause more than one consecutive update, regardless of your industry or business schedule. For example, if you're two updates behind, and you find a critical issue with the Microsoft service update during validations in your sandbox environment after the update, you can contact Microsoft Support to pause the update to your production environment. The issue must be logged as an active bug/regression with Microsoft. This requirement applies only if you're more than two updates behind and can't use the pause updates functionality that is available in LCS to pause the update to your production environment.
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

You can also edit an existing pause to cancel it so that updates are resumed. To edit a pause, select **Pause upcoming update**. The max one update pause limitation still applies, i.e. you cannot edit to extend the pause duration past one update.

Any time that you pause an update or edit an existing pause, a notification appears at the top of the **Update settings** tab. This notification shows what has been paused. An email is also sent to all stakeholders (the project owner and environment manager) to inform them that a service update for the selected environments has been paused. If someone cancels an existing pause and resumes updates, the notification disappears, and an email is sent to inform the stakeholders that the paused update has been resumed.

> [!IMPORTANT]
> You can pause an update through LCS until four hours before the start of the downtime window.
>
> You can cancel a pause and resume updates only seven days or more before the start of the downtime date. If there are less than seven days before your downtime starts, you won't be able to cancel a pause.

## What happens after the pause duration expires?

Cumulative service updates help guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

There are two ways to cancel a pause, so that updates are resumed:

- Someone manually cancels a pause, as explained in the previous section.
- The duration that was set for the pause expires, and updates to the configured environments are automatically resumed.

In both cases, an email is sent to inform the stakeholders.

For more information about service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
