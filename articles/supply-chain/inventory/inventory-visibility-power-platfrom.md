---
title: Configure Inventory Visibility on Power Platforms
description: This topic describes how to set up Inventory Visibility on Power Platforms
author: yufeihuang
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Configure Inventory Visibility on Power Platforms

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

Inventory Visibility add-in provides the model-driven power app *Inventory Visibility Configuration* used to set up the on-hand configuration and soft reservation configuration. The default configuration setting includes the value from Dynamics 365 Supply Chain Management (data source "FnO") once the Inventory Visibility add-in has been installed. You can review the default setting and modify the configuration based on your business requirements and external system inventory posting requirements in [Microsoft Dataverse](/powerapps/maker/common-data-service/data-platform-intro) to standardize how inventory changes can be posted, organized, and queried across the multiple systems.

## Prerequisites

Before you begin the steps provided in this topic, first install and setup the add-in as described in [Inventory Visibility Add-in](inventory-visibility.md).

## Step 1: Define data sources

In this step, you define each *data source* that you want to integrate with Inventory Visibility. Inventory Visibility supports the integration with various data sources, such as your point of sale (POS) system, Dynamics 365 Supply Chain Management and other external systems. By default, Dynamics 365 Supply Chain Management is set up as a default data source ("FnO") in the Inventory Visibility.

To add a data source: <!-- KFM: Where are we adding this data source? CRM or IV? -->

1. Open the the **On-hand configuration** page. <!-- KFM: How do I get to this page. Is this in SCM? -->
1. Open the **Data Source** tab.
1. Select **New Data Source** to add a new data source.

## Step 2: Set up dimension mappings

Inventory Visibility provides a list of base dimensions that can be mapped from the dimensions of your data source. There are 33 dimensions available for mapping.

- If you are using Dynamics 365 Supply Chain Management as one of your data sources, then by default, 13 dimensions are mapped to Dynamics 365 Supply Chain Management standard dimensions. The other 12 (inventDimension1 - inventDimension12) are mapped to custom dimensions within Supply Chain Management. There are 8 extended dimensions left, which you can map to external data sources.

- If you do not use Dynamics 365 Supply Chain Management as any of your data sources, you can freely map the dimensions. Refer to the following table for the full list of available dimensions.

If your dimension is not on the default dimensions list, and if you are using an external data source, we recommend that you use ExtendedDimension1 – ExtendedDimension8 to do the mapping.

| Dimension Type | Dimension Name |
|---|---|
| Product | ColorId |
| Product | SizeId |
| Product | StyleId |
| Product | ConfigId |
| Tracking | BatchId |
| Tracking | SerialId |
| Location | LocationId |
| Location | SiteId |
| Inventory Status | StatusId |
| Warehouse Specific | WMSLocationId |
| Warehouse Specific | WMSPalletId |
| Warehouse Specific | LicensePlateId |
| <!-- KFM: Value needed --> | VersionId |
| Inventory (Custom) | InventDimension1 – InventDimension12 |
| <!-- KFM: Value needed --> | ExtendedDimension1 - ExtendedDimension8 |

To add dimension mappings:

1. Go to the **Dimension Mappings** area. <!-- KFM: How do I get to this page. Is this in SCM? -->
1. Select **Add** to add new dimension mappings.
1. In the **Dimension Name** field, specify the source dimension.
1. From **To Base Dimension** drop down list, select the dimension within Inventory Visibility that you want to map.
1. Select **Save** when you finish.

For example, if your data source includes a product color dimension, you can map it to base dimension "ColorID" to add a customer dimension "ProductColor" in the data source "exterchannel". It is mapped to the "ColorId" base dimension. <!-- KFM: This example isn't clear. Please revise. -->

## Step 3: Create a physical measure

When a data source posts an inventory change to Inventory Visibility, it posts with *physical measures*, which are modifiers that reflect the summarized inventory transaction statuses. Queries can be based on the physical measure.

Inventory Visibility has a list of default physical measures taken from the inventory transaction statuses on the **On-hand list** page in Supply Chain Management (**Inventory Management \> Inquiries and Report \> On-hand list**). <!-- KFM: How does the following table relate to this page? I don't see those anywhere here. -->

