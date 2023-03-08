---
title: Parameters not used by Planning Optimization
description: This article lists the parameters that Planning Optimization doesn't currently consider during its operation.
author: t-benebo
ms.date: 03/08/2023
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

  - **Current forecast plan** – Planning Optimization does not consider this parameter. Please create a **Master plan** with **Forecast model** specified.
  - **Copy the complete and updated static master plan to the dynamic master plan** – This is not supported in Planning Optimization. You can run each plan independently and results will not be copied from one to another. 
  - **Start time for calculated delays** – This is not supported in Planning Optimization. 
  - **Use dynamic negative days** – Planning Optimization always uses the *Dynamic negative days* approach.
  - **Today's date calendar** – Not supported. Planning Optimization always uses current time rounded to the next whole hour. 
  - **Use of cache** – This parameter is not considered as Planning Optimization manages perfomance and scaling.  
  - **Number of tasks in helper task bundle** – This parameter is not considered as Planning Optimization manages perfomance and scaling. 
  - **Pre-processing: Automatically filter by items with direct demand** – This is not supported in Planning Optimization.  
  - **Post-processing: Automatically filter by items with direct demand** – This is not supported in Planning Optimization.   
  - **Number of threads** – This parameter is not considered as Planning Optimization manages perfomance and scaling. 
  - **Planning process timeout in minutes** – In Planning Optimization there is a fixed timeout of 1 hour. 
  - **Scheduling start time** – This is not considered in Planning Optimization. With Planning Optimization, an explosion run is a run of the plan for the selected item(s). 

- **Planned orders** tab:

  - **Receipt time** – This is not supported in Planning Optimization. Receipt time matches exactly demand time in Planning Optimization. 

- **Number sequences** tab:
  - **Master scheduling planned order number** - Planning Optimization will take its own number sequence, that is not possible to be selected. Thus, this parameter is not considered.

## Coverage groups page

Planning Optimization doesn't use the following parameters or options on the **Coverage groups** page:

- **General** FastTab:

  - **Positive days** – The *Positive days* value isn't used. With Planning Optimization, positive days are considered infinite.
 
- **Other** FastTab:

  - **Freeze time fence (days)** – Pending *Freeze time fence* support 
  - **BOM explosion time fence (days)** – This is not supported in Planning Optimization. 
  - **Capacity scheduling time fence (days)** – This is not supported in Planning Optimization. 
  - **Forecast plan time fence** – Forecast plan is not supported in Planning Optimization. Please use a Master plan with the Forecast model set as a Forecast plan. 

- **Delays** FastTab:

  - **Calculated delays** – This parameter is not considered, delays are always calculated for the coverage group. 
  - **Calculate delays time fence (days)** – This parameter is not considered, delays are calculated for the **coverage time fence (days)**. 

## Item coverage page

Planning Optimization doesn't use the following parameters or options on the **Item coverage** page:

- **General** tab:

  - **Planned order type** – Planning Optimization doesn't support the *Kanban* option.
  - **Freeze time fence (days)** – Pending *Freeze time fence* support.
  - **BOM explosion time fence (days)** – This is not supported in Planning Optimization. 
  - **Fulfill minimum** – Planning Optimization doesn't support the *Today's date*, *First issue*, and *Coverage time fence* options. It always uses the *Today's date + procurement time* option.
  - **Minimum periods** – This is not supported in Planning Optimization. 
  - **Planning formula** – Pending *Planning items support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Default priority** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Current priority** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Date changed** – Supported in version 10.0.33 and later. The feature *Process Manufacturing support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Master plans page

Planning Optimization doesn't use the following parameters or options on the **Master plans** page:

- **General** FastTab:

  - **Include continuity plan** – This is not supported. 
  - **Backward scheduling capacity time fence** – This is not supported. 
  - **Capacity time fence for bottleneck resources** – This field will no longer be supported in Planning Optimization, as we detected that customers were not using it. 
  - **Planned orders** – Planning Optimization uses fixed number sequences.
  - **Session** – Planning Optimization uses fixed number sequences.
  - **Continuity plan** – This is not supported.

- **Time fences in days** FastTab:

  - **Freeze** – *Freeze time fence* isn't yet supported in Planning Optimization.
  - **Explosion** – This is not supported in Planning Optimization. 
  - **Forecast plan** – This is not supported in Planning Optimization. 
  - **Continuity plan** – This is not supported in Planning Optimization. 
  - **Calculated delays** – This parameter is not considered. Calculated delays are created for the **coverage time fence (days)**.

- **Calculated delays** FastTab:

  - **Ensure that the planned orders are not created prior to the master planning run date** – This is not supported in Planning Optimization. Planned orders are never created in the past. 
  - **Add the calculated delay to the requirement date** (in the **Planned purchase orders** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned production orders** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned transfer** section) – Starting January 18, 2023, Planning Optimization supports this field.
  - **Add the calculated delay to the requirement date** (in the **Planned kanban** section) – Kanban is not supported in Planning Optimization. 

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




  


 
