---
title: Inventory Visibility inventory allocation
description: This article explains how to set up and use the inventory allocation feature, which lets you set aside dedicated inventory to ensure that you can fulfill your most profitable channels or customers.
author: yufeihuang
ms.date: 05/27/2022
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

It is common that organizations need to pre-alocate their onhand stock to most important sales channels, customer groups, regions or to specific promotion events so that the preallocated stocks are protected against any other usage and can only be consumed via sales transactions that are relevant to the allocation. Inventory allocation in inventory visibility is a typical practice in the sales operational planning process, and is done before the actual sales activities occur and a sales order is created.

For example, Contoso produces a very popular bike, due to recent supply chain disruption all its in-transit stocks are affected therefore Contoso only have limited onhand stock and need to make best use of the stocks. Contoso operates both online and in-store sales. In each sales channel, the company has a few important corporate partners (marketplaces and large retailers) that demand that a specific portion of the bike's available inventory be saved for them. Therefore, the bicycle company must be able to balance stock distribution across channels and also manage the expectations of its VIP partners. The best way to achieve both goals is to use inventory allocation, so that each channel and retailer can receive specific allocated quantities that can be sold to consumers later.

Inventory allocation has two basic business purposes:

- **Inventory protection (ringfencing)** – Organizations want to pre-allocate restricted or limited stock to prioritized channels, regions, VIP customers, and subsidiary companies. The Inventory Visibility allocation feature aims to protect the allocated inventory, so that the other allocations, reservations, or other sales demands won't affect the previously allocated inventory.
- **Oversell control** – The Inventory Visibility allocation feature aims to put a restriction on the previously allocated quantities, so that the receiving party (for example, a channel or customer group) won't over-consume them when the actual sales transaction that is based on a soft reservation goes into effect.

## Allocation definition in Inventory Visibility Service
### Allocation Virtual Pool
Although the allocation feature in Inventory Visibility service doesn't set aside physical inventory quantities, it does refer to available physical inventory quantity to define its initial **available to allocate** virtual pool quantity. Inventory allocation in Inventory Visibility is a soft allocation. It's done before actual sales transactions occur and doesn't depend on sales orders. For example, you can allocate stock to your most important sales channels or large corporate retailers before any end customers visit the sales channel or retail store to purchase it.

