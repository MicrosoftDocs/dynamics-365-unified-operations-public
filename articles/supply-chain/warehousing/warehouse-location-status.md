---
# required metadata

title: Warehouse location status
description: This article provides an overview of the Warehouse location status feature.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLocationProfile,WHSLocation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.7

---

# Warehouse location status

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes several location fields that give you flexibility when you work with and maintain locations. You can include location statuses in the location directive query to provide better control over warehouse flow.

The following four fields on the **Locations** page track information about the current status of a location. These fields let warehouse managers get an overview of the status of the warehouse locations. They also allow for advanced reporting and filtering.

- **Item number** – The item that is currently in the location. If the location contains multiple items, this field is blank.
- **Last activity date and time** – The timestamp of the last warehouse transaction that was performed against the location.
- **Aging date** – The date when the inventory in the location was brought into the warehouse. This value is calculated based on the aging date of the license plate. It's accurate for locations that are license plate–tracked, but it might not be accurate for locations that aren't license plate–tracked.
- **Location status** – The status of the location. There are four possible values:

    - **Undetermined** – The location profile can't track status. Therefore, the current status is unknown.
    - **Empty** – There is currently no inventory in the location.
    - **Picking** – Outbound transactions have been performed against the location since it was last empty.
    - **Storage** – Only inbound transactions have been performed against the location since the location was last empty.

## Turn the Warehouse location status feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Warehouse location status* feature in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

## Set up warehouse location status

### Prepare the sample data that is required for the example scenario

Before you start to work through the scenario, you must activate sample data and set up the feature as described in this section. To complete the example scenario, you must use either the Warehouse Management mobile app or the browser-based emulator. The steps that are provided here use the Warehouse Management mobile app. The steps for the browser-based emulator are similar.

#### Use the USMF legal entity

To work through the example scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

#### Set up location profiles

The example scenario requires that you prepare two location profiles.

1. Go to **Warehouse management \> Setup \> Warehouse \> Location profiles**.
1. Select **Edit** to put the page into edit mode.
1. Select the **BULK-06** profile.
1. On the **General** FastTab, set the following values:

    - **Enable item in location:** Set this option to _Yes_.
    - **Enable location activity date and time:** Set this option to _Yes_.
    - **Enable location status:** Set this option to _Yes_.

    These options control whether the reference fields on the location are active.

1. Repeat steps 3 through 4 for the **PICK-06** profile.

> [!NOTE]
> When the parameters on the location profile (**Enable item in location**, **Enable location activity**, **Enable location status**) are set to *Yes*, the system immediately updates the relevant locations by executing the *warehouse location status consistency check* job.

### Scenario

1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Create purchase order** dialog box, on the **Vendor** FastTab, in the **Vendor account** field, select *104*.
1. On the **General** FastTab, in the **Warehouse** field, select *61*.
1. Select **OK**.
1. Your new purchase order (PO) is opened. It includes an empty line in the **Purchase order lines** grid. On this line, set the following values:

    - **Item number:** _A0002_
    - **Quantity:** _5_

1. On the Action Pane, on the **Purchase** tab, in the **Actions** group, select **Confirm** to confirm the purchase order.
1. On the mobile device, go to **Inbound \> Purchase Receive**.
1. Select the **PONUM** field, enter the PO number, and confirm.
1. Select the **ITEM** field, enter *A0002* as the item number, and confirm.
1. On the **QTY** page, enter *5* as the quantity, and confirm.

    You can enter the quantity in either of the following ways:

    - Select the plus sign (**+**) or minus sign (**–**) button to add or subtract a numerical value.
    - Select the blank field between the plus sign (**+**) and minus sign (**–**) buttons to open the number pad.

