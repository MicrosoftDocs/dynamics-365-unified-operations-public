---
title: Configure the production floor execution interface
description: Learn how to create one or more configurations for the production floor execution interface with an outline on working with production floor execution.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/19/2024
ms.custom: 
  - bap-template
---

# Configure the production floor execution interface

[!include [banner](../includes/banner.md)]

Shop floor workers use the production floor execution interface to register their daily work, such as when they start a job, report feedback about jobs, register indirect activities, and report absence. These registrations are the basis for tracking progress and cost on production orders, and for calculating the basis for the workers' pay.

When you open the production floor execution interface, it automatically loads a selected configuration and job filter that are specific to the browser and device. In the configuration, you set the policies that must be applicable for a specific usage. Here are some usage examples:

- On a device in the company hall, employees clock in when they come into the office, and they clock out when they leave for the day.
- On a device on the shop floor, machine operators register when they start and complete jobs. They also register breaks and indirect activities.

This article describes the various options for configuring a production floor execution interface for each device in use at your site.

## Turn on the production floor execution interface optional features

The production floor execution interface is always available in Supply Chain Management. But several optional features can be turned on or off for your system. Use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to turn on any or all of the features described in the following subsections as required.

### Register material consumption

This feature enables workers to use the production floor execution interface to register material consumption, batch numbers, and serial numbers. Some manufacturers, especially those in the process industries, must explicitly register the amount of material that is consumed for each batch or production order. For example, workers might use a scale to weigh the amount of material that is consumed as they work. To ensure full material traceability, these organizations must also register the batch numbers that were consumed to produce each product.

> [!IMPORTANT]
>
> This feature only supports items that *are not* enabled to use warehouse management processes (WMS).

