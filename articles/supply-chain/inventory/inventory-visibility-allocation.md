---
title: Inventory Visibility inventory allocation
description: This topic explains how to set up and use the inventory allocation feature, which lets you to set aside dedicated inventory to ensure you can fulfill your most profitable channels or customers.
author: yufeihuang
ms.date: 05/13/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2022-05-13
ms.dyn365.ops.version: 10.0.27
---

# Inventory Visibility inventory allocation

[!include [banner](../includes/banner.md)]

## Business background and purpose

Manufactures, retailers, and other supply chain business holders, in many cases, need to preallocate stock for important sales channels, locations, or customers, specific sales events. Inventory allocation is a typical practice in the sales operational planning process, and it happens before the actual sales activities take place and before the creation of sales order. For example, a bicycle company has limited stock available for a very popular bike. This company operates its sales both online and in-store, and within each sales channel this company has a few important corporate partners (market places and big retailors) who also demand a certain portion of this bike's available inventory to be saved to them. In this case, as the bicycle company would like to balance stock distribution across channels and also manage expectation of VIP partners, the best way to do this is to using inventory allocation so that each channel and retailor can receive certain allocated quantities to sell to consumers later on.

The fundamental business purpose of the inventory allocation is as follows:

- **Inventory protection (ringfencing):** Organizations want to preallocate restricted or limited stocks to prioritized channels, regions, VIP customers, and subsidiary companies. Inventory Visibility allocation feature aims to protect the allocated inventory so that the other allocations, reservations or other sales demands will not affect the already allocated inventory.

- **Oversell control:** for the allocated quantities, the Inventory Visibility allocation feature aims to put a restriction on the already allocated quantities so that the receiving party (such as a channel or customer group) won't over consume the allocated quantities when the actual sales transaction based on a soft reservation kicks in.

## Allocation definition in Inventory Visibility Service

Although the allocation feature in Inventory Visibility service doesn't set aside physical inventory quantities, it does refer to available physical inventory quantity to define its initial *available to allocate* virtual pool quantity. Inventory allocation in Inventory Visibility is a soft allocation; it happens before actual sales transactions takes place and doesn't have a dependency on sales orders. For example, you can allocate to your most important sales channels or big cooperate retailors before any end-customer visits the sales channel or retail store to purchase.

