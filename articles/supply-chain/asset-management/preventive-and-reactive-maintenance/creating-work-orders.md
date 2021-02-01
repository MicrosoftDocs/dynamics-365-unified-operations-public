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

    - **One work order per line** - Create one work order per maintenance schedule line
    - **One work order per** -  Creates work orders grouped according to the options you enable in this area.

1. Select a **Work order type** to use on all the work orders you create.

1. Select **OK** to create the work orders according to your settings.

## Apply rules for grouping work orders while running a maintenance plan

> [!IMPORTANT]
> The functionality that is described in this section is available as part of a preview release. The content and the functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/one-version).

As described in the previous section, the **Create work orders** dialog box lets you set up criteria for grouping jobs under work orders. For example, you can select to group by maintenance plan, asset, and functional location. This option is also available when you generate work orders automatically while running a maintenance plan.

### Enable this feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Asset Management*
- **Feature name:** *(Preview) Apply rules for grouping work orders while running a maintenance plan*

### Use this feature

To take advantage of this feature, the following two conditions must be fulfilled:

- The maintenance plan lines must have **Auto create** set to *Yes*. <!-- KFM: Where do I find these? -->
- You must run or schedule the maintenance plan by selecting one of the following commands from the navigator: <!-- KFM: Any of these, or just some/one of them? -->
  - **Asset Management \> Periodic \> Preventive maintenance \> Schedule maintenance plans**
  - **Asset Management \> Periodic \> Preventive maintenance \> Schedule maintenance rounds**
  - **Asset Management \> Periodic \> Preventive maintenance \> Update maintenance job type default references**
- In the dialog box for running or scheduling the plan, you must set **Automatically create work order from schedule** to *Yes*.
