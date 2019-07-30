---
# required metadata

title: Set the session idle timeout
description: This topic describes how to et the session idle timeout.
author: hasaid
manager: AnnBe
ms.date: 07/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SystemAdministrationWorkspaceForm
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 13531
ms.search.region: Global
# ms.search.industry: 
ms.author: hasaid
ms.search.validFrom: 2019-08-02
ms.dyn365.ops.version: AX 7.0.0

---

# Set the session idle timeout

[!include [banner](../includes/banner.md)]

> [!NOTE]
> This feature is available in Platform update 29 and later.

The session idle timeout setting represents the amount of time a user can be inactive before the user's session times out and closes. It only affects user browser sessions.

You can set the values from 5 minutes to 60 minutes.

This function is exposed to the UI and has a default value of 30 minutes. You can set the value up to 60 minutes, but doing so might cause extra load on the system.

> [!IMPORTANT]
> If you previously set a session idle timeout in the web.config (**WebClientStatefulSessionTimeoutInSeconds** key) through a support request, then that old value will still be honored. The change in default will only affect those who had not explicitly set a new session idle timeout in the web config.

To change the value from the UI, follow these steps:

1. From the Finance and Operations Dashboard, click on the **System Administration** workspace.
2. Click on **System Settings**. This opens the **System parameters** form.
3. In the **Session management** section, set the **Session idle timout in minutes** to the desired value.
4. Click **Save**. 

    If you set the value greater than 30, you will be prompted to confirm your selection. The confirmation prompt is "Increasing the idle session timeout can cause extra load on your system, which can lead to a decrease in performance. Are you sure you want to continue?" The higher the value is, the higher the load will be, and the load can affect system performance negatively. Click **Yes** to save the changes, or **No** to revert to the existing value.