The difference between inventory allocation and [inventory soft reservation](inventory-visibility-reservations.md) is that soft reservation is usually tied up to actual sales transactions (sales order lines). Therefore, if you want to use the allocation and soft reservation features together, the recommended flow is that you will do inventory allocation first, and then soft reserve against the allocated quantities, see [Consume as a soft reservation](#consume-to-soft-reserved) for more details.

The inventory allocation feature lets sales planners or key account managers manage and pre-allocate important stocks across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities so that replenishment or reallocation can be made on-time, which is especially important at fast-sale or promotion events where the capability to have real-time visibility into allocation, consumption, and allocation balance is particularly useful.

## Terminology

The following terms and concepts are useful when discussing inventory allocation:

- **Allocation group** - The group that owns the allocation, such as a sales channel, customer group, or order type.
- **Allocation group value** - The value of each allocation group. For example, a *web* or *store* could be the value of the sales channel allocation group, while *VIP* or *normal* could be the value for the customer allocation group.
- **Allocation hierarchy** - Allows you to combine allocation groups in a hierarchical way. For example, you can define *channel* as hierarchy level 1, *region* as level 2, and *customer* group as level 3. Later, when you are doing inventory allocation, you will need to specify the allocation group value following the allocation hierarchy sequence. For example, you might allocate 200 red bikes to the Web channel, the London region, and the VIP customer group.
- **Available to allocate** - this is the *virtual common pool* that indicates the quantity available for further allocation. It is a calculated measure that can be defined freely with your own formula. If you are also using the soft reservation feature, we recommend that you use the same formula to calculate available-to-allocate and available-to-reserve.
- **Allocated** - this shows the allocated quota that can be consumed by the allocation groups. It is a physical measure
- **Consumed** - this indicates how many quantities have been consumed against the original allocated quantity. It is a physical measure. By adding numbers to this physical measure, it will automatically reduce the Allocated physical measure.

The following illustration shows the inventory allocation workflow.

![Allocation business flow](media/inventory-visibility-allocation-flow.png "Invetory Visibility allocation business flow")

## Set up inventory allocation

The inventory allocation feature comprises the following components:

1. Predefined, allocation-related data source, physical measures, and calculated measures.
2. Customizable allocation groups with at most 8 levels.
3. A set of allocation APIs including:
   - allocate
   - reallocate
   - unallocate
   - consume
   - query

The configuration of allocation feature contains two steps:

- Set up the [datasoure](inventory-visibility-configuration.md#data-source-configuration) and its [measures]((inventory-visibility-configuration.md#data-source-configuration-physical-measures)
- Set up the allocation group name and hierarchy

### Predefined data source

When you enable the allocation feature and call configuration update API, Inventory Visibility will create one predefined data source and several initial measures.

The data source name is `@iv`.

The initial physical measures are:

- `@iv`
  - `@allocated`
  - `@cumulative_allocated`
  - `@consumed`
  - `@cumulative_consumed`

The initial calculated measures are:

- `@iv`
  - `@availiable_to_allocate` = `??` - `??` - `@allocated`

### Add other physical measures to the available-to-allocate calculated measure

To use allocation, you must set up the available-to-allocate calculated measure (`@iv`.`@availiable_to_allocate`). For example, if you have data source `fno` and measure `onordered`, and you want to do allocation for this measure, then `@iv.@availiable_to_allocate` should contain `fno.onordered` in the formula, such as:

`@iv.@availiable_to_allocate` = `fno.onordered` - `@allocated`

### Change the allocation group name

At most, there can be 8 allocation group names set. The groups have a hierarchy.

To set the group names, go to the **Inventory Visibility Power App Configuration** page. To get there, open your Dataverse environment, then go to the Inventory Visibility Power App and select **Configuration \> Allocation**.

For example, if you use 4 group names and set them to [`channel`, `customerGroup`, `region`, `orderType`], then these names will be valid for allocation-related requests when you call the configuration-update API.

### Using the allocation API

Detailed API information is available at the [Inventory Visibility Swagger page](https://inventoryservice.wus-il101.gateway.prod.island.powerapps.com/swagger/index.html).

There are 5 allocation APIs opened for now:

- POST ​/api​/environment​/{environmentId}​/allocation​/allocate
- POST ​/api​/environment​/{environmentId}​/allocation​/unallocate
- POST ​/api​/environment​/{environmentId}​/allocation​/reallocate
- POST ​/api​/environment​/{environmentId}​/allocation​/consume
- POST ​/api​/environment​/{environmentId}​/allocation​/query

#### Allocate

Call the `Allocate` API allocate a product with specific dimensions. The request body schema is:

```json
{
  "id": "string",
  "productId": "string",
  "dimensionDataSource": "string",
  "targetGroups": {
    "groupA": "string",
    "groupB": "string",
    "groupC": "string"
  },
  "quantity": 0,
  "organizationId": "string",
  "dimensions": {
    "dimension1": "string",
    "dimension2": "string",
    "dimension3": "string"
  }
}
```

For example, you want to allocate 10 quantity for product: Bike, site: 1, location: 11, color: red, channel: Online, customer group: VIP, and region: US. To do so, you can make a call with the following body content:

```json
{
  "id": "???",
  "productId": "Bike",
  "targetGroups": {
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

The quantity must always be greater than 0.

#### Unallocate

`Unallocate` is the revert operation of `Allocate`. Negative quantity is not allowed in an `Allocate` operation. The body of `Unallocate` is exactly same as `Allocate`.

#### Reallocate

Use the `Reallocate` API to move some allocated quantity to another group combination. The request body schema is :

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
  "targetGroups": {
    "groupD": "string",
    "groupE": "string",
    "groupF": "string"
  },
  "quantity": 0,
  "organizationId": "string",
  "dimensions": {
    "dimension1": "string",
    "dimension2": "string",
    "dimension3": "string"
  }
}
```

For example, we can move 2 bikes with dimensions \[site=1, location=11, color=red\] from \[Online, VIP, US\] to \[Online, VIP, EU\] by calling the `Reallocate` API with the following body text:

```json
{
  "id": "???",
  "productId": "Bike",
  "sourceGroups": {
    "channel": "Online",
    "customerGroup": "VIP",
    "region": "US"
  },
  "targetGroups": {
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

#### Consume

Use the `Consume` to post the consumption quantity against allocation. For example, you might use this API to move some allocated quantity to some real measures. The request body schema is as follows:

```json
{
  "id": "string",
  "productId": "string",
  "dimensionDataSource": "string",
  "targetGroups": {
    "groupA": "string",
    "groupB": "string",
    "groupC": "string"
  },
  "quantity": 0,
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

For example, there are 8 allocated bikes with dimensions \[site=1, location=11, color=red\] for allocation group \[Online, VIP, US\], and the availiable to allocate formula is:

`@iv.@availiable_to_allocate` = `fno.onordered` - `@allocated`

These 8 bikes are allocated from the `fno.onordered` measure.

Now, 3 bikes are sold and they are taken from the allocation pool. To register this, you could make a call with the following request body:

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
  "targetGroups": {
    "channel": "Online",
    "customerGroup": "VIP",
    "region": "US"
  },
  "quantity": 3,
  "physicalMeasures": {
    "fno": {
      "onordered": "Subtraction"
    }
  }
}
```

After this call, the allocated quantity for this product will reduce by 3 and also Inventory Visibility will generate an on-hand change event with `fno.onordered` = -3. You could instead choose to keep the `fno.onordered` value as it is and just consume the allocated quantity, but then you would need to create another physical measure to keep these consumed quantities, or use our predefined measure `@iv.@consumed`.

#### <a name="consume-to-soft-reserved"></a>Consume as a soft reservation

The `Consume` API can also consume the allocated quantity as a soft reservation. This means that the `Consume` operation will reduce the allocated quantity and then do a soft reservation for that quantity. To do this, you must also be using the [soft reservation](inventory-visibility-reservations.md) feature of Inventory Visibility.

For example, suppose you have set a soft reservation modifier (measure) as `iv.softreserved`. The availiable-to-reserve calculated measure's formula is:

`iv.availiable_to_reserve` = `fno.onordered` - `iv.softreserved`

When using this with the allocation feature, add `@iv.@allocated` to `iv.availiable_to_reserve`. The formula will then be:

`iv.availiable_to_reserve` = `fno.onordered` - `iv.softreserved` - `@iv.@allocated`

Then also update `@iv.@availiable_to_allocate` to same value.

When you want to consume 3 quantity and reserve them directly, you can make a call with the following request body:

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
  "targetGroups": {
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

Notice that in this request, `iv.softreserved` has value `Addition`, not `Subtraction`.
