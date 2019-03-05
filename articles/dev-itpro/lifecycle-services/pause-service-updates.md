---
# required metadata

title: Pause service updates through Lifecycle Services (LCS)
description: This topic provides information for you to pause service updates to your environments.
author: manalidongre
manager: AnnBe
ms.date: 03/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# Pause service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This topic explains how to pause getting updates to your sandbox and production environments using Lifecycle Services (LCS).

> [!IMPORTANT]
> This feature is available only for customers that are on **version 8.1 and above** and are **not** part of the [First release](../../fin-and-ops/get-started/public-preview-releases.md) program. We are working on enabling this for First release customers and for customers that are on older versions of the product. 

With One Version, Microsoft will update your configured sandbox and production environment to the latest service update released by Microsoft. Microsoft notifies you of an upcoming update to your environment via email as well as through notifications in LCS. At this point if you are for some reason unable to move forward with the update you have the option to pause the update through LCS.

For more details on how to change the configured sandbox environment and set the production update cadence, see [CConfigure service updates through Lifecycle Services (LCS)] (configure-service-updates.md).

## Who can pause a service update?
The ability to pause updates is only available for **implementation projects** and to users (customer/partner) who are assigned to the **project owner** role in LCS.

Our goal with One Version is that customers are always running on the latest set of fixes released by Microsoft to ensure that you have the best service experience and hence we don't allow pausing updates forever.

To be able to pause updates through LCS, you cannot be more than 2 updates behind the latest update released by Microsoft. For example, if the last update released by Microsoft is version 8.1.3, then a customer that is on version 8.1.2 and version 8.1.1 **will** be able to pause. However, a customer that is on version 8.1.0 **will not** be able to pause as they are more than 2 releases behind.

## What can I pause?
You have the following options if you choose to pause updates:

- You can pause getting updates only to production environment.
- You can pause updates to both sandbox and production environments.

You can pause only up to 2 continuous updates at a time. You will not be allowed to pause more than 2 updates. This is inline with what is communicated that you will be able to pause up to 3 months, which is 2 updates. For example, if you are on version 8.1.3, then you will be able to pause update version 10.0.0 and version 10.0.1. You will not be able to pause version 10.0.2.

>[!NOTE]
>If you pause getting updates to sandbox, production will be auto selected as we always update the configured sandbox before updating production.

## How do I pause?
To pause getting updates use the following steps:

1. Navigate to the **Project Settings** page in your  **implementation**  project.
2. A new tab called **Update settings** will be available that has the pause update option.
3. Toggle the Pause updates slider **ON**.
4. Click on **Edit Settings** button to specific what you want to pause.
5. On the slider that opens, select if you want to pause getting updates to production only or if you want to pause both sandbox and production.
6. Click **Next**.
7. Select the **Reason** for pausing getting updates. If you select **Issue found during validations** as the reason, you will need to enter a valid support ticket number. You can add any additional details so that Microsoft can understand why you'd like to pause updates.
8. Select **Confirm** once you are done.

You have the option to **Edit an existing pause** to either pause for a longer duration or to un-pause/resume updates. You can do so by clicking on **Edit Settings**. The rest of the steps and restrictions that apply in terms of how many updates you can pause will still be there.

You have the option to **Cancel a pause** and resume getting updates to your environments. To cancel, toggle the Pause updates slider **OFF**.

Any time you choose to pause updates or edit an existing pause, the Update settings page will get a notification bar at the top showing what has been paused.  An email is also sent to all the stakeholders (project owner and environment manager) notifying them that service updates have been paused to the selected environments. If someone cancels the pause and chooses to resume updates the notification bar goes away and an email is sent informing the stakeholders that updates are now resumed.

>[!IMPORTANT]
>You have the option to pause updates up to 4 hours prior to start of the downtime window. Once we have crossed the 4 hour prior to downtime window limit, you will not be allowed to pause through the LCS user interface.

## What happens after the pause duration expires?
Our goal with One Version is that customers are always running on the latest set of fixes released by Microsoft to ensure you have the best service experience and hence we don't allow pausing updates forever. Once the pause duration expires, service updates will be resumed to the configured environments.

Updates are resumed after a pause for two reasons:

1. Someone cancelled an ongoing pause.
2. Pause duration has expired and updates are automatically resumed on the configured environments.

An email notifying the stakeholders is sent in both the scenarios.

For more details about One Version and Microsoft-managed service updates, see [One Version service updates FAQ](../../fin-and-ops/get-started/one-version.md).
