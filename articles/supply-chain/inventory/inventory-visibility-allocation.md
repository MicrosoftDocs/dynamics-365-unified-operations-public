---
title: Inventory Visibility inventory allocation
description: This article explains how to set up and use the inventory allocation feature, which lets you set aside dedicated inventory to ensure that you can fulfill your most profitable channels or customers.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 01/10/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility inventory allocation

[!include [banner](../includes/banner.md)]

## Business background and purpose

Organizations often have to preallocate their on-hand stock to their most important sales channels, customer groups, regions, and promotional events to ensure that the preallocated stock is protected against any other use and can be consumed only via sales transactions that are relevant to the allocation. Inventory allocation in Inventory Visibility is a component of the sales operational planning process, and is done before any actual sales activities occur or a sales order is created.

For example, a company that is named Contoso produces a popular bike. Unfortunately, because a recent supply chain disruption has affected all in-transit stock of that bike, Contoso has only limited on-hand stock and must make best use of it. Contoso operates both online and in-store sales. In each sales channel, the company has a few important corporate partners (marketplaces and large retailers) that demand that a specific portion of the bike's available inventory be saved for them. Therefore, the bicycle company must be able to balance stock distribution across channels and also manage the expectations of its VIP partners. The best way to achieve both goals is to use inventory allocation, so that each channel and retailer can receive specific allocated quantities that can be sold to consumers later.

Inventory allocation has two basic business purposes:

- **Inventory protection (ring fencing)** – Organizations want to preallocate restricted or limited stock to prioritized channels, regions, VIP customers, and subsidiary companies. The Inventory Visibility allocation feature aims to protect the allocated inventory, so that the other allocations, reservations, or other sales demands won't affect the previously allocated inventory.
- **Oversell control** – The Inventory Visibility allocation feature aims to put a restriction on the previously allocated quantities, so that the receiving party (for example, a channel or customer group) won't over-consume them when the actual sales transaction that is based on a soft reservation goes into effect.

## Allocation definition in Inventory Visibility Service

### Allocation Virtual Pool

Although the allocation feature in Inventory Visibility doesn't set aside physical inventory quantities, it does refer to the available physical inventory quantity to define its initial *available to allocate* virtual pool quantity. Inventory allocation in Inventory Visibility is a soft allocation. It's done before actual sales transactions occur and doesn't depend on sales orders. For example, you can allocate stock to your most important sales channels or large corporate retailers before any end customers visit the sales channel or retail store to purchase it.

### Difference between inventory allocation and soft reservation

