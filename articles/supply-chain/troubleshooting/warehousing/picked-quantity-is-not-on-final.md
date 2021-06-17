---
title: You can't confirm a shipment because items haven't been picked
description: You can't confirm a shipment because items haven't been picked
author: perlynne
ms.date: 04/21/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: lbc
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.18
---

# You can't confirm a shipment because items haven't been picked

Error code: LoadNotPickedAndMovedToFinalShippingLocation

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> Some of the items that are needed for load %1 have not yet been picked and moved to the final shipping location.

Therefore, you can't confirm the shipment for the load.

## Cause

The load or shipment can't be confirmed in its current state because one of the following conditions might exist:

- The related work hasn't yet been picked and moved to the final shipping location.
- The picked work quantity doesn't match the created work quantity on the load line.
- The location directive has been configured with packing location as the final shipping location while using Wave template containerization.

## Resolution

The load or shipment is currently in a state where shipment confirmation fails. To fix this issue, complete one of the following tasks:
- Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match.
- Cancel the works that have been created with the packing location as the final shipping location, reconfigure the location directive, and re-release the load.

### Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Cancel the works that have been created with the packing location as the final shipping location, reconfigure the location directive, and re-release the load.

Use the following procedure to cancel the already created works with the packing final put location with the automated containerization in place.

1. Go to **Warehouse management \> Periodic tasks \> Clean up \> Cancel work**.
1. In the **Work ID** field, specify the ID of the work that you want to cancel, and that currently has a **Work status** value of *Open*, *In progress*, *Canceled*, *Combined*, or *Closed*.
1. Select **OK**.
1. Select **Yes** to confirm that you want to cancel the work.
1. Repeat this procedure for the other works, if necessary.

For more information, see [Cancel warehouse work for exception handling](../../warehousing/cancel-warehouse-work.md).

Use the following procedure to reconfigure the location directive to not use packing location as the final shipping location if there is an automated containerization defined through the Wave template.

1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the **Work order type** field, select *Sales orders*.
1. Select the location directive that is used for the automated containerization.
1. On the **Location Directive Actions** FastTab, select the **Edit query**.
1. In the query editor dialog box, on the **Range** tab, find the row where the **Field** field is set to *Location profile*, and verify that the **Criteria** field for that row is not set to location profile with packing location type. Adjust the **Criteria** field to correct final put location.

Use the following procedure to re-release the load and create the works with the correct final shipping location.

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. In the **Loads** section, find the load that needs to be released.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse. 
1. Repeat this procedure for the other loads, if necessary.