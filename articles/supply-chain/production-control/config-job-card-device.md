---
# required metadata

title: Configure job card for devices
description: This topic describes the various options for configuring the job card device
author: johanhoffmann
manager: tfehr
ms.date: 05/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgRegistrationSetupTouch
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: Release 10.0.12
---

# Configure job card for devices

[!include [banner](../includes/banner.md)]

The job card device is used by the shop floor workers to register their daily work, such as when starting jobs, reporting feedback on jobs, registering indirect activities, and reporting absence. These registrations are the basis for tracking progress and cost on production orders and for calculating the basis for the workers' pay. This topic describes the various options for configuring job card devices.

## Enable new features in feature management

A few of the settings described in this topic must be enabled on your system before they will be available to you. Use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to enable any or all of the following features as required:

### Generate license plate

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Enable automatic generation of license plate number when reporting as finished in the job card device*

### Print label

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Print label from Job Card Device*

### Allow locking of touch screen

To make this feature available, enable the following feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

- *(Preview) Feature for locking job card device and job card terminal so that they can be sanitized* <!-- KFM: This looks like the right one. Seems like there is no additional prerequisite. Please confirm. -->

## Manage and configure your devices

To configure your device configurations, go to **Production control > Setup > Manufacturing execution > Configure job card for devices**. The **Configure job card for devices** page opens, which shows a list of existing configurations. From here, you can do the following: <!-- KFM: How does a configuration get activated on a given device?-->

- Select any device configuration listed in the left column to view and edit it.
- Select **New** on the Action Pane to add a new device configuration to the list. Then enter a name in the **Configuration** field to identify the new configuration. The value you enter here must be unique among all device configurations, and you won't be able to edit it later.

See the following sections for details about each of the settings and FastTabs provided here.

## General settings

The **General** FastTab lets you configure each of the various options available for the selected device configuration. The following settings are available here:

- **Report quantity at clock-out** - Set this to **Yes** to prompt workers to report feedback on jobs in progress when clocking out. When set to **No**, workers won't not be prompted.
- **Lock employee** - When this option is set to **Yes**, the job card device won't return to the sign-in page when a worker starts a job. When set to **No**, the job card device page will always return to the sign-in page when a worker starts a job. <!-- KFM: Does this mean that a worker remains signed in until they explicitly sign out? -->
- **Barcode scanner** - Set this to **Yes**, to display a field for identifying a production job.  <!-- KFM: What does this have to do with a bar code scanner? -->
- **Use the actual time of registration** - Set to specify if you want to use the time the worker signs in to the device or the actual time where the worker is making a registration in the job card device. <!-- KFM: I don't understand. What are we registering here? Job completion? Clock in? -->
- **Single worker** - Set this option to **Yes** if only one worker uses the job card device. When this option is selected, <!-- KFM: each worker remains signed in until they explicitly sign out, so --> the device won't return to the sign-in screen each time the worker starts a new job from the device. While this option is selected, the **Lock employee** option is also automatically set to **Yes**.
- **Allow workers to set personal filters** - Set this option to **Yes** to allow workers to filter the assigned jobs shown on the device. The worker can select among three filter criteria: **Production unit**, **Resource group** and **Resource**. Only jobs that are scheduled on resources matching the selected filter criteria will be shown on the device. <!-- KFM: Can they select just one of these, or any combination (including all or none) of these? -->
- **Allow locking the touchscreen** - Set this option to **Yes** to allow workers to lock the job card device touchscreen so they can sanitize it. When enabled, a **Lock screen for sanitizing** button is added to the device sign-in page. When a worker selects this button, the touchscreen temporarily locks to prevent unintended input and a countdown timer is shown. The worker can now safely clean the device and the screen. When the countdown completes, the touchscreen automatically unlocks again.
- **Screen lock duration** - When the **Allow locking touchscreen** option is enabled, use this option so specify number of seconds the touchscreen should be locked for sanitizing. The duration must be between 5 and 120 seconds.
- **Production unit** - Select a production unit to be applied as a default filter criterion for the assigned jobs shown to each worker. Only jobs that are scheduled on resources grouped under the selected production unit will be displayed by the device. <!-- KFM: How does this (and similar setting here) interact with the **Allow personal features** option? -->
- **Resource group** - Select a resource group to be applied as a default filter criterion for the assigned jobs shown to each worker. Only jobs that are scheduled on resources grouped under the selected resource group will be displayed by the device.
- **Resource** - Select a resource to be applied as a default filter criterion for the assigned jobs shown to each worker. Only jobs that are scheduled on the selected resource will be displayed by the device.
- **Generate license plate** - Set this option to **Yes** to generate a new license plate each time a worker uses the job card device to report as finished. The license plate number is generated from a number sequence set up on the **Warehouse management parameters** page. When set to **No**, workers must specify an existing license plate when reporting as finished.
- **Print label** - Set this option to **Yes** to print a license plate label when a worker uses the job card device to report as finished. The configuration of the label is set up in document routing, as described in [Document routing layout for license plate labels](../warehousing/document-routing-layout-for-license-plates.md).

## Assigned users

Use the **Assigned users** FastTab to associate one or more system users (warehouse workers) with the current device configuration. Only workers associated a given configuration can sign in to the job card device where that configuration is active. Each worker can only be assigned to one configuration. <!-- KFM: I think "system user" = worker in this context. True? Please confirm. -->

## Additional resources

[Report as finished from the job card device](report-finished-job-device.md)
