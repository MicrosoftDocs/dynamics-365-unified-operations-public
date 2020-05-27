---
# required metadata

title: Configure job card for devices
description: XXXX
author: johanhoffmann
manager: tfehr
ms.date: 05/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: XXXX
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
<!-- KFM: In above meta data, add: 

description: Add description based on intro
ms.search.form: Add the form name for context help; I think that's (other?): JmgRegistrationSetupTouch

 -->


# Configure job card for devices

[!include [banner](../includes/banner.md)]

The job card device is used by the shop floor workers to make their daily work related registrations such as starting and reporting feedback on jobs and registering indirect activities and absence. The registrations are the basis for tracking progress and cost on production orders and calculating the basis for the workers pay. This topic descripe the different options for configuring the job card device.

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

To make this feature available, enable the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in order):

1. 
1. 

## Manage and configure your devices

To configure your job card devices, go to **Production control > Setup > Manufacturing execution > Configure job card for devices**. The **Configure job card for devices** page opens, which shows a list of existing devices. From here, you can do the following:

- Select any device listed in the left column to view and edit the configuration settings for that device
- Select **New** on the Action Pane to add a new device to the list. Then enter a name in the **Configuration** field to identify the new device. The value you enter here must be unique among all devices, and you won't be able to edit it later.

See the following sections for details about each of the settings and FastTabs provided here.

## General settings

The **General** FastTab lets you configure each of the various options available for the job card device. The following settings are available here:

- **Report quantity at clock-out** - When this option is selected the user of the job card device will be prompted for reporting feedback on a job in progress when clocking out. If the option is not selected the user will not be prompted to provide feedback on jobs in progress. 
- **Lock employee** - When this option is selected, the job card device page will not return to the log-in page when the user of the job card device starts a job. When this option is not selected, the job card device page will always return to the log-in page when the user starts a job. 
- **Barcode scanner** - When this option is selected a field for the identification of a production job is shown in the job card device screen. 
- **Use the actual time of registration** - Use this option to specify if you want to use the time the worker logs in to the device or the actual time where the worker is making a registration in the job card device. 
- **Single worker** - Select this option to indicate that only one worker is using the job card device. When this option is selected the device will not return to the log-in screen when the user starts a job from the device. 
- **Allow workers to set personal filters** - Select this option to allow the user of the job card device to apply a filter on the assigned jobs available on the device. The user can select between three filter criteria **Production unit**, **Resource group** and **Resource**. Only jobs that are scheduled on resources matching the selected filter criteria will be shown on the device.
- **Allow locking the touchscreen** - Select this option to lock the job card device touchscreen for sanitization. When enabled, a button called "Lock screen for sanitizing" is added to the device log-in page. When a user selects this button, the touchscreen temporarily locks to prevent unintended input and a countdown timer is shown. The user can now safely clean the device and the screen. When the countdown completes, the touchscreen automatically unlocks again.
- **Screen lock duration** - When the **Allow locking touchscreen** option is enabled, use this option so specify number of seconds the device touchscreen should be locked for sanitizing. Number of seconds must be greater than 5 and lower than 120 seconds.
- **Production unit** - Select a production unit as a default filter criteria for the assigned jobs shown for the user of the job card device. Only jobs that are scheduled on resources grouped under the selected production unit will be shown in the device.
- **Resource group** - Select a Resource group as a default filter criteria for the assigned jobs shown for the user of the job card device. Only jobs that are scheduled on resources grouped under the selected resource group will be shown in the device.
- **Resource** - Select a Resource as a default filter criteria for the assigned jobs shown for the user of the job card device. Only jobs that are scheduled on the selected resource will be shown in the device.
- **Generate license plate** - Select this option to generate a new license plate when the user does report as finished on the job card device. The license plate number is generated from a number sequence set up in the warehouse parameter page. If this option is not selected the user will have to specify an existing license plate during registration of report as finished.
- **Print label** - Select this option to print a license plate label during register report as finished. The configuration of the label is setup in document routing: https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/document-routing-layout-for-license-plates

## Assigned users

Use the **Assigned users** FastTab to associate a system user to the configuration. Only system users associated the configuration can log in to the job card device with that configuration. A user can only be assoicated one configuration.

## Additional resources

[Report as finished from the job card device](report-finished-job-device.md)
