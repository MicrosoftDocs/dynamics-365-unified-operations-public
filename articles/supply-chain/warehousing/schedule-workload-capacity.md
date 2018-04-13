---
# required metadata

title: Schedule workload capacity
description: This topic describes how to set up and schedule the the workload capaccity for workers in a warehouse or for an entire warehouse.
author: MarkusFogelberg
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  WMSWorkloadCapacity
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

[!include[banner](../includes/banner.md)]

# Schedule workload capacity

You can schedule workload capacity for warehouses, and also project the current
and future workloads for the workers in individual warehouses. You can project
the workload for the whole warehouse, or you can project the workload separately
for incoming and outgoing workloads.

To project workload output for selected warehouses, master scheduling data must
be available for the selected warehouses. For more information, see [Master plans]
/[master-planning](https://github.com/MicrosoftDocs/Dynamics-365-Operations/tree/master/articles/supply-chain/master-planning)/**master-plans.md**.

Schedule and view workloads for a warehouse

To schedule workload capacity for a warehouse, you create a workload setup for
one or more warehouses, and then associate the workload setup with a master
plan. In the workload capacity setup, you can define limits on weight or volume
for incoming and outgoing transactions. You can also create more than one setup
for each warehouse and then associate the setup with individual master plans.
For example, you might do this to comply with seasonal changes in the workforce.

If the workers for a warehouse work with transactions for both incoming and
outgoing workloads, you can configure the warehouse capacity setup to project
the workload in a combined view.

To schedule and view workloads for warehouses, you must do the following tasks:

1.  Create a workload capacity setup and define workload capacity limits for one
    or more warehouses.

2.  Associate the workload capacity setup with a master plan to create workload
    projections and to specify how long the projections will apply.

Create a workload capacity setup for a warehouse

1.  Select **Inventory management** \> **Setup** \> **Warehouse monitoring** \>
    **Workload capacity**.

2.  Select **New** at the top of the page to create a workload capacity setup.

3.  Under **Warehouses**, select **New**, and then enter values on the line to
    associate a warehouse with the workload capacity setup.

4.  Select the **Combined inbound and outbound workload** check box to display
    the total workload for incoming and outgoing transactions in one view on the
    **Workload capacity** report.

5.  On the **Transaction types** tab, select the incoming and outgoing
    transaction types that the workload limits will apply to.

>   **Note**

>   You must select at least one transaction type for both the incoming and
>   outgoing workloads.

Volume and weight

You can set up limits for volume or weight depending on which limitations are
relevant for the warehouse workforce. The limits that you specify are included
in the workload capacity projection that you can view on the **Workload
capacity** report.

To project information about volume and weight for items, the standard volume of
one inventory item, and the weight of one inventory item must be specified for
all products. The fields that are required are available in the **Released
product details** form on the **Manage inventory** FastTab, in the following
field groups:

-   **Handling**

-   **Physical dimensions**

-   **Weight measurements**

If this information is not specified correctly, you will receive a message when
you generate the **Workload capacity** report. From the report, you can drill
down to identify the information that is missing to project the future workload.

Associate a workload capacity setup with a master plan

1.  Click **Inventory management** \> **Periodic** \> **Schedule workload**.

2.  In the **Master plan** field, select the master plan to use for workload
    projections.

3.  In the **Number of days** field, specify the number of days that the
    workload projection covers.

4.  In the **Workload** field, select the workload setup to associate with the
    master plan.

View workload capacity

1.  Click **Inventory management** \> **Inquiries and reports** \> **Physical
    inventory reports** \> **Workload capacity**.

2.  In the **Number of columns** field, specify the number of columns to display
    on the report.

3.  In the **Order type** field, select **Planned and confirmed**, **Planned**,
    or **Confirmed** to indicate the type of orders to project on the report.

4.  In the **Load type** field, select a load type to indicate if the workload
    capacity should be projected for volume, or weight.

5.  In the **Workload capacity** field, select a workload capacity setup.

WMSWorkloadCapacity
