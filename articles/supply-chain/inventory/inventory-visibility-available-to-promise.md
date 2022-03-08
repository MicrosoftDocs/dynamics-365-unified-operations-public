---
title: Inventory Visibility on-hand change schedule and available to promise
description: This topic describes how to schedule future on-hand changes and calculate available-to-promise (ATP) quantities.
author: yufeihuang
ms.date: 03/04/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2022-03-04
ms.dyn365.ops.version: 10.0.26
---

# Inventory Visibility on-hand change schedule and available to promise

[!include [banner](../includes/banner.md)]

This topic describes how to set up the *On-hand change schedule* feature to schedule future on-hand changes and calculate available-to-promise (ATP) quantities. ATP is the quantity of an item that is available and can be promised to a customer in the next period time, and making use of this calculation can greatly increase your order fulfillment capability.

For many manufactures, retailors, or sellers, just knowing the current on-hand isn't sufficient. Companies need full visibility of future availability. This future availability should consider future supply, future demand, and ATP.

## Turn on and set up the reservation feature

To turn on the *On-hand change schedule* feature, follow these steps:

1. Sign into Power Apps and open Inventory Visibility.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnhandChangeSchedule* feature.

To set up the ATP setting, follow these steps:

1. Open the **ATP setting** page.
1. Select the calculated measure's **Data source**, **Calculated measure** and its **Schedule period**. The **Schedule period** is integrates from 1 day to 7 days. <!-- KFM: Confirm that these bold words are UI text. Clarify "is integrates from 1 day to 7 days". -->

The calculated measure to calculate the ATP quantities should be defined before. For more information about calculated measure, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures)

Users can add multiple calculated measures to calculate ATP quantities, but the total modifiers used in these calculation measures should be less than 8.

## On-hand change schedule and ATP calculations

After turning on the *On-hand change schedule* feature, you must select a calculated measure to calculate on-hand and ATP, and set a period for the on-hand change schedule.

**ATP calculated measure** is a pre-defined calculated measure, the sum of its addition modifiers' quantities is supply quantities and the sum of its subtraction modifiers' quantities is demand quantities, **On-hand change = supply – demand**.

**Schedule period** is a period of time which allows users post scheduled on-hand change. And when users query products stock with time, they will get the scheduled on-hand changes and ATP each day in the period.

> [!IMPORTANT]
> The schedule period includes today, which means you can schedule the on-hand changes from today to the (schedule period - 1) days in the future.

After turn on the feature and set configuration, users can post on-hand changes with specific date in a ATP schedule period to plan to upcoming on-hand changes. But these changes are uncommitted and won't effected real on-hand quantities, if users want it real happen, they need use post on-hand to change it and revert the scheduled one's. Users can post scheduled on-hand changes from today to the next period of days and query them with ATP quantities. The ATP quantities are calculated by using the minimum projected on-hand quantities in the ATP calculation period. The ATP quantities for a specific day are the minimum projected on-hand quantities from the day to the end of this period, which means the remaining available on-hand quantities which can be promised at that day.

**Projected on-hand quantities** reflect the planed on-hand in the future, which equal current on-hand quantities add all scheduled on-hand change quantities from today to the date.

## Example

User sets a calculated measure **on-hand** as ATP calculated measure with schedule period 7. **On-hand = supply – demand**.

If today is 2022/02/01, current on-hand quantities is 20, and the user posts a scheduled demand with quantity 3 today(2022/02/01). The projected on-hand is 7. If the user queries ATP value at that time(2022/02/01), the ATP quantities in each day in this period is 17.

| Date | OnHand| Supply | Demand | ProjectOnHand | ATP |
| --- | --- | --- | --- | --- | --- |
| 2022/02/01 | 20 |  | 3 | 17 | 17 |
| 2022/02/02 | 20 |  |  | 17 | 17 |
| 2022/02/03 | 20 |  |  | 17 | 17 |
| 2022/02/04 | 20 |  |  | 17 | 17 |
| 2022/02/05 | 20 |  |  | 17 | 17 |
| 2022/02/06 | 20 |  |  | 17 | 17 |
| 2022/02/07 | 20 |  |  | 17 | 17 |

And then, the user posts a scheduled supply with quantity 10 the day after tomorrow(2022/02/02) and query the the quantities, the result will be like below:

| Date | OnHand| Supply | Demand | ProjectOnHand| ATP |
| --- | --- | --- | --- | --- | --- |
| 2022/02/01 | 20 |  | 3 | 17 | 17 |
| 2022/02/02 | 20 |  |  | 17 | 17 |
| 2022/02/03 | 20 | 10 |  | 27 | 27 |
| 2022/02/04 | 20 |  |  | 27 | 27 |
| 2022/02/05 | 20 |  |  | 27 | 27 |
| 2022/02/06 | 20 |  |  | 27 | 27 |
| 2022/02/07 | 20 |  |  | 27 | 27 |

Then, the users posts a scheduled demand with quantity 15 on 2022/02/04, posts a supply with quantity 1 on 2022/02/05, and posts a scheduled demand with quantity 3 on 2022/02/06 and query the quantities, the result will be like below.

| Date | OnHand| Supply | Demand | ProjectOnHand| ATP |
| --- | --- | --- | --- | --- | ---  |
| 2022/02/01 | 20 |  | 3 | 17 | 12 |
| 2022/02/02 | 20 |  |  | 17 | 12 |
| 2022/02/03 | 20 | 10 |  | 27 | 12 |
| 2022/02/04 | 20 |  | 15 | 12 | 12 |
| 2022/02/05 | 20 | 1 |  | 13 | 13 |
| 2022/02/06 | 20 | 3 |  | 16 | 16 |
| 2022/02/07 | 20 |  |  | 16 | 16 |

And if the demand order today is committed, the user should post a on-hand change request to increase the on-hand quantity from 10 to 13, and also post a schedule demand with quantity -3 to revert the scheduled change. The result should be like below table.

| Date | OnHand| Supply | Demand | ProjectOnHand| ATP |
| --- | --- | --- | --- | --- | --- |
| 2022/02/01 | 17 |  | 0 | 17 | 12 |
| 2022/02/02 | 17 |  |  | 17 | 12 |
| 2022/02/03 | 17 | 10 |  | 27 | 12 |
| 2022/02/04 | 17 |  | 15 | 12 | 12 |
| 2022/02/05 | 17 | 1 |  | 13 | 13 |
| 2022/02/06 | 17 | 3 |  | 16 | 16 |
| 2022/02/07 | 17 |  |  | 16 | 16 |

A day has passed and the current time has become 2022/02/02, the result will be like below table.

| Date | OnHand| Supply | Demand | ProjectOnHand| ATP |
| --- | --- | --- | --- | --- | --- |
| 2022/02/02 | 17 |  |  | 17 | 12 |
| 2022/02/03 | 17 | 10 |  | 27 | 12 |
| 2022/02/04 | 17 |  | 15 | 12 | 12 |
| 2022/02/05 | 17 | 1 |  | 13 | 13 |
| 2022/02/06 | 17 | 3 |  | 16 | 16 |
| 2022/02/07 | 17 |  |  | 16 | 16 |
| 2022/02/08 | 17 |  |  | 16 | 16 |

However, if two days passed and current time is 2022/02/04, the scheduled supply on 2022/02/03 has not be committed, the result will be like below table:

| Date | OnHand| Supply | Demand | ProjectOnHand| ATP |
| --- | --- | --- | --- | --- | --- |
| 2022/02/04 | 17 |  | 15 | 2 | 2 |
| 2022/02/05 | 17 | 1 |  | 3 | 3 |
| 2022/02/06 | 17 | 3 |  | 6 | 6 |
| 2022/02/07 | 17 |  |  | 6 | 6 |
| 2022/02/08 | 17 |  |  | 6 | 6 |
| 2022/02/09 | 17 |  |  | 6 | 6 |
| 2022/02/10 | 17 |  |  | 6 | 6 |

Scheduled on-hand changes will not influence actual on-hand.

The ATP quantity that is shown is always greater than or equal to 0 (zero). If the calculation returns a negative ATP quantity (for example, if the quantity that was previously promised exceeds the available quantity), the quantity is automatically set to 0.

## Call the on-hand change schedule API

On-hand change schedules are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as `/api/environment/{environment-ID}/on-hand/changeschedule`.

For a on-hand change schedule, the request body must contain an organization ID, a product ID, scheduled date and quantities-by date. The date should not be earlier than today and later than the end of this schedule period.

> [!NOTE]
> If the scheduled on-hand changes are committed or canceled, user needs to revert the schedule by setting the quantity to a negative value.

Here is an example of the request body, for reference.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/changeschedule

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

# Body
{
    "id": "id-bike-0001",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red",
        "SizeId": "small"
    },
    "quantityByDate":
    {
        "2022/02/04":
        {
            "pos":{
                "inbound": 10,
            },
        },
    },
}
```

And users can also post bulk requests to service's URL such as `/api/environment/{environment-ID}/on-hand/changeschedule`.

## Call on-hand change schedule and ATP Query API

Set **"QueryATP"** option as **true** to query scheduled on-hand changes and ATP results.
For more information about calculated measure, see [Reservation configuration](#x) <!--KFM: Provide link -->.

Here is an example of the request body, for reference.

```json
Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/changeschedule/bulk

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

[
    {
        "id": "id-bike-0001",
        "organizationId": "usmf",
        "productId": "Bike",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red",
            "SizeId": "small"
        },
        "quantityByDate":
        {
            "2022/02/04": // today
            {
                "pos":{
                    "inbound": 10,
                },
            },
        },
    },
    {
        "id": "id-bike-0001",
        "organizationId": "usmf",
        "productId": "Car",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red",
            "SizeId": "small"
        },
        "quantityByDate":
        {
            "2022/02/05":
            {
                "pos":{
                    "outbound": 10,
                },
            },
        },
    }
]
```

Here is an example of the request body, for reference.

## Query scheduled on-hand change and ATP results

Here is an example of the request body, for reference.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/reserve

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

# Body
{
    "id": "id-bike-0001",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "ColorId": "Red",
        "SizeId": "small"
    },
    "quantityDataSource": "iv",
    "modifier": "SoftReservOrdered",
    "quantity": 1,
    "ifCheckAvailForReserv": true
}
```
