---
# required metadata

title: Pause service updates through Lifecycle Services (LCS)
description: This topic explains how to pause service updates to your environments.
author: angelmarshall
ms.date: 01/31/2022
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
ms.author: tsmarsha
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# Pause service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This topic explains how to pause updates to your sandbox and production cloud environments by using Microsoft Dynamics Lifecycle Services (LCS). This topic does not apply to on-premises environments.

> [!IMPORTANT]
> This feature is available only to customers who are using **version 8.1 and later** or are using **version 7.3**, and who are **not** part of the [First release](../../../fin-ops-core/fin-ops/get-started/public-preview-releases.md) program. Microsoft is working to make the feature available to First release customers. For customers who are on version 7.1, 7.2, or 8.0, you can take the update manually using the regular servicing flows.

Microsoft updates your configured sandbox and production environments to the latest service update that Microsoft has released. Microsoft notifies you about upcoming updates to your environments via email and through notifications in LCS. At that point, if you can't proceed with the update for some reason, you can pause it through LCS.

For more information about how to change the configured sandbox environment and set the production update cadence, see [Configure service updates through Lifecycle Services (LCS)](configure-service-updates.md).

## Who can pause service updates?

Only users (customers or partners) who are assigned to the **project owner** role in LCS can pause updates. Additionally, updates can be paused only for **implementation projects**.

Staying current with service updates helps guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

You can't use LCS to pause updates if you're three or more updates behind the latest update that Microsoft has released. For example, if the latest update that Microsoft has released is version 10.0.0, customers who are on version 8.1.3, version 8.1.2, and version 8.1.1 **can** pause updates. However, customers who are on version 8.1.0 **can't** pause updates, because they are more than three updates behind. Customers who are on version 7.3 can get only platform updates. For example, if the last platform update that Microsoft has released is Platform update 25, customers who are on Platform update 24, Platform update 23, and Platform update 22 **can** pause updates. However, customers who are on Platform update 21 **can't** pause updates.

## What can I pause?

If you decide to pause updates, you have these options:

- Pause updates only to your production environment.
- Pause updates to both your sandbox environment and your production environment.
- Pause updates to additional sandbox environments by pausing your production environment.
- Pause updates in LCS implementation project by updating the environments to a version within N-3 then pause the updates from LCS. 

> [!NOTE]
> If the update to the production environment is paused, all additional sandbox environment updates will be paused as well. Note how the versions are referenced:
> 
> - Version N is the latest version, for example: 10.0.24
> - Version N-2 is one version older than N, for example: 10.0.23
> - Version N-3 is two versions older than N, for example: 10.0.22

You can pause a maximum of three continuous updates at a time. For example, if you're using version 8.1.3, you can pause update version 10.0.0, 10.0.1 and 10.0.2. However, you can't pause update version 10.0.3. In addition, in the month of June, you can pause the next three updates. However, you will not be able to pause updates scheduled for October, November, December and later. Similarly, for customers on version 7.3 for platform only updates, if you’re using Platform update 23 then you can pause update 24, update 25, and update 26, but you cannot pause update 27. We will be releasing 8 updates in a year. We require you to take at least two updates in a year.

> [!IMPORTANT]
>  There is no way to pause more than three updates, regardless of your industry or business schedule. If you are more than three updates behind and you find a critical issue with the Microsoft service update during validations in your sandbox environment after the update, you can contact Microsoft Support to pause the update to your production environment. The issue must be logged as an active bug/regression with Microsoft.  This is only required if you are more than three updates behind and you are unable to use the pause updates functionality available in LCS to pause the update to production.

> If you pause updates to your sandbox environment, updates are automatically also paused for your production environment, because Microsoft always updates configured sandbox environments before production environments.

## Can I pause updates to only my additional sandbox environments?
 
**No**, you can't pause updates to only additional sandbox environments.  

## What if the update to the default sandbox environment is paused? 

If the update to the default sandbox environment is paused, then the updates to the production environment and all additional sandbox environments will also be paused. 

## How do I pause updates?

To pause updates, follow these steps.

1. In LCS, in your implementation project, open the **Project settings** page.

    This page has a new tab that is named **Update settings**.

2. Select the **Update settings** tab in the **Pause Updates** section, and then select **Pause upcoming update**.
3. In the dialog box that appears, select whether you want to pause updates to your production environment only, or to both your sandbox environment and your production environment.
4. Select **Next**.
5. Select your reason for pausing updates. If you select **Issue found during validations**, you must enter a valid support ticket number. You can add any additional details that will help Microsoft understand why you want to pause updates.
6. When you've finished, select **Confirm**.

You can also edit an existing pause. You can either extend the duration of the pause, so that updates are paused for a longer time, or cancel it, so that updates are resumed. To edit a pause, select **Pause upcoming update**. The limitations about the number of updates that you can pause still apply.

Any time that you pause updates or edit an existing pause, a notification appears at the top of the **Update settings** tab. This notification shows what has been paused. An email is also sent to all stakeholders (the project owner and environment manager), to notify them that service updates for the selected environments have been paused. If someone cancels an existing pause and resumes updates, the notification disappears, and an email is sent to inform the stakeholders that updates have resumed.

> [!IMPORTANT]
> You can pause updates through LCS until four hours before the start of the downtime window.

> You can cancel a pause and choose to resume updates only 7 days prior to the start of the downtime date. If you are past that date then you will not be able to cancel a pause.

## What happens after the pause duration expires?

Cumulative service updates help guarantee that customers always run on the latest set of fixes that Microsoft has released, so that they have the best service experience. Therefore, Microsoft doesn't allow updates to be paused indefinitely.

There are two ways to cancel pauses, so that updates are resumed:

- Someone manually cancels an ongoing pause, as explained in the previous section.
- The duration that was set for the pause expires, and updates to the configured environments are automatically resumed.

In both cases, an email is sent to inform the stakeholders.

For more information about service updates, see [One Version service updates FAQ](../../../fin-ops-core/fin-ops/get-started/one-version.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
