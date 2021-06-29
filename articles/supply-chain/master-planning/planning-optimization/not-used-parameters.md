---
title: Parameters that are not used by Planning Optimization
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
ms.dyn365.ops.version: AX 7.0.0
---

# Parameters that are not used by Planning Optimization

[!include [banner](../../includes/banner.md)]

This topic lists parameters that are currently not considered by Planning Optimization during its operation. Planning service may skip a parameter because, for example, related functionality is not supported yet or when the parameter becomes obsolete due to functional changes.
Below is the list of parameters that are not used by Planning Optimization and the reason for such behavior. Parameters are grouped based on the pages where they are located.

## Master planning parameters page 
<!---**Master planning parameters** page !-->
- **General** tab
    - **Current forecast plan**, pending *Forecast* support.
    - **Current static master plan**, pending *Copy static to dynamic plan* support.
    - **Current dynamic master plan**, pending *Copy static to dynamic plan* support.
    - **Copy the complete and updated static master plan to the dynamic master plan**, pending *Copy static to dynamic plan* support.
    - **Start time for calculated delays**, pending *Calculated delays* support.
    - **Use dynamic negative days**, Planning Optimization always uses *Dynamic negative days* approach.
    - **Today's date calendar**, pending *Scheduling* support.
    - **Use of cache**, Azure subscription configuration handles performance points.
    - **Number of tasks in helper task bundle**, Azure subscription configuration handles performance points.
    - **Pre-processing: Automatically filter by items with direct demand**, Azure subscription configuration handles performance points.
    - **Post-processing: Automatically filter by items with direct demand**, Azure subscription configuration handles performance points.
    - **Number of orders in firming bundle**, Azure subscription configuration handles performance points.
    - **Number of threads**, Azure subscription configuration handles performance points.
    - **Planning process timeout in minutes**, Azure subscription configuration handles performance points.
    - **Scheduling start time**, pending *Scheduling* support.
- **Planned orders** tab
    - **Receipt time**, pending *Scheduling* support.
    - **Production**, pending *Scheduling* support.
    - **Project** field group, pending *Scheduling* support.
- **Standard update** tab
    - **Update marking**, pending *Firming* support.
    - **Stop firming if an error occurs**, pending *Firming* support.
    - **Group by vendor**, pending *Firming* support.
    - **Group by buyer group**, pending *Firming* support.
    - **Group by purchase agreement**, pending *Firming* support.
    - **Group by period**, pending *Firming* support.
    - **Find purchase agreement**, pending *Firming* support.
    - **Group by planning priority**, pending *Firming* support.
    - **Group by period**, pending *Firming* support.

## Coverage groups page
- **General** FastTab
    - **Positive days**, pending *Positive days* support.
    - **Consume on-hand inventory**, pending *Consumption of on-hand inventory* support.
    - **Use the specified BOM or formula version**, pending *Formula versions with Co/By product* support.
    - **Use the specified route version**, pending *Demand with specific BOM or route requirements defined* support.
- **Action** FastTab	
    - **Action message**, pending *Actions* support.
    - **Action time fence**, pending *Actions* support.
    - **Postpone margin**, pending *Actions* support.
    - **Advance margin**, pending *Actions* support.
    - **Basis date**, pending *Actions* support.
    - **Advance**, pending *Actions* support.
    - **Postpone**, pending *Actions* support.
    - **Decrease**, pending *Actions* support.
    - **Increase**, pending *Actions* support.
    - **Derived actions**, pending *Actions* support.
- **Other** FastTab	
    - **Freeze time fence (days)**, *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **BOM explosion time fence (days)**, pending *Scheduling* support.
    - **Capacity scheduling time fence (days)**, pending *Scheduling* support.
    - **Approved requisition time fence (days)**, pending *Requisition* support.
    - **Forecast plan time fence**, pending *Forecast* support.