To use this functionality, the feature that is named *Register material consumption on the production floor execution interface (non-WMS)* must be turned on in  [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.32, this feature is turned on by default.

### <a name="tracked-components"></a>Tracked components (preview)

[!INCLUDE [preview-banner-section](~/../shared-content/shared/preview-includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

This feature lets workers and managers register batch/serial numbers for materials and components that are used in manufacturing processes. They can then associate those numbers with the batch/serial numbers of the products that are produced. In this way, manufacturers can optimize their processes, enhance product quality, and respond quickly to any issues that arise. Managers can use the item tracing report to effectively track batch/serial numbers that are registered through the *Tracked components* feature.

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.40 or later.
- The feature that's named *Tracked components* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- You must make the feature available to workers by adding a **Tracked components** button to the appropriate tab and toolbar, as described in [Design the production floor execution interface](production-floor-execution-tabs.md).

For more information about this feature, see [Register batch/serial numbers for finished products and their components (preview)](production-floor-execution-use.md#tracked-components).

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Work with production floor execution configurations

To create and maintain production floor execution configurations, go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**. The **Configure production floor execution** page shows a list of existing configurations. On this page, you can perform the following actions:

- Select any production floor configuration that is listed in the left column to view and edit it.
- On the Action Pane, select **New** to add a new configuration to the list. Then, in the **Configuration** field, enter a name to identify the new configuration. The name that you enter must be unique among all configurations, and you won't be able to edit it later. In the **Description** field, you can optionally enter a description of the configuration.

Next, configure the various settings for the selected configuration, as described in the following subsections.

### The General FastTab

The following settings are available on the **General** FastTab:

- **Clock in and out only** – Set this option to *Yes* to create a simplified interface that provides only clock-in and clock-out functionality. This setting disables most of the other options on this page. You must remove all lines from the **Tab selection** FastTab before you can enable this option.
- **Enable search** – Set this option to *Yes* to include a search field on the jobs list. Workers can find a specific job by entering the job ID, or they can find all jobs for a specific order by entering the order ID. Workers can enter the ID by using a keypad or scanning a bar code.
- **Enable search by project ID** – Set this option to *Yes* to enable workers to search by project ID (in addition to job ID and order ID) in the search field of the production floor execution interface. You can set this option to *Yes* only when the **Enable search** option is also set to *Yes*.
- **Auto-open start dialog** – When this option is set to *Yes*, the **Start job** dialog box is automatically opened when workers use the search bar to find a job.
- **Auto-open report progress dialog** – When this option is set to *Yes*, the **Report progress** dialog box is automatically opened when workers use the search bar to find a job.
- **Enable adjust material** – Set this option to *Yes* to enable the **Adjust material** button in the **Report progress** dialog box. Workers can select this button to adjust material consumption for the job.
- **Report quantity at clock-out** – Set this option to *Yes* to prompt workers to report feedback about jobs that are in progress when they clock out. When this option is set to *No*, workers won't be prompted.
- **Lock employee** – When this option is set to *No*, workers will be signed out immediately after they make a registration (such as a new job). The interface will then return to the sign-in page. When this option is set to *Yes*, workers will stay signed in to the production floor execution interface. However, a worker can manually sign out so that another worker can sign in while the production floor execution interface continues to run under the same system user account.
- **Use the actual time of registration** – Set this option to *Yes* to set the time for each new registration to the exact time when the worker submitted the registration. When this option is set to *No*, the sign-in time is used instead. You will usually want to set this option to *Yes* if you've set the **Lock employee** and/or **Single worker** option to *Yes* in cases where workers often remain signed in for longer periods.
- **Single worker** – Set this option to *Yes* if only one worker uses each production floor execution interface where this configuration is active. When this option is set to *Yes*, the **Lock employee** option is automatically set to *Yes*. In addition, this setting removes the requirement (and ability) for the worker to sign in by using a badge ID or personnel number. Instead, the worker signs in to Microsoft Dynamics 365 Supply Chain Management by using a system user account that is linked to a *time registered worker*, and gets signed in to the production floor execution interface as that worker at the same time. Learn more in [Set up worker accounts to use the production floor execution interface](production-floor-execution-worker-accounts.md).
- **Enable numpad** – Set this option to *Yes* to add a numpad to the sign-in screen, which allows workers to enter their badge ID or personal number using a touch-screen numpad. Set this option to *No* to hide the numpad.
- **Allow locking the touchscreen** – Set this option to *Yes* to allow workers to lock the touchscreen of the production floor execution interface so that they can sanitize it. When this option is set to *Yes*, a **Lock screen for sanitizing** button is added to the sign-in page. When a worker selects this button, the touchscreen is temporarily locked to prevent unintended input. A countdown timer is also shown. The worker can then safely clean the device and the screen. When the countdown is completed, the touchscreen is automatically unlocked.
- **Screen lock duration** – When the **Allow locking touchscreen** option is set to *Yes*, use this option to specify the number of seconds that the touchscreen should be locked for sanitizing. The duration must be between 5 and 120 seconds.
- **Generate license plate** – Set this option to *Yes* to generate a new license plate every time that a worker uses the production floor execution interface to report as finished. The license plate number is generated from a number sequence that is set up on the **Warehouse management parameters** page. When this option is set to *No*, workers must specify an existing license plate when they report as finished.
- **Print label** – Set this option to *Yes* to print a license plate label when a worker uses the production floor execution interface to report as finished. The configuration of the label is set up in document routing, as described in [Document routing label layouts](../warehousing/document-routing-layout-for-license-plates.md).

### The Tab selection FastTab

Use the settings on the **Tab selection** FastTab to select which tabs the production floor execution interface should show when the current configuration is active. You can design as many tabs as you need, and then add and arrange them as you require by using the buttons on the FastTab toolbar. For information about how to design tabs and work with the settings here, see [Design the production floor execution interface](production-floor-execution-tabs.md).

### The Report progress FastTab

The following settings are available on the **Report progress** FastTab:

- **Enable adjust material** – Set this option to *Yes* to include the **Adjust material** button in the **Report progress** dialog box. Workers can select this button to adjust material consumption for the job.
- **Default remaining quantity** – Set this option to *Yes* to pre-fill the expected remaining quantity for a production job in the **Report progress** dialog box.

## Clean up job configurations

When the shop floor supervisor sets up the production floor execution interface, they select a configuration and a job filter. These selections are stored in a reference table in Supply Chain Management, and the browser uses an ID that is stored in a local cookie to find the correct row in that table. The table also logs the date and time that a worker last signed in to each device.

A batch job periodically cleans entries in the references table for devices that haven't logged any activity in the last 60 days. You can also manually clean the entries at any time by following these steps.

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. On the Action Pane, select **Clean up client configurations**.
1. In the **Clean up client configuration** dialog box, set the **Number of days** field to the number of days of inactivity (before today) to consider. You will remove all configurations and sign-in records for devices that haven't been active during that time.
1. Select **OK** to clean up the relevant configurations, based on the **Number of days** setting.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
