---
title: The Inventory Visibility Power App
description: This topic describes how to use the Inventory Visibility Power App.
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

# The Inventory Visibility Power App

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to use the Inventory Visibility Power App.

Inventory Visibility provides a model-driven Power App for visualization. The app contains 3 pages: **Configurations**, **APIs**, and **On-hand list**. It has following features:

- Provides UI for on-hand configuration and soft reservation configuration
- Supports real-time Inventory on-hand query on various dimension combinations
- Provides UI for posting reservation request
- Provides a customized view of on-hand list for products with all dimensions

## Prerequisites

Before you begin the steps provided in this topic, first install and setup the add-in as described in [Inventory Visibility Add-in](inventory-visibility-setup.md).

## <a name="configuration"></a>Configurations

The **Configurations** page helps you set up the on-hand configuration and soft reservation configuration. The default configuration includes the value from Dynamics 365 Supply Chain Management (data source `fno`) once the Inventory Visibility add-in has been installed. You can review the default setting and modify the configuration based on your business requirements and your external system inventory posting requirements in [Microsoft Dataverse](/powerapps/maker/common-data-service/data-platform-intro) to standardize how inventory changes can be posted, organized, and queried across the multiple systems.

### Define data sources

You define each *data source* that you want to integrate with Inventory Visibility. Inventory Visibility supports the integration with various data sources, such as your point of sale (POS) system, Dynamics 365 Supply Chain Management and other external systems. By default, Dynamics 365 Supply Chain Management is set up as a default data source (`fno`) in the Inventory Visibility.

To add a data source:

1. Sign in to your Power Apps environment and open **Inventory Visibility**.
1. Go to the **Configurations** page and open the **Data Source** tab.
1. Select **New Data Source** to add a new data source.

### Set up dimension mappings

Inventory Visibility provides a list of base dimensions that can be mapped from the dimensions of your data source. There are 33 dimensions available for mapping.

- If you are using Dynamics 365 Supply Chain Management as one of your data sources, then by default, 13 dimensions are mapped to the Supply Chain Management standard dimensions. The other 12 (`inventDimension1` - `inventDimension12`) are mapped to custom dimensions within Supply Chain Management. There are 8 extended dimensions left, which you can map to external data sources.

- If you do not use Dynamics 365 Supply Chain Management as any of your data sources, you can freely map the dimensions. Refer to the following table for the full list of available dimensions.

If your dimension is not on the default dimensions list, and if you are using an external data source, we recommend that you use `ExtendedDimension1` – `ExtendedDimension8` to do the mapping.

| Dimension Type | Dimension Name |
|---|---|
| Product | `ColorId` |
| Product | `SizeId` |
| Product | `StyleId` |
| Product | `ConfigId` |
| Tracking | `BatchId` |
| Tracking | `SerialId` |
| Location | `LocationId` |
| Location | `SiteId` |
| Inventory Status | `StatusId` |
| Warehouse Specific | `WMSLocationId` |
| Warehouse Specific | `WMSPalletId` |
| Warehouse Specific | `LicensePlateId` |
| Other | `VersionId` |
| Inventory (Custom) | `InventDimension1` – `InventDimension12` |
| Other | `ExtendedDimension1` - `ExtendedDimension8` |

To add dimension mappings:

1. Sign in to your Power Apps environment and open **Inventory Visibility**.
1. Go to the **Configuration** page and open the **Data Source** tab.
1. In the **Dimension Mappings** section, select **Add** to add new dimension mappings.
1. In the **Dimension Name** field, specify the source dimension.
1. From the **To Base Dimension** drop down list, select the dimension within Inventory Visibility that you want to map.
1. Select **Save**.

![Set up dimension mappings](media/inventory-visibility-dimension-mapping.png "Set up dimension mappings")

For example, if your data source includes a product color dimension, you can map it to base dimension `ColorId` to add a customer dimension `ProductColor` in the data source `exterchannel`. It is mapped to the `ColorId` base dimension.

## Create a physical measure

When a data source posts an inventory change to Inventory Visibility, it posts with *physical measures*, which are modifiers that reflect the summarized inventory transaction statuses. Queries can be based on the physical measure.

Inventory Visibility has a list of default physical measures taken from the inventory transaction statuses on the **On-hand list** page in Supply Chain Management (**Inventory Management \> Inquiries and Report \> On-hand list**).

| Modifier | Name |
|---|---|
| `PhysicalInvent` | Physical Inventory |
| `ReservPhysical` | Physical Reserved |
| `AvailPhysical` | Available Physical |
| `ReservOrdered` | Ordered Reserved |
| `PostedQty` | Posted Quantity |
| `Deducted` | Deducted |
| `Picked` | Picked |
| `Received` | Received |
| `Registered` | Registered |
| `Arrived` | Arrived |
| `Ordered` | Ordered |
| `OnOrder` | On Order |
| `QuotationReceipt` | Quotation Receipt |
| `QuotationIssue` | Quotation Issue |

You don't need to recreate the default physical measures if the data source is Dynamics 365 Supply Chain Management, but for external data sources, you can create new physical measures using the following steps:

1. Sign in to your Power Apps environment and open **Inventory Visibility**.
1. Go to the **Configuration** page and open the **Data Source** tab.
1. In the **Physical Measures** section, select **Add**, specify your source measure name, and save your changes.

## Define the product hierarchy index

By setting up aggregated dimension groups, you will be able to use Inventory Visibility to query inventory on-hand status. In Inventory Visibility, each dimension group is called **Index**. Each index corresponds to a set number. Based on how you will query on Inventory Visibility, you can decide which dimensions will be used to set up the indexing.

To set up your product hierarchy index:

1. Sign in to your Power Apps environment and open **Inventory Visibility**.
1. Go to the **Configuration** page and open the **Product Hierarchy Index** tab.
1. In the **Dimension Mappings** section, select **Add** to add new dimension mappings.
1. A list of indexes is provided by default. To modify an existing index, select **Edit** or **Add** on the relevant existing index section. To create new index set, select **New index set**. Refer to the following table for the settings. Make the following settings for each row in each index set:
    - **Set number** – This number is automatically generated. Dimensions belonging to the same group (index) will be grouped together and allocated with the same set number.
    - **Dimension** – Select from the list of base dimensions in the lookup field.
    - **Hierarchy** – This number is automatically generated. Hierarchy is used to define the supported dimension combinations that can be queried within a dimension group (index). For example, if you set up a dimension group with a hierarchy sequency of *Style*, *Color*, and *Size*, the system supports the result of three query groups. The first group is style only. The second group is combination of style and color. And the third group is the combination of style, color, and size. The other combinations are not supported.

