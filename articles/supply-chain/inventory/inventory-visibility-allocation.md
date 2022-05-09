# Inventory Allocation

[!include [banner](../includes/banner.md)]

## Business Background and Purpose

Manufactures, Retailers and other supply chain business holders in many cases need to pre-allocation stocks for important sales channels, locations or customers, or a specific sales event. Inventory Allocation is a typical practice in the Sales Operational Planning process, and it happens before the actual sales activities take place and before the creation of Sales Order. For example a bicycle company has limited stocks available for a very popular bike. This company operates its sales both online and in-store, additionaly within each sales channel this company has a few important coporate partners (market places and big retailors) who also demands certain portion of this bike's available inventory to be 'saved' to them. In this case as the bicycle company would like to balance stock distribution across channels and also manage expectation of VIP partners, the best way to do this is to using inventory allocation so that each channel and retailors can receive certain allocated quantities for them to sell to consumers later on.

The fundamental business purpose of the inventory allocation is as below:

- **Inventory Protection (‘ringfence’):** Organisations wants to pre-allocate restricted or limited stocks to prioritised channels, regions, VIP customers, subsidiary companies. Inventory Visibility allocation feature aims to protect the allocated inventory so that the other allocations, reservations or other sales demands will not affect the already allocated inventory.

- **Oversell Control:** for the allocated quantities, Inventory Visibility allocation feature also aims to put a restriction on the already allocated quantities so that the allocation receiver party (channels, customer groups) will not over consume the allocated quantities when actual sales transaction based soft reservation kicks in.

## Allocation Definition in Inventory Visibility Service

To achieve the business purposes stated above, despite that the Allocation feature in Inventory Visibility service does not set aside physical inventory quantities, it does refer to available physical inventory quantity to define its initial 'Available to Allocate' virtual pool quantity. Inventory allocation in Inventory Visibility Service is a soft allocation, it happens before actual sales transaction takes places and does not have dependency on sales orders. For example, you can allocate to your most important sales channels or big cooperate retailors before any end-customers visits the sales channel or the retail store to purchase.

