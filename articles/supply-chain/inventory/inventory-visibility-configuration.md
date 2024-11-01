---
title: Configure Inventory Visibility data sources
description: Learn how to configure Inventory Visibility data sources with an outline on differences between Inventory Visibility UI version 1 and UI version 2.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 11/30/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Configure Inventory Visibility data sources

[!include [banner](../includes/banner.md)]

This article offers a comprehensive overview of data source configuration for Inventory Visibility. It covers the essential steps for setting up and optimizing data source configurations to enhance your inventory management processes.

Each data source configuration includes the following components:

- Data source name
- Dimensions (dimension mapping)
- Physical measures
- Calculated measures

> [!NOTE]
> If you recently transitioned from UI version 1 to UI version 2, see the [Differences between Inventory Visibility UI version 1 and UI version 2](#differences-between-v1-and-v2) section of this article to learn what has changed.
>
> For new installations, we recommend that you use UI version 2 from the start. If you're still using UI version 1, we recommend that you test the new version and then [upgrade to UI version 2](inventory-visibility-ui-version-2.md) as soon as possible.

## Prerequisites

Before you begin, install and set up the Inventory Visibility Add-in as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).

## <a name="differences-between-v1-and-v2"></a>Differences between Inventory Visibility UI version 1 and UI version 2

The Inventory Visibility app in Microsoft Power Apps supports [two versions of the user interface](inventory-visibility-ui-version-2.md): UI version 1 and UI version 2. Each version uses a different and independent collection of configuration settings. Therefore, you must choose which version you prefer to use.

When you're setting up data sources, UI version 2 differs from UI version 1 in the following ways:

- **Physical measures** – In UI version 2, you no longer have to specify the data source for a physical measure. By default, UI version 2 uses the current data source.
- **Calculated measures** – In UI version 2, you specify calculated measures in two steps:

    1. Set up calculated measure metadata to specify the name and data source for a calculated measure.
    1. Add calculated measure lines. Each line consists of a physical measure name and an operator (addition or subtraction) that's used to combine the line with the other lines during the calculation.

## <a name="data-source-configuration"></a>Add data sources (data source names)

Each data source represents a system that your data comes from. Example data source names include *fno* (which corresponds to Dynamics 365 Supply Chain Management) and *pos* (which stands for "point of sale"). By default, Supply Chain Management is set up as a default data source (*fno*) in Inventory Visibility.

> [!NOTE]
> The *fno* data source is reserved for Supply Chain Management. If your Inventory Visibility Add-in is integrated with a Supply Chain Management environment, we recommend that you don't delete configurations that are related to *fno* in the data source.

> [!IMPORTANT]
> When you add a data source, be sure to validate the data source name, physical measures, and dimension mappings before you update the configuration for the Inventory Visibility service. You won't be able to modify these settings after you select **Update Configuration**.

### Add a data source in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To add a data source in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Data source settings** tile, select **Manage**.
1. On the **Data source settings** page, select **New** on the toolbar to add a data source. Enter a name for the new data source (for example, *ecommerce* or another meaningful data source ID).
1. Select **Save**.

### Add a data source in UI version 1

This section applies when you're using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

To add a data source in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Data Source** tab, select **New data source** to add a data source. Enter a name for the new data source (for example, *ecommerce* or another meaningful data source ID).

> [!NOTE]
> When you add a data source, be sure to validate the data source name, physical measures, and dimension mappings before you update the configuration for the Inventory Visibility service. You won't be able to modify these settings after you select **Update Configuration**.

## <a name="data-source-configuration-dimension"></a>Dimensions (dimension mapping)

The purpose of the dimension configuration is to standardize the multi-system integration for posting events and queries, based on dimension combinations. Inventory Visibility provides a list of base dimensions that can be mapped from the dimensions of your data source. Thirty-three dimensions are available for mapping.

- If you're using Supply Chain Management as one of your data sources, 13 dimensions are already mapped to the Supply Chain Management standard dimensions by default. The other 12 dimensions (*inventDimension1* through *inventDimension12*) are also mapped to custom dimensions in Supply Chain Management. The remaining eight dimensions (*ExtendedDimension1* through *ExtendedDimension8*) are extended dimensions that you can map to external data sources.
- If you don't use Supply Chain Management as one of your data sources, you can freely map the dimensions. The following table shows the full list of available dimensions.

