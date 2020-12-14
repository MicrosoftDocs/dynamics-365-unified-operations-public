---
# Delivery information setup

title: Delivery information setup
description: This topic describes how to set up delivery information options for the Landed cost module.
author: mkirknel
manager: tfehr
ms.date: 12/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mkirknel
ms.search.validFrom: 2020-12-09
ms.dyn365.ops.version: Release 10.0.17
---

# Delivery information setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to set up delivery information options for the Landed cost module.

## Shipping ports

Shipping ports identify where goods are being shipped from and to. For each voyage, a to-port and a from-port will be defined based on the journey selected for the voyage vessel. The shipping ports are used to build the legs of a journey along with the voyage activities. Shipping ports are generally defined using the name of the city and country where the physical shipping port is located.

To work with shipping ports, go to **Landed cost \> Delivery information setup \> Shipping ports**. Here, you can view, add, and remove records for each of your shipping ports. The following table describes the settings available for shipping port.

| **Setting** | **Description** |
| --- | --- |
| **Shipping port** | Enter a unique identification name/number for the shipping port. |
| **Description** | Enter a description of the shipping port |

## Tracking control center

Use the **Tracking control center** to set up the lead times, status updates, and flow of information associated with a voyage as the shipping containers move from one leg to the next. When you create a tracking control record, the record is associated to a particular leg of a voyage journey. When a voyage updates the identified leg, the record will update and populate as defined. You can update tracking information for individual voyages from the **All voyages** page.

To open the tracking control center, go to **Landed cost \> Delivery information setup \> Tracking control center**.

The **Tracking control center** shows one of three different page views depending what is selected for the **Create type** drop-down list on the list pane (*Blank*, *Lead time*, or *Status update*). Each of the different create types updates a different set of information associated with the progress of a voyage from the point of origin to the final destination.

Fields listed below are shown on the **Tracking control center** with all three create types available for update and configuration.

| **Setting** | **Description** |
| --- | --- |
| **Activity** | Identifies the type of activity applied to a shipping container. |
| **Matching criteria** | This determines how the system identifies a match with a rule. In each instance, it will review the data in the source and destination tables to determine when and if a field is updated.<p>**Example**: The **Source table** is *voyages* and the **Destination table** is *Purchase header* or *Purchase lines*. The voyages table has a **From port** of *Hong Kong* and the purchase header has a **From port** of *Shanghai*. A rule is then created that has uses the from-port *Hong Kong*. The **Matching criteria** values in that control center will then work as follows:</p><ul><li>**Both** – Nothing will update because the two ports do not match.</li><li>**Source** – This would update because the source table's from-port is *Hong Kong*.</li><li>**Target** – This would not update because the destination table's from-port is *Shanghai*. |
| **Copy action** | The options are *Copy* and *Default*. Select *Copy* to copy the value in the source field to the destination field. Select *Default* to set a static value for the destination field. |
| **Default** | When the **Copy action** is set to *Default*, the **Default** field sets the value of the default in the destination field. For example, if the action is regarding a port update and the copy action is set to default, the default field will be a port identified here. |
| **Leg** | The leg of the journey for which the specified action occurs, such as loading or customs. |
| **Service provider** | If a specific service provider is used for this status update/leg of the journey, the service provider is listed. Service providers are defined in the vendor account. |

### Lead time types

The *Lead time* is the estimated time a voyage will require to complete a defined leg of a journey on a voyage. The lead time on each leg of a journey is used to calculate the estimated delivery date of a voyage. This date is then populated on every purchase line within a voyage in the **Confirmed delivery date** field on the purchase line.

Use lead times to manage the updating of dates. Activities are automatically generated when a journey template is used on a voyage. Link activities to legs of a journey by creating the lead time and status rules from the leg.

> [!NOTE]
> The **Tracking control center** should be accessed from the **Legs** page to configure lead times. Set the **Create type** to *Lead time* and then select **New** to create a new record in the tracking control center.<!-- KFM: I don't understand this note. If this is required, it should be part of the procedure, but it still needs to be clearer. -->

Lead times can be created between two different dates within the Landed cost module and the purchasing module. Matching fields can be used to further control this setting. If a date is altered for the source field, the target field and shipment status on the purchase line will be updated (depending on the matching fields selected). <!-- KFM: I don't understand any of this. -->

<!-- KFM: What does this procedure do? It doesn't really match the advice given so far (eg, to start from a leg). -->

1. On the list pane, set **Create type** to **Lead time**
1. Select **New** on the Action Pane.
1. Several fields are automatically populated as follows:
    - **Source table** - *Container activities*
    - **Source field** - *Start date*
    - **Target table** - *Container activities*
    - **Target field** - *Estimated end date*
1. Select the **Activity**.
1. Enter the **Lead time** in days.

### Status update types

Records with a **Create type** of *Status update* will update the status of a purchase order lines or the status at the voyage/shipping-container/folio level, and they can be independently set. Use this to inform the user or department teh stage of a particular voyage (such as documents received or goods in transit).

> [!NOTE]
> The **Tracking control center** should be accessed from the **Legs** page to configure status updates. Set the **Create type** to *Status update* and then select **New** to create a new record in the tracking control center.<!-- KFM: I don't understand this note. If this is required, it should be part of the procedure, but it still needs to be clearer. -->

When the **Create type** is set to *Status update*, the **Tracking control center** provides a **Lines** section where you can define a cost area and the updated status of the voyage. For example, if the **Cost area** is set to *Container* and the **Voyage status** is set to *Goods in transit*, then when an order completes the specified step, the voyage status of the shipping container will update to *Goods in Transit*.

Status updates provide the status of the voyage throughout the voyage lines and purchase order lines associated to the voyage. As a voyage moves through its journey from the port, sailing, customs, and to the destination warehouse, the **Voyage status** field provides a quick reference into what stage the items are at. <!-- KFM: Where is the **Status update** field? -->

1. On the list pane, set **Create type** to **Lead time**
1. Select **New** on the Action Pane.
1. Several fields are automatically populated as follows:
    - **Source table** - *Container activities*
    - **Source field** - *Actual end date*
    - **Target table** - (blank)
    - **Target field** - (blank)
1. Select the **Activity**.
1. In the **Lines** fast tab, enter the status updates for each cost area.

### Blank types

Use records with a **Create type** of *Blank* to override or input a field value based on the data of another field. A field from the Landed cost module will overwrite data in other areas of Supply Chain Management based on rules set up within the **Tracking control center**.

> [!NOTE]
> The tracking control center should be accessed from the tracking control center form to configure override scenarios. Set the **Create type** to *Blank* to create a new record in the tracking control center. <!-- KFM: I don't understand this note. Replace with a procedure, maybe? -->

### Required tracking control setup

There are two records that must be set up in the tracking control center for all journey templates. These two records both have a **Create type** of *Blank* and are used in all Landed cost implementations. These help ensure that the purchase confirmed date and goods in transit expected dates are updated on voyages and related purchase order lines as expected.

The first record is required for updating the purchase line, and must have the following settings:

- **Source table** - *Container activities*
- **Source field** - *Estimated end date*
- **Target table** - *Purchase lines*
- **Target field** - *Confirmed or delivery date*

The second record is required for updating the goods in transit transaction, and must have the following settings:

- **Source table** - *Container activities*
- **Source field** - *Estimated end date*
- **Target table** - *Goods in transit order*
- **Target field** - *Expected date*
