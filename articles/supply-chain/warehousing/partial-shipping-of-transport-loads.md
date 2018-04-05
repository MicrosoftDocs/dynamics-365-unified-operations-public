---
# required metadata

title: Partial shipping of a transport load
description: This topic describes how you can partially ship a load and postpone the planning of capacity for the load.
author: Mirzaab
manager: AnnBe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 1705903
ms.assetid: 427e01b3-4968-4cff-9b85-1717530f72e4
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 8.0.0
---

# Partial shipping of a transport load

[!include[banner](../includes/banner.md)]

Partial shipping of a staged load

With the setup to ship a partial load you can handle loads where the capacity
cannot be determined until all sales lines have been added to a load. The
process can then be finalized when the exact pallet count is known. So, the
decision about what pallets will be assigned to what transport is postponed
until the moment where a transport is being physically loaded out of the staged
inventory.

This feature offers an alternative to the enforcement of a more rigid structure
where you need to pre-determine what pallets will be assigned to what transport
to have picking or loading work created. It allows users to configure individual
loads for a partial ship confirmation which enables the transport loading
processes for those loads. With this option, the transportation planning
department can plan loads without having to consider the capacity of individual
transports.

At the time of loading, workers can define new or identify an existing transport
load that a pallet can be loaded to. This data can be recorded via a mobile
device.

This feature allows several warehouse workers to load inventory from the same or
from different loads onto the same truck and the loads can then be fully or
partially shipped.

NOTE: To be able to load inventory from a load to a certain transport load and
to partially ship the load, work must be generated with a loading class.
Ordinary picking work of the type Picking cannot be loaded to a transport load
such as a truck.

Set up transport loads for partial shipping

The setup requirements to partially ship loads include the following two steps.

**Set the loading strategy**

Set the loading strategy to allow partial loading. You can set the loading
strategy after you have created a load.

1.  Select **Warehouse management \> Loads \> All loads**.

2.  Select a load and click **Header**.

3.  In the **Loading strategy** field, select **Partial load shipping allowed**.

**Create a menu item for loading of transport loads**

Create a new menu item that allows loading of transport loads. A transport load
allows you to group work lines from one or from multiple loads. Everything that
is added to the transport load can then be shipped using a mobile scanner.

1.  Select **Warehouse management \> Setup \> Mobile device \> Mobile device
    menu items**.

2.  Select **New** and in the **Mode** field, select **Work**.

3.  Set the **Use existing work** slider to **Yes**.

4.  On the **General** tab, in the **Directed by** field, select **Transport
    loading**.

NOTE: To allow ship confirmation on a mobile scanner, select **Transport load**
in the **Allowed ship confirmation type** field.

**Ship confirm a transport load from the client**

Using this setup, you can ship confirm a transport load that includes a full
load or a partially loaded load.

Select **Warehouse management \> Loads \> Transport loads.**

Select **Ship and receive**, and, under **Confirm**, select **Transport**. Using
this procedure, you can ship confirm a transport load that includes a full load
or a partially loaded load.
