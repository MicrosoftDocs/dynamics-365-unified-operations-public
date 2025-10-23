---
title: Delivery information setup
description: Learn how to set up delivery information for the Landed cost module, including outlines on shipping ports and tracking control centers.
author: prasungoel 
ms.author: prasungoel 
ms.reviewer: kamaybac
ms.search.form: ITMPortTable, ITMLeadTimeTable, ITMLegTable
ms.topic: how-to
ms.date: 09/19/2025
ms.custom: 
  - bap-template
---

# Delivery information setup

[!include [banner](../../includes/banner.md)]

This article describes how to set up delivery information for the **Landed cost** module.

## Shipping ports

Shipping ports identify where goods are being shipped from and to. For each voyage, you define a "to" port and a "from" port, based on the journey that you select for the voyage vessel. Shipping ports build the legs of a journey and the voyage activities. Typically, you define them by using the name of the city and the country/region where the physical shipping port is located.

To work with shipping ports, go to **Landed cost** \> **Delivery information setup** \> **Shipping ports**. There, you can view, add, and remove records for your shipping ports. The following table describes the fields that are available for each record.

| Field | Description |
|---|---|
| Shipping port | Enter a unique identification name or number for the shipping port. |
| Description | Enter a description of the shipping port. |

## <a name="tracking-control-center"></a>Tracking control center

Use the Tracking control center to set up the lead times, status updates, and flow of information that is associated with a voyage as the shipping containers move from one leg to the next. When you create a tracking control record, you associate it with a specific leg of a journey for a voyage. When a voyage updates a leg, the associated record updates and fills in as defined. You can update tracking information for individual voyages from the **All voyages** page.

To open the Tracking control center, go to **Landed cost** \> **Delivery information setup** \> **Tracking control center**.

The Tracking control center shows one of three page views, depending on the value that you select in the **Create type** field in the list pane: *Blank*, *Lead time*, or *Status update*. Each create type updates a different set of information that is associated with the progress of a voyage from the point of origin to the final destination.

### Common rule settings

The following table shows the fields that are available for all three create types in the Tracking control center.

| Field | Description |
|---|---|
| Source table, Source field | These fields identify a source table and field in the database. The rule loads the value in the field and then uses it in the way that other settings of the rule define. |
| Target table, Target field | These fields identify a destination table and field in the database. The rule loads the value in the field and then uses it (or overwrites it) in the way that other settings of the rule define. |
| Activity | This field identifies the type of activity that the rule applies to a shipping container that matches the rule. |
| Matching criteria | This field determines how the system identifies a match for a rule. In each instance, the system reviews the data in the source and destination tables to determine whether and when a field should be updated in the target table.<p>For example, the source table is *Voyages*, and the target table is *Purchase header* or *Purchase lines*. The *Voyages* table has a **From port** value of *Hong Kong Special Administrative Region*, and the *Purchase header* table has a **From port** value of *Shanghai*. A rule is then created that has *Hong Kong Special Administrative Region* as the "from" port. In this case, the values of the **Matching criteria** field work in the following way:</p><ul><li>**Both** – The target field isn't updated, because one of the two ports doesn't match.</li><li>**Source** – The target field is updated, because the source table's "from" port is *Hong Kong Special Administrative Region*.</li><li>**Target** – The target field isn't updated, because the destination table's "from" port is *Shanghai* (not *Hong Kong Special Administrative Region*).</li></ul> |
| Copy action | The available values are *Copy* and *Default*. Select *Copy* to copy the value in the source field to the destination field. Select *Default* to set a static value for the destination field. |
| Default | When the **Copy action** field is set to *Default*, the **Default** field defines the default value of the destination field. For example, if the action is related to a port update, and the **Copy action** field is set to *Default*, the **Default** field identifies a port. |
| Leg | This field identifies the leg of the journey that the specified action occurs for, such as loading or customs. |
| Service provider | If a specific service provider is used for the current status update/leg of the journey, this field identifies the service provider. Service providers are defined in the vendor account. |

### Lead time rules

Lead time is the estimated time that a voyage needs to complete a defined leg of a journey. The lead time for each leg of a journey helps calculate the estimated delivery date for the voyage. Enter this date in the **Confirmed delivery date** field on every purchase line in the voyage.

Use lead time rules to manage date updates. When you use a journey template for a voyage, activities are automatically generated.

To add a lead time rule to the Tracking control center, follow these steps.

