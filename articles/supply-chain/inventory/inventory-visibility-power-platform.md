---
title: Inventory Visibility Power Apps
description: This topic describes how to use Inventory Visibility Power Apps.
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

# Inventory Visibility Power Apps

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to use Inventory Visibility Power Apps.

The Inventory Visibility provides a model-driven Power Apps for visualization. The app contains 3 pages: Configurations, Apis, On-Hand List. It has following features:

- Provides UI for on-hand configuration and soft reservation configuration
- Supports real-time Inventory on-hand query on various dimension combinations
- Provides UI for posting reservation request
- Provides a customized view of on-hand list for products with all dimensions

## Prerequisites

Before you begin the steps provided in this topic, first install and setup the add-in as described in [Inventory Visibility Add-in](inventory-visibility-setup.md).

## <a id="configuration"></a>Configurations

Configurations page helps customer to set up on-hand configuration and soft reservation configuration. The default configuration setting includes the value from Dynamics 365 Supply Chain Management (data source "FnO") once the Inventory Visibility add-in has been installed. You can review the default setting and modify the configuration based on your business requirements and external system inventory posting requirements in [Microsoft Dataverse](/powerapps/maker/common-data-service/data-platform-intro) to standardize how inventory changes can be posted, organized, and queried across the multiple systems.

### Define Data Source

You define each *data source* that you want to integrate with Inventory Visibility. Inventory Visibility supports the integration with various data sources, such as your point of sale (POS) system, Dynamics 365 Supply Chain Management and other external systems. By default, Dynamics 365 Supply Chain Management is set up as a default data source ("FnO") in the Inventory Visibility.

To add a data source:

1. Sign in to your Power Apps environment and open **Inventory Visibility** powerApps. <!-- KFM: Is this the right way to say this? Any more detail needed? -->
1. Go to the **Configurations** page and open the **Data Source** tab.
1. Select **New Data Source** to add a new data source.

### Set up dimension mappings

Inventory Visibility provides a list of base dimensions that can be mapped from the dimensions of your data source. There are 33 dimensions available for mapping.

- If you are using Dynamics 365 Supply Chain Management as one of your data sources, then by default, 13 dimensions are mapped to Dynamics 365 Supply Chain Management standard dimensions. The other 12 (inventDimension1 - inventDimension12) are mapped to custom dimensions within Supply Chain Management. There are 8 extended dimensions left, which you can map to external data sources.

- If you do not use Dynamics 365 Supply Chain Management as any of your data sources, you can freely map the dimensions. Refer to the following table for the full list of available dimensions.

If your dimension is not on the default dimensions list, and if you are using an external data source, we recommend that you use *ExtendedDimension1* – *ExtendedDimension8* to do the mapping.

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
| Other | VersionId |
| Inventory (Custom) | InventDimension1 – InventDimension12 |
| Other | ExtendedDimension1 - ExtendedDimension8 |

To add dimension mappings:

1. Sign in to your Power Apps environment and open **Inventory Visibility** powerApps. <!-- KFM: Is this the right way to say this? Any more detail needed? -->
1. Go to the **Configuration** page and open the **Data Source** tab.
1. In the **Dimension Mappings** section, select **Add** to add new dimension mappings.
1. In the **Dimension Name** field, specify the source dimension.
1. From the **To Base Dimension** drop down list, select the dimension within Inventory Visibility that you want to map.
1. Select **Save**.

![Set up dimension mappings](media/inventory-visibility-dimension-mapping.png "Set up dimension mappings")

For example, if your data source includes a product color dimension, you can map it to base dimension "ColorID" to add a customer dimension "ProductColor" in the data source "exterchannel". It is mapped to the "ColorId" base dimension. <!-- KFM: This example isn't clear. Please revise. -->

## Create a physical measure

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

You don't need to recreate the default physical measures if the data source is Dynamics 365 Supply Chain Management, but for external data sources, you can create new physical measures using the following steps:

1. Sign in to your Power Apps environment and open **Inventory Visibility** powerApps.<!-- KFM: Is this the right way to say this? Any more detail needed? -->
1. Go to the **Configuration** page and open the **Data Source** tab.
1. In the **Physical Measures** section, select **Add**, specify your source measure name, and save your changes.

## Define product hierarchy index

By setting up aggregated dimension groups, you will be able to use Inventory Visibility to query inventory on-hand status. In Inventory Visibility, each dimension group is called **Index**. Each index corresponds to a set number. Based on how you will query on Inventory Visibility, you can decide which dimensions will be used to set up the indexing.

To set up your product hierarchy index:

1. Sign in to your Power Apps environment and open **Inventory Visibility** powerApps. <!-- KFM: Is this the right way to say this? Any more detail needed? -->
1. Go to the **Configuration** page and open the **Product Hierarchy Index** tab.
1. In the **Dimension Mappings** section, select **Add** to add new dimension mappings.
1. A list of indexes is provided by default. To modify an existing index, select **Edit** or **Add** on the relevant existing index section. To create new index set, select **New index set**. Refer to the following table for the settings. Make the following settings for each row in each index set:
    - **Set number** – This number is automatically generated. Dimensions belonging to the same group (index) will be grouped together and allocated with the same set number.
    - **Dimension** – Select from the list of base dimensions in the lookup field.
    - **Hierarchy** – This number is automatically generated. Hierarchy is used to define the supported dimension combinations that can be queried within a dimension group (index). For example, if you set up a dimension group with a hierarchy sequency of *Style*, *Color*, and *Size*, the system supports the result of three query groups. The first group is style only. The second group is combination of style and color. And the third group is the combination of style, color, and size. The other combinations are not supported.

For more information, refer to the *Product Index Hierarchy Configuration* section of the [Inventory Visibility Configurations](./inventory-visibility-configuration.md#index-configuration) topic.

### Example

This section provides an example of how the hierarchy works. The following table provides a list of available inventories for this example.

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

## Set up a custom calculated measure

You can use Inventory Visibility to query both on inventory physical measures and on *custom calculated measures*.

The configuration lets you define a set of modifiers to addition or subtraction group and get the aggregated output quantity. <!-- KFM: What do you mean by "addition or subtraction group"? Are those two groups, one named "addition" and one named "subtraction"? -->

1. Sign in to your Power Apps environment and open **Inventory Visibility** powerApps. <!-- KFM: Is this the right way to say this? Any more detail needed? -->
1. Go to the **Configuration** page and open the **Calculated Measure** tab.

1. Select **New Calculate Measure** to add the new calculated measure. Make settings as described in the following table. <!-- KFM: This table doesn't match the screen shot, nor does it match the following example -->

    | Field | Value |
    |---|---|
    | New calculated measure name | Enter the calculated measure name. |
    | Data source | The querying system is a data source to query on the custom calculated measure. <!-- KFM: This isn't clear. Please revise. --> |
    | Modifier data source | Enter the data source of the modifier. |
    | Modifier | Enter the modifier name. |
    | Modifier type | Select the modifier type (*Addition* or *Subtraction*). |

Below is an example of the *MyCustomAvailableforReservation* custom calculated measurement. For more information on this example, see the *Data source configuration* section of the [Inventory Visibility Configurations](./inventory-visibility-configuration.md#data-source-configuration) topic.
<!-- KFM: This table doesn't match the screen shot, nor does it match the settings described in the procedure -->
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

### <a id="setup-reservation-mapping"></a>Set up soft reservation mapping

In order to edit Soft Reserveration Mapping Tab, you need to enable `OnHandReservation` feature. Go to **Feature Management** Tab, turn on **OnHandReservation** feature.

By setting up the mapping from the physical measure to the calculated measure, the Inventory Visibility service will automatically validate the reservation availability based on the physical measure.

Before setting up this mapping, the physical measures, calculated measures, and their data sources must be defined on the **Data source** and **Calculated measure** tabs of the **Configurations** page in Power Apps (as described previously in this topic).

To define the soft reservation mapping:

1. Define the physical measure that serves as the soft reservation measure, for example *softreservordered*. <!-- KFM: How/where do I do that? -->
1. On the **Calculated measure** tab of the **Configurations** page, define the *available for reservation* (AFR) calculated measure, which contains the AFR computation formula that you want to map to the physical measure. For example, you might set up *availforreserv* (available for reservation) to map to the previously defined physical measure *softreservordered*, thereby enabling you to find which quantities with *softreservordered* inventory status will be available for reservation. The AFR computation formula is shown in the following table:

    | Modifier | Data Source | Measure |
    |---|---|---|
    | Addition | fno | availphysical |
    | Addition | pos | inbound |
    | Subtraction | pos | outbound |
    | Subtraction | iv | softreservordered |

1. Go to the **Configuration** page and open the **Soft Reservation Mapping** tab.
1. Set up the mapping from the physical measure to the calculated measure. <!-- KFM: How do I do that? --> Following the previous example, you could use the following settings to map *availforreserv* (available for reservation) to the previously defined physical measure *softreservordered*.

    | Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
    |---|---|---|---|
    | iv | softreservordered | iv | availforreserv |

### <a id="setup-reservation-hierarchy"></a>Set up soft reservation hierarchy

In order to edit Soft Reservation Hierarchy Tab, you need to enable `OnHandReservation` feature. Go to **Feature Management** Tab, turn on **OnHandReservation** feature.

The reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as product index hierarchy works for on-hand queries.

The reservation hierarchy is allowed to be different from the on-hand index hierarchy. This allows category management where users break down the dimensions into details to specify the needs for making more precise reservations.

#### Example

Your system is set up with teh following reservation hierarchy.

| Dimension | Hierarchy |
|---|---|
| ColorId | 1 |
| SizeId  | 2 |
| StyleId | 3 |

Given the reservation hierarchy example, you can do reservation in the following 4 dimension orders:

1. () – no dimension given
2. (ColorId)
3. (ColorId, SizeId)
4. (ColorId, SizeId, StyleId)

The dimension order should strictly follow the reservation hierarchy sequence one by one. However, reservations with, for example, (ColorId, StyleId) would not be allowed because this sequence is not defined in the reservation hierarchy example.

### <a id="feature-switch"></a>Control feature manangement

Inventory Visibility add-in provides some features such as OnHandReservation, OnHandMostSpecificBackgroundService. These features is off by default, to use it, you need to turn on the toggle.
  
1. Go to the **Configuration** page and open the **Feature Management** tab.
1. select the feature that you want to change, click **ToggleSwitch**.

### Complete and update the configuration

Once you have completed configuration, you must commit all these changes to Inventory Visibility. To do this, select **Update Configuration** at top right corner of the **Configurations** page in Power Apps.

For the first time you click **Update Configuration** button, it will pop up a login modal to ask you enter the credentials info.

- The **Client Id** is the Azure application ID you create for Invent Visibility.
- The **Tenant Id** is your Azure tenant ID.
- The **Client Secret** is the Azure application secret you create for Invent Visibility.

After you login, it will upadte the configuration changes to the Inventory Visibility Service to make it work.

### <a id="get-service-endpoint"></a>Get service endpoint

If you don't know the correct Inventory Visibility Service endpoint you can use, go to the  **Configurations** page, just click the **Show Service Endpoint** button on top right corner, it will show you the correct service endpoint.

## Operational Visibility

The Operational Visibility page helps customer to get real-time Inventory on-hand query result on various dimension combinations and post reservation request when you have already opened the **OnHandReservation** feature.

### Onhand Query

Onhand query tab is used to get real-time Inventory on-hand query result.

When you click this tab, it will pop up settings modal to ask you enter the credentials info in order to get bearerToken used to query Inventory Visibility Service. You can just paste the bearer token in the **BearerToken** field, and close this modal. Then you can post onhand query request.

If the BearToken is invalid or expired, you need to paste a new one in the **BearerToken** field. If you enter the correct Client Id, Tenant Id, Client Secret value, you jsut need to click **refresh** button, it will get a new valid bearer token automatically.
To post a on hand query,  you just need to enter the field following the pattern in the [Query with Post method](./inventory-visibility-api.md#query-with-post-method) the request body.
![On-hand query settings](media/inventory-visibility-query-settings.png "On-hand query settings")

### Reservation Posting

Reservation Posting tab is used to post a reservation request. In order to post a reservation request, you need to make sure you open the feature  **OnHandReservation**. To know more about this feature, go to [Inventory Visibility Reservations](./inventory-visibility-reservations.md).

To post a reservation request,  you just need to enter the field following the pattern in the [Create One Reservation Event](./inventory-visibility-api.md#create-one-reservation-event) the request body. And click **Post** button, you can see the request response details by click **Show Details**. You can get the **reservationId** from here.

## Inventory Summary

Inventory Summary is a customized view for Inventory OnHand Sum Entity, it provides an on-hand list for products with all dimensions. You can use the **Advanced Filter** default prodived by the Dataverse to create a personal view to see the rows that are important to you. The advanced filter options let you create a wide range of views from simple to complex. It also lets you add grouped and nested conditions to the filters.

To know more about how to use **Advanced Filter**, go to [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced)

At the top of the customer view has three drop down lists **Default Dimension**, **Custom Dimension**, **Measure**, you can use this to control which columns can be visible.
In the Inventory Summary, you can click the column header to filter the current result or sort it.

At the bottom of the customer view, you can see footer like `50 records (13 selected)`,`50 records` means the current loaded records from the **Advanced Filter** result. `13 selected` means the selected rocords using the header column filter for the loaded records.

At the bottom, you can see a load more button, click this button to load more records from the Dataverse, the default loaded records is 50 records. When you click it, it will load next 1000 records into this view. The number in the **Load More** button tells you the current loaded records and the total records for the the **Advanced Filter** result.

![Inventory Summary](media/inventory-visibility-onhand-list.png "Inventory Summary")