| Modifier | Name |
|---|---|
| PhysicalInvent | Physical Inventory |
| ReservPhysical | Physical Reserved |
| AvailPhysical | Available Physical |
| ReservOrdered | Ordered Reserved |
| PostedQty | Posted Quantity |
| Deducted | Deducted |
| Picked | Picked |
| Received | Received |
| Registered | Registered |
| Arrived | Arrived |
| Ordered | Ordered |
| OnOrder | On Order |
| QuotationReceipt | Quotation Receipt |
| QuotationIssue | Quotation Issue |

You don't need to recreate the default physical measures if the data source is Dynamics 365 Supply Chain Management. But for an external system data source, you can create new physical measures in the **Physical Measures** section. To do this, select **Add**, specify your source measure name, and save your change. <!-- KFM: Where is the **Physical Measures** section? -->

## Step 4: Define Product Hierarchy Index

By setting up aggregated dimension groups, you will be able to use Inventory Visibility to query inventory on-hand status. In Inventory Visibility, each dimension group is called **Index**. Each index corresponds to a set number. Based on how you will query on Inventory Visibility, you can decide which dimensions will be used to set up the indexing.

For more information, refer to the *Indexing* section of the [Install and configure the Inventory Visibility Add-in](inventory-visibility.md) topic.

On the **On-hand configuration** page, open the **Product Hierarchy Index** tab to set up the indexes. A list of indexes is provided by default. To modify the existing indexes, select **Edit** or **Add** on the existing index section. To create new index set, select **New index set**. Refer to the following table for the settings. <!-- KFM: How do I get to the **On-hand configuration** page? -->

| Field | Value | Details |
|---|---|---|
| Set number | This number is automatically generated. | Dimensions belonging to the same group (index) will be grouped together and allocated with the same set number. |
| Dimension | Select the specific dimension | Select from the list of base dimensions in the lookup field. |
| Hierarchy | This number is automatically generated. | Hierarchy is used to define the supported dimension combinations that can be queried within a dimension group (index). For example, if you set up a dimension group with a hierarchy sequency of *Style*, *Color*, and *Size*, the system supports the result of three query groups. The first group is style only. The second group is combination of style and color. And the third group is the combination of style, color, and size. The other combinations are not supported. Please refer the following example for details. |

Here is an example of how the hierarchy setting works. Below is a list of available inventories.

| **Item** | **Style** | **Color** | **Size** | **Quantity** |
|---|---|---|---|---|
| I0001 | Wide | Black | Small | 1 |
| I0001 | Wide | Black | Large | 2 |
| I0001 | Wide | Red | Small | 3 |
| I0001 | Regular | Black | Small | 4 |
| I0001 | Regular | Black | Large | 5 |
| I0001 | Regular | Red | Small | 6 |
| I0001 | Regular | Red | Large | 7 |

The index hierarchy is set as follows:

| Key | Set Number | Hierarchy |
|---|---|---|
| StyleId | 1 | 1 |
| ColorId | 1 | 2 |
| SizeId | 1 | 3 |

As per the above settings, the *Style*, *Color* and *Size* would be the dimension combination for using the Inventory Visibility query. The hierarchy setup enables external systems to query the inventory on-hand in the following ways:

1. () – Grouped by all, with the following output:
    - I0001, 28

1. (StyleId) – Group by style, the output as:
    - I0001, Wide, 6
    - I0001, Regular, 22

1. (StyleId, ColorId) – Grouped by the combination of style and color value, with the following output:
    - I0001, Wide, Black,3
    - I0001, Wide, Red, 3
    - I0001, Regular, Black, 9
    - I0001, Regular, Red, 13

1. (StyleId, ColorId, SizeId) – Grouped by the combination of style, color and size, with the following output:
    - I0001, Wide, Black, Small,1
    - I0001, Wide, Black, Large, 2
    - I0001, Wide, Red, Small, 3
    - I0001, Regular, Black, Small, 4
    - I0001, Regular, Black, Large, 5
    - I0001, Regular, Red, Small, 6
    - I0001, Regular, Red, Large, 7

## Step 5: Set up a custom calculated measure

You can use Inventory Visibility to query both on inventory physical measures and on *custom calculated measures*.

