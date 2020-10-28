---
# required metadata

title: Configure the production floor execution interface
description: This topic describes how to create one or more configurations for the production floor execution interface. When you open the production floor execution interface, it automatically loads a selected configuration and job filter that are specific to the browser and device. In the configuration, you set the policies that must be applicable for a specific usage.
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

# Configure the production floor execution interface

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Shop floor workers use the production floor execution interface to register their daily work, such as when they start a job, report feedback about jobs, register indirect activities, and report absence. These registrations are the basis for tracking progress and cost on production orders, and for calculating the basis for the workers' pay.

When you open the production floor execution interface, it automatically loads a selected configuration and job filter that are specific to the browser and device. In the configuration, you set the policies that must be applicable for a specific usage. Here are some usage examples:

- On a device in the company hall, employees clock in when they come into the office, and they clock out when they leave for the day.
- On a device on the shop floor, machine operators register when they start and complete jobs. They also register breaks and indirect activities.

This topic describes the various options for configuring job card devices.

## Turn on new features in feature management

The production floor execution interface itself, plus several of the optional settings that are described in this topic, must be turned on in your system before they will be available to you. Use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to turn on any or all of the features described in the following subsections as required.

### The production floor execution interface

This is the primary feature described in this topic. It adds the production floor execution interface to your system.

To make this feature available, turn on the following feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):  
- Production floor execution

### Generate license plates

These features make license plate functionality available to the  production floor execution interface.

To make this feature available, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

1. License plate for reporting as finished added to the Job Card Device
1. Enable automatic generation of license plate number when reporting as finished in the job card device

### Print labels

These features make label printing functionality available to the production floor execution interface.

To make this feature available, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

1. License plate for reporting as finished added to the Job Card Device
1. Print label from Job Card Device

### Allow locking the touch screen

This feature adds a button to the production floor execution interface that enables workers to sanitize the touch screen.

To make this feature available, turn on the following feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- Feature for locking job card device and job card terminal so that they can be sanitized

## Work with production floor execution configurations

To create and maintain device configurations, go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**. The **Configure production floor execution** page shows a list of existing configurations. On this page, you can perform the following actions:

- Select any production floor configuration that is listed in the left column to view and edit it.
- Select **New** on the Action Pane to add a new device configuration to the list. Then, in the **Configuration** field, enter a name to identify the new configuration. The name that you enter must be unique among all device configurations, and you won't be able to edit it later.

Next, configure the various settings for the selected device configuration. The following fields are available:

- **Report quantity at clock-out** – Set this option to *Yes* to prompt workers to report feedback about jobs that are in progress when they clock out. When this option is set to *No*, workers won't be prompted.
- **Lock employee** – When this option is set to *No*, workers will be signed out immediately after they make a registration (such as a new job). The device will then return to the sign-in page. When this option is set to *Yes*, workers will stay signed in to the job card device. However, a worker can manually sign out so that another worker can sign in while the job card device continues to run under the same system user account. For more information about these types of accounts, see [Assigned users](config-job-card-device.md#assigned-users).
- **Use the actual time of registration** – Set this option to *Yes* to set the time for each new registration to the exact time when the worker submitted the registration. When this option is set to *No*, the sign-in time is used instead. You will usually want to set this option to *Yes* if you've set the **Lock employee** and/or **Single worker** option to *Yes* in cases where workers often remain signed in for longer periods.
- **Single worker** – Set this option to *Yes* if only one worker uses each job card device where this configuration is active. When this option is set to *Yes*, the **Lock employee** option is automatically set to *Yes*. In addition, this setting removes the requirement (and ability) for the worker to sign in by using a badge ID (or another similar ID). Instead, the worker signs in to Microsoft Dynamics 365 Supply Chain Management by using a system user account that is linked to a *time registered worker* (from the *workers* table), and gets signed in to the job card device as that worker at the same time.
- **Allow locking the touchscreen** – Set this option to *Yes* to allow workers to lock the touchscreen of the job card device so that they can sanitize it. When this option is set to *Yes*, a **Lock screen for sanitizing** button is added to the device sign-in page. When a worker selects this button, the touchscreen is temporarily locked to prevent unintended input. A countdown timer is also shown. The worker can then safely clean the device and the screen. When the countdown is completed, the touchscreen is automatically unlocked.
- **Screen lock duration** – When the **Allow locking touchscreen** option is set to *Yes*, use this option to specify the number of seconds that the touchscreen should be locked for sanitizing. The duration must be between 5 and 120 seconds.
- **Generate license plate** – Set this option to *Yes* to generate a new license plate every time that a worker uses the job card device to report as finished. The license plate number is generated from a number sequence that is set up on the **Warehouse management parameters** page. When this option is set to *No*, workers must specify an existing license plate when they report as finished.
- **Print label** – Set this option to *Yes* to print a license plate label when a worker uses the job card device to report as finished. The configuration of the label is set up in document routing, as described in [Document routing layout for license plate labels](../warehousing/document-routing-layout-for-license-plates.md).

## Clean up job configurations

When the shop floor supervisor sets up the production floor execution interface, they select a configuration and a job filter. These selections are stored in a reference table in Supply Chain Management, and the browser uses an ID that is stored in a local cookie to find the correct row in that table. The table also logs the date and time that a worker last signed in to each device.

A batch job periodically cleans entries in the references table for devices that haven't logged any activity in the last 60 days. You can also manually clean the entries at any time by following these steps.

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. On the Action Pane, select **Clean up client configurations**.
1. In the **Clean up client configuration** dialog box, set the **Number of days** field to the number of days of inactivity (before today) to consider. You will remove all configurations and sign-in records for devices that haven't been active during that time.
1. Select **OK** to clean up the relevant configurations, based on the **Number of days** setting.
