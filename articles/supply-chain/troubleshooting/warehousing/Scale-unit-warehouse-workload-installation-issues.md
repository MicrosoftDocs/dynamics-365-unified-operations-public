---
title: Processing issues occur after a scale unit warehouse workload is installed
description: This topic describes issues that can occur soon after a scale unit warehouse workload is installed, and gives advice for fixing them.
author: perlynne
ms.date: 1/13/2022
ms.topic: troubleshooting
ms.search.form: WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-01-13
ms.dyn365.ops.version: 10.0.25
---

# Processing issues occur after a scale unit warehouse workload is installed

This topic describes issues that can occur soon after a scale unit warehouse workload is installed, and gives advice for fixing them.

## Issue 1: Error after a load is released from a load planning workbench

### Symptoms of issue 1

When you release a load from the **Load planning workbench** or **Outbound load planning workbench** page, you receive an error message that has the following form:

> An exception was caught when posting the load %1, load could not be released.
> 
> UPDATE WHSSHIPMENTTABLE SET ...
> 
> Cannot edit a record in Shipments (WHSShipmentTable). Shipment ID: ...

Here is an actual example that includes sample data:

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

- The system includes an unreleased load where multiple lines are associated with different orders, and some load lines aren't associated with a shipment.
- The system is set up to use shipment consolidation.

In a distributed hybrid topology deployment, each load and shipment record is marked as owned by a specific scale unit or hub. When you release a load from the **Load planning workbench** page, the system changes the assigned ownership. However, because of the previously listed conditions, the system might be unable to resolve the data ownership. Therefore, it fails to release the load to the warehouse.

### Resolution of issue 1

Split the load into two smaller loads before you release it to the warehouse.

## Issue 2: Error while a wave is processed on a scale unit

### Symptoms of issue 2

When you're processing a wave on a scale unit, you receive an error message that has the following form:

> You cannot modify load line with RecId = %1, load id= %2 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.

Here is an actual example that includes sample data:

> Infolog for job Execute Wave USMF-000000012 (9223377668365210)  
> Infolog for task Execute Wave USMF-000000012 (9223377668370462)  
> You cannot modify load line with RecId = 68719478242, load id= USMF-000034 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.

### Cause of issue 2

In a distributed hybrid topology deployment, ownership of the load and shipment data is assigned to a specific scale unit or hub. As part of the waving processing, ownership of the data is expected to be assigned to a scale unit.

When you install a scale unit warehouse workload, if an open shipment is associated with a load and a wave, the system can't control the data ownership. Therefore, the wave processing fails on the scale unit.

### Resolution of issue 2

Release the load to the warehouse from the hub.

## Troubleshoot issues by viewing a record's ownership and destination

In a distributed hybrid topology deployment, many types of records are marked as owned by a specific scale unit or hub. After you switch to a distributed hybrid topology and/or set up a new scale unit warehouse workload, the system assigns ownership to each relevant record. This process can sometimes cause errors or unexpected results. Therefore, the information about a record's ownership and transfer destination can help you troubleshoot issues that occur after you make those types of changes.

Follow these steps to view the ownership and transfer destination of a record.

1. Open the relevant record.
1. On the Action Pane, on the **Options** tab, in the **Record info** group, select **Show all fields**.
1. The page that appears shows values for all the fields that are available for the selected record. Review the following fields:

    - **SYSSCALEUNITID** – This field shows the current owner of the record.
    - **SYSTARGETSCALEUNITID** – This field shows the scale unit ID of the hub or scale unit that the record will be transferred to when the current owner has finished working with it. The value of this field is used by batch jobs that manage this type of process. Although this field isn't directly related to ownership, ownership might change when the record is transferred. In some cases, this field will be blank.
