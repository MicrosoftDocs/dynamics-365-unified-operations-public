---
# required metadata

title: Configure job card for devices
description: This article describes the various options for configuring the job card device.
author: johanhoffmann
ms.date: 05/29/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JmgRegistrationSetupTouch, JmgRegistrationTouchUserConfiguration
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: 10.0.12
---

# Configure job card for devices

[!include [banner](../includes/banner.md)]

The job card device is used by the shop floor workers to register their daily work, such as when jobs are started, reporting feedback on jobs, registering indirect activities, and reporting absence. These registrations are the basis for tracking progress and cost on production orders and for calculating the basis for the workers' pay. This article describes the various options for configuring job card devices.

## Enable new features in feature management

A few of the settings described in this article must be enabled on your system before they will be available to you. Use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to enable any or all of the following features as required.

### Generate license plate

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *License plate for reporting as finished added to the Job Card Device*<br>(As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management version 10.0.25, this feature is mandatory.)
1. *Enable automatic generation of license plate number when reporting as finished in the job card device*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory.)

### Print label

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *License plate for reporting as finished added to the Job Card Device*<br>(As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management version 10.0.25, this feature is mandatory.)
1. *Print label from Job Card Device*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory.)

### Allow locking of touch screen

As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Feature for locking job card device and job card terminal so that they can be sanitized* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Manage your device configurations

To set up your device configurations, go to **Production control > Setup > Manufacturing execution > Configure job card for devices**. The **Configure job card for devices** page opens, which shows a list of existing configurations. From here, you can do the following: 

- Select any device configuration listed in the left column to view and edit it.
- Select **New** on the Action Pane to add a new device configuration to the list. Then enter a name in the **Configuration** field to identify the new configuration. The value you enter here must be unique among all device configurations, and you won't be able to edit it later.

Refer to following sections for details about each of the settings for configuring job card devices.

## General settings

The **General** FastTab lets you configure each of the various options available for the selected device configuration. The following settings are available:

- **Report quantity at clock-out** - Set this to **Yes** to prompt workers to report feedback on jobs in progress when clocking out. When set to **No**, workers won't not be prompted.
- **Lock employee** -  When this option is set to **No**, each worker will be logged out immediately after they make a registration (such as a new job), and then the device will return to the log-in page. When this option is set to **Yes**, each worker will stay logged in to the job card device. However, the worker will still be able to log out manually to allow another worker to log in while the job card device remains running under the same system user account. For more information about these types of accounts, see [Assigned users](#assigned-users).
- **Bar code scanner** - Set this to **Yes** to provide an option on the job card device that allows workers register the start of a new job by scanning a bar code.
- **Use the actual time of registration** - Set this to **Yes** to set the time for each new registration to be equal to the exact time that registration was submitted by a worker. Set to **No** to use the log-in time instead. You'll usually want to set this to **Yes** if you have enabled the **Lock employee** and/or **Single worker** options, where workers often remain logged in for longer periods.
- **Single worker** - Set this option to **Yes** if only one worker uses each job card device where this configuration is active. When this option is selected, the **Lock employee** option is automatically set to **Yes**. In addition, this option removes the requirement (and ability) for the worker to log in using a badge ID (or similar). Instead the worker signs in to Supply Chain Management using a system user account linked to a *time registered worker* (from the *workers* table) and gets logged in to the job card device as that worker at the same time.  For more information about these types of accounts, see [Assigned users](#assigned-users).
- **Allow workers to set personal filters** - Set this option to **Yes** to allow workers to filter the jobs shown to them on the device. The worker can modify values for any of the three filter criteria: **Production unit**, **Resource group** and **Resource**. Only jobs that are scheduled on resources matching the selected filter criteria will be shown on the device. You can also assign default values for any or all of these criteria, and those will apply even with this option is not selected.
- **Allow locking the touchscreen** - Set this option to **Yes** to allow workers to lock the job card device touchscreen so they can sanitize it. When enabled, a **Lock screen for sanitizing** button is added to the device log-in page. When a worker selects this button, the touchscreen temporarily locks to prevent unintended input and a countdown timer is shown. The worker can now safely clean the device and the screen. When the countdown completes, the touchscreen automatically unlocks again.
- **Screen lock duration** - When the **Allow locking touchscreen** option is enabled, use this option so specify number of seconds the touchscreen should be locked for sanitizing. The duration must be between 5 and 120 seconds.
- **Production unit** - Select a production unit to be applied as a default filter criterion for the list of jobs shown to each worker. Only jobs that are scheduled on resources grouped under the selected production unit will initially be displayed by the device. If **Allow workers to set personal filters** is enabled, workers will be able to edit this value, otherwise this filter will always apply when this device configuration is active.
- **Resource group** - Select a resource group to be applied as a default filter criterion for the list of jobs shown to each worker. Only jobs that are scheduled on resources grouped under the selected resource group will initially be displayed by the device. If **Allow workers to set personal filters** is enabled, workers will be able to edit this value, otherwise this filter will always apply when this device configuration is active.
- **Resource** - Select a resource to be applied as a default filter criterion for the list of jobs shown to each worker. Only jobs that are scheduled on the selected resource will initially be displayed by the device. If **Allow workers to set personal filters** is enabled, workers will be able to edit this value, otherwise this filter will always apply when this device configuration is active.
- **Generate license plate** - Set this option to **Yes** to generate a new license plate each time a worker uses the job card device to report as finished. The license plate number is generated from a number sequence set up on the **Warehouse management parameters** page. When set to **No**, workers must specify an existing license plate when reporting as finished.
- **Print label** - Set this option to **Yes** to print a license plate label when a worker uses the job card device to report as finished. The configuration of the label is set up in document routing, as described in [Document routing label layouts](../warehousing/document-routing-layout-for-license-plates.md).

<a name="assigned-users"></a>

## Assigned users

Use the **Assigned users** FastTab to associate one or more system users with the current device configuration. Each system user can only be assigned one job device configuration.

When setting up a device, an IT worker typically signs in to Supply Chain Management using a system user account. Thereafter, the job device configuration associated with that system user applies for as long as that system user remains signed in. These system user accounts are typically limited to allow access only to the job card device page and no other part of Supply Chain Management.

After the system user is signed in and the job device configuration is loaded, workers can then log in to the job card device using their *time registered worker* account (for example, by scanning a bar code on their badge) so they can start new jobs and make other kinds of registrations. Various workers can log in and out during the day, while the same device configuration remains in effect on that machine because the system user remains signed in to Supply Chain Management for the day.

However, as mentioned previously, when you use a device configuration with the **Single worker** option, workers themselves typically sign in to Supply Chain Management using a system user linked to their own *time registered worker* account, so they load the device configuration and log in as a worker on the job card device at the same time.

## Additional resources

[Report as finished from the job card device](report-finished-job-device.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]