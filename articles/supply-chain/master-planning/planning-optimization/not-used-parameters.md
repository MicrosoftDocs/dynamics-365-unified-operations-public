---
title: Parameters not used by Planning Optimization
description: This topic lists parameters that are currently not considered by Planning Optimization during its operation.
author: crytt
ms.date: 6/29/2021
ms.topic: article
ms.search.form: ReqParameters, ReqGroup, ReqItemTable, ReqPlanSched, EcoResProductDetailsExtended, InventItemOrderSetup, WorkCalendarTable, PdsDispositionMaster
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-29
ms.dyn365.ops.version: 10.0.20
---

# Parameters not used by Planning Optimization

[!include [banner](../../includes/banner.md)]

This topic lists parameters that are currently not considered by Planning Optimization during its operation. The planning service may skip a parameter, for example, because related functionality is not supported yet or if the parameter has become obsolete due to functional changes.

Each of the following sections lists parameters that aren't used by Planning Optimization and the reason they aren't used. The parameters are grouped based on the pages where they are located.

## Master planning parameters page

The following parameters or options from the **Master planning parameters** page aren't used by Planning Optimization:

- **General** tab
    - **Current forecast plan** – Pending *Forecast* support.
    - **Current static master plan** – Pending *Copy static to dynamic plan* support.
    - **Current dynamic master plan** – Pending *Copy static to dynamic plan* support.
    - **Copy the complete and updated static master plan to the dynamic master plan** – Pending *Copy static to dynamic plan* support.
    - **Start time for calculated delays** – Pending *Calculated delays* support.
    - **Use dynamic negative days** – Planning Optimization always uses *Dynamic negative days* approach.
    - **Today's date calendar** – Pending *Scheduling* support.
    - **Use of cache** – Azure subscription configuration handles performance points.
    - **Number of tasks in helper task bundle** – Azure subscription configuration handles performance points.
    - **Pre-processing: Automatically filter by items with direct demand** – Azure subscription configuration handles performance points.
    - **Post-processing: Automatically filter by items with direct demand** – Azure subscription configuration handles performance points.
    - **Number of orders in firming bundle** – Azure subscription configuration handles performance points.
    - **Number of threads** – Azure subscription configuration handles performance points.
    - **Planning process timeout in minutes** – Azure subscription configuration handles performance points.
    - **Scheduling start time** – Pending *Scheduling* support.
- **Planned orders** tab
    - **Receipt time** – Pending *Scheduling* support.
    - **Production** – Pending *Scheduling* support.
    - **Project** field group – Pending *Scheduling* support.
- **Standard update** tab
    - **Update marking** – Pending *Firming* support.
    - **Stop firming if an error occurs** – Pending *Firming* support.
    - **Group by vendor** – Pending *Firming* support.
    - **Group by buyer group** – Pending *Firming* support.
    - **Group by purchase agreement** – Pending *Firming* support.
    - **Group by period** – Pending *Firming* support.
    - **Find purchase agreement** – Pending *Firming* support.
    - **Group by planning priority** – Pending *Firming* support.
    - **Group by period** – Pending *Firming* support.

## Coverage groups page

The following parameters or options from the **Coverage groups** page aren't used by Planning Optimization:

- **General** FastTab
    - **Positive days** – Pending *Positive days* support.
    - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.
    - **Use the specified BOM or formula version** – Pending *Formula versions with Co/By product* support.
    - **Use the specified route version** – Pending *Demand with specific BOM or route requirements defined* support.
- **Action** FastTab
    - **Action message** – Pending *Actions* support.
    - **Action time fence** – Pending *Actions* support.
    - **Postpone margin** – Pending *Actions* support.
    - **Advance margin** – Pending *Actions* support.
    - **Basis date** – Pending *Actions* support.
    - **Advance** – Pending *Actions* support.
    - **Postpone** – Pending *Actions* support.
    - **Decrease** – Pending *Actions* support.
    - **Increase** – Pending *Actions* support.
    - **Derived actions** – Pending *Actions* support.
- **Other** FastTab
    - **Freeze time fence (days)** – *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **BOM explosion time fence (days)** – Pending *Scheduling* support.
    - **Capacity scheduling time fence (days)** – Pending *Scheduling* support.
    - **Approved requisition time fence (days)** – Pending *Requisition* support.
    - **Forecast plan time fence** – Pending *Forecast* support.
- **Delays** FastTab
    - **Calculated delays** – Pending *Calculated delays* support.
    - **Calculate delays time fence (days)** – Pending *Calculated delays* support.

## Item coverage page

The following parameters or options from the **Item coverage** page aren't used by Planning Optimization:

- **General** tab
    - **Planned order type** – The*Kanban* option isn't supported by Planning Optimization, pending *Kanban* support.
    - **Freeze time fence (days)** – *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **BOM explosion time fence (days)** – Pending *Scheduling* support.
    - **Capacity scheduling time fence (days)** – Pending *Scheduling* support.
    - **Approved requisition time fence (days)** – Pending *Requisition* support.
    - **Fulfill minimum** – The options *Today's date*, *First issue*, and *Coverage time fence* options aren't supported by Planning Optimization. Planning Optimization always uses the *Today's date + procurement time* option.
    - **Minimum periods** – Pending *Minimum inventory level* support.
    - **Planning formula** – Pending *Formula versions with Co/By products* support.
    - **Default priority** – Pending *Formula versions with Co/By products* support.
    - **Current priority** – Pending *Formula versions with Co/By products* support.
    - **Date changed** – Pending *Formula versions with Co/By products* support.
    - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.

## Master plans page

The following parameters or options from the **Master plans** page aren't used by Planning Optimization:

- **General** FastTab
    - **Include on-hand inventory** – Pending *Consumption of on-hand inventory* support.
    - **Override on hand** – Pending *Consumption of on-hand inventory* support.
    - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.
    - **Include inventory transactions** – Pending *Consumption of on-hand inventory* support.
    - **Include sales quotations** – Pending *Sales quotations* support.
    - **Include request for quotations** – Pending *Request for quotations* support.
    - **Use shelf life dates** – Pending *Shelf life* support.
    - **Include continuity plan** – Pending *Continuity scheduling* support.
    - **Scheduling method** – Pending *Scheduling* support.
    - **Finite property** – Pending *Scheduling* support.
    - **Backward scheduling capacity time fence** – Pending *Scheduling* support.
    - **Finite capacity** – Pending *Scheduling* support.
    - **Finite capacity time fence** – Pending *Scheduling* support.
    - **Finite capacity for bottleneck resources** – Pending *Scheduling* support.
    - **Capacity time fence for bottleneck resources** – Pending *Scheduling* support.
    - **Planned orders** – Planning Optimization use fixed number sequences.
    - **Session** – Planning Optimization use fixed number sequences.
    - **Continuity plan** – Planning Optimization use fixed number sequences.
- **Time fences in days** FastTab
    - **Freeze** – *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **Explosion** – Pending *Scheduling* support.
    - **Forecast plan** – Pending additional *Forecast* support.
    - **Capacity** – Pending *Scheduling* support.
    - **Continuity plan** – Pending *Continuity scheduling* support.
    - **Action message** – Pending *Actions* support.
    - **Calculated delays** – Pending additional *Calculated delays* support.
    - **Sequencing** – Pending *Production* support.
- **Calculated delays** FastTab
    - **Ensure that the planned orders are not created prior to the master planning run date** – Pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned purchase orders** field group – Pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned production orders** field group – Pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned transfer** field group – Pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned kanban** field group – Pending *Calculated delays* support.
- **Sequencing** FastTab
    - **Sequence planned orders after master planning** – Pending *Sequencing* support.
    - **Bucket type** – Pending *Sequencing* support.
    - **Period type** – Pending *Sequencing* support.
    - **Number of buckets in the campaign cycle** – Pending *Sequencing* support.

## Released product details page

The following parameter option from the **Released product details** page isn't used by Planning Optimization:

- **Engineer** FastTab
    - **Production type** – The *Planning item* option isn't supported by Planning Optimization, pending *Planning items* support.

## Default order settings page

The following parameter option from the **Default order settings** page isn't used by Planning Optimization:

- **Inventory** FastTab
    - **Delivery date control** – The *CTP* option isn't supported by Planning Optimization, pending *CTP* support.

## Working time calendars page

The following parameter from the **Working time calendars** page isn't used by Planning Optimization:

- **Base calendar** – Pending *Base calendars* support.

## Batch disposition master page

The following parameter from the **Batch disposition master** page isn't used by Planning Optimization:

- **Setup** FastTab
    - **Nettable** – Pending *Batch disposition codes* support.
