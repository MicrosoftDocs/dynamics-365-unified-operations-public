---
# required metadata

title: Configure the production floor execution interface
description: This topic describes how to create one or more configurations production floor execution interface. When you open the production floor execution interface, it automatically loads a selected configuration and job filter that is specific for that browser and device. In the configuration, you set the policies that must be applicable for a specific usage.
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

The production floor execution interface is used by shop floor workers to register their daily work, such as when starting a job, reporting feedback on jobs, registering indirect activities, and reporting absence. These registrations are the basis for tracking progress and cost on production orders and for calculating the basis for the workers' pay.

When you open the production floor execution interface, it automatically loads a selected configuration and job filter that is specific for that browser and device. In the configuration, you set the policies that must be applicable for a specific usage, such as:

- On a device located the company hall, employees clock-in when they come into the office and clock-out when they leave for the day.

- On a device located the shop floor, machine operators register when they start and complete jobs, and also breaks and indirect activities.

This topic describes the various options for configuring job card devices.

## Enable new features in feature management

A few of the settings described in this topic must be enabled on your system before they will be available to you. Use the [Feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) page to enable any or all of the following features as required.

### Generate license plate

To make this feature available, enable the following features in [feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Enable automatic generation of license plate number when reporting as finished in the job card device*

### Print label

To make this feature available, enable the following features in [feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview) (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Print label from Job Card Device*

### Allow locking the touch screen

To make this feature available, enable the following feature in [feature management](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview):

- *(Preview) Feature for locking job card device and job card terminal so that they can be sanitized*

## Work with production floor execution configurations

To create and maintain device configurations, go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**. The **Configure production floor execution** page opens, which shows a list of existing configurations. From here, you can do the following:

- Select any production floor configuration listed in the left column to view and edit it.

- Select **New** on the Action Pane to add a new device configuration to the list. Then enter a name in the **Configuration** field to identify the new configuration. The value you enter here must be unique among all device configurations, and you won't be able to edit it later.

Then configure each of the various options for the selected device configuration. The following settings are available:

- **Report quantity at clock-out** - Set this to *Yes* to prompt workers to report feedback on jobs in progress when clocking out. When set to *No*, workers won't be prompted.

- **Lock employee** - When this option is set to *No*, each worker will be signed out immediately after they make a registration (such as a new job), and then the device will return to the sign-in page. When this option is set to *Yes*, each worker will stay signed in to the job card device. However, the worker will still be able to sign out manually to allow another worker to sign in while the job card device remains running under the same system user account. For more information about these types of accounts, see [Assigned users](config-job-card-device.md#assigned-users).

- **Use the actual time of registration** - Set this to *Yes* to set the time for each new registration to be equal to the exact time that registration was submitted by a worker. Set to *No* to use the sign-in time instead. You'll usually want to set this to *Yes* if you have enabled the **Lock employee** and/or **Single worker** options, where workers often remain signed in for longer periods.

- **Single worker** - Set this option to *Yes* if only one worker uses each job card device where this configuration is active. When this option is selected, the **Lock employee** option is automatically set to *Yes*. In addition, this option removes the requirement (and ability) for the worker to sign in using a badge ID (or similar). Instead the worker signs in to Supply Chain Management using a system user account linked to a *time registered worker* (from the *workers* table) and gets signed in to the job card device as that worker at the same time.

- **Allow locking the touchscreen** - Set this option to *Yes* to allow workers to lock the job card device touchscreen so they can sanitize it. When enabled, a **Lock screen for sanitizing** button is added to the device sign-in page. When a worker selects this button, the touchscreen temporarily locks to prevent unintended input and a countdown timer is shown. The worker can now safely clean the device and the screen. When the countdown completes, the touchscreen automatically unlocks again.

- **Screen lock duration** - When the **Allow locking touchscreen** option is enabled, use this option so specify number of seconds the touchscreen should be locked for sanitizing. The duration must be between 5 and 120 seconds.

- **Generate license plate** - Set this option to *Yes* to generate a new license plate each time a worker uses the job card device to report as finished. The license plate number is generated from a number sequence set up on the **Warehouse management parameters** page. When set to *No*, workers must specify an existing license plate when reporting as finished.

- **Print label** - Set this option to *Yes* to print a license plate label when a worker uses the job card device to report as finished. The configuration of the label is set up in document routing, as described in [Document routing layout for license plate labels](../warehousing/document-routing-layout-for-license-plates.md).

## Clean up job configurations

When the shop floor supervisor sets up the production floor execution interface, he or she selects a configuration and a job filter. These selections are stored in a reference table in Supply Chain Management, and the browser uses an ID stored in a local cookie to find the right row in that table. The table also logs the date and time since the last time a worker signed in to each device.

A batch job periodically cleans entries in the references table for devices that have not logged any activity within the last 60 days. You can also clean the entries at any time by executing it manually as follows:

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. On the Action Pane, select **Clean up client configurations** to open the **Clean up client configuration** dialog box.
1. Set **Number of days** to the number of days of inactivity (before today) to consider. You will remove all configurations and sign-in records for devices that have not been active during that time.
1. Select **OK** to clean up the relevant configurations according to your **Number of days** setting.
