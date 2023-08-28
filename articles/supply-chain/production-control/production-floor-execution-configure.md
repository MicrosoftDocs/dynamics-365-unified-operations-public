---
# required metadata

title: Configure the production floor execution interface
description: This article describes how to create one or more configurations for the production floor execution interface. When you open the production floor execution interface, it automatically loads a selected configuration and job filter that are specific to the browser and device. In the configuration, you set the policies that must be applicable for a specific usage.
author: johanhoffmann
ms.date: 11/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: JmgProductionFloorExecutionConfiguration
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-10-05
ms.dyn365.ops.version: 10.0.15
---

# Configure the production floor execution interface

[!include [banner](../includes/banner.md)]

Shop floor workers use the production floor execution interface to register their daily work, such as when they start a job, report feedback about jobs, register indirect activities, and report absence. These registrations are the basis for tracking progress and cost on production orders, and for calculating the basis for the workers' pay.

When you open the production floor execution interface, it automatically loads a selected configuration and job filter that are specific to the browser and device. In the configuration, you set the policies that must be applicable for a specific usage. Here are some usage examples:

- On a device in the company hall, employees clock in when they come into the office, and they clock out when they leave for the day.
- On a device on the shop floor, machine operators register when they start and complete jobs. They also register breaks and indirect activities.

This article describes the various options for configuring a production floor execution interface for each device in use at your site.

## Turn on the production floor execution interface and its related optional features

The production floor execution interface itself, plus several of the optional settings that are described in this article, must be turned on for your system before you can use them. Use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to turn on any or all of the features described in the following subsections as required.

### The production floor execution interface

This is the primary feature described in this article and is a prerequisite for all of the other features mentioned in this section. As of Supply Chain Management 10.0.25, it is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Production floor execution* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Generate license plates

These features make license plate functionality available to the production floor execution interface. If you'd like to use them, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

1. *License plate for reporting as finished added to the Job Card Device*<br>(As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management version 10.0.25, this feature is mandatory.)
1. *Enable automatic generation of license plate number when reporting as finished in the job card device*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory.)

### Print labels

These features make label printing functionality available to the production floor execution interface. If you'd like to use them, turn on the following features in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order):

1. *License plate for reporting as finished added to the Job Card Device*<br>(As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management version 10.0.25, this feature is mandatory.)
1. *Print label from Job Card Device*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory.)

### Allow locking the touch screen

This feature makes it possible to allow workers to lock the touchscreen so that they can sanitize it.

As of Supply Chain Management version 10.0.21, this feature is turned on by default. As of Supply Chain Management 10.0.25, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.25, then admins can turn this functionality on or off by searching for the *Feature for locking job card device and job card terminal so that they can be sanitized* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Asset management functionality for the production floor execution interface

This feature adds an asset management tab to the production floor execution interface. Workers can use this tab to select an asset that is connected to a machine resource that is within the selected filter of the job list. For the selected machine asset, the worker can view the state and health of the asset from counter values for up to four selected counters.

As of Supply Chain Management version 10.0.25, this feature is turned on by default. As of Supply Chain Management version 10.0.29, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Asset management functionality for the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Job search

This feature makes it possible to add a search field to the jobs list. Workers can find a specific job by entering the job ID or find all jobs for a specific order by entering the order ID. Workers can enter the ID by using a keypad or by scanning a bar code.

As of Supply Chain Management version 10.0.25, this feature is turned on by default. As of Supply Chain Management version 10.0.29, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Job search for the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Report on co-products and by-products

This feature lets workers use the production floor execution interface to report progress on batch orders. This reporting includes reporting on co-products and by-products.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Report on co- and by-products from the production floor execution interface* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Display full serial, batch, and license plate numbers

This feature provides an improved experience for viewing lists of serial, batch, and license plate numbers in the production floor execution interface. The display changes from a card view that shows a limited number of characters to a list view that provides enough space to show the full values. The list also provides the ability to search for specific numbers.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Show full serial, batch, and license plate numbers in the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

As of Supply Chain Management version 10.0.25, this feature is turned on by default. Admins can turn this functionality on or off by searching for the *Show full serial, batch, and license plate numbers in the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Register material consumption

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]
<!-- KFM: Preview until further notice -->

This feature enables workers to use the production floor execution interface to register material consumption, batch numbers, and serial numbers. Some manufacturers, especially those in the process industries, must explicitly register the amount of material that is consumed for each batch or production order. For example, workers might use a scale to weigh the amount of material that is consumed as they work. To ensure full material traceability, these organizations must also register the batch numbers that were consumed to produce each product.

