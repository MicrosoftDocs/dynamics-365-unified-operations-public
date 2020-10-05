---
# required metadata

title: Set up a device to run the production floor execution interface
description: The production floor execution interface is set up for each specific device on the production floor. Companies typically set up each device differently depending on the purpose the device serves. For example, a company could have one device in the reception area, where workers clock in and clock out, and another on the shop floor where workers manage their jobs.
author: johanhoffmann
manager: tfehr
ms.date: 10/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-10-05
ms.dyn365.ops.version: Release 10.0.15
---

# Set up a device to run the production floor execution interface

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The production floor execution interface is set up for each specific device on the production floor. Companies typically set up each device differently depending on the purpose the device serves. For example, a company could have one device in the reception area, where workers clock in and clock out, and another on the shop floor where workers manage their jobs.

## Set the configuration and filters for a specific device

To set configuration and job filters for a device, sign in to the **Production floor execution** page using an account with a security role that includes the *Maintain time supervisor* duty. Of the out-of-box security roles, only *Shop floor supervisor* have this duty. To set the configuration and filters, do the following:

1. Go to the device you want to set up and sign in to Supply Chain Management as a shop floor supervisor (using an account that includes the *Maintain time supervisor* duty).
1. Make sure a configuration is available for the device that you are setting up. If no configuration already exists, then a default configuration is provided. For more information about how to make a configuration, see: [Configure the production floor execution interface](production-floor-execution-configure.md).
1. Go to **Production control \> Manufacturing execution \>Production floor execution.**
1. Depending on whether the production floor execution interface has already been configured on the current device, you will either see a welcome screen (if the device has never been configured) on the sign-on screen (if it has already been configured at least once). Either way, select the **Configure** button.
1. Select a configuration from the list.
1. Select **Next.**
1. Select one or more filters to apply to the current device. These settings will limit the jobs shows on this device to help make sure that only relevant jobs appear. To set a filter, select the filter type to open a list of values and then select the value to filter on. The following filters are available:
    - **Production unit**: This is the highest-level filter. It typically refers to a large work area with several resource groups and individual resources in it.
    - **Resource group**: This is a mid-level filter. It typically refers to a collection of related resources in a limited area of the workspace. If you select a **Production unit** first, then the list of resource groups will only show groups from that unit. Otherwise, all available resource groups are shown.
    - **Resource**: This is the most specific filter. It typically refers to a specific machine or other single resource. If you select a **Resource group** and/or **Production unit** first, then the list of resource groups will only show resources from that group or unit. Otherwise, all available resources are shown.

1. Select **OK**.
1. The sign-in screen is shown and your device is ready for use.

## Allow a worker to override the default filters

You can give specific workers permission to change the filter settings on any device that they use. For workers that have this permission, the production floor execution interface provides a **Filter** button on the **All jobs** and **Active job** pages.

> [!NOTE]
> When a worker changes a filter, the new filter will apply from then on for all users who sign in to the device.

To allow a worker to override the default job filters set up for a device:

1. Go to **Time and attendance \> Setup \> Time registration workers**.
1. Select a worker from the list to open that worker's **Time registration workers** page.
1. Open the **Time registration** tab and set **Set filters** to *Yes*.

## Run the interface in full screen

Often, you will run the production floor execution interface on a device used exclusively for this purpose. Therefore, it might make sense to run the interface in full-screen mode without showing any navigation and/or browser chrome.

- To hide the left bar shown by Supply Chain Management, add the following text to the end of the URL in the browser address bar: `&limitednav=true`.
- To also hide the address bar in the browser, use the browser's native full-screen mode. (See your browser's documentation for instructions.)

 The following illustration shows how the interface looks by default (top) compared to how it looks when running full-screen and with the left tab hidden (bottom).

![Standard vs full screen interface](media/pfei-full-screen.png "Standard vs full-screen interface")

## Extend the session past 12 hours

By default, the production floor execution interface automatically signs out if nobody uses it for 12 hours. Thereafter, a Supply Chain Management user must sign in again. However, you can extend the time-out limit to up to 90 days.

To extend the time-out limit, sign in to Supply Chain Managment. Then go to **System administration \> Users \> Session extensions**. Then specify the Supply Chain Management user account used to sign in to the device and the number of hours the session should stay active for.