- **Delays** FastTab	
    - **Calculated delays**, pending *Calculated delays* support.
    - **Calculate delays time fence (days)**, pending *Calculated delays* support.

## Item coverage page
- **General** tab
    - *Kanban* option in **Planned order type** field, pending *Kanban* support.
    - **Freeze time fence (days)**, *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **BOM explosion time fence (days)**, pending *Scheduling* support.
    - **Capacity scheduling time fence (days)**, pending *Scheduling* support.
    - **Approved requisition time fence (days)**, pending *Requisition* support.
    - *Todays' date, First issue, Coverage time fence* options in **Fulfill minimum** field, Planning Optimization always uses *Today's date + procurement time* option.
    - **Planning formula**, pending *Formula versions with Co/By products* support.
    - **Default priority**, pending *Formula versions with Co/By products* support.
    - **Current priority**, pending *Formula versions with Co/By products* support.
    - **Date changed**, pending *Formula versions with Co/By products* support.
    - **Consume on-hand inventory**, pending *Consumption of on-hand inventory* support.

## Master plans page
- **General** FastTab	
    - **Include on-hand inventory**, pending *Consumption of on-hand inventory* support.
    - **Override on hand**, pending *Consumption of on-hand inventory* support.
    - **Consume on-hand inventory**, pending *Consumption of on-hand inventory* support.
    - **Include inventory transactions**, pending *Consumption of on-hand inventory* support.
    - **Include sales quotations**, pending *Sales quotations* support.
    - **Include request for quotations**, pending *Request for quotations* support.
    - **Use shelf life dates**, pending *Shelf life* support.
    - **Include continuity plan**, pending *Continuity scheduling* support.
    - **Scheduling method**, pending *Scheduling* support.
    - **Finite property**, pending *Scheduling* support.
    - **Backward scheduling capacity time fence**, pending *Scheduling* support.
    - **Finite capacity**, pending *Scheduling* support.
    - **Finite capacity time fence**, pending *Scheduling* support.
    - **Finite capacity for bottleneck resources**, pending *Scheduling* support.
    - **Capacity time fence for bottleneck resources**, pending *Scheduling* support.
    - **Planned orders**, Planning Optimization use fixed number sequences.
    - **Session**, Planning Optimization use fixed number sequences.
    - **Continuity plan**, Planning Optimization use fixed number sequences.
- **Time fences in days** FastTab	
    - **Freeze**, *Freeze time fence* is not planned to be supported in Planning Optimization.
    - **Explosion**, pending *Scheduling* support.
    - **Forecast plan**, pending additional *Forecast* support.
    - **Capacity**, pending *Scheduling* support.
    - **Continuity plan**, pending *Continuity scheduling* support.
    - **Action message**, pending *Actions* support.
    - **Calculated delays**, pending additional *Calculated delays* support.
    - **Sequencing**, pending *Production* support.
- **Calculated delays** FastTab	
    - **Ensure that the planned orders are not created prior to the master planning run date**, pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned purchase orders** field group, pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned production orders** field group, pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned transfer** field group, pending *Calculated delays* support.
    - **Add the calculated delay to the requirement date** under **Planned kanban** field group, pending *Calculated delays* support.
- **Sequencing** FastTab	
    - **Sequence planned orders after master planning**, pending *Sequencing* support.
    - **Bucket type**, pending *Sequencing* support.
    - **Period type**, pending *Sequencing* support.
    - **Number of buckets in the campaign cycle**, pending *Sequencing* support.

## Released product details page
- **Engineer** FastTab	
    - *Planning item* option in the **Production type** field, pending *Planning items* support.

## Default order settings page
- **Inventory** FastTab	
    - *CTP* option in the **Delivery date control** field, pending *CTP* support.

## Working time calendars page
- **Base calendar**, pending *Base calendars* support.

## Batch disposition master page
- **Setup** FastTab
    - **Nettable**, pending *Batch disposition codes* support.