There are two versions of this feature. One supports items that *are not* enabled to use warehouse management processes (WMS). The other supports items that *are* enabled to use WMS. To use this functionality, turn on one or both of the following features in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (in this order), depending on whether you have items that are enabled for WMS:

- *Register material consumption on the production floor execution interface (non-WMS)* (As of Supply Chain Management version 10.0.32, this feature is turned on by default.)
- *(Preview) Register material consumption on the production floor execution interface (WMS-enabled)*

> [!IMPORTANT]
> You can use the non-WMS feature alone. However, if you use WMS, you must enable both features.

### Report on catch weight items

Workers can use the production floor execution interface to report progress on batch orders for catch weight items. Batch orders are created from formulas, which can be defined to have catch weight items as formula items, co-products, and by-products. A formula can also be defined to have formula lines for ingredients that are defined for catch weight. Catch weight items use two units of measure to track inventory: catch weight quantity and inventory quantity. For example, in the food industry, boxed meat can be defined as a catch weight item, where the catch weight quantity is used to track the number of boxes and the inventory quantity is used to track the weight of the boxes.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.36, it's turned on by default. Admins can turn this functionality on or off by searching for the *Report on catch weight items from the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### The "My day" dialog

The **My day** dialog provides workers with an overview of their daily registrations and current balances for paid time, paid overtime, absence, and paid absence.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *"My day" view for the production floor execution interface* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Teams

When multiple workers are assigned to the same production job, they can form a team. The team can nominate one worker as a pilot. The remaining workers then automatically become assistants of that pilot. For the resulting team, only the pilot must register job status. Time records apply to all team members.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *Production teams in the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Additional configuration in the production floor execution interface

This feature adds settings for the following functionality to the **Configure production floor execution** page:

- Automatically open the **Start job** dialog box when a search is completed.
- Automatically open the **Report progress** dialog box when a search is completed.
- Pre-fill the remaining quantity in the **Report progress** dialog box.
- Enable material consumption adjustments from the **Report progress** dialog box. (This functionality also requires the *Register material consumption on the production floor execution interface (non-WMS)* feature.)
- Enable searches by project ID.

Information about how to use the settings is provided later in this article.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.36, it's turned on by default. Admins can turn this functionality on or off by searching for the *Additional configuration on the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Enable the my jobs tab

The **My jobs** tab lets workers easily view all unstarted and unfinished jobs that are assigned specifically to them. It's useful in companies where jobs are sometimes or always assigned to specific workers (human resources) instead of other types of resources (such as machines).

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, it's turned on by default. As of Supply Chain Management version 10.0.36, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.36, then admins can turn this functionality on or off by searching for the *My jobs tab on the production floor execution interface* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Enable use of a numpad on the sign-in page

This feature lets admins add a numpad control to the sign-in page for the production floor execution interface. Workers can then sign in by using the numpad to enter their badge ID or personal number.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.36, it's turned on by default. Admins can turn this functionality on or off by searching for the *Enable use of a numpad in the sign-in page* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

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
- **Lock employee** – When this option is set to *No*, workers will be signed out immediately after they make a registration (such as a new job). The interface will then return to the sign-in page. When this option is set to *Yes*, workers will stay signed in to the production floor execution interface. However, a worker can manually sign out so that another worker can sign in while the production floor execution interface continues to run under the same system user account. For more information about these types of accounts, see [Assigned users](config-job-card-device.md#assigned-users).
- **Use the actual time of registration** – Set this option to *Yes* to set the time for each new registration to the exact time when the worker submitted the registration. When this option is set to *No*, the sign-in time is used instead. You will usually want to set this option to *Yes* if you've set the **Lock employee** and/or **Single worker** option to *Yes* in cases where workers often remain signed in for longer periods.
- **Single worker** – Set this option to *Yes* if only one worker uses each production floor execution interface where this configuration is active. When this option is set to *Yes*, the **Lock employee** option is automatically set to *Yes*. In addition, this setting removes the requirement (and ability) for the worker to sign in by using a badge ID (or another similar ID). Instead, the worker signs in to Microsoft Dynamics 365 Supply Chain Management by using a system user account that is linked to a *time registered worker* (from the *workers* table), and gets signed in to the production floor execution interface as that worker at the same time.
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
