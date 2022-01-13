---
title: Processing issues occur after installing a scale unit warehouse workload.
description: This topic describes issues that can occur soon after installing a scale unit warehouse workload, and gives advice for how to fix them.
author: perlynne
ms.date: 1/13/2022
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-01-13
ms.dyn365.ops.version: 10.0.25
---

# Processing issues occur after installing a scale unit warehouse workload

This topic describes issues that can occur soon after installing a scale unit warehouse workload, and gives advice for how to fix them.

## Issue 1: Error after releasing a load from a load planning workbench

### Symptoms of issue 1

When you release a load from the **Load planning workbench** or **Outbound load planning workbench**, the Infolog shows an error with the following form:

> An exception was caught when posting the load %1, load could not be released.
> 
> UPDATE WHSSHIPMENTTABLE SET ...
> 
> Cannot edit a record in Shipments (WHSShipmentTable). Shipment ID: ...

Here is an actual example of this error message, including sample data:

> An exception was caught when posting the load USMF-000033, load could not be released.
session 5133 (Admin)
>
> UPDATE WHSSHIPMENTTABLE SET ORDERNUM=?,RECVERSION=?,MODIFIEDDATETIME=?,MODIFIEDBY=? WHERE ((RECID=?) AND (RECVERSION=?))  
> [Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Scale Unit @@ attempted to update records owned by Scale Unit @A.  
> Object Server Azure:
>
> Cannot edit a record in Shipments (WHSShipmentTable). Shipment ID: USMF-000031, USMF-000033. The SQL database has issued an error.

### Cause of issue 1

This issue can occur if the following combination of conditions exists when you install the scale unit warehouse workload:

- The system includes an unreleased load with multiple lines associated to different orders where not all load lines are associated to a shipment.
- The system is set to use shipment consolidation.

In a distributed hybrid topology deployment, each load and shipment record is marked as owned by a specific a scale unit or hub. When you release a load from the **Load planning workbench**, the system changes the assigned ownership. However, as a result of the listed conditions, the system may be unable to resolve the data ownership and will therefore fail to release to warehouse.

### Resolution of issue 1

Split the load into two smaller loads before releasing to warehouse.

## Issue 2: Error while processing a wave on a scale unit

### Symptoms of issue 2

When you are processing a wave on a scale unit, the Infolog shows an error with the following form:

> You cannot modify load line with RecId = %1, load id= %2 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.

Here is an actual example of this error message, including sample data:

> Infolog for job Execute Wave USMF-000000012 (9223377668365210)  
> Infolog for task Execute Wave USMF-000000012 (9223377668370462)  
> You cannot modify load line with RecId = 68719478242, load id= USMF-000034 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.

### Cause  of issue 2

In a distributed hybrid topology deployment, the load and shipment data gets assigned an ownership of either the hub or a scale unit and as part of the waving process the data is expected being in the ownership of a scale unit.

When installing a scale unit warehouse workload and having a open shipment associated to a load and wave, the system cannot control the data ownership and will thereby fail the wave processing on the scale unit.

### Resolution of issue 2

Release the load to warehouse from the hub.

## Troubleshoot issues by viewing record ownership and destination

In a distributed hybrid topology deployment, many types of records are marked as owned by a specific a scale unit or hub. After you switch to a distributed hybrid topology and/or set up a new scale unit warehouse workload, the system assigns ownership to each relevant record, which can sometimes produce errors or unexpected results. Viewing ownership and transfer destination information can therefore help you to troubleshoot issues that occur after you make these types of changes.

Use the following procedure to view the ownership and transfer destination of a record.

1. Open the relevant record.
1. On the Action Pane, open the **Options** tab and, from the **Record info** group, select **Show all fields**.
1. A page opens showing values for all of the fields available for your selected record. Look for the following field values:
    - **SYSSCALEUNITID** – Shows the current owner of the record.
    - **SYSTARGETSCALEUNITID** – Shows the scale unit ID of the hub or scale unit where this record will be transferred to when the current owner is done working with it. This value is used by batch jobs that manage this type of process. This value isn't directly related to ownership, but ownership may change when the record is transferred. In some cases, this value will be blank.
