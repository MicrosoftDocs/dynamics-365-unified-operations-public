---
# required metadata

title: Warehouse location status
description: This topic provides an overview of Warehouse location status.
author: Mirzaab
manager: AnnBe
ms.date: 12/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations, Supply Chain Management
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2019-12-31
ms.dyn365.ops.version: 10.0.1

---

# Warehouse location status

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management includes several location fields to provide flexibility in working with and maintaining locations. Location statuses can be included in the location directives query for better warehouse flow control.

There are four fields on the **Locations** page that track information about the current state of a location. These fields allow warehouse managers to get a status overview of the warehouse locations, and also enable advanced reporting and filtering. These fields are:

- **Item number:** Item that is currently in the location. If the location contains multiple items, this field will be blank.
- **Last activity date and time:** Timestamp of the last warehouse transaction that was performed against the location.
- **Aging date:** Date the inventory in the location was brought into the warehouse. This value is calculated based on the license plate aging date. It is accurate for license plate-tracked locations but not guaranteed to be accurate for non-license plate-tracked locations.
- **Location status:** There are four options for location status:
  - **Undetermined:** Location profile cannot track status. Current status is unknown.
  - **Empty:** There is currently no inventory in the location.
  - **Picking:** Outbound transactions have been performed against the location after it was last empty.
  - **Storage:** Only inbound transactions have been performed since the location was last empty.

## Enable the warehouse location status feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Warehouse location status

## Setup warehouse location status

### Prepare the sample data required for this example scenario

Before you start working through the scenario, you must activate sample data and set up the feature as described in this section. The scenario requires you to access the Dynamics 365 for Finance and Operations - Warehousing app (or, the browser based emulator) to complete scenario activity. Steps provided here will follow the mobile app activity, the browser based steps will be similar.

#### Use the USMF legal entity

To work through the example scenario using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

#### Set up location profiles

The example scenario requires that you prepare two location profiles as follows:

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.

1. Select **Edit** to put the page into edit mode.

1. Select the **BULK-06** profile.

1. On the **General** FastTab, make the following settings:

    - **Enable item in location** - Set to "Yes".
    - **Enable location activity date and time** - Set to "Yes".
    - **Enable location status** - Set to "Yes".

    These parameters control whether the references field on the location are active or not.

1. Select the **PICK-06** profile and repeat the previous step for that profile.

### Scenario

1. Go to **Procurement and Sourcing > Purchase orders > All purchase orders**.

1. Select **New**.

1. In the **Create purchase order** flyout **Vendor** fast tab **Vendor account** field, select **104**.

1. In the **General** fast tab **Warehouse** field, select **61**.

1. Select **OK**.

1. Your new purchase order opens. It includes an empty line in the **Purchase order lines** section. Enter the following values for this line:

    - **Item number** - "A0002"
    - **Quantity** - "5"

1. Confirm the purchase order. On the Action Pane select **Purchase**, in the **Actions** group select **Confirm**.

1. Open the mobile device and go to **Inbound > Purchase Receive**.

1. Select the **PONUM** field

1. Enter the **PO number** and select **Enter** (or, select the check mark at bottom of the screen).

1. Select the **ITEM** field.

1. Enter the **Item number**, **A0002** and select **Enter**.

1. The **QTY** screen gives you two options to enter a value, select the **Plus (+)** or **Minus (-)** fields to add or subtract a numerical value; or, select the **Empty** space between the (-) and (+) fields to open the number pad. Enter **5** then select the **Check mark** button to confirm your entry.

1. Confirm your selection of item **A0002*** and **QTY** by selecting **Enter**. You will see a message at the bottom of the screen indicating **Work Completed**.

1. Select the **3 lines** (*Hamburger*) in the upper right corner and select **Cancel** to exit **Purchase Receive** and return to the *Inbound* menu.

1. On the purchase order, select **Work details** in the **Purchase order lines** area. Select the **General** tab, note the **Work ID** and **Target license plate ID** that were created.

1. In the **Lines** section and note the **Pick** and **Put** *Location*.

1. On the mobile device, go to **Inbound > Purchase Put-away**.

1. Select the **ID** field.

1. **Enter** the **Work ID**, select **Enter**.

1. Confirm the *Pick* entry by selecting **Enter**.

1. Select the **3 lines** (*Hamburger*) in the upper right corner and select **Done** to complete the *Pick* work.