1. Follow one of these steps:

    - Go to **Landed cost** \> **Multi-leg journey setup** \> **Legs**. Select the leg that you want to set up lead times for. On the Action Pane, select **Tracking control center**. The Tracking control center is preloaded with information about the selected leg.
    - Go to **Landed cost** \> **Delivery information setup** \> **Tracking control center**. You must then manually select a leg in step 4 of this procedure.

1. In the list pane, set the **Create type** field to *Lead time*.
1. On the Action Pane, select **New**.
1. If you started from the Tracking control center in step 1, set the **Leg** field to the leg that you want to create a lead time rule for. If you started from the **Legs** page, the **Leg** field is preset to the leg that you selected before you opened the Tracking control center.

    Based on the value of the **Leg** field, several fields are automatically set, as shown here:

    - **Source table:** *Container activities*
    - **Source field:** *Start date*
    - **Target table:** *Container activities*
    - **Target field:** *Estimated end date*

1. In the **Activity** field, select the activity that the current rule should apply to.
1. In the **Lead time** field, enter the lead time (in days) that should be applied when the current rule is triggered.

### Status update rules

Records where the **Create type** field is set to *Status update* update the status of purchase order lines, or the status at the voyage, shipping container, or folio level. You can set the statuses independently. Use them to inform the user or department about the stage of a voyage (such as documents received or goods in transit).

When you set the **Create type** field to *Status update*, the Tracking control center includes a **Lines** FastTab where you can define a cost area and the updated status of the voyage. For example, you have a line where the **Cost area** field is set to *Container*, and the **Voyage status** field is set to *Goods in transit*. In this case, when an order completes the specified leg, the **Voyage status** field of the shipping container updates to *Goods in Transit*.

Status updates provide the status of a voyage throughout the voyage lines and purchase order lines that are associated with that voyage. As a voyage moves through its journey from the port, sailing, and customs, to the destination warehouse, the **Voyage status** field of the voyage record provides a quick view of the stage that the items are at.

To add a status update rule to the Tracking control center, follow these steps.

1. Follow one of these steps:

    - Go to **Landed cost** \> **Multi-leg journey setup** \> **Legs**. Select the leg that you want to set up a status update for, and then, on the Action Pane, select **Tracking control center**. The Tracking control center is preloaded with information about the selected leg.
    - Go to **Landed cost** \> **Delivery information setup** \> **Tracking control center**. You must then manually select a leg in step 4 of this procedure.

1. In the list pane, set the **Create type** field to *Status update*.
1. On the Action Pane, select **New**.
1. If you started from the Tracking control center in step 1, set the **Leg** field to the leg that you want to create a status update rule for. If you started from the **Legs** page, the **Leg** field is preset to the leg that you selected before you opened the Tracking control center.

    Based on the value of the **Leg** field, several fields are automatically set, as shown here:

    - **Source table:** *Container activities*
    - **Source field:** *Actual end date*
    - **Target table:** This field is left blank.
    - **Target field:** This field is left blank.

1. In the **Activity** field, select the activity that your rule should apply to.
1. On the **Lines** FastTab, enter the status updates for each cost area.

### Blank type rules

You use records that have a **Create type** value of *Blank* to override or enter a field value, based on the data of another field. A field from Landed cost will overwrite data in other areas of Microsoft Dynamics 365 Supply Chain Management, based on rules that are set up in the Tracking control center.

1. Go to **Landed cost** \> **Delivery information setup** \> **Tracking control center**.
1. In the list pane, set the **Create type** field to *Blank*.
1. On the Action Pane, select **New**.
1. Define the source and destination values, matching criteria, copy action, and other relevant parameters, as required for your rule.

### Required tracking control setup

For every journey template, two records must be set up in the Tracking control center. Both these records have a **Create type** value of *Blank* and are used in all Landed cost implementations. They help ensure that the purchase confirmed date and goods in transit expected dates are updated for voyages and on related purchase order lines in the expected way.

The first record is required to update purchase lines. It must have the following settings:

- **Source table:** *Container activities*
- **Source field:** *Estimated end date*
- **Target table:** *Purchase lines*
- **Target field:** *Confirmed or delivery date*

The second record is required to update goods in transit transactions. It must have the following settings:

- **Source table:** *Container activities*
- **Source field:** *Estimated end date*
- **Target table:** *Goods in transit order*
- **Target field:** *Expected date*
