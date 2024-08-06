---
title: Parameters not used by Planning Optimization
description: Learn about the parameters that Planning Optimization doesn't currently consider during its operation with an outline on the master planning parameters page.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 03/08/2023
ms.reviewer: kamaybac
ms.search.form: ReqParameters, ReqGroup, ReqItemTable, ReqPlanSched, EcoResProductDetailsExtended, InventItemOrderSetup, WorkCalendarTable, PdsDispositionMaster
---

# Parameters not used by Planning Optimization

[!include [banner](../../includes/banner.md)]

This article lists the parameters that Planning Optimization doesn't currently consider during its operation. The planning service might skip a parameter because, for example, related functionality isn't yet supported. Alternatively, the parameter might have become obsolete because of functional changes.

The following sections list the parameters that Planning Optimization doesn't use on specific pages. They also explain why each parameter isn't used.

## Master planning parameters page

Planning Optimization doesn't use the following parameters or options on the **Master planning parameters** page:

- **General** tab:

  - **Current forecast plan** – Planning Optimization doesn't consider this parameter. Instead, create a master plan that specifies a forecast model.
  - **Copy the complete and updated static master plan to the dynamic master plan** – Not supported by Planning Optimization. You can run each plan independently, but results won't be copied between them.
  - **Start time for calculated delays** – Not supported by Planning Optimization.
  - **Use dynamic negative days** – Planning Optimization always uses the *Dynamic negative days* approach.
  - **Today's date calendar** – Not supported by Planning Optimization. Planning Optimization always uses current time rounded to the next whole hour.
  - **Use of cache** – This parameter isn't considered because Planning Optimization manages performance and scaling.  
  - **Number of tasks in helper task bundle** – This parameter isn't considered because Planning Optimization manages performance and scaling.
  - **Pre-processing: Automatically filter by items with direct demand** – Not supported by Planning Optimization.  
  - **Post-processing: Automatically filter by items with direct demand** – Not supported by Planning Optimization.
  - **Number of threads** – This parameter isn't considered because Planning Optimization manages performance and scaling.
  - **Planning process timeout in minutes** – In Planning Optimization, there's a fixed timeout of 1 hour.
  - **Scheduling start time** – This parameter isn't considered by Planning Optimization. With Planning Optimization, an explosion run is a run of the plan for the selected item(s).

- **Planned orders** tab:

  - **Receipt time** – Not supported by Planning Optimization. The receipt time exactly matches the demand time in Planning Optimization.

- **Number sequences** tab:

  - **Master scheduling planned order number** – Planning Optimization uses its own number sequence, which can't be selected, so this parameter isn't considered.

## Coverage groups page

Planning Optimization doesn't use the following parameters or options on the **Coverage groups** page:

- **Other** FastTab:

  - **Freeze time fence (days)** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, the feature that is named *Freeze time fence support for Planning Optimization* must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Forecast plan time fence** – Forecast plans aren't supported by Planning Optimization. Instead, create a master plan that specifies a forecast model.

- **Delays** FastTab:

  - **Calculated delays** – This parameter isn't considered because delays are always calculated for the coverage group.
  - **Calculate delays time fence (days)** – This parameter isn't considered because delays are calculated for the **Coverage time fence (days)**.

## Item coverage page

Planning Optimization doesn't use the following parameters or options on the **Item coverage** page:

- **General** tab:

  - **Planned order type** – Planning Optimization doesn't support the *Kanban* option.
  - **Freeze time fence (days)** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, the feature that is named *Freeze time fence support for Planning Optimization* must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Fulfill minimum** – Planning Optimization doesn't support the *Today's date*, *First issue*, and *Coverage time fence* options. It always uses the *Today's date + procurement time* option.
  - **Minimum periods** – Not supported by Planning Optimization.
  - **Planning formula** – Pending. *Planning items support for Planning Optimization* must be enabled in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Master plans page

Planning Optimization doesn't use the following parameters or options on the **Master plans** page:

- **General** FastTab:

  - **Include continuity plan** – Not supported by Planning Optimization.
  - **Capacity time fence for bottleneck resources** – This field will no longer be supported by Planning Optimization because we detected that customers weren't using it.
  - **Planned orders** – Planning Optimization uses fixed number sequences.
  - **Session** – Planning Optimization uses fixed number sequences.
  - **Continuity plan** – Not supported by Planning Optimization.

- **Time fences in days** FastTab:

  - **Freeze** – Freeze time fence is supported in Supply Chain Management version 10.0.40 and later. To use it, the feature that is named *Freeze time fence support for Planning Optimization* must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
  - **Forecast plan** – Not supported by Planning Optimization.
  - **Continuity plan** – Not supported by Planning Optimization.
  - **Calculated delays** – This parameter isn't considered. Calculated delays are created for the **coverage time fence (days)**.
  - **Capacity** – Not supported by Planning Optimization.

- **Calculated delays** FastTab:

  - **Ensure that the planned orders are not created prior to the master planning run date** – Not supported by Planning Optimization. Planning Optimization never creates planned orders in the past.
  - **Add the calculated delay to the requirement date** (in the **Planned kanban** section) – Kanban isn't supported by Planning Optimization.

- **Action message** FastTab:

  - **Update postponed date as requirement date** – This parameter is discontinued with Planning Optimization.


## Released product details page

Planning Optimization doesn't use the following parameter option on the **Released product details** page:


## Scheduling parameters page

Planning Optimization doesn't use the following parameters or options on the **Scheduling parameters** page:

- **Schedule timeout enabled** – In Planning Optimization, schedule timeout is always enabled.
- **Maximum scheduling time per sequence** – Not supported by Planning Optimization.
- **Schedule optimization timeout enabled** – Not supported by Planning Optimization.
- **Optimization attempts timeout** – Not supported by Planning Optimization.
- **Keep production unit** – Not supported by Planning Optimization.
- **Keep warehouse from resource** – Not supported by Planning Optimization.