### Difference between inventory allocation and soft reservation
[Soft Reservation](inventory-visibility-reservations.md) is usually linked to actual sales transactions (sales order lines). Both allocation and soft reservation can be used independently but if you want to use them together, soft reservation should happen after allocation is done. We recommend that you do inventory allocation first and then soft reserve against the allocated quantities to achieve near real-time consumption against allocation. For more information, see [Consume as a soft reservation](#consume-to-soft-reserved).

The inventory allocation feature lets sales planners or key account managers to manage and pre-allocate important stock across allocation groups (such as channels, regions, and customer groups). It also supports real-time tracking, adjustment, and analytics of consumption against allocated quantities, so that replenishment or reallocation can be done on time. This ability to have real-time visibility into allocation, consumption, and allocation balance is especially important at fast-sale or promotion events.

## Terminology

The following terms and concepts are useful in discussions of inventory allocation:

- **Allocation group** – The group that owns the allocation, such as a sales channel, customer group, or order type.
- **Allocation group value** – The value of each allocation group. For example, *web* or *store* might be the value of the sales channel allocation group, whereas *VIP* or *normal* might be the value of the customer allocation group.
- **Allocation hierarchy** – A means to combine allocation groups in a hierarchical manner. For example, you can define *channel* as hierarchy level 1, *region* as level 2, and *customer group* as level 3. During inventory allocation, you must follow the allocation hierarchy sequence when you specify the value of the allocation group. For example, you might allocate 200 red bikes to the *Web* channel, the *London* region, and the *VIP* customer group.
- **Available to allocate** – The *virtual common pool* that indicates the quantity that is available for further allocation. It's a calculated measure that you can freely define by using your own formula. If you're also using the soft reservation feature, we recommend that you use the same formula to calculate available-to-allocate and available-to-reserve.
- **Allocated** – A physical measure that shows the allocated quota that can be consumed by the allocation groups, it is deducted at the same time when **consumed** quantity is added.
- **Consumed** – A physical measure that indicates that quantities that have been consumed against the original allocated quantity. As numbers are added to this physical measure, the Allocated physical measure is automatically reduced.

The following illustration shows the business workflow for inventory allocation.

![Inventory Visibility allocation business workflow.](media/inventory-visibility-allocation-flow.png "Inventory Visibility allocation business workflow.")

The following illustration shows the allocation hierchy and allocation groups. The **Virtual Common Pool** here is the Available to allocate quantity.

![Inventory Visibility allocation hierarchy.](media/inventory-visibility-allocation-hierarchy.png "Inventory Visibility allocation hierarchy.")
## Set up inventory allocation

The inventory allocation feature consists of the following components:

- The predefined, allocation-related data source, physical measures, and calculated measures.
- Customizable allocation groups that have a maximum of eight levels.
- A set of allocation application programming interfaces (APIs):
  - allocate
  - reallocate
  - unallocate
  - consume
  - query

The process of configuring the allocation feature has three steps:

- Enable the feature via Inventory Visibility power app > Configuration > Feature Management & Settings > Allocation
- Set up the [data source](inventory-visibility-configuration.md#data-source-configuration) and its [measures](inventory-visibility-configuration.md#data-source-configuration-physical-measures).
- Set up the allocation group name and hierarchy.

### Predefined data source

When you enable the allocation feature and call the configuration update API, Inventory Visibility creates one predefined data source and several initial measures.

The data source is named `@iv`with a set of default physical measures. You can view them via Inventory Visibility power app > Configuration > Data Source, you can see a **Datasource - @IV**
Unfold the datasource @iv to see a list of initial physical measures:

- `@iv`
  - `@allocated`
  - `@cumulative_allocated`
  - `@consumed`
  - `@cumulative_consumed`

Go to **Calculated Measures** tab to see the initial calculated measure named **@AVAILABLE_TO_ALLOCATE of @IV**:

- `@iv`
  - `@iv.@available_to_allocate` = `??` – `??` – `@iv.@allocated`

### Add other physical measures to the available-to-allocate calculated measure

To use allocation, you must set up the formula of available-to-allocate calculated measure (`@iv.@available_to_allocate`) correctly. For example, you have `fno` data source and the `onordered` measure, the `pos` data source and the `inbound` measure, and you want to do allocation on the on hand for the sum of `fno.onordered` and `pos.inbound`. In this case, `@iv.@available_to_allocate` should contain `pos.inbound` and `fno.onordered` in the formula. Here's an example:

`@iv.@available_to_allocate` = `fno.onordered` + `pos.inbound` – `@iv.@allocated`

> [!NOTE]
> Data source `@iv` is a predefined data source and the physical measures defined in `@iv` with prefix `@` are predefined measures. These measures are a predefined configuration for the allocation feature, so don't change or delete them or you're likely to encounter unexpected errors when using the allocation feature.
>
> You can add new physical measures to the predefined calculated measure `@iv.@available_to_allocate`, but you must not change its name.

### Manage allocation groups

A maximum of eight allocation group names can be set. The groups have a hierarchy. Follow the below steps to view and update allocation groups.

1. **Inventory Visibility Power App** \> **Configuration** \> **Allocation** \> **Edit Configuration**. You can see by default we have an allocation hierarchy with four layers: Channel (top layer) - customerGroup (second layer) - Region (third layer) - OrderType (fourth layer).
1. You can remove the existing allocation group by clicking the cross next to it (you need to be very cautious about deleting or changing the allocation hierarchy mapping, refer to [Allocation using Tips](inventory-visibility-allocation.md#allocation-using-tips) for guidance). You can also add new allocation groups on the hierarchy by typing in the new group name directly in the field.
1. Once you are done with allocation group and hierarchy settings, save and click **Update Configuration** on the upper right.
1. The values of the configured allocation groups will be updated when you create allocation via either UI or API POST ​/api​/environment​/{environmentId}​/allocation​/allocate

You will find details about both approach in the later sections within this doc.

If you use four group names and set them to \[`channel`, `customerGroup`, `region`, `orderType`\], these names will be valid for allocation-related requests when you call the configuration update API.

### Allocation using Tips

- For every product, the allocation function should use in the same *dimension level* according to the product index hierarchy you set in the [product index hierarchy configuration](inventory-visibility-configuration.md#index-configuration). For example, suppose your index hierarchy is \[`Site`, `Location`, `Color`, `Size`\]. If you allocate some quantity for one product in the dimension level \[`Site`, `Location`, `Color`\], the next time you want to allocate this product, you should also allocate at the same level, \[`Site`, `Location`, `Color`\]. If you use the level \[`Site`, `Location`, `Color`, `Size`\] or \[`Site`, `Location`\], the data will be inconsistent.
- **Modify allocation groups and hierachy**: If you already have allocation data in the system, deleting existing allocation groups or shifting the allocation group hierarchy will corrupt the existing mapping between the allocation groups, therefore make sure you manually clean up all the old data before you update your new configuration. Adding new allocation groups to lowest hierarchy does not impact existing mapping therefore no need to clean the data.
- Allocation will only succeed when the product has positive available_to_allocate quantity.
- To allocate products from a high *allocation level* group to a subgroup, use the `Reallocate` API. For example, you have an allocation group hierarchy \[`channel`, `customerGroup`, `region`, `orderType`\], and you want to allocate some product from allocation group \[Online, VIP\] to the sub allocation group \[Online, VIP, EU\], use the `Reallocate` API to move the quantity. If you use the `Allocate` API, it will allocate the quantity from the virtual common pool.
- If you want to view overall product availability (the common pool), you can use the [Query on-hand](inventory-visibility-api.md#query-on-hand) API to request the inventory amount of "Available to Allocate", and then you can make the allocation decisions based on this information.

## <a name="using-allocation-api"></a>Use the allocation API

Currently, five allocation APIs are opened:

- POST ​/api​/environment​/{environmentId}​/allocation​/allocate is to create initial allocation
- POST ​/api​/environment​/{environmentId}​/allocation​/unallocate is to revert/remove the allocated quantities
- POST ​/api​/environment​/{environmentId}​/allocation​/reallocate is to move allocated quantity from existing allocation to another allocation group(s)
- POST ​/api​/environment​/{environmentId}​/allocation​/consume is to use (deduct) the allocated quantity
- POST ​/api​/environment​/{environmentId}​/allocation​/query is to check existing allocation records agains allocation groups and hierarchy

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
    "quantity": 0,
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
        "channel": "Web",
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
    "quantity": 0,
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
        "channel": "Web",
        "customerGroup": "VIP",
        "region": "US"
    },
    "groups": {
        "channel": "Web",
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

Use the `Consume` API to post the consumption quantity against allocation. For example, you might use this API to move allocated quantity to some real measures. Here's the schema for the request body.

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
        "channel": "Web",
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

After this call, the allocated quantity for the product will be reduced by 3. In addition, Inventory Visibility will generate an on-hand change event where `pos.inbound` = *-3*. Alternatively, you can keep the `pos.inbound` value as it is and just consume the allocated quantity. However, in this case, you must either create another physical measure to keep the consumed quantities or use the predefined measure `@iv.@consumed`.

In this request, notice that the physical measure you use in the consume request body should use the opposite modifier type(Addition or Subtraction), compared with the modifier type used in the calculated measure. So in this consume body,  `iv.inbound`  has the value `Subtraction`, not `Addition`.

The `fno` data source can't be used in the consume body as we always claimed that Inventory Visibility can't change any data for the `fno` data source. The data flow is one-way, which means that all quantity changes for the `fno` data source must come from your Supply Chain Management environment.

### <a name="consume-to-soft-reserved"></a>Consume as a soft reservation

The `Consume` API can also consume the allocated quantity as a soft reservation. In this case, the `Consume` operation will reduce the allocated quantity and then do a soft reservation for that quantity. To use this approach, you must also be using the [soft reservation](inventory-visibility-reservations.md) feature of Inventory Visibility.

For example, you have set a soft reservation physical measure as `iv.softreserved`. The following formula is used for the available-to-reserve calculated measure:

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
        "channel": "Web",
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

Use the `Query` API to retrieve allocation related information for some products. You can use dimension filters and allocation group filters to narrow down the results. The dimensions must match exactly the one you want to retrieve, for example, \[site=1, location=11\] will have non-related results compared with \[site=1, location=11, color=red\].

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
    "groups": {
        "channel": "Web",
        "customerGroup": "VIP",
        "region": "US"
    },
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
        "channel": "Web",
        "customerGroup": "VIP",
        "region": "US"
    },
}
```
## Use the Allocation User Interface

You can also manually manage allocations via UI. Go to Inventory Visibility power app \> **Operational Visibility** \> **Allocation** to take all the actions
### Create Allocation
Click the **+allocate** button > fill the the Base Fiels, and Dimensions and the target allocation groups value > click submit. Please note when you select the collect datasource in the **Dimensions** section, a dimensions drop down list will be available for you to specify dimensions (for example siteId). After that fiels for you to enter dimension values will appear.
### Consume
Click **Consume** to consume the allocation, make sure you enter exactly the same sets of organization and dimension information as you entered for allocation creation in order to consume within the correct allocation group and hierarchy

### Reallocation
Click **Reallocate** to move existing allocated quantity from one set of allocation groups to the other set of allocation groups.

### Query
Click **Query** and enter product organization, dimension and allocation groups information to obtain query result of existing allocations.
