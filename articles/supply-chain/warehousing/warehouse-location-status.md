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

## Try out this feature

### Prepare the sample data required for this example scenario

Before you start working through the scenario, you must activate sample data and set up the feature as described in this section.

#### Use the USMF legal entity

To work through the example scenario using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

#### Set up location profiles

The example scenario requires that you prepare two location profiles as follows:

1. Go to **Warehouse management > Setup > Warehouse > Location profiles**.

1. Select **Edit** to put the page into edit mode.

1. Select the "BULK-06" profile.

1. On the **General** FastTab, make the following settings:

    - **Enable item in location** - Set to "Yes".
    - **Enable location activity date and time** - Set to "Yes".
    - **Enable location status** - Set to "Yes".

    These parameters control whether the references field on the location are active or not.

1. Select the "PICK-06" profile and repeat step 3 for that profile.

### Example scenario

1. Go to **Procurement and Sourcing > Purchase orders > All purchase orders**.

1. Select **New**.

1. In the **Vendor account** field, select "104".

1. In the **Warehouse** field, select "61". 

1. Select **OK**.

1. Your new purchase order opens. It includes an empty line in the **Purchase order lines** section. Enter the following values for this line:

    - **Item number** - "A0002"
    - **Quantity** - "5"

1. Reserve the order line and release to warehouse.

1. Open the mobile device and go to **Inbound > Purchase Receive**. 

1. Enter the PO number and item, followed by the full quantity of the line.

1. On the purchase order, select **Work details** in the **Purchase order lines** area. On the **General** tab, note the work ID that was created.

1. On the mobile device, go to **Inbound > Purchase Put-away** and enter the work ID.

1. Complete the pick and the put, noting the putaway location.

1. In Supply Chain Management, go to **Warehouse management > Setup > Warehouse > Locations**.

1. Filter on **Location**, and enter the putaway location from the purchase order work.

    - The **Location status** column shows a value of "Storage" because the last transaction against this location was put.
    - The **Item number** column shows a value of "A0002", which is the item that was received and put to the location.
    - The **Last activity date and time** column shows the timestamp for when the work was completed at the location.

1. On the mobile device, go to **Quality > Movement** and enter the putaway location from the purchase order work as the location. 

1. Confirm the full quantity. Enter "06A07R2S1B" as the put location and accept the system-generated license plate.

1. In Supply Chain Management, on the **Locations** page, refresh and view the original putaway location again. Notice that the **Location Status** is now "Empty", and the **Item number** column is blank.

1. View the record for "06A07R2S1B" and notice that the **Status** changed to "Storage" and the **Item number** and **Last Activity Date and Time** fields are updated.

1. Go to **Sales and marketing > Sales orders > All sales orders**.

1. Select **New**.

1. In the **Customer account** field, select "US-002".

1. In the **Warehouse** field, select "61".

1. Select **OK**.

1. Your new sales order opens. It includes an empty line in the **Sales order lines** section. Enter the following values for this line:

    - **Item number** - "A0002"
    - **Quantity** - "1"

1. Reserve the order line and release to warehouse.

1. In the **Sales order lines** section, open the **Warehouse** menu and select "Work details" Copy the **Work ID** that was created.

1. On the mobile device, go to **Outbound > Sales picking** and enter the work ID from above.

1. Enter the putaway location created earlier and confirm the pick and put.

1. In Supply Chain Management, go to the **Locations** page. Notice that the **Location Status** for the location the sales order work picked from is updated to "Picking", and the **Last Activity Date and Time** fields are updated.

> [!NOTE]
> The location fields are only updated by warehouse transactions. Moving inventory using a journal, or other non-WHS processes will not update the fields.