[Soft reservations](inventory-visibility-reservations.md) are often linked to actual sales transactions (sales order lines). Both allocation and soft reservation can be used independently, but if you want to use them together, soft reservation should be done after allocation. We recommend that you do inventory allocation first and then soft reserve against the allocated quantities to achieve near-real-time consumption against allocation. For more information, see [Consume as a soft reservation](#consume-to-soft-reserved).

The inventory allocation feature lets sales planners or key account managers manage and preallocate important stock across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities, to ensure that replenishment or reallocation can be done on time. This ability to have real-time visibility into allocation, consumption, and allocation balance is especially important at fast-sale or promotion events.

## Terminology

The following terms and concepts are useful in discussions of inventory allocation:

- **Allocation group** – The group that owns the allocation, such as a sales channel, customer group, or order type.
- **Allocation group name** – The name of each allocation group. For example, *web* or *store* might be the name of the sales channel allocation group, whereas *VIP* or *normal* might be the name of the customer allocation group.
- **Allocation hierarchy** – A means to combine allocation groups in a hierarchical manner. A maximum of eight levels of hierarchy are supported. In Power Apps, on the **Allocation configuration** page for Inventory Visibility, they are labeled **Group0** to **Group7**. For example, you could define *Channel* as hierarchy level 1 (**Group0**), *Region* as level 2 (**Group1**), and *Customer group* as level 3 (**Group2**). During inventory allocation, you must follow the allocation hierarchy sequence when you specify the value of the allocation group. For example, you could create an allocation of 200 red bikes to the *Web* channel, the *London* region, and the *VIP* customer group. <!--KFM: Do we still use these group labels? The don't seem to appear in the UI (anymore?). I think these are now labeled as "group levels"? -->
- **Available to allocate** – The *virtual common pool* that indicates the quantity that is available for further allocation. It's a calculated measure that you can freely define by using your own formula. If you're also using the soft reservation feature, we recommend that you use the same formula to calculate available-to-allocate and available-to-reserve.
- **Allocated** – A physical measure that shows the allocated quota that can be consumed by the allocation groups. It's deducted at the same time that the consumed quantity is added.
- **Consumed** – A physical measure that indicates that quantities that have been consumed against the original allocated quantity. As numbers are added to this physical measure, the Allocated physical measure is automatically reduced.

The following illustration shows the business workflow for inventory allocation.

![Inventory Visibility allocation business workflow.](media/inventory-visibility-allocation-flow.png "Inventory Visibility allocation business workflow.")

The following illustration shows the allocation hierarchy and allocation groups. The *virtual common pool* shown here is the available-to-allocate quantity.

[<img src="media/inventory-visibility-allocation-hierarchy.png" alt="Inventory Visibility allocation hierarchy." title="Inventory Visibility allocation hierarchy" width="720" />](media/inventory-visibility-allocation-hierarchy.png)

## Turn on and set up inventory allocation in UI version 2 (preview)

[!INCLUDE [preview-banner-section](../includes/preview-banner-section.md)]

<!--KFM: preview until further notice -->

This section applies when you are using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

To set up inventory allocation, you must complete the following tasks, which are described in the subsections of this section:

- Enable the allocation feature and update the configuration to initialize it.
- Set up the *available to allocate* calculated measure (and include the *allocated* physical measure in the calculation).
- Set up your allocation groups
- Update the configuration to activate your new settings

[!INCLUDE [preview-note](../includes/preview-note.md)]

### Enable the inventory allocation feature

Follow these steps to enable the inventory allocation feature.

1. In the **Inventory Visibility** app, select **Feature management** on the navigation pane.
1. On the **Inventory allocation** tile, select **Manage**.
1. Set **Enable feature** to *Yes*.
1. On the toolbar, select **Save**.
1. On the navigation pane, select **Admin Settings**.
1. On the **Update configuration** tile, select **Manage**.
1. Check your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all of the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration change.

### Set up the *available to allocate* calculated measure

When you enable the allocation feature and update the configuration (as described in the previous section), Inventory Visibility creates one predefined data source and several initial measures.

The data source is named *@iv*. It includes the following set of default physical measures:

- *@allocated*
- *@cumulative_allocated*
- *@consumed*
- *@cumulative_consumed*

To use allocation, you must correctly set up the formula for the available-to-allocate calculated measure (*@iv.@available_to_allocate*). For example, you could have the the *onordered* physical measure in the *fno* data source and the *inbound* physical measure in the *pos* data source. You could then allocate on-hand stock for the sum of *fno.onordered* and *pos.inbound*. In this case, *@iv.@available_to_allocate* should contain *pos.inbound* and *fno.onordered* in the formula. Here's an example calculation:

*@iv.@available_to_allocate* = *fno.onordered* &plus; *pos.inbound* &minus; *@iv.@allocated*

> [!NOTE]
> Data source *@iv* is a predefined data source and the physical measures defined in *@iv* with prefix *@* are predefined measures. These measures are a predefined configuration for the allocation feature, so don't change or delete them or you're likely to encounter unexpected errors when using the allocation feature.
>
> You can add new physical measures to the predefined calculated measure *@iv.@available_to_allocate*, but you must not change its name.

Follow these steps to set up the *available to allocate* calculated measure:

1. Open the **Inventory Visibility** app in Power Apps.
1. On the navigation pane, select **Feature Management**.
1. On the **Data source settings** tile, select **Manage**.
1. Open the data source named *@iv*.
1. In the **Calculated Measures** section, open the record named *@available_to_allocate* (if it already exists) or create a new one with this **Calculated measure name** and **Save**.
1. In the **Calculated measure details** section, add the physical measures you want to use to calculate your available-to-allocate quantities. Be sure to include the *@iv.@allocated* physical measure in the formula.

### Set up your allocation groups and hierarchy

Each allocation created in Inventory Visibility must be assigned to a specific *allocation group*. You can create up to eight allocation groups, and must assign a level to each of them to establish a group hierarchy.

You can assign up to 8 groups, each of which has a name and a level defined as an integer from 0 to 7, which correspond to **Group0** to **Group7** in the hierarchy. The level determines the order in which the groups are used in the allocation hierarchy. The group that is assigned to level 0 is the highest level in the hierarchy, and the group that is assigned to level 7 is the lowest level in the hierarchy.

When creating an allocation, hierarchies must be specified from the highest to the lowest order. For example, suppose your configuration has *Country/region* for **Group0**, *State* for **Group1**, and *City* for **Group2**. *Country/region* and *State* are both required when specifying *City*, however, an allocation can be created with *Country/region* and *State*, or *Country/region* only.

Follow these steps to set up your allocation groups and hierarchy:

1. In the **Inventory Visibility** app, select **Feature Management** on the navigation pane.
1. On the **Inventory allocation** tile, select **Manage**.
1. In the **Allocation group** section, use the **New allocation group** button on the section toolbar to add a row for each allocation group you need and assign it a level between 0- and 7. To edit an existing group, select its name in the **Allocation group name** column.
1. On the page toolbar, select **Save**.

> [!IMPORTANT]
> Be careful when deleting or changing the allocation hierarchy. For guidance, see [Tips for using allocation](#allocation-tips).

### Update the configuration to activate your new settings

<!--KFM: I added this. Am I right that we need this section here? -->

After you are done updating your configuration, you must apply the changes to activate them. To do this, follow these steps:

1. In the **Inventory Visibility** app, select **Admin Settings** on the navigation pane.
1. On the **Update configuration** tile, select **Manage**.
1. Check your modifications in the dialog box.

    > [!IMPORTANT]
    > Be sure to verify all of the important modifications that are about to be made to your data sources, physical measures, and dimension mappings.

1. Select **Confirm Update** to apply your configuration change.

## Turn on and set up inventory allocation in UI version 1

This section applies when you are using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

Follow these steps to enable inventory allocation and set up allocation groups if you are using UI version 1:

1. Enable the inventory allocation feature.

    Go to **Legacy UI \> Configuration**. Open the **Feature Management & Settings** tab and turn on the feature named *Inventory Allocation*. Select **Update configuration** on top-right corner to apply the new setting.

1. Configure the *available to allocate* calculated measure and *allocated* physical measure.

    Open the **Calculated Measure** tab to view the initial calculated measure, which is named *@iv.@available_to_allocate*. Edit the formula to meet your business needs by adding and remove physical measures. Be sure to include the *@iv.@allocated* physical measure in the formula. <!--KFM: There is no measure with this name in my env. -->

1. Set up your allocation groups and hierarchy.

    Open the **Allocation** tab. In the default allocation configuration, there are four levels of hierarchy, from the highest to lowest: *Channel* (**Group0**), *customerGroup* (**Group1**), *Region* (**Group2**), and *OrderType* (**Group3**). You can edit the groups by working in the **Edit configuration** field. To remove an existing allocation group, select the **X** next to its name. To add a add new allocation group, type a new the name of each new group directly in the **Edit configuration** field. Select **Save** when you are done editing the groups. <!--KFM: This didn't seem to work when I tried it. -->

1. Update the configuration to activate your new settings.

    When you've finished configuring the allocation group and hierarchy settings, select **Save**, then select **Update Configuration** in the upper right.

The values of the configured allocation groups will be updated when you create an allocation by using either the user interface or API POST (`/api/environment/\{environmentId\}/allocation/allocate`). Details about both approaches are provided later in this article. If you use four group names and set them to \[`channel`, `customerGroup`, `region`, `orderType`\], these names will be valid for allocation-related requests when you call the configuration update API.

> [!NOTE]
> Settings to the allocation feature enabled status and allocation groups made in UI version 1 and UI version 2 don't affect one another. Only those settings applied to the [active UI version](inventory-visibility-ui-version-2.md) apply.

> [!IMPORTANT]
> Be careful when deleting or changing the allocation hierarchy. For guidance, see [Tips for using allocation](#allocation-tips).

## <a name="allocation-tips"></a>Tips for using allocation

- For every product, the allocation function must use the same *dimension level* according to the on-hand index configuration set up in the [on-hand index configuration](inventory-visibility-power-platform.md#index). For example, suppose your index hierarchy is \[`Site`, `Location`, `Color`, `Size`\]. If you allocate some quantity for one product in the dimension level \[`Site`, `Location`, `Color`\], the next time you want to allocate this product, you must also allocate at the same level, \[`Site`, `Location`, `Color`\]. If you use the level \[`Site`, `Location`, `Color`, `Size`\] or \[`Site`, `Location`\], the data will be inconsistent.
- When you modify allocation groups and the hierarchy, if allocation data already exists in the system, deletion of existing allocation groups or a shift in the allocation group hierarchy will corrupt the existing mapping between the allocation groups. Therefore, be sure to use the `unallocate` API to remove all old data before updating the configuration. However, you don't need to clean up the data if you are only adding new allocation groups to the lowest hierarchy.
- Allocation will succeed only for products that have a positive `available_to_allocate` quantity.
- To allocate products from a high allocation hierarchy group to a subgroup, use the `Reallocate` API. For example, if you have an allocation group hierarchy \[`channel`, `customerGroup`, `region`, `orderType`\], and you want to allocate some product from allocation group \[`Online`, `VIP`\] to the sub allocation group \[`Online`, `VIP`, `EU`\], use the `Reallocate` API to move the quantity. If you use the `Allocate` API, it will allocate the quantity from the virtual common pool.
- To view overall product availability (the common pool), use the [query on-hand](inventory-visibility-api.md#query-on-hand) API to request the inventory amount that is *available to allocate*. You can then make allocation decisions based on this information.

## <a name="using-allocation-api"></a>Use the allocation APIs

The following table lists the allocation APIs that are available.

| Method | API | Description |
| --- | --- | --- |
| POST | `/api/environment/\{environmentId\}/allocation/allocate` | Create an allocation |
| POST | `/api/environment/\{environmentId\}/allocation/unallocate` | Revert or remove allocated records |
| POST | `/api/environment/\{environmentId\}/allocation/reallocate` | Move allocated quantities from an existing allocation to other allocation groups |
| POST | `/api/environment/\{environmentId\}/allocation/consume` | Deduct (use) the allocated quantity |
| POST | `/api/environment/\{environmentId\}/allocation/query` | Check existing allocation records against the allocation groups and hierarchy |

### Allocate

Call the `Allocate` API to allocate a product that has specific dimensions. Here's the schema for the request body.

```json
{
    "id": "string",
    "productId": "string",
    "dimensionDataSource": "string",
    "groups": {
        "groupA": "string",
        "groupB": "string",
        "groupC": "string"
    },
    "quantity": decimal,
    "organizationId": "string",
    "dimensions": {
        "dimension1": "string",
        "dimension2": "string",
        "dimension3": "string"
    }
}
```

For example, you want to allocate a quantity of 10 for product *Bike*, site *1*, location *11*, color *red*, channel *Online*, customer group *VIP*, and region *US*. To do this allocation, you can make a call that has the following body content.

```json
{
    "id": "test101",
    "productId": "Bike",
    "groups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "US"
    },
    "quantity": 10,
    "organizationId": "usmf",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    }
}
```

The quantity must always be more than 0 (zero).

> [!NOTE]
> More often than not, `siteId` and `locationId` are required because they aren't empty for most data sources. In the rare case where either `siteId` or `locationId` is empty for a data source, allocation from that data source must omit the empty dimension too.

### Unallocate

Use the `Unallocate` API to reverse the `Allocate` operation. Negative quantity isn't allowed in an `Allocate` operation. The body of `Unallocate` is identical to the body of `Allocate`.

### Reallocate

Use the `Reallocate` API to move some allocated quantity to another group combination. Here's the schema for the request body.

```json
{
    "id": "string",
    "productId": "string",
    "dimensionDataSource": "string",
    "sourceGroups": {
        "groupA": "string",
        "groupB": "string",
        "groupC": "string"
    },
    "groups": {
        "groupD": "string",
        "groupE": "string",
        "groupF": "string"
    },
    "quantity": decimal,
    "organizationId": "string",
    "dimensions": {
        "dimension1": "string",
        "dimension2": "string",
        "dimension3": "string"
    }
}
```

For example, you can move two bikes that have the dimensions \[site=1, location=11, color=red\] from allocation group \[Online, VIP, US\] to allocation group \[Online, VIP, EU\] by calling the `Reallocate` API and providing the following body text.

```json
{
    "id": "test102",
    "productId": "Bike",
    "sourceGroups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "US"
    },
    "groups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "EU"
    },
    "quantity": 2,
    "organizationId": "usmf",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    }
}
```

### Consume

Use the `Consume` API to post the consumption quantity against allocation. For example, you could use this API to move allocated quantity to some real measures. Here's the schema for the request body.

```json
{
    "id": "string",
    "productId": "string",
    "dimensionDataSource": "string",
    "groups": {
        "groupA": "string",
        "groupB": "string",
        "groupC": "string"
    },
    "quantity": decimal,
    "organizationId": "string",
    "dimensions": {
        "dimension1": "string",
        "dimension2": "string",
        "dimension3": "string"
    },
    "physicalMeasures": {
        "datasource1": {
            "measure": "string" // Addition or Subtraction
        }
    }
}
```

For example, there are eight allocated bikes that have the dimensions \[site=1, location=11, color=red\] for allocation group \[Online, VIP, US\]. The following available-to-allocate formula is used:

`@iv.@available_to_allocate` = `fno.onordered` + `pos.inbound` – `@iv.@allocated`

The eight bikes are allocated from the `pos.inbound` measure.

Now, three bikes are sold, and they're taken from the allocation pool. To register this move, you can make a call that has the following request body.

```json
{
    "id": "test103",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    },
    "groups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "US"
    },
    "quantity": 3,
    "physicalMeasures": {
        "pos": {
            "inbound": "Subtraction"
        }
    }
}
```

After this call, the allocated quantity for the product will be reduced by 3. In addition, Inventory Visibility will generate an on-hand change event where `pos.inbound` = *-3*. Alternatively, you can keep the `pos.inbound` value as is, and just consume the allocated quantity. However, in this case, you must either create another physical measure to keep the consumed quantities or use the predefined measure `@iv.@consumed`.

In this request, notice that the physical measure you use in the consume request body should use the opposite modifier type(Addition or Subtraction), compared with the modifier type used in the calculated measure. So in this consume body, `iv.inbound` has the value `Subtraction`, not `Addition`.

The `fno` data source can't be used in the consume body as we always claimed that Inventory Visibility can't change any data for the `fno` data source. The data flow is one-way, which means that all quantity changes for the `fno` data source must come from your Supply Chain Management environment. 

### <a name="consume-to-soft-reserved"></a>Consume as a soft reservation

The `Consume` API can also consume the allocated quantity as a soft reservation. In this case, the `Consume` operation will reduce the allocated quantity and then create a soft reservation for that quantity. To use this approach, you must also be using the [soft reservation](inventory-visibility-reservations.md) feature of Inventory Visibility.

For example, you've set a soft reservation physical measure as `iv.softreserved`. The following formula is used for the available-to-reserve calculated measure:

`iv.available_to_reserve` = `fno.onordered` + `pos.inbound` – `iv.softreserved`

To use this setup with the allocation feature, add `@iv.@allocated` to `iv.available_to_reserve` to produce the following formula:

`iv.available_to_reserve` = `fno.onordered` + `pos.inbound` – `iv.softreserved` – `@iv.@allocated`

Then update `@iv.@available_to_allocate` to the same value.

When you want to consume a quantity of 3 and directly reserve this quantity, you can make a call that has the following request body.

```json
{
    "id": "???",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    },
    "groups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "US"
    },
    "quantity": 3,
    "physicalMeasures": {
        "iv": {
            "softreserved": "Addition"
        }
    }
}
```

In this request, notice that `iv.softreserved` has the value `Addition`, not `Subtraction`.

### Query

Use the `Query` API to retrieve allocation related information for some products. You can use dimension filters and allocation group filters to narrow down the results. *The dimensions must match exactly the one you want to retrieve*, for example, \[site=1, location=11\] will have unrelated results compared with \[site=1, location=11, color=red\].

```json
{
    "productId": "string",
    "organizationId": "string",
    "dimensions": {
        "dimension1": "string",
        "dimension2": "string",
        "dimension3": "string"
    },
    "groups": {
        "additionalProp1": "string",
        "additionalProp2": "string",
        "additionalProp3": "string"
    },
}
```

For example, use \[site=1, location=11, color=red\] and empty groups field to get all allocation records:

```json
{
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    },
    "groups": {},
}
```

Use \[site=1, location=11, color=red\] and groups \[channel=Online, customerGroup=VIP, region=US\] to get allocation records for this group:

```json
{
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "siteId": "1",
        "locationId": "11",
        "colorId": "red"
    },
    "groups": {
        "channel": "Online",
        "customerGroup": "VIP",
        "region": "US"
    },
}
```

## Use the allocation user interface

You can manually manage allocations using the Inventory Visibility app in Power Apps.

> [!IMPORTANT]
> In the current version of the Inventory Visibility app, you can only manage allocations when you are using Inventory Visibility UI version 1. If you are using UI version 2, you must use the APIs to manage allocations. For more information about the two user interface versions and how to switch between them, see [Inventory Visibility app user interface versions](inventory-visibility-ui-version-2.md) <!-- KFM: I think this is true. -->

### Open the allocation user interface

To open the allocation user interface, follow these steps.

1. Sign in to your Power Apps environment and open the **Inventory Visibility** app.
1. At the bottom of the navigation pane, open the **Change area** menu and select **Legacy UI**.
1. On the navigation pane, select **Operational visibility** and then open the **Allocation** tab.

### Create an allocation

Follow these steps to create an allocation in the Inventory Visibility app.

1. Open the allocation user interface, as described previously.
1. On the toolbar, select **Allocate**.
1. Set the **Base fields**, **Dimensions**, and **Target allocation groups** values. When you are selecting values in the **Dimensions** section, first select a data source, then select a dimension from that data source, and then enter dimension values in the fields that appear each time you add a dimension.
1. Select **submit**.

### Consume an allocation

On the toolbar of the **Allocation** tab, select **Consume** to consume an allocation. To ensure that you consume within the correct allocation group and hierarchy, enter the same sets of organization and dimension details when you specified creating the allocation.

### Reallocate an allocation

On the toolbar of the **Allocation** tab, select **Reallocate** to move existing allocated quantity from one set of allocation groups to another.

### Query existing allocations

On the toolbar of the **Allocation** tab, select **Query**, and then enter product, organization, dimension, and allocation group values to obtain query results of existing allocations.
