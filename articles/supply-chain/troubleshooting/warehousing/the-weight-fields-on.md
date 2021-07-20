---
title: The weight fields on load lines don't match the weight fields on the load
description: The weight fields on load lines don't match the weight fields on the load
author: perlynne
ms.date: 04/15/2021
ms.topic: troubleshooting
ms.search.form: WHSShipmentDetails_WHSShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-05-15
ms.dyn365.ops.version: 10.0.18
---

# The weight fields on load lines don't match the weight fields on the load

Error codes: WHSLoadWeightOnLinesDoNotMatchLoadWarning

## Symptoms

The system shows the following error message:

> The weight fields on load lines do not match the weight fields on load %1. Run the Warehouse load weight consistency check to recalculate the weight fields.

## Cause

The **Net weight** and **Tara weight** fields are set to *0* (zero) on the load line. However, the weight fields aren't set to *0* for the weight measurements on the product. When weight fields aren't set on the load line, any corrections of the quantity on the load line might cause incorrect weight calculation on the load. This issue might occur if the weights on the product have been changed since the load line was created.

## Resolution

By default, when a load line is created, the weight fields from the product are entered on it. If the weight is zero, you can recalculate it by using the *Warehouse load weight consistency check* functionality.

1. Go to **System administration \> Periodic tasks \> Database \> Consistency check**.
1. In the **Consistency check** dialog box, set the **Module** field to *Warehouse management*.
1. Set the **Check/Fix** field to *Fix error*.
1. In the checkbox list, select the **Warehouse load weight consistency check** checkbox, and make sure that only the row for this checkbox is highlighted.
1. At the top of the checkbox list, select the ellipsis button (**...**), and then select **Dialog** on the menu.
1. In the **Warehouse load weight consistency check** dialog box, set the following fields to specify the criteria that the consistency check should run for:

    - **Load ID:** Specify a load ID. Leave this blank to check all load IDs.
    - **Item number:** Specify an item number. Leave this blank to check all items.
    - **Always recalculate weight on loads:** Set this option to *Yes*.
    - **Allow overwrite of weight on load lines:** Set this option to *Yes*.

1. Select **OK** to close the **Warehouse load weight consistency check** dialog box.
1. Select the ellipsis button, and then select **Execute** on the menu.

The weight is recalculated based on the criteria that you specified. Select the **Message details** link to view the result of the consistency check.