For more information, refer to the *Product Index Hierarchy Configuration* section of the [Inventory Visibility Configurations](inventory-visibility-configuration.md#index-configuration) topic.

### Example

This section provides an example of how the hierarchy works. The following table provides a list of available inventory for this example.

| Item | Style | Color | Size | Quantity |
|---|---|---|---|---|
| I0001 | Wide | Black | Small | 1 |
| I0001 | Wide | Black | Large | 2 |
| I0001 | Wide | Red | Small | 3 |
| I0001 | Regular | Black | Small | 4 |
| I0001 | Regular | Black | Large | 5 |
| I0001 | Regular | Red | Small | 6 |
| I0001 | Regular | Red | Large | 7 |

The index hierarchy is set as follows:

| Key | Set number | Hierarchy |
|---|---|---|
| `StyleId` | 1 | 1 |
| `ColorId` | 1 | 2 |
| `SizeId` | 1 | 3 |

As per the above settings, the *Style*, *Color* and *Size* would be the dimension combination for using the Inventory Visibility query. The hierarchy setup enables external systems to query the inventory on-hand in the following ways:

1. `()` – Grouped by all, with the following output:
    - I0001, 28

1. `(StyleId)` – Group by style, the output as:
    - I0001, Wide, 6
    - I0001, Regular, 22

1. `(StyleId, ColorId)` – Grouped by the combination of style and color value, with the following output:
    - I0001, Wide, Black,3
    - I0001, Wide, Red, 3
    - I0001, Regular, Black, 9
    - I0001, Regular, Red, 13

1. `(StyleId, ColorId, SizeId)` – Grouped by the combination of style, color and size, with the following output:
    - I0001, Wide, Black, Small,1
    - I0001, Wide, Black, Large, 2
    - I0001, Wide, Red, Small, 3
    - I0001, Regular, Black, Small, 4
    - I0001, Regular, Black, Large, 5
    - I0001, Regular, Red, Small, 6
    - I0001, Regular, Red, Large, 7

## Set up a custom calculated measure

You can use Inventory Visibility to query both on inventory physical measures and on *custom calculated measures*.

The configuration lets you define a set of modifiers to add or subtract to get the total aggregated output quantity.

1. Sign in to your Power Apps environment and open **Inventory Visibility**.
1. Go to the **Configuration** page and open the **Calculated Measure** tab.

1. Select **New Calculate Measure** to add the new calculated measure. Make settings as described in the following table.

    | Field | Value |
    |---|---|
    | New calculated measure name | Enter the calculated measure name. |
    | Data source | The querying system is a data source. |
    | Modifier data source | Enter the data source of the modifier. |
    | Modifier | Enter the modifier name. |
    | Modifier type | Select the modifier type (*Addition* or *Subtraction*). |

Below is an example of the *MyCustomAvailableforReservation* custom calculated measurement. For more information on this example, see the *Data source configuration* section of the [Inventory Visibility Configurations](inventory-visibility-configuration.md#data-source-configuration) topic.
| Calculated measure data source | Calculated measure | Modifier data source | Modifier | Modifier type |
|---|---|---|---|---|
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `availphysical` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedintotal` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedreserved` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `mypos` | `Inbound` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `mypos` | `Outbound` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `exterchannel` | `received` | `Addition` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `exterchannel` | `issued` | `Subtraction` |
| `CustomChannel` | `MyCustomAvailableforReservation` | `Exteexterchannelrchannel` | `reserved` | `Subtraction` |

### <a name="setup-reservation-mapping"></a>Set up soft reservation mapping

To edit the **Soft Reserveration Mapping** Tab, you must enable the *OnHandReservation* feature. Go to **Feature Management** tab and turn on *OnHandReservation* feature.

By setting up the mapping from the physical measure to the calculated measure, the Inventory Visibility service will automatically validate  reservation availability based on the physical measure.

Before setting up this mapping, the physical measures, calculated measures, and their data sources must be defined on the **Data source** and **Calculated measure** tabs of the **Configurations** page in Power Apps (as described previously in this topic).

To define the soft reservation mapping:

1. Define the physical measure that serves as the soft reservation measure (for example `softreservordered`).
1. On the **Calculated measure** tab of the **Configurations** page, define the *available for reservation* (AFR) calculated measure, which contains the AFR computation formula that you want to map to the physical measure. For example, you might set up `availforreserv` (available for reservation) to map to the previously defined physical measure `softreservordered`, thereby enabling you to find which quantities with `softreservordered` inventory status will be available for reservation. The AFR computation formula is shown in the following table:

    | Modifier | Data Source | Measure |
    |---|---|---|
    | `Addition` | `fno` | `availphysical` |
    | `Addition` | `pos` | `inbound` |
    | `Subtraction` | `pos` | `outbound` |
    | `Subtraction` | `iv` | `softreservordered` |

1. Go to the **Configuration** page and open the **Soft Reservation Mapping** tab.
1. Set up the mapping from the physical measure to the calculated measure. Following the previous example, you could use the following settings to map `availforreserv` (available for reservation) to the previously defined physical measure `softreservordered`.

    | Physical measure data source | Physical measure | Available for reservation data source | Available for reservation calculated measure |
    |---|---|---|---|
    | `iv` | `softreservordered` | `iv` | `availforreserv` |

### <a name="setup-reservation-hierarchy"></a>Set up soft reservation hierarchy

To edit the **Soft Reservation Hierarchy** Tab, you must enable the *OnHandReservation* feature. Go to **Feature Management** Tab, turn on the *OnHandReservation* feature.

The reservation hierarchy describes the sequence of dimensions to specify when making reservations. It works the same way as the product index hierarchy works for on-hand queries.

The reservation hierarchy is allowed to be different from the on-hand index hierarchy. This allows category management where users break down the dimensions into details to specify the needs for making more precise reservations.

#### Example

Your system is set up with the following reservation hierarchy.

| Dimension | Hierarchy |
|---|---|
| `ColorId` | 1 |
| `SizeId ` | 2 |
| `StyleId` | 3 |

Given the reservation hierarchy example, you can do reservation in the following dimension orders:

- `()` – no dimension given
- `(ColorId)`
- `(ColorId, SizeId)`
- `(ColorId, SizeId, StyleId)`

The dimension order should strictly follow the reservation hierarchy sequence one by one. However, reservations with, for example, `(ColorId, StyleId)` would not be allowed because this sequence is not defined in the reservation hierarchy example.

### <a name="feature-switch"></a>Control feature management

The Inventory Visibility Add-in provides some features such as *OnHandReservation* and *OnHandMostSpecificBackgroundService*. These features are off by default. To use them, go to the **Configuration** page, open the **Feature Management** tab, and turn them on.

### Complete and update the configuration

Once you have completed the configuration, you must commit all the changes to Inventory Visibility. To do this, select **Update Configuration** at the top right corner of the **Configurations** page in Power Apps.

For the first time you select the **Update Configuration** button, the system will request your credentials.

- The **Client Id** is the Azure application ID you create for Invent Visibility.
- The **Tenant Id** is your Azure tenant ID.
- The **Client Secret** is the Azure application secret you create for Invent Visibility.

After you login, it will update the configuration in the Inventory Visibility Service.

### <a name="get-service-endpoint"></a>Find the service endpoint

If you don't know the correct Inventory Visibility service endpoint, go to the  **Configurations** page and select the **Show Service Endpoint** button at top right corner. The page will show you the correct service endpoint.

## Operational visibility

The **Operational Visibility** page provides real-time on-hand inventory query results based on various dimension combinations, and lets you post reservation request when the *OnHandReservation* feature is enabled.

### On-hand query

The **On-hand query tab** shows you the results of a real-time on-hand inventory query.

When you open this tab, the system will request your credentials in order to get the bearer token required to query the Inventory Visibility service. You can just paste the bearer token in the **BearerToken** field and close the dialog. Then you can post an on-hand query request.

If the bearer token is invalid or expired, you need to paste a new one in the **BearerToken** field. Enter the correct **Client ID**, **Tenant ID**, **Client Secret** values and then select the **refresh** button. The system will then get a new, valid bearer token automatically.

To post an on-hand query, enter the query using the pattern described in [Query with post method](inventory-visibility-api.md#query-with-post-method) in the request body.

![On-hand query settings](media/inventory-visibility-query-settings.png "On-hand query settings")

### Reservation posting

Use the **Reservation posting** tab to post a reservation request. Before you can post a reservation request, you must enable the *OnHandReservation* feature. To learn more about this feature, see [Inventory Visibility reservations](inventory-visibility-reservations.md).

To post a reservation request, you must enter a value using the pattern described in [Create one reservation event](inventory-visibility-api.md#create-one-reservation-event) in the request body. Then select the **Post** button. You can see the request response details by selecting **Show Details**. You can also get the **reservationId** from here.

## Inventory summary

**Inventory summary** is a customized view for the *Inventory OnHand Sum Entity*. It provides an on-hand list for products with all dimensions. You can use the **Advanced filter** provided by Dataverse to create a personal view to see the rows that are important to you. The advanced filter options let you create a wide range of views from simple to complex. They also let you add grouped and nested conditions to the filters.

To learn more about how to use the **Advanced filter**, see [Edit or create personal views using advanced grid filters](/powerapps/user/grid-filters-advanced)

The top of the customer view provides three drop-down lists (**Default Dimension**, **Custom Dimension**, and **Measure**) You can use these to control which columns are visible.

In the **Inventory Summary**, you can select the column header to filter the current result or sort it.

At the bottom of the customer view, you can see information such as **50 records (13 selected)** or **50 records**. These refer to the currently loaded records from the **Advanced Filter** result. The text **13 selected** refers to the number of records selected using the header column filter for the loaded records.

At the bottom, you can see a **Load more** button. Select this button to load more records from Dataverse. The default number of loaded records is 50. When you select **Load more**, it will load next available records into this view. The number in the **Load More** button tells you the current loaded records and the total records for the the **Advanced Filter** result.

![Inventory Summary](media/inventory-visibility-onhand-list.png "Inventory Summary")