The difference between inventory allocation and [inventory soft reservation](inventory-visibility-reservations.md) is that soft reservation is usually tied up to actual sales transactions, i.e. sales order lines. Therefore if you want to use allocation and soft reservation features together, the recommended flow is that you will do inventory allocation first, and then soft reserve agaist the allocated quantities, see [Consume as Soft Reserved](#consume-to-soft-reserved) for more details.

Inventory Visibility service's allocation feature allows sales planners or key account managers to manage and pre-allocate important stocks across alloction groups (i.e. channels, regions, customer groups, etc.) and also have real-time tracking, adjustment and analytics of the consumption against allocated quanties so that replenishment or reallocation can be made on time, especially in fast-sale or promotion events, the capability to have real-time visibility into allocation and consumtion and allocation balance is super useful.

## Terminologies

**Allocation Group** - This is the allocation owner groups such as sales channels, customer groups, order types, etc.

**Allocation Group value** - this is the value of each allocation group. For example, web or store are the value of sales channel allocation group, while VIP or normal can be the value for customer allocation group

**Allocation Hierarchy** - this allows you to combine allocation groups in a hierarchical way. For example, you can define channel as hierarchy level 1, region as level 2 and customer group as level 3, etc. Later on when you are doing inventory allocation, you will need to specify the allocation group value following the allocation hierarchy sequence. For example, allocate 200 red bike to Channel-web,region-London,customer group-VIP

**Available to Allocate** - this is the 'Virtual Common Pool' that indicateds how many quantities are available for further allocation. It is a calculated measure that can be defined freely with your own formula. If you are also using soft reservation feature at the same time, for best practice we recommend you to use the same formula to calculate Available to Allocate and Available to Reserve

**Allocated** - this shows the allocated quota that can be consumed by the allocation groups. It is a physical measure
Consumed - this indicates how many quantities have been consumed against the original allocated quantity. It is a physical measure. By adding numbers to this physical measure, it will automatically reduce the Allocated physical measure.

![Allocation business flow](media/inventory-visibility-allocation-flow.png "Invetory Visibility allocation business flow")

## Set Up Allocation Configuration

The Allocation in Inventory Visibility contains:

1. Predefined allocation related datasource, physical measures and calculated measures.
2. Customizable allocation groups with at most 8 level.
3. A set of allocation APIs including:
   - allocate
   - reallocate
   - unallocate
   - consume
   - query

The configuration of allocation feature contains 2 parts:

- [datasoure](inventory-visibility-configuration.md#data-source-configuration) and its [measures]((inventory-visibility-configuration.md#data-source-configuration-physical-measures)
- allocation group name and hierarchy

### Pre-Defined datasource

When you enable allocation feature and call configuration update api, Inventory Visibility will create one predefined datasource and some measures in configuration.

The datasource name is `@iv`.

The physical measures contains:

- `@iv`
  - `@allocated` // current allocated quantity
  - `@cumulative_allocated` // cumulative allocated quantity
  - `@consumed` // TBD ???
  - `@cumulative_consumed` // cumulative consumed quantity

The calculated measures contains:

- `@iv`
  - `@availiable_to_allocate` = `??` - `??` - `@allocated`

### Add other physical measures to Avaliable to Allocate calculated measure

To use allocation, the Avaliable to Allocate calculated measure (`@iv`.`@availiable_to_allocate`) must be setup.
For example, if you has datasource `fno` and measure `onordered`, you want to do allocation for this measure,
the `@iv`.`@availiable_to_allocate` should contains `fno`.`onordered` in the formula, which means:

`@iv`.`@availiable_to_allocate` = `fno`.`onordered` - `@allocated`

### Change allocation group name

There is at most 8 allocation group names can be set, the groups has hierarchy.
You can come to Inventory Visibility Power App Configuration Page to set these group names:

Your Dataverse environment => Inventory Visibility Power App -> Configuration -> Allocation

For example, we use 4 group names and set them to [`channel`, `customerGroup`, `region`, `orderType`],
after calling configuration update api, these names will be valid for allocation related request.

### How to Use Allocation Api

You can find very detailed infomation in [Inventory Visibility Swagger Page](https://inventoryservice.wus-il101.gateway.prod.island.powerapps.com/swagger/index.html).

There are 5 allocation APIs opened for now:

- POST ​/api​/environment​/{environmentId}​/allocation​/allocate
- POST ​/api​/environment​/{environmentId}​/allocation​/unallocate
- POST ​/api​/environment​/{environmentId}​/allocation​/reallocate
- POST ​/api​/environment​/{environmentId}​/allocation​/consume
- POST ​/api​/environment​/{environmentId}​/allocation​/query

#### Allocate

Calling `Allocate` api can do an allocation for some product with specific dimension,
the request body schema is:

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

For example you want to allocate 10 quantity for product `Bike` in site `1`, location `11` with color `red`, for channel `Online`, customer group `VIP` and region `US`,
you can make a call with body:

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

The quantity should always be greater than 0.

#### Unallocate

`Unallocate` is the revert operation for `Allocate`, as negative quantity is not allowed in `Allocate` operation.
The body if `Unallocate` is exactly same as `Allocate`.

#### Reallocate

`Reallocate` API is used to move some allocated quantity to another group combination.
The request body schema is :

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

For example, we can move 2 `Bike` with dimension [site=`1`, location=`11`, color=`red`] from [`Online`,`VIP`,`US`] to [`Online`,`VIP`,`EU`] by calling `Reallocate` api with body:

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

`Consume` API is used to post the consumption quantity against allocation. You can decide to use this api to move some allocated quantity to some real measures.
The request body schema is:

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

For example, there is 8 allocated `Bike` with dimension [site=`1`, location=`11`, color=`red`] for allocation group [`Online`,`VIP`,`US`], and the availiable to allocate formula is
`@iv`.`@availiable_to_allocate` = `fno`.`onordered` - `@allocated`, these 8 bikes are allocated from `fno`.`onordered` measure.

Now there is 3 `Bike`s sold and they are taken from allocation pool, you can make a call with request body:

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

After this call, the allocated quantity for this product will reduce 3 and also Inventory Visibility will generate a onhand change event with `fno`.`onordered`= `-3`.
Of course you can choose to keep the `fno`.`onordered` value as it is and just consume the allocated quantity, but you need to create another physical measure to keep these consumed quantities, or use our predefined measure `@iv`.`@consumed`.

#### <a name="consume-to-soft-reserved"></a>Consume as Soft Reserved

`Consume` API can also consume the allocated quantity to soft resevation measure directly, which means a `Consume` operation will reduce the allocated quantity and then do a soft reservation for these quantity, to use these you need to enable [Soft Reservation](inventory-visibility-reservations.md) Feature of Inventory Visibility firstly.

For example, you have set a soft reservation modifier(measure) as `iv`.`softreserved`, the availiable to reserve calcualted measure's formula is `iv`.`availiable_to_reserve` = `fno`.`onordered` - `iv`.`softreserved`.
When using with allocation feature, add `@iv`.`@allocated` to `iv`.`availiable_to_reserve`, the formula will be
`iv`.`availiable_to_reserve` = `fno`.`onordered` - `iv`.`softreserved` - `@iv`.`@allocated`.
Then also update the `@iv`.`@availiable_to_allocate` to same value.

When you want to consume 3 quantity and reserve them directly, you can make a call with request body:

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

Notice that in this request, the `iv`.`softreserved` has value `Addition`, not subtraction.