1. Confirm your selection of item number *A0002* and a quantity of *5*. A "Work Completed" message appears at the bottom of the page.
1. Select the Menu button (sometimes referred to as the hamburger or the hamburger button) in the upper-right corner, and then select **Cancel** to exit **Purchase Receive** and return to the **Inbound** menu.
1. On the purchase order page, select **Work details** above the **Purchase order lines** grid.
1. On the **General** tab, notice the **Work ID** and **Target license plate ID** values that were created.
1. In the **Lines** section, notice the **Location** values for the *Pick* and *Put* work types.
1. On the mobile device, go to **Inbound \> Purchase Put-away**.
1. Select the **ID** field, enter the work ID, and confirm.
1. Confirm once more to complete the *Pick* entry.
1. Select the Menu button in the upper-right corner, and then select **Done** to complete the *Pick* work.
1. Make a note of the Putaway location, and confirm. A "Work Completed" message appears at the bottom of the page.
1. Select the Menu button in the upper-right corner, and then select **Cancel** to exit **Purchase Put-away** and return to the **Inbound** menu.
1. Select **Back** to return to the main menu.
1. In Dynamics 365 Supply Chain Management, go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. Filter on **Location**, and enter the putaway location from the purchase order work. You should see the following results:

    - The **Location status** column shows a value of *Storage*, because the last transaction against this location was a put.
    - The **Item number** column shows a value of *A0002*, because that item was received and put to the location.
    - The **Last activity date and time** column shows the timestamp for the date and time when the work was completed at the location.

1. On the mobile device, go to **Quality \> Movement**.
1. Select the **LOC/LP** field, and enter the location you made note of in the previous steps.
1. Confirm the information that is shown. Make a note of the license plate number that is generated.
1. On the **To Information** screen, select the **LOC/LP** field, and enter *06A07R2S1B* as the location to move the item to.
1. On the **To Information** screen, confirm the **LP** value (the target license plate ID), which is automatically generated. A "Work Completed" message appears at the bottom of the page.
1. Select the Menu button in the upper-right corner, and then select **Cancel** to exit **Movement** and return to the **Quality Management** menu.
1. Select **Back** to return to the main menu.
1. In Dynamics 365 Supply Chain Management, go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. Refresh the **Locations** page, and view the original putaway location again. Notice that the **Location status** field is now set to *Empty*, and the **Item number** column is blank.
1. View the record for location *06A07R2S1B*, and notice that the **Status** value has changed to *Storage*, and the **Item number** and **Last activity date and time** fields have been updated.
1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New**.
1. In the **Create sales order** dialog box, in the **Customer account** field, select *US-002*.
1. In the **Warehouse** field, select *61*.
1. Select **OK**.
1. Your new sales order is opened. It includes an empty line in the **Sales order lines** grid. On this line, set the following values:

    - **Item number:** _A0002_
    - **Quantity:** _1_

1. On the **Sales order lines** FastTab, on the **Inventory** menu, select **Reservation**.
1. On the **Reservation** page, select **Reserve lot** to reserve the order line. Then select the **Close** button (**X**) in the upper-right corner to close the page.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. In the **Sales order lines** section, on the **Warehouse** menu, select **Work details**.
1. Copy the **Work ID** value that was created.
1. On the mobile device, go to **Outbound \> Sales picking**.
1. Select the **ID** field, enter the work ID that you copied earlier, and confirm.
1. On the **Sales orders: Pick** page, the **LOC** field suggests the picking location as the putaway location that was created earlier. Make a note of the location.
1. Select the **LOC** field, enter the location, and confirm.
1. Select the **LP** field, enter the license plate number that you made a note of during the Movement activity, and confirm.
1. Select the **Item** field, enter the *A0002* as the item number, and confirm.
1. On the **QTY** page, enter *1* as the quantity, and confirm.

    You can enter the quantity in either of the following ways:

    - Select the plus sign (**+**) or minus sign (**–**) button to add or subtract a numerical value.
    - Select the blank field between the plus sign (**+**) and minus sign (**–**) buttons to open the number pad.

1. Select the **TARGET LP** field, enter a user-defined target license plate ID, and confirm.
1. Confirm once more to complete the picking work. A "Work Completed" message appears at the bottom of the page.
1. Select the Menu button in the upper-right corner, and then select **Cancel** to complete the picking activity and return to the **Outbound** menu.
1. In Dynamics 365 Supply Chain Management, go to **Warehouse management \> Setup \> Warehouse \> Locations**.
1. Filter on **Location**, and enter the pick location from the sales order work.
1. Notice that the **Location status** field for the location that the sales order work picked from is now set to *Picking*, and the **Last activity date and time** field has been updated.

> [!NOTE]
> The location fields are updated only by warehouse transactions. If you move inventory by using a journal or other non-WMS processes, the fields won't be updated.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]