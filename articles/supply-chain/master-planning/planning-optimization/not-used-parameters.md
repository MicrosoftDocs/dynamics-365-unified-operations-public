---
title: Parameters not used by Planning Optimization
description: This article lists the parameters that Planning Optimization doesn't currently consider during its operation.
author: t-benebo
ms.date: 01/18/2023
ms.topic: article
ms.search.form: ReqParameters, ReqGroup, ReqItemTable, ReqPlanSched, EcoResProductDetailsExtended, InventItemOrderSetup, WorkCalendarTable, PdsDispositionMaster
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-06-29
ms.dyn365.ops.version: 10.0.20
---

# Parameters not used by Planning Optimization

[!include [banner](../../includes/banner.md)]

This article lists the parameters that Planning Optimization doesn't currently consider during its operation. The planning service might skip a parameter because, for example, related functionality isn't yet supported. Alternatively, the parameter might have become obsolete because of functional changes.

The following sections list the parameters that Planning Optimization doesn't use on specific pages. They also explain why each parameter isn't used.

## Master planning parameters page

Planning Optimization doesn't use the following parameters or options on the **Master planning parameters** page:

- **General** tab:

  - **Current forecast plan** – Pending *Forecast* support.
  - **Current static master plan** – Pending *Copy static to dynamic plan* support.
  - **Current dynamic master plan** – Pending *Copy static to dynamic plan* support.
  - **Copy the complete and updated static master plan to the dynamic master plan** – Pending *Copy static to dynamic plan* support.
  - **Start time for calculated delays** – Pending *Calculated delays* support.
  - **Use dynamic negative days** – Planning Optimization always uses the *Dynamic negative days* approach.
  - **Today's date calendar** – Pending *Scheduling* support.
  - **Use of cache** – The configuration of the Microsoft Azure subscription handles performance points.
  - **Number of tasks in helper task bundle** – The Azure subscription configuration handles performance points.
  - **Pre-processing: Automatically filter by items with direct demand** – The Azure subscription configuration handles performance points.
  - **Post-processing: Automatically filter by items with direct demand** – The Azure subscription configuration handles performance points.
  - **Number of orders in firming bundle** – The Azure subscription configuration handles performance points.
  - **Number of threads** – The Azure subscription configuration handles performance points.
  - **Planning process timeout in minutes** – The Azure subscription configuration handles performance points.
  - **Scheduling start time** – Pending *Scheduling* support.

- **Planned orders** tab:

  - **Receipt time** – Pending *Scheduling* support.
  - **Production** – Pending *Scheduling* support.
  - Fields in the **Project** section – Pending *Scheduling* support.

## Coverage groups page

Planning Optimization doesn't use the following parameters or options on the **Coverage groups** page:

- **General** FastTab:

  - **Positive days** – The *Positive days* value isn't used. With Planning Optimization, positive days are considered infinite.
  - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.
  - **Use the specified BOM or formula version** – Pending *Formula versions with Co/By product* support.
  - **Use the specified route version** – Pending *Demand with specific BOM or route requirements defined* support.


- **Other** FastTab:

  - **Freeze time fence (days)** – *Freeze time fence* support isn't planned in Planning Optimization.
  - **BOM explosion time fence (days)** – Pending *Scheduling* support.
  - **Capacity scheduling time fence (days)** – Pending *Scheduling* support.
  - **Approved requisition time fence (days)** – Pending *Requisition* support.
  - **Forecast plan time fence** – Pending *Forecast* support.

- **Delays** FastTab:

  - **Calculated delays** – Pending *Calculated delays* support.
  - **Calculate delays time fence (days)** – Pending *Calculated delays* support.

## Item coverage page

Planning Optimization doesn't use the following parameters or options on the **Item coverage** page:

