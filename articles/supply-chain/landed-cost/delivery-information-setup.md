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

To work with shipping ports, go to **Module Maple (preview) \> Delivery information setup \> Shipping ports**. Here, you can view, add, and remove records for each of your shipping ports. The following table describes the settings available for shipping port.

| **Setting** | **Description** |
| --- | --- |
| **Shipping port** | Enter a unique identification name/number for the shipping port. |
| **Description** | Enter a description of the shipping port |

## Tracking control center

Use the **Tracking control center** to set up the lead times, status updates, and flow of information associated with a voyage as the shipping containers move from one leg to the next. The **Tracking control center** configures the information by splitting up the details into three different areas. The page will change views as you select each type of action within the create function. When you create a tracking control record, the record is associated to a particular leg of a voyage journey. When a voyage updates the identified leg, the record will update and populate as defined. You can update tracking information for individual voyages from the **All voyages** page.

To open the tracking control center, go to **Module Maple (preview) \> Delivery information setup \> Tracking control center**.

The **Tracking control center** shows one of three different page views depending on the value selected for the **Create type** drop-down list on the list pane. Each of the different area types updates a different set of information associated with the progress of a voyage from the point of origin to the final destination.

Fields listed below are shown on the **Tracking control center** with all three areas available for update and configuration.

| **Setting** | **Description** |
| --- | --- |
| **Activity** | Applicable to the container activities form |
| **Matching criteria** | This determines how the system identifies a match with a rule. In each instance it will review the data in the source and destination tables to determine when and if a field is updated.<p>**Example**: The **Source table** is *voyages* and the **Destination table** is *Purchase header* or *Purchase lines*. The voyages table has a **From port** of *Hong Kong* and the purchase header has a **From port** of *Shanghai*. A rule is then created that has uses the from-port *Hong Kong*. The **Matching criteria** values in tht control center will then work as follows:</p><ul><li>**Both** – Nothing will update because the two ports do not match.</li><li>**Source** – This would update because the source table's from-port is *Hong Kong*.</li><li>**Target** – This would not update because the destination table's from-port is *Shanghai*. |
| **Lead time** | The lead time between the selected source and target fields will be specified here. The lead time field is only available for edit when the type is set to &#39;Lead time&#39;. |
| **Copy action** | The options are Copy and Default. The copy will copy the value in the source field to the destination field. Default will require a specified value for the destination field. |
| **Default** | If the copy action is set to Default, the Default field sets the value of the default in the destination field. For example, if the action is regarding the port updates and the copy action is set to default, the default field will be a port identified by the drop-down. |
| **Leg** | The identified leg of the journey that the specified action occurs, such as loading, or customs. |
| **Service provider** | If a specific service provider is used for this status update/leg of the journey, the service provider is listed. Service providers are defined in the vendor account. |
| **Lines** | In the lines section of the form, users can define the cost area and the update value of the shipment. If the cost area is set to Container and the voyage status is set to &quot;Goods in Transit&quot; , when an order completes the specified step, the voyage status of the shipping container will update to &quot;Goods in Transit&quot;. |

### Lead times

Lead times are the estimated time a voyage will require to complete the defined leg of a journey on a voyage. The lead time on each leg of a journey will be used to calculate the estimated delivery date of a voyage. This date is then populated on every purchase line within a voyage in the confirmed delivery date field on the purchase line.

Manage the updating of dates using **lead times**. Activities are automatically generated when a journey template is used on a voyage. Link activities to legs of a journey by creating the lead times/status rule via the leg.

> [!NOTE]
> The tracking control center should be accessed from the **Legs** page to configure lead times. Select **create type Status update and create a new record**.

Lead times can be created between two different dates within Module Maple (preview) and the purchasing module. Matching fields can be used to further control this setting. If a date is altered for the source field, the target field and shipment status on the purchase line will be updated (depending on the matching fields selected).

1. Select **Create type** to **Lead time \> New**.
1. The source/target table/field will be automatically populated as follows:
    - **Source table** - *Container activities*
    - **Source field** - *Start date*
    - **Target table** - *Container activities*
    - **Target field** - *Estimated end date*
1. Select the activity.
1. Enter the lead time.

### Status updates

The **Create type** of *Status* will update a status whether it is a status on the purchase order lines or a status at the Voyage/Shipping Container/Folio level, and they can be independently set. This would be used to inform the user or department where a particular &quot;Voyage&quot; is. I.e. documents received or goods in transit.

> [!NOTE]
> Tracking control center should be accessed from the legs form to configure status updates. Set the **Create type** to *Status update* and then select **New** to create a new record in the tracking control center.

Status updates provide the status of the voyage throughout the voyage lines and purchase order lines associated to the voyage. As a voyage moves through its journey from the port, sailing, customs, and to the destination warehouse, the status update field provides a quick reference into what stage the items are at.

1. Select Create type Status update \> The source/target table/field will be automatically populated as follows:

    - **Source table** - *Container activities*
    - **Source field** - *Actual end date*
    - **Target table** - (blank)
    - **Target field** - (blank)

1. Select the activity.
1. In the **Lines** fast tab, enter the status updates for each cost area.

### Blank types

With the **Create type** of *Blank* users can override/input a field based on the data of another field. A field from Module Maple (preview) will overwrite data in other areas of Supply Chain Management based on rules set up within the tracking control center. There are two options available for this:

- **Copy** the value.
- **Default** a value of the target field. A good example of the blank type tracking control records are the two required tracking control field setups for Module Maple configuration.

> [!NOTE]
> The tracking control center should be accessed from the tracking control center form to configure override scenarios. Set the **Create type** to *Blank* to create a new record in the tracking control center.

### Required tracking control setup

There are two records that must be set up in the tracking control center for all journey templates. These two records are both blank record types and are used in all Module Maple implementations This will ensure that the purchase confirmed date and goods in transit expected dates are updated on shipments and related purchase order lines as expected.

The first record is required for updating the purchase line, and will be the creation type of &#39;Blank&#39; It must have the following settings:

- **Source table** - *Container activities*
- **Source field** - *Estimated end date*
- **Target table** - *Purchase lines*
- **Target field** - *Confirmed or delivery date*

The second record is required for updating the goods in transit transaction and will be the creation type of &#39;Blank&#39;. It must have the following settings:

- **Source table** - *Container activities*
- **Source field** - *Estimated end date*
- **Target table** - *Goods in transit order*
- **Target field** - *Expected date*
