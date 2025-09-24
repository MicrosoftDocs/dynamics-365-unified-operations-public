---
title: Get notified about service updates through Lifecycle Services (LCS)
description: Learn about the various ways that you can be notified about service updates to your environments the notifications that you receive.
author: angelmarshall
ms.author: tsmarsha
ms.topic: article
ms.date: 11/25/2024
ms.custom:
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-3-31
ms.search.form: 
ms.dyn365.ops.version: Platform update 24 
---

# Get notified about service updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article explains how you can stay up to date about service updates from Microsoft.

Microsoft uses service updates to update your configured sandbox and production environments to the latest released version. Microsoft notifies you about upcoming updates to your environments via email and through notifications in Microsoft Dynamics Lifecycle Services (LCS).

Here are the different types of notifications that you will receive:

- **Notification when an update is made available:** When a new release is made generally available, Microsoft surfaces a notification in your implementation projects' action center. You can then save that update in your projects' asset library, if you want to apply the update to your environments before Microsoft does an automatic update. When Microsoft does an automatic update, it also saves a copy of the update in your projects' asset library. 
- **Notification that is sent five days before the update:** Microsoft notifies you five days before it updates your environment. After you've configured your update cadence, you will receive notifications about upcoming updates five days before they occur. These notifications take three forms:

    - **Email notification:** Project owners, environment managers, and users who are listed as additional stakeholders for an environment are notified by email about the upcoming update.
    - **Notification bar on the environment details page:** A notification that appears on the environment details page in LCS informs the customer about the upcoming update.
    - **Upcoming update reflects the update:** On the environment details page in LCS, select **Maintain &gt; Upcoming Update** to open a dialog box that contains details about the upcoming update.

    > [!IMPORTANT]
    > Notifications for Product quality updates (PQU) aren't delivered this way. For more information on PQUs, see :
    > 
    > [Proactive quality updates overview](../get-started/quality-updates.md)
    > 
    > [Release schedule for proactive quality updates](../get-started/quality-updates-faq.md)

- **Notification that is sent one hour before the update:** One hour before the start of the downtime window, users in the application receive a notification. This notification asks users to save their work, because the environment will be taken down for an update.
- **Notification that is sent when the update is completed:** After Microsoft has finished updating your configured environment, it notifies you by email about the outcome of the update. This email is always sent, regardless of whether the update was successfully applied. It's sent to project owners, environment managers, and users who are listed as the additional stakeholders for the environment. If Microsoft can't start the update for some reason, the email includes a reason to explain why the update wasn't started.

After you receive a notification, if you can't proceed with the update for some reason, you can pause it. For more information about how to pause updates to configured sandbox and production environments, see [Pause service updates through Lifecycle Services (LCS)](pause-service-updates.md).

For more information about One Version and Microsoft-managed service updates, see [One Version service updates FAQ](../../fin-ops/get-started/one-version.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