1. Make note of the Put **Loc** (Putaway). Confirm the *Put* entry by selecting **Enter**. You will see a message at the bottom of the screen indicating **Work Completed**.

1. Select the **3 lines** (*Hamburger*) in the upper right corner and select **Cancel** to exit **Purchase Put-away** and return to the *Inbound* menu.

1. Select **Back** to return to the **Main Menu**.

1. In Finance and Operations, go to **Warehouse management > Setup > Warehouse > Locations**.

1. Filter on **Location**, and enter the putaway location from the purchase order work.

    - The **Location status** column shows a value of "Storage" because the last transaction against this location was put.
    - The **Item number** column shows a value of "A0002", which is the item that was received and put to the location.
    - The **Last activity date and time** column shows the timestamp for when the work was completed at the location.

1. On the mobile device, go to **Quality** then select **Movement**.

1. Select the **LOC/LP** field.

1. Enter the **Location** from the putaway location in the prior steps.

1. Confirm the information displayed by selecting **Enter**. Note the License plate number.

1. Select the *To Information* **LOC/LP** field.

1. Enter **06A07R2S1B** as the location to move the item into.

1. Confirm the *To Information* **LP** (Target license plate ID) automatically generated by selecting **Enter**. You will see a message at the bottom of the screen indicating **Work Completed**.

1. Select the **3 lines** (*Hamburger*) in the upper right corner and select **Cancel** to exit **Movement** and return to the *Quality Management* menu. Select **Back** to return to the **Main Menu**.

1. In Finance and Operations, go to **Warehouse management > Setup > Warehouse > Locations**.

1. On the **Locations** page, refresh and view the original putaway location again. Notice that the **Location Status** is now "Empty", and the **Item number** column is blank.

1. View the record for location **06A07R2S1B** and notice that the **Status** changed to "Storage" and the **Item number** and **Last Activity Date and Time** fields are updated.

1. Go to **Sales and marketing > Sales orders > All sales orders**.

1. Select **New**.

1. In the **Create sales order** flyout, **Customer account** field, select **US-002**.

1. In the **Warehouse** field, select **61**.

1. Select **OK**.

1. Your new sales order opens. It includes an empty line in the **Sales order lines** section. Enter the following values for this line:

    - **Item number** - "A0002"
    - **Quantity** - "1"

1. In the **Sales order lines** fast tab, select **Inventory** from the action pane then select **Reservation**.

1. On the **Reservation** form, select **Reserve lot** to reserve the order line. Select the **(X)** in the top right corner to close the form.

1. On the Sales order Action Pane, select **Warehouse** and in the *Actions* group select **Release to warehouse**.

1. In the **Sales order lines** section action pane, open the **Warehouse** menu and select **Work details**. Copy the **Work ID** that was created.

1. On the mobile device, Select **Outbound**.

1. Select **Sales picking**.

1. Select the **ID** field.

1. Enter the **Work ID** you copied above. Select **Enter**.

1. The *Sales orders: Pick* **LOC** field will suggest the picking location as the putaway location created earlier. Note the location and select the **LOC** field.

1. Enter the location and select **Enter**.

1. Select the **LP** field.

1. Enter the License plate number noted in the Movement activity above. Select **Enter**.

1. Select the **Item** field.

1. Enter the item number **A0002**. Select **Enter**.

The **QTY** screen gives you two options to enter a value, select the **Plus (+)** or **Minus (-)** fields to add or subtract a numerical value; or, select the **Empty** space between the (-) and (+) fields to open the number pad. Enter **1** then select the **Check mark** button to confirm your entry.

1. Select the **TARGET LP** field.

1. Enter a user defined **Target license plate ID**. Select **Enter**.

1. Confirm the picking work by selecting **Enter**. You will see a message at the bottom of the screen indicating **Work Completed**.

1. Select the **3 lines** (*Hamburger*) in the upper right corner and select **Cancel** to complete picking activity and return to the Outbound menu.

1. In Finance and Operations, go to **Warehouse management > Setup > Warehouse > Locations**.

1. Filter on **Location**, and enter the pick location from the sales order work.

1. Notice that the **Location Status** for the location the sales order work picked from is updated to "Picking", and the **Last Activity Date and Time** field is updated.

> [!NOTE]
> The location fields are only updated by warehouse transactions. Moving inventory using a journal, or other non-WHS processes will not update the fields.
