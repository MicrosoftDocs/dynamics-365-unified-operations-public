---
# required metadata

title: Get notified about Service Updates through Lifecycle Services
description: This topic provides information for how you can get notifications around service updates to your environments.
author: manalidongre
manager: AnnBe
ms.date: 06/22/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 266824
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Get notified about Service Updates through Lifecycle Services

[!include [banner](../includes/banner.md)]

This topic explains how you can stay up to date about the service updates from Microsoft.

With ONE Version, Microsoft will update your configured sandbox and production environment to the latest service update released by Microsoft. Microsoft notifies you of an upcoming update to your environment via email as well as through notifications in LCS.

Following are the different types of notifications you will get:

1. **Notification sent 5 days prior to the update** :
Microsoft notifies you 5 days prior to updating your environment. Once you have configured your update cadence you will get notifications about an upcoming update 5 days prior to the update.
- Email notification:
  Project owners, environment manager and users listed as additional stakeholders for an environment are notified via email about the     upcoming update.

- Notification bar on the environment details page:
  A toast notification shows up on the environment details page informing the customer of the upcoming update.

- Upcoming update reflects the update:
  On the LCS environment details page, select **Maintain \&gt; Upcoming Update**. This opens a slider which will contain details about     the upcoming update.

2. **Notification sent 1 hour prior to the actual update** :
1 hour prior to the start of the downtime window, users within Finance and Operations will get a notification asking them to save their work as the environment will be taken down for an update.

3. **Notification sent on the completion of the update** :
Once we are done updating your configured environment, Microsoft will notify you about the outcome of the update regardless of whether the update was successfully applied or not. This email is sent all users that are assigned the project owner, environment manager and users designated as the additional stakeholders for the environment. If for some reason we are unable to start the update the email will contain a reason explaining why the update was not started.

>[!NOTE]
> Once you receive the notification, if you are unable to move forward with the update for some reason you can learn more on how to pause getting updates to configured sandbox and production environment by checking the [Pause Service Updates](pause-service-updates.md) topic.

> [!NOTE]
> For more details on ONE Version and Microsoft managed service updates, check the [ONE Version FAQ](Dynamics-365-Operations/articles/fin-and-ops/get-started/one-version.md) topic.
