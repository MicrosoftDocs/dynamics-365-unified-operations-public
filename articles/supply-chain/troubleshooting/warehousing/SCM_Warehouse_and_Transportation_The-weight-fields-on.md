---
title: The weight fields on load lines do not match the weight fields on load
description: The weight fields on load lines do not match the weight fields on load
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021
ms.topic: troubleshooting
ms.search.form: WHSShipmentDetails_WHSShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-03-24
ms.dyn365.ops.version: 10.0.18
---

# The weight fields on load lines do not match the weight fields on load

Error codes: WHSLoadWeightOnLinesDoNotMatchLoadWarning, WAX1967, WHSShipConfirm, WHSLoadWeightOnLinesDoNotMatchLoadWarning

The system displays the following error message:

> The weight fields on load lines do not match the weight fields on load %1. Run the Warehouse load weight consistency check to recalculate the weight fields.

## Issue description

The **Net weight** and **Tara weight** are set to zero on the load line. The weight fields are not zero on the weight measurements on the product. When weight fields are not set on the load line, any corrections of the quantity on the load line might result in incorrect weight calculation on the load. This might be the case if the weights on the product have been changed since the load line was created.

## Resolution

When a load line is created, the weight fields from the product will be defaulted on the load line. If the weight is zero, it can be recalculated using the **Warehouse load weight consistency check**.

1. Go to **System administration \> Periodic tasks \> Database \> Consistency check** to open the **Consistency check** dialog box.
1. Set **Module** to *Warehouse management*.
1. Set **Check/Fix** to *Fix error*.
1. In the check box list, select the **Warehouse load weight consistency check** check box and make sure that only this row is highlighted.
1. At the top of the check box list, select the ellipsis button to open a drop-down list and then select **Dialog** from the list.
1. The **Warehouse load weight consistency check** dialog box opens. Make the following settings to specify the values for which the consistency check should run:

    - **Load ID:** Specify a load ID. Leave this blank to check all load IDs.
    - **Item number:** Specify an item number. Leave this blank to check all items.
    - **Always recalculate weight on loads:** Set to *Yes*.
    - **Allow overwrite of weight on load lines:** Set to *Yes*.

1. Select **OK** to close the **Warehouse load weight consistency check** dialog box.
1. Select the ellipsis button to open a drop-down list and then select **Execute** from the list

The weight will be recalculated based on the criteria selected. Select the **Message details** link to see the result of the executed consistency check.
