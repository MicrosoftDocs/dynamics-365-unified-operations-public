---
# required metadata

title: Creating work orders
description: This topic explains how to create work orders in Asset Management.
author: johanhoffmann
manager: tfehr
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.17


---

# Creating work orders

[!include [banner](../../includes/banner.md)]

Once you have scheduled preventive maintenance jobs, the next step is to create work orders for the jobs. You can do this using one of the maintenance schedules. The scheduled jobs in a maintenance schedule can have different reference types, as described in the following table.

| Reference type | Description |
|---|---|
| Maintenance plans | Preventive maintenance jobs based on maintenance plan types "Time" or "Counter". |
| Maintenance rounds | Preventive maintenance jobs containing several assets that require a similar type of maintenance. |
| Maintenance request | Manually created request for maintenance or repair of an asset, which can be converted into a work order. |

## Create work orders based on your maintenance schedule

To create work orders based on your maintenance schedule:

1. Go to one of the following pages, depending on how you would like to select schedule items for your work orders:
    - **Asset management \> Management schedule \> All maintenance schedule**
    - **Asset management \> Management schedule \> Open maintenance schedule lines**
    - **Asset management \> Management schedule \> Open maintenance schedule pools**

1. On the grid, mark the check box for each of the scheduled maintenance jobs that you want to create a work order for and then select **Work order** on the Action Pane.

1. The **Create work orders** dialog box opens. The **Maintenance forecast hours** field shows the total number of forecast hours for the selected lines.

    ![Figure 1](media/18-preventive-maintenance.png)

1. In the **Parameters** section, select how many work orders should be created. Select one of the following options:

    - **One work order per line** - Create one work order per maintenance schedule line.
    - **One work order per** -  Create work orders grouped according to the options you enable in this area.

1. Select a **Work order type** to use on all the work orders you create.

1. Select **OK** to create the work orders according to your settings.

## Group work order lines that are created automatically while running a maintenance plan

> [!IMPORTANT]
> The functionality that is described in this section is available as part of a preview release. The content and the functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

This feature lets you establish rules for grouping work order lines under a single work order when the system is set to generate work orders automatically based on a maintenance plan. Previously, automatically generated work orders could only contain a single line, but now it's possible to group them, for example, per asset, per asset type, or per functional location. (Manually generated work orders could already be grouped in this way, as described in the previous section.)

### Enable grouping for automatically generated work orders

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Asset Management*
- **Feature name:** *(Preview) Apply rules for grouping work orders while running a maintenance plan*

### Set up grouping for automatically generated work orders

To set up grouping for automatically generated work orders, do the following:

1. Go to **Asset management \> Setup \> Preventative maintenance \> Maintenance plans** and do the following for each plan where you want to generate grouped work orders:
    1. Select the plan on the list pane.
    1. Expand the **Lines** FastTab.
    1. Make sure that each line has its **Auto create** check box selected.
1. Go to **Asset Management \> Periodic \> Preventive maintenance \> Schedule maintenance plans**. The **Schedule maintenance plans** dialog box opens.
1. In the **Period** section, establish how often the relevant plans should run.
1. Set **Automatically create work order from schedule** to *Yes*.
1. Select one of the following options in the **Work order** area:
    - **One work order per line** - Create one work order per maintenance schedule line. (This provides the same functionality as when the *Apply rules for grouping work orders while running a maintenance plan* isn't enabled.)
    - **One work order per** -  Create work orders grouped according to the options you enable in this area.
1. If you only want to run some of your maintenance plans with these options, expand the **Records to include** FastTab and add filters as needed, just as with other batch jobs in Supply Chain Management.
1. Expand the **Run in the background** FastTab and set up batch and scheduling options as needed, just as with other batch jobs in Supply Chain Management.
1. Select **OK** to run and/or schedule the selected maintenance plans.
