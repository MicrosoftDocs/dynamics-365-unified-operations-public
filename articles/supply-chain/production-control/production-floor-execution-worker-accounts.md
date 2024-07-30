---
title: Set up worker accounts to use the production floor execution interface
description: This article explains how to set up worker accounts to enable workers to sign in and use the production floor execution interface
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/18/2024
ms.custom: 
  - bap-template
---


# Set up worker accounts to use the production floor execution interface

[!include [banner](../includes/banner.md)]

This article explains how to set up worker accounts to enable workers to sign in and use the production floor execution interface.

## Choose sign-in requirements

Workers begin work by signing in to the production floor execution interface. You can choose to require workers to identify themselves using either their personnel number or badge number, and can also choose to require a password.

To choose your sign-in requirements, follow these steps:

1. Go to **Time and attendance** \> **Setup** \> **Time and attendance parameters**.
1. On the **General** tab, make the following settings:
    - **Use password** – If you want to require a password, set this to *Yes*. Set to *No* if you want to allow workers to sign in using only their badge ID or personnel number. If you choose to require a password, you must assign one to each worker account as described later in this article.
    - **Use badge ID** – Set to *Yes* to require users to sign in using their badge ID. Set to *No* to require users to sign in using their personnel number. All worker accounts automatically have a unique personnel number. If you choose to require a badge ID, you must assign one to each worker account as described later in this article..
1. On the Action Pane, select **Save**.

## Set up a worker account

Workers sign in using credentials that are associated with their worker account. You can also set each worker account to prevent or allow the worker to change the filter settings on any device that they use.

To set up a worker account, follow these steps:

1. Go to **Human resources** \> **Workers** \> **Workers**.
1. Either find and open the account you want to set up or select **New** on the Action Pane to create a new worker account.
1. Open the **Time registration** tab.
1. Find the **Activate on registration terminals** button on the **Time registration** FastTab toolbar.
    - If the button is grayed out, then the worker is already set up as a *time registered worker*, in which case you can skip this step.
    - If the button is available, then select it to open the **Create time registration worker** dialog. Make all of the required settings and select **OK**. The worker is now set up as a *time registered worker*.
1. Make the following settings to enable the worker to sign in to the production floor execution interface and choose whether the worker can override default job filters:
    - **Identification** – If you set up your system to require a password when signing in to the production floor execution interface, enter a password for the current worker here.
    - **Badge ID** – If you set up your system to require a badge ID when signing in to the production floor execution interface, enter a badge ID for the current worker here.
    - **Set filters** – To allow a worker to override the default job filters that have been set up for a device, set this option to *Yes*. For more information about this option, see [Set up a device to run the production floor execution interface](production-floor-execution-setup.md).

    > [!NOTE]
    > Each worker's personnel number is automatically assigned by the system and can't be changed. You can read each worker's personnel number next to their name on the details page, or in the **Personnel number** column on the list page. This is the ID that workers must use to sign in if you set up your system to require a personnel number instead of a badge ID.

1. Continue to set up the worker account as required. When you're done, select **Save** on the Action Pane.

## Single worker configuration

It's possible to configure a production floor execution interface device to be used by a single worker. This option removes the requirement (and ability) for the worker to sign in by using a badge ID or personnel number. Instead, the worker signs in to Microsoft Dynamics 365 Supply Chain Management by using a system user account that is linked to a *time registered worker*, and gets signed in to the production floor execution interface as that worker at the same time. For details about how to set up this option, see [Configure the production floor execution interface](production-floor-execution-configure.md).
