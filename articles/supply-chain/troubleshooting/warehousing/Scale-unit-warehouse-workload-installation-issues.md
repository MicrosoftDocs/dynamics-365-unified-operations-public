---
title: Processing issues 'right after' scale unit warehouse workload installation.
description: After deploying a warehouse work load some processes might fail. This topic lists the reasons and workarounds.
author: perlynne
ms.date: 1/3/2022
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-01-15
ms.dyn365.ops.version: 10.0.25
---

# Processing issues after a scale unit warehouse workload installation

## Symptoms #1
When releasing a load from the **Load planning work bench**/**Outbound load planning work bench** an Infolog error is shown:
> An exception was caught when posting the load %1, load could not be released.
> <p>UPDATE WHSSHIPMENTTABLE SET ...</p>
> <p>Cannot edit a record in Shipments (WHSShipmentTable). Shipment ID: ...</p>
<!--
An exception was caught when posting the load USMF-000033, load could not be released.
session 5133 (Admin)
UPDATE WHSSHIPMENTTABLE SET ORDERNUM=?,RECVERSION=?,MODIFIEDDATETIME=?,MODIFIEDBY=? WHERE ((RECID=?) AND (RECVERSION=?))
[Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Scale Unit @@ attempted to update records owned by Scale Unit @A.
Object Server Azure:
Cannot edit a record in Shipments (WHSShipmentTable). Shipment ID: USMF-000031, USMF-000033. The SQL database has issued an error.
-->

## Cause #1
In a hybrid topology deployment the load and shipment data gets assigned an ownership of either the hub or a scale unit and as part of the release to warehouse process from the **Load planning workbench**, the ownership of data will change.
When installing a scale unit warehouse workload and having a non released load containing multiple lines associated to different orders where not all the load lines are associated to a shipment, and using shipment consolidation - the system cannot control the data ownership and will thereby fail the release to warehouse process.

## Resolution #1
Split the load into two before releasing to warehouse.

>

## Symptoms #2
When running the wave processing on a scale unit the following Infolog error is shown:

> You cannot modify load line with RecId = %1, load id= %2 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.
<!--
Infolog for job Execute Wave USMF-000000012 (9223377668365210)
Infolog for task Execute Wave USMF-000000012 (9223377668370462)
You cannot modify load line with RecId = 68719478242, load id= USMF-000034 as it is still owned by the enterprise hub. Please make sure that the corresponding outbound load has been released to a scale unit and thereby warehouse order lines created.
-->

## Cause #2
In a hybrid topology deployment the load and shipment data gets assigned an ownership of either the hub or a scale unit and as part of the waving process the data is expected being in the ownership of a scale unit.
When installing a scale unit warehouse workload and having a open shipment associated to a load and wave, the system cannot control the data ownership and will thereby fail the wave processing on the scale unit.

## Resolution #2

Release the load to warehouse from the hub.


## View ownership of records

You can use the following procedure to view the ownership of a particular record.

1. In the page showing the record select **Options \> Record info \> Show all fields**.
1. Find the field **SYSSCALEUNITID** - this will be the current owner of the record. And **SYSTARGETSCALEUNITID** can become the owner, depending on data processing.