> [!NOTE]
> If you use Supply Chain Management, and you change the default dimension mappings between Supply Chain Management and Inventory Visibility, the changed dimension won't sync data. Therefore, if your dimension isn't on the default dimension list, and you're using an external data source, we recommend that you use *ExtendedDimension1* through *ExtendedDimension8* to do the mapping.

| Dimension type | Base dimension |
|---|---|
| Product | *ColorId* |
| Product | *SizeId* |
| Product | *StyleId* |
| Product | *ConfigId* |
| Tracking | *BatchId* |
| Tracking | *SerialId* |
| Location | *LocationId* |
| Location | *SiteId* |
| Inventory status | *StatusId* |
| Warehouse specific | *WMSLocationId* |
| Warehouse specific | *WMSPalletId* |
| Warehouse specific | *LicensePlateId* |
| Others | *VersionId* |
| Inventory (custom) | *InventDimension1* through *InventDimension12* |
| Extension | *ExtendedDimension1* through *ExtendedDimension8* |
| System | *Empty* |

> [!NOTE]
> The dimension types that are listed in the preceding table are for your reference only. You don't have to define them in Inventory Visibility.
>
> The inventory (custom) dimensions might be reserved for Supply Chain Management. In that case, use the extended dimensions instead.

External systems can access Inventory Visibility through its RESTful APIs. For the integration, Inventory Visibility lets you configure the *external data source* and the mapping from the *external dimensions* to the *base dimensions*. Here's an example of a dimension mapping table.

| External dimension | Base dimension |
|---|---|
| *MyColorId* | *ColorId* |
| *MySizeId* | *SizeId* |
| *MyStyleId* | *StyleId* |
| *MyDimension1* | *ExtendedDimension1* |
| *MyDimension2* | *ExtendedDimension2* |

By configuring a dimension mapping, you can send the external dimensions directly to Inventory Visibility. Inventory Visibility will then automatically convert external dimensions to base dimensions.

### Add dimension mappings in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To add a dimension mapping in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Data source settings** tile, select **Manage**.
1. On the **Data source settings** page, select the data source where you want to set up a dimension mapping.
1. In the **Dimension mappings** section, select **New Dimension Mapping** on the toolbar.
1. On the **New Dimension Mapping** page, set the following fields:

    - **Customer dimension** – Enter the name of the source dimension.
    - **Base Dimension** – Select the dimension in Inventory Visibility that you want to map to.

    For example, you've already created a data source that's named *ecommerce*, and it includes a product color dimension. In this case, to do the mapping, first add *ProductColor* to the **Dimension Name** field for the *ecommerce* data source. Then select *ColorId* in the **To Base Dimension** field.

1. On the toolbar, select **Save**.

### Add dimension mappings in UI version 1

To add a dimension mapping in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Data source** tab, expand the data source where you want to set up a dimension mapping.
1. In the **Dimension Mappings** section, select **Add** to add a dimension mapping row. Then set the following fields for the new row:

    - **Dimension Name** – Enter the name of the source dimension.
    - **To Base Dimension** – Select the dimension in Inventory Visibility that you want to map to.

1. Select the **Save** link for the new row.

## <a name="data-source-configuration-physical-measures"></a>Physical measures

When a data source posts an inventory change to Inventory Visibility, it posts that change by using *physical measures*. Physical measures modify the quantity and reflect the inventory status. You can define your own physical measures based on your requirements. Queries can be based on the physical measures.

Inventory Visibility provides a list of default physical measures that are mapped to Supply Chain Management (the *fno* data source). These default physical measures are taken from the inventory transaction statuses on the **On-hand list** page in Supply Chain Management (**Inventory Management** \> **Inquiries and Report** \> **On-hand list**). The following table provides an example of physical measures.

| Physical measure name | Description |
|---|---|
| *NotSpecified* | Not specified |
| *Arrived* | Arrived |
| *AvailOrdered* | Available ordered |
| *AvailPhysical* | Available physical |
| *Deducted* | Deducted |
| *OnOrder* | OnOrder |
| *Ordered* | Ordered |
| *PhysicalInvent* | Physical inventory |
| *Picked* | Picked |
| *PostedQty* | Posted quantity |
| *QuotationIssue* | Quotation issue |
| *QuotationReceipt* | Quotation receipt |
| *Received* | Received |
| *Registered* | Registered |
| *ReservOrdered* | Ordered reserved |
| *ReservPhysical* | Physical reserved |
| *OrderedSum* | Ordered in total |

If your data source is Supply Chain Management, you don't have to recreate the default physical measures. However, for external data sources, you can create new physical measures as you require.

### Add physical measures in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To add a physical measure in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Data source settings** tile, select **Manage**.
1. On the **Data source settings** page, select the data source where you want to do the dimension mapping. Then, in the **Physical Measure** section, select **New physical measure** on the toolbar. <!--KFM: Note that the current label is **New Dimension Mapping** -->
1. On the **New physical measure** page, set the following fields for the new physical measure:

    - **Display name** – Enter a name that's unique not only within the new measure's own data source but also across all data sources. The recommended format is \<*Data source*\>.\<*Physical measure name*\> (for example, *ecommerce.returned*). This format ensures that the display name is distinct and unique across all data sources. <!--KFM: Is it really the display name, not the measure name, that must be unique? -->
    - **Physical measure name** – Enter the name of the physical measure.

1. On the toolbar, select **Save**.

### Add physical measures in UI version 1

This section applies when you're using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

To add a physical measure in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Data source** tab, expand the data source where you want to set up a physical measure.
1. In the **Physical measure** section, select **Add** to add a physical measure row. Then, in the **Measure name** field for the new row, enter the name of the measure. For example, enter *Returned* if you want to record returned quantities in this data source for Inventory Visibility.
1. Select the **Save** link for the new row.

### Extended dimensions

If you're using external data sources, you can take advantage of the extensibility that the solution offers by creating [class extensions](../../fin-ops-core/dev-itpro/extensibility/class-extensions.md) for the `InventOnHandChangeEventDimensionSet` and `InventInventoryDataServiceBatchJobTask` classes.

Be sure to synchronize with the database after creating the extensions in order for the custom fields to be added in the `InventSum` table. You can then refer to the "Dimensions" section earlier in this article, to map your custom dimensions to any of the eight extended dimensions in `BaseDimensions` in Inventory.

> [!NOTE]
> For additional details about creating extensions, see [Extensibility home page](../../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md).

## Calculated measures

You can use Inventory Visibility to query on both inventory physical measures and *custom calculated measures*. Calculated measures provide a customized computation formula that consists of a combination of physical measures. This functionality lets you define a set of physical measures that will be added, and/or a set of physical measures that will be subtracted, to form the customized measurement.

> [!IMPORTANT]
> A calculated measure is a composition of physical measures. Its formula can include only physical measures without duplicates, not calculated measures.

The configuration lets you define a set of calculated measure formulas that includes modifiers of addition or subtraction to get the total aggregated output quantity.

### Add calculated measures in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To add a calculated measure in UI version 2, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Data source settings** tile, select **Manage**.
1. On the **Data source settings** page, select the data source where you want to do the dimension mapping. Then, in the **Calculated measures** section, select **New calculated measure** on the toolbar.
1. On the **New calculated measure** page, set the following fields for the new calculated measure:

    - **Calculated measure display name** – Enter a name that's unique not only within the new measure's own data source but also across all data sources. The recommended format is \<*Data source*\>.\<*Calculated measure name*\> (for example, *iv.TotalAvailable*). This format ensures that the display name is distinct and unique across all data sources. <!--KFM: Is it really the display name, not the measure name, that must be unique? -->
    - **Calculated measure name** – Enter the name of the calculated measure.

1. On the toolbar, select **Save & close**. The page is refreshed and now includes the **Calculated measure details** section.
1. In the **Calculated measure details** section, select **New calculated measure details V2** on the toolbar to add a modifier row for the calculated measure.
1. On the **New calculated measure detail** page, set the following fields for the new modifier:

    - **Calculated measure formula description** – Enter a detailed explanation of the significance and purpose of the formula in the calculated measure.
    - **+/- to result** – Select the modifier type (*Addition* or *Subtraction*).
    - **Physical measure name reference** – Select the name of the measure (from the selected data source) that provides the value for the modifier.

1. On the toolbar, select **Save & close**.
1. Repeat steps 7 through 9 until you've added all the modifiers that are required to complete the formula for your calculated measure.
1. On the toolbar, select **Save**.

### Add calculated measures in UI version 1

This section applies when you're using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

To add a calculated measure in UI version 1, follow these steps.

1. Sign in to your Power Apps environment, and open the **Inventory Visibility** app.
1. On the **Change area** menu at the bottom of the navigation pane, select **Legacy UI**.
1. On the navigation pane, select **Configuration**.
1. On the **Calculated measure** tab, select **New Calculate Measure** to add a calculated measure.
1. Set the following fields for the new calculated measure:

    - **New calculated measure name** – Enter the name of the calculated measure.
    - **Data source** – Select the data source to include the new calculated measure in. The querying system is a data source.

1. A new, blank modifier line is automatically included for the new calculated measure. Set the following fields for it:

    - **Modifier** – Select the modifier type (*Addition* or *Subtraction*).
    - **Data source** – Select the data source where the measure that provides the modifier value is found.
    - **Measure** – Select the name of the measure (from the selected data source) that provides the value for the modifier.

1. Select **Save measure** to save your settings so far.
1. If you must add another modifier line, select **Add** to add a row, and then set the fields as you did for the first row. When you've finished, select the **Save** link for the row.
1. Repeat the previous step until you've added all the required modifiers and completed the formula for your calculated measure.
1. Select **Save**.

### Work with calculated measures in Inventory Visibility

For example, a fashion company operates across three data sources:

- `pos` – Corresponds to the store channel.
- `fno` – Corresponds to Supply Chain Management.
- `ecommerce` – Corresponds to your web channel.

Without calculated measures, when you query for product D0002 (Cabinet) under site 1, warehouse 11, and a `ColorID` dimension value of `Red`, you might get the following query result, which shows inventory quantities under each preconfigured physical measure. However, you don't have visibility into the total available for reservation quantities across your data sources.

```json
[
    {
        "productId": "D0002",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red"
        },
        "quantities": {
            "pos": {
                "inbound": 80.0,
                "outbound": 20.0
            },
            "fno": {
                "availphysical": 100.0,
                "orderedintotal": 50.0,
                "orderedreserved": 10.0
            },
            "ecommerce": {
                "received": 90.0,
                "scheduled": 30.0,
                "issued": 60.0,
                "reserved": 40.0
            }
        }
    }
]
```

You then configure a calculated measure that's named `MyCustomAvailableforReservation`, as shown in the following table. This calculated measure will be consumed by the consumption system.

| Consumption system | Calculated measure | Data source | Physical measure | Calculation type |
|---|---|---|---|---|
| `CrossChannel` | `MyCustomAvailableforReservation` | `fno` | `availphysical` | `Addition` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedintotal` | `Addition` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `fno` | `orderedreserved` | `Subtraction` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `pos` | `inbound` | `Addition` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `pos` | `outbound` | `Subtraction` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `ecommerce` | `received` | `Addition` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `ecommerce` | `scheduled` | `Addition` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `ecommerce` | `issued` | `Subtraction` |
| `CrossChannel` | `MyCustomAvailableforReservation` | `ecommerce` | `reserved` | `Subtraction` |

When this computation formula is used, the new query result will include the customized measurement.

```json
[
    {
        "productId": "D0002",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red"
        },
        "quantities": {
            "pos": {
                "inbound": 80.0,
                "outbound": 20.0
            },
            "fno": {
                "availphysical": 100.0,
                "orderedintotal": 50.0,
                "orderedreserved": 10.0
            },
            "ecommerce": {
                "received": 90.0,
                "scheduled": 30.0,
                "issued": 60.0,
                "reserved": 40.0
            },
            "CrossChannel": {
                "MyCustomAvailableforReservation": 220.0
            }
        }
    }
]
```

The `MyCustomAvailableforReservation` output, based on the calculation setting in the custom measurements, is 100 + 50 – 10 + 80 – 20 + 90 + 30 – 60 – 40 = 220.

## <a name="default-configuration-sample"></a>The default data source configuration

This section provides details about the default data source configuration that's set up when you install Inventory Visibility. You can modify this configuration as you require.

> [!IMPORTANT]
> The default configuration has evolved through various version iterations. It's possible that your sandbox environment was initially set up with an outdated default configuration, while your production environment was initialized with the latest version of the default configuration. If you've customized your third-party system based on an outdated default configuration, it might encounter issues when your production environment goes live, especially if you haven't reviewed and adjusted the configuration. To prevent this scenario, we recommend thoroughly reviewing and updating your draft and runtime configurations before transitioning your production environment.

### Data source configuration

#### Configuration of the iv data source

This section describes how the *iv* data source is configured.

##### Physical measures configured for the "iv" data source

The following physical measures are configured for the *iv* data source:

- *Ordered*
- *Softreserved*

##### AvailableToReserve calculated measure

The *AvailableToReserve* calculated measure is configured for the *iv* data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | *fno* | *PhysicalInvent* |
| Addition | *fno* | *Ordered* |
| Addition | *fno* | *Arrived* |
| Addition | *pos* | *Inbound* |
| Addition | *iv* | *Ordered* |
| Subtraction | *fno* | *ReservPhysical* |
| Subtraction | *iv* | *Softreserved* |
| Subtraction | *pos* | *Outbound* |
| Subtraction | *fno* | *Softreserved* |

##### TotalAvailable calculated measure

The *TotalAvailable* calculated measure is configured for the *iv* data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | *fno* | *AvailOrdered* |
| Subtraction | *iv* | *Softreserved* |
| Subtraction | *@iv* | *@allocated* |

##### TotalOnHand calculated measure

The *TotalOnHand* calculated measure is configured for the *iv* data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | *fno* | *PhysicalInvent* |

#### Configuration of the "fno" data source

This section describes how the *fno* data source is configured.

##### Dimension mappings for the "fno" data source

The dimension mappings that are listed in the following table are configured for the *fno* data source.

| External dimension | Base dimension |
|---|---|
| *InventBatchId* | *BatchId* |
| *InventColorId* | *ColorId* |
| *InventLocationId* | *LocationId* |
| *InventSerialId* | *SerialId* |
| *InventSiteId* | *SiteId* |
| *InventSizeId* | *SizeId* |
| *InventStatusId* | *StatusId* |
| *InventStyleId* | *StyleId* |
| *LicensePlateId* | *LicensePlateId* |
| *WMSLocationId* | *WMSLocationId* |
| *WMSPalletId* | *WMSPalletId* |
| *ConfigId* | *ConfigId* |
| *InventVersionId* | *VersionId* |
| *InventDimension1* | *CustomDimension1* |
| *InventDimension2* | *CustomDimension2* |
| *InventDimension3* | *CustomDimension3* |
| *InventDimension4* | *CustomDimension4* |
| *InventDimension5* | *CustomDimension5* |
| *InventDimension6* | *CustomDimension6* |
| *InventDimension7* | *CustomDimension7* |
| *InventDimension8* | *CustomDimension8* |
| *InventDimension9* | *CustomDimension9* |
| *InventDimension10* | *CustomDimension10* |
| *InventDimension11* | *CustomDimension11* |
| *InventDimension12* | *CustomDimension12* |

##### Physical measures configured for the "fno" data source

The following physical measures are configured for the *fno* data source:

- *Arrived*
- *PhysicalInvent*
- *ReservPhysical*
- *onorder*
- *notspecified*
- *availordered*
- *availphysical*
- *picked*
- *postedqty*
- *quotationreceipt*
- *received*
- *ordered*
- *ReservOrdered*
- *OrderedSum*
- *SoftReserved*

#### Configuration of the "pos" data source

This section describes how the data source *pos* is configured.

##### Physical measures for the "pos" data source

The following physical measures are configured for the *pos* data source:

- *Inbound*
- *Outbound*

##### AvailQuantity calculated measure

The *AvailQuantity* calculated measure is configured for the *pos* data source as shown in the following table.

| Calculation type | Data source | Physical measure |
|---|---|---|
| Addition | *fno* | *AvailPhysical* |
| Addition | *pos* | *Inbound* |
| Subtraction | *pos* | *Outbound* |

#### Configuration of the "iom" data source

The following physical measures are configured for the *iom* (Intelligent Order Management) data source:

- *OnOrder*
- *OnHand*

#### Configuration of the "erp" data source

The following physical measures are configured for the *erp* (enterprise resource planning) data source:

- *Unrestricted*
- *QualityInspection*

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