- **General** tab:

  - **Planned order type** – Planning Optimization doesn't support the *Kanban* option, pending *Kanban* support.
  - **Freeze time fence (days)** – *Freeze time fence* support isn't planned in Planning Optimization.
  - **BOM explosion time fence (days)** – Pending *Scheduling* support.
  - **Approved requisition time fence (days)** – Pending *Requisition* support.
  - **Fulfill minimum** – Planning Optimization doesn't support the *Today's date*, *First issue*, and *Coverage time fence* options. It always uses the *Today's date + procurement time* option.
  - **Minimum periods** – Pending *Minimum inventory level* support.
  - **Planning formula** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Default priority** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Current priority** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Date changed** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.

## Master plans page

Planning Optimization doesn't use the following parameters or options on the **Master plans** page:

- **General** FastTab:

  - **Override on hand** – Pending *Consumption of on-hand inventory* support.
  - **Consume on-hand inventory** – Pending *Consumption of on-hand inventory* support.
  - **Include sales quotations** – Pending *Sales quotations* support.
  - **Include request for quotations** – Pending *Request for quotations* support.
  - **Use shelf life dates** – Pending *Shelf life* support.
  - **Include continuity plan** – Pending *Continuity scheduling* support.
  - **Scheduling method** – Pending *Scheduling* support.
  - **Finite property** – Pending *Scheduling* support.
  - **Backward scheduling capacity time fence** – Pending *Scheduling* support.
  - **Finite capacity** – Pending *Scheduling* support.
  - **Finite capacity time fence** – Pending *Scheduling* support.
  - **Capacity time fence for bottleneck resources** – This field will no longer be supported on Planning Optimization, as we detected that customers were not using it. 
  - **Planned orders** – Planning Optimization uses fixed number sequences.
  - **Session** – Planning Optimization uses fixed number sequences.
  - **Continuity plan** – Planning Optimization uses fixed number sequences.

- **Time fences in days** FastTab:

  - **Freeze** – *Freeze time fence* isn't yet supported in Planning Optimization.
  - **Explosion** – Pending *Scheduling* support.
  - **Forecast plan** – Pending additional *Forecast* support.
  - **Continuity plan** – Pending *Continuity scheduling* support.
  - **Calculated delays** – Pending additional *Calculated delays* support.
  - **Sequencing** – Pending *Production* support.

- **Calculated delays** FastTab:

  - **Ensure that the planned orders are not created prior to the master planning run date** – Pending *Calculated delays* support.
  - **Add the calculated delay to the requirement date** (in the **Planned purchase orders** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned production orders** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned transfer** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned kanban** section) – Starting January 18, 2023, Planning Optimization supports this field.

- **Action message** FastTab:

  - **Update postponed date as requirement date** - This parameter is discontinued with Planning Optimization.

- **Sequencing** FastTab:

  - **Sequence planned orders after master planning** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Bucket type** –  Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Period type** –  Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Number of buckets in the campaign cycle** –  Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Released product details page

Planning Optimization doesn't use the following parameter option on the **Released product details** page:

- **Engineer** FastTab:

  - **Production type** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Default order settings page

Planning Optimization doesn't use the following parameter option on the **Default order settings** page:

- **Inventory** FastTab:

  - **Delivery date control** – Planning Optimization doesn't support the *CTP* option, pending *CTP* support.
  - **Inventory lead time** – In versions of the Planning Optimization service that are older than the August 6, 2021 release, Planning Optimization uses this parameter to calculate the correct order and delivery dates, but it doesn't save the calculated lead time itself to the planned order. In later versions, the service also uses the calculated lead time to set the **Lead time** field and **Working days** option as required for the relevant planned order.
  - **Working days** – In versions of the Planning Optimization service that are older than the August 6, 2021 release, Planning Optimization uses this parameter to calculate the correct order and delivery dates, but it doesn't save the calculated lead time itself to the planned order. In later versions, the service also uses the calculated lead time to set the **Lead time** field and **Working days** option as required for the relevant planned order.


 
