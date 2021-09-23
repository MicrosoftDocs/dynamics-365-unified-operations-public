--- 
title: Mixed inventory types when using dock management profile 
description: For a dock management profile to effectively manage the mixing of inventory, a work header break must be set up first. This page explains how to do it. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Inventory types are being mixed when using a dock management profile

## Symptoms

You're using *shipment consolidation policies*. You've set up a *dock management profile* for a *location profile*, but when work is created, the inventory types are mixed at the final location.

## Resolution

Dock management profiles require work to be split up front. In other words, the dock management profile expects that a work header won't have multiple put locations.

For the dock management profile to effectively manage the mixing of inventory, a work header break must be set up.

In this example, our dock management profile is configured such that **Inventory types that should not be mixed** is set to *Shipment ID*, and we'll set up a work header break for it:

1. Go to **Warehouse management \> Setup \> Work \> Work templates**.
1. Select the **Work order type** to edit (for example, *Purchase orders*).
1. Select the work template to edit.
1. On the Action Pane, select **Edit query**.
1. Open the **Sorting** tab and add a row with the following settings:
    - **Table** - *Temporary work transactions*
    - **Derived table** - *Temporary work transactions*
    - **Field** - *Shipment ID*
1. Select **OK**.
1. You return to the **Work templates** page. On the Action Pane, select **Work header breaks**.
1. On the Action Pane, select **Edit**.
1. Select the check box associated with the **Field name** *Shipment ID*.
1. On the Action Pane, select **Save**.