The configuration lets you define a set of modifiers to addition or subtraction group and get the aggregated output quantity. <!-- KFM: What do you mean by "addition or subtraction group"? Are those two groups, one named "addition" and one named "subtraction"? -->

On the **On-hand Configuration page**, open the **Calculated Measure** tab. Then select **New Calculate Measure** to add the new customer calculated measure.

| Field | Value |
|---|---|
| New calculated measure name | Enter the calculated measure name. |
| Data source | The querying system is a data source to query on the custom calculated measure. <!-- KFM: This isn't clear. Please revise. --> |
| Modifier data source | Enter the data source of the modifier. |
| Modifier | Enter the modifier name. |
| Modifier type | Select the modifier type (*Addition* or *Subtraction*). |

Below is an example of the `MyCustomAvailableforReservation` custom calculated measurement. For more information on this example, please refer to the *Custom measurement* section of the [Install and configure the Inventory Visibility Add-in](inventory-visibility.md) topic.

| Calculated measure data source | Calculated measurers | Modifier data source | Modifier | Modifier type |
|---|---|---|---|---|
| CustomChannel | MyCustomAvailableforReservation | FnO | availphysical | Addition |
| CustomChannel | MyCustomAvailableforReservation | FnO | orderedintotal | Addition |
| CustomChannel | MyCustomAvailableforReservation | FnO | orderedreserved | Subtraction |
| CustomChannel | MyCustomAvailableforReservation | mypos | Inbound | Addition |
| CustomChannel | MyCustomAvailableforReservation | mypos | Outbound | Subtraction |
| CustomChannel | MyCustomAvailableforReservation | exterchannel | received | Addition |
| CustomChannel | MyCustomAvailableforReservation | exterchannel | issued | Subtraction |
| CustomChannel | MyCustomAvailableforReservation | Exterchannel | reserved | Subtraction |

## Step 6: Reservation configuration

### Step 6.1: Define the soft reservation mapping

Before setting up this mapping, the physical measures, calculated measures, and their data sources must be defined on the **Data Source** tab and **Calculated Measure** tab. <!-- KFM: Where are these tabs? -->

1. Go to **Configuration \> Soft reservation mappings**. <!-- KFM: Where are we here? -->
1. Define the physical measure that serves as the soft reservation measure, for example *softreservordered*.
1. Define the available for reservation (AFR)) calculated measure, which contains the AFR computation formula that you want to map to the physical measure. For example, *availforreserv* (available for reservation) to map to the previously defined physical measure *softreservordered* <!-- KFM: Incomplete sentence. Please revise. --> . Indicating whatever quantities with *softreservordered* inventory status will be available for reservation <!-- KFM: Incomplete sentence. Please revise. --> . The AFR computation formula is shown in the following table:

    | Modifier | Data Source | Measure |
    |---|---|---|
    | Addition | fno | availphysical |
    | Addition | pos | inbound |
    | Subtraction | pos | outbound |
    | Subtraction | iv | softreservordered |

By setting up the mapping from the physical measure to the calculated measure, the Inventory Visibility service will automatically validate the reservation availability based on the physical measure. Refer to the following table for example mappings.

| Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
|---|---|---|---|
| iv | softreservordered | iv | availforreserv |

### Step 6.2: Define the soft reservation hierarchy

The reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as product index hierarchy works for on-hand queries.  

The reservation hierarchy is allowed to be different from the on-hand index hierarchy. This allows category management where users break down the dimensions into details to specify the needs for making more precise reservations.

#### Example

Your system is set up with teh following reservation hierarchy.

| Dimension  | Hierarchy  |
|---|---|
| ColorId  | 1  |
| SizeId  | 2  |
| StyleId | 3  |

Given the reservation hierarchy example, you can do reservation in the following 4 dimension orders:

1. () – no dimension given
2. (ColorId)
3. (ColorId, SizeId)
4. (ColorId, SizeId, StyleId)

The dimension order should strictly follow the reservation hierarchy sequence one by one. However, reservations with, for example, (ColorId, StyleId) would not be allowed because this sequence is not defined in the reservation hierarchy example.

## Step 7: Complete and update the configuration

Once you have completed configuration, you must commit all these changes to Inventory Visibility. To do this, select **Update Configuration** at top right corner. <!-- KFM: Which page are we on here? -->
