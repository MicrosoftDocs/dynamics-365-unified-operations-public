---
title: Maintenance downtime for work orders
description: Learn how to create maintenance downtime registrations on the asset that is selected on a work order, including a process for creating downtime reason codes.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: EntAssetProductionStopType, EntAssetObjectProductionStop
ms.topic: how-to
ms.date: 09/08/2026
ms.custom:
  - bap-template
---

# Maintenance downtime for work orders

[!INCLUDE [banner](../../includes/banner.md)]

When necessary, you can create maintenance downtime registrations for selected assets on a work order. Each registration records a period when an asset wasn't available, along with a reason code that explains why. These registrations provide the downtime figures on the **Asset KPIs** page. By using them, you can measure availability, count stops, and calculate mean time between stops for each asset.

To get started, go to the **Maintenance downtime reason codes** page to establish the maintenance downtime reason codes that you want to use, such as *Breakdown* and *Planned stop*. Then, create maintenance downtime registrations on the **Maintenance downtime** page and add the relevant maintenance downtime reason codes.

> [!NOTE]
> Maintenance downtime registrations record downtime that already occurred. They're not the same as *maintenance downtime activities*, which you use to plan a stop before it happens. Learn more in [Maintenance downtime activities](../preventive-and-reactive-maintenance/maintenance-stop.md).

## Create maintenance downtime reason codes

A maintenance downtime reason code explains why an asset was unavailable, and it controls whether that downtime counts toward the asset's KPIs. Create one reason code for each type of stop that you want to tell apart in your reporting. Examples include a mechanical breakdown, a material shortage, and a planned service window. After you create the reason codes, they become available on every maintenance downtime registration.

1. Select **Asset management** > **Setup** > **Work orders** > **Maintenance downtime reason codes**.

1. On the Action Pane, select **New**.

1. In the **Maintenance downtime reason code** field, enter an ID for the maintenance downtime reason code. This field is required, and each ID must be unique.

1. In the **Name** field, enter a name.

1. Select the **KPI include** check box if you want to include the reason code in calculations of key performance indicators (KPIs) for the asset. In general, planned production stops shouldn't be included in KPI calculations, because they don't affect expected performance.

1. On the Action Pane, select **Save**.

Registrations that use a reason code where **KPI include** is selected contribute to the **Downtime**, **Uptime**, **Availability %**, **Number of stops**, and **MTBS** values on the **Asset KPIs** page. Registrations that have no reason code are also counted. Only registrations that use a reason code where **KPI include** is cleared are left out. Learn more in [Asset KPIs](../controlling-and-reporting/asset-kpis.md).

After you use a reason code on a registration, you can't delete it.

The following illustration shows an example of the **Maintenance downtime reason codes** page.

:::image type="content" source="media/15-work-orders.png" alt-text="Screenshot of the Maintenance downtime reason codes page that lists five reason codes, each with the KPI include check box selected." lightbox="media/15-work-orders.png":::

After you create the maintenance downtime reason codes that you want to use, you can create maintenance downtime registrations for work orders and assets.

## Create maintenance downtime registrations

A maintenance downtime registration records a period when an asset was unavailable. You create it from the work order that covers the downtime, so that it's tied to both the asset and the work done on it. After you save the registration, the downtime is reflected in the asset's availability and stop-related KPIs.

1. Go to **Asset management** > **Work orders** > **All work orders** or **Active work orders**.

1. Select the work order you want to work with.

1. On the Action Pane, open the **Work order** tab and, from the **Asset** group, select **Maintenance downtime**.

1. On the Action Pane, select **New**.

1. In the **From** and **To** fields, define the date and time interval for the maintenance downtime registration. **From** is required, and **To** must be later than **From**. Both fields show the time zone that the value is expressed in.

    > [!NOTE]
    > When you leave the **To** field, the system automatically calculates the duration in hours and inserts it into the **Duration** field. You can't edit **Duration** yourself. Learn more in [How the duration is calculated](#how-the-duration-is-calculated).

1. In the **Maintenance downtime reason code** field, select a reason code. A reason code is optional. However, if you leave this field blank, the registration is still counted as downtime in the asset KPI calculations. To keep downtime out of those calculations, you must select a reason code that has the **KPI include** check box cleared.

1. Repeat steps 4 through 6 to add more registrations.

1. On the Action Pane, select **Save**.

The **Asset**, **Functional location**, and **Work order** fields are filled in automatically from the work order that you started from, and you can't change them afterward. If the registration isn't related to a work order, the functional location is taken from the asset instead.

You can't create two registrations that have the same asset, **From** value, and **To** value.

The following illustration shows an example of maintenance downtime registration.

:::image type="content" source="media/16-work-orders.png" alt-text="Screenshot of the Maintenance downtime page that shows a registration line with the asset, functional location, work order, From and To values, calculated duration, and reason code." lightbox="media/16-work-orders.png":::

## How the duration is calculated

The **Duration** value isn't simply the elapsed time between **From** and **To**. The system counts only the working hours that the applicable calendar defines. For example, an interval from 8:00 AM to 2:30 PM produces 6.5 hours only if all of those hours are working time in that calendar. If the calendar has no working times in the selected period, the duration is 0.

Which calendar applies depends on how you set up the asset. If you select a resource in the **Resource** field on the **Fixed asset** FastTab of the **All assets** page, the system uses the calendar that you assign to that resource, as shown in the following illustration.

:::image type="content" source="media/17-work-orders.png" alt-text="Screenshot of the All assets page for a conveyor belt asset, where the Resource field on the Fixed asset FastTab is highlighted." lightbox="media/17-work-orders.png":::

If you don't select a resource on the asset, the standard calendar that you select on the **Asset management parameters** page is used, as shown in the following illustration.

:::image type="content" source="media/18-work-orders.png" alt-text="Screenshot of the Asset management parameters page, where the Standard calendar field is highlighted on the Assets tab." lightbox="media/18-work-orders.png":::

> [!NOTE]
> Set up all calendars that you use in the Asset management module at **Organization administration** > **Setup** > **Calendars** > **Calendars**.

## View all maintenance downtime registrations

To see an overview of maintenance downtime registrations for all assets, go to **Asset management** > **Inquiries** > **Maintenance downtime**.

## Related information

- [Maintenance downtime activities](../preventive-and-reactive-maintenance/maintenance-stop.md)
- [Asset KPIs](../controlling-and-reporting/asset-kpis.md)
- [Introduction to work orders](introduction-to-work-orders.md)
- [Introduction to assets](../objects/introduction-to-objects.md)
