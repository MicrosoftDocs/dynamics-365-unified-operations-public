# Inventory Visibility Onhand Change Schedule and ATP
This topic describes how to set up the "Onhand Change Schedule" feature to schedule onhand changes in the future and calculate ATP(Available to Promise) quantities.
For many manufactures, retailors or sellers knowing just current on-hand is not sufficient. Companies need to be able to have visibility on future availability. This future availability should consider future supply, demand and ATP. ATP (available-to-promise) is the quantity of an item that is available and can be promised to a customer in the next period time, can greatly increase your order fulfillment capability.


## Onhand change schedule and ATP calculations
After turn on the "Onhand Change Schedule" feature, users need to select a calculated measure to calculate onhand and ATP and a schedule period for onhand change schedule.

**ATP calculated measure** is a pre-definedd calculated measure, the sum of its addition modifiers' quantities is supply quantities and the sum of its substraction modifiers' quantities is demand quantities, onhand change = supply - demand.

**Schedule period** is a period of time which allows users post scheduled onhand change. And when users query products stock with time, they will get the scheduled onhand changes and ATP each day in the period. ***Notice: The period includes today, which means users can schedule the onhand changes from today to the (schedule period - 1) days in the future.**

After turn on the feature and set configuration, users can post onhand changes with specific date in a ATP schedule period to plan to upcoming onhand changes. But these changes are uncommited and won't effected real onhand quantities, if users want it real happen, they need use post onhand to change it and revert the scheduled one's. Users can post scheduled onhand changes from today to the next period of days and query them with ATP quantities. The ATP quantities are calculated by using the miniumum projected onhand quantities in the ATP calculatio period. The ATP quantities for a specific day are the minimun projected onhand quantities from the day to the end of this period, which means the remaining available onhand quantities which can be promised at that day.

**"Projected onhand quantities"** reflect the planed onhand in the future, which equal current onhand quantities add all scheduled onhand change quantities from today to the date.

## Example

User sets a calculated measure ***onhand*** as ATP calculated measure with schedule period 7. ***Onhand = supply - demand***.
If today is 2022/02/01, current onhand quantities is 20, and the user posts a scheduled demand with quantity 3 today(2022/02/01). The projected onhand is 7. If the user queries ATP value at that time(2022/02/01), the ATP quantities in each day in this period is 17.
|Date       |OnHand|Supply  |Demand |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----:  |:----:       |:----:|
|2022/02/01 |20    |       |3       |17           |17    |
|2022/02/02 |20    |       |        |17           |17    |
|2022/02/03 |20    |       |        |17           |17    |
|2022/02/04 |20    |       |        |17           |17    |
|2022/02/05 |20    |       |        |17           |17    |
|2022/02/06 |20    |       |        |17           |17    |
|2022/02/07 |20    |       |        |17           |17    |

And then, the user posts a scheduled supply with quantity 10 the day after tomorrow(2022/02/02) and query the the quantities, the result will be like below:
|Date       |OnHand|Supply |Demand |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----: |:----:       |:----:|
|2022/02/01 |20    |       |3      |17           |17    |
|2022/02/02 |20    |       |       |17           |17    |
|2022/02/03 |20    |10     |       |27           |27    |
|2022/02/04 |20    |       |       |27           |27    |
|2022/02/05 |20    |       |       |27           |27    |
|2022/02/06 |20    |       |       |27           |27    |
|2022/02/07 |20    |       |       |27           |27    |

Then, the users posts a scheduled demand with quantitiy 15 on 2022/02/04, posts a supply with quantity 1 on 2022/02/05, and posts a scheduled demand with quantity 3 on 2022/02/06 and query the quantities, the result will be like below.
|Date       |OnHand|Supply |Demand  |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----:  |:----:       |:----:|
|2022/02/01 |20    |       |3       |17           |12    |
|2022/02/02 |20    |       |        |17           |12    |
|2022/02/03 |20    |10     |        |27           |12    |
|2022/02/04 |20    |       |15      |12           |12    |
|2022/02/05 |20    |1      |        |13           |13    |
|2022/02/06 |20    |3      |        |16           |16    |
|2022/02/07 |20    |       |        |16           |16    |

And if the demand order today is committed, the user should post a onhand change request to increase the onhand quantity from 10 to 13, and also post a schedule demand with quantity -3 to revert the scheduled change. The result should be like below table.
|Date       |OnHand|Supply |Demand  |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----:  |:----:       |:----:|
|2022/02/01 |17    |       |0       |17           |12    |
|2022/02/02 |17    |       |        |17           |12    |
|2022/02/03 |17    |10     |        |27           |12    |
|2022/02/04 |17    |       |15      |12           |12    |
|2022/02/05 |17    |1      |        |13           |13    |
|2022/02/06 |17    |3      |        |16           |16    |
|2022/02/07 |17    |       |        |16           |16    |

A day has passed and the current time has become 2022/02/02, the result wil be like below table.
|Date       |OnHand|Supply |Demand  |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----:  |:----:       |:----:|
|2022/02/02 |17    |       |        |17           |12    |
|2022/02/03 |17    |10     |        |27           |12    |
|2022/02/04 |17    |       |15      |12           |12    |
|2022/02/05 |17    |1      |        |13           |13    |
|2022/02/06 |17    |3      |        |16           |16    |
|2022/02/07 |17    |       |        |16           |16    |
|2022/02/08 |17    |       |        |16           |16    |

However, if two days passed and current time is 2022/02/04, the scheduled supply on 2022/02/03 has not be committd, the result will be like below table:
|Date       |OnHand|Supply |Demand  |ProjectOnHand|ATP   |
|:----:     |:----:|:-----:|:----:  |:----:       |:----:|
|2022/02/04 |17    |       |15      |2            |2     |
|2022/02/05 |17    |1      |        |3            |3     |
|2022/02/06 |17    |3      |        |6            |6     |
|2022/02/07 |17    |       |        |6            |6     |
|2022/02/08 |17    |       |        |6            |6     |
|2022/02/09 |17    |       |        |6            |6     |
|2022/02/10 |17    |       |        |6            |6     |

Scheduled onhand changes will not influence actual onhand.



The ATP quantity that is shown is always greater than or equal to 0 (zero). If the calculation returns a negative ATP quantity (for example, if the quantity that was previously promised exceeds the available quantity), the quantity is automatically set to 0.

## Turn on and set up the reservation feature
To turn on the "Onhand change schedule" feature, follow these steps.
1. Sign into Power Apps and open Inventory Visibility.
2. Open the Configuration page.
3. On the Feature Management tab, turn on the "OnhandChangeSchedule" feature.

To set up the ATP setting, follow these steps,

1. Open the ATP setting page.
2. Select the calculated measure's Data Source, Calculated measure and its schedule period. The schedule period is integrates from 1 day to 7 days.

The calculated measure to calcualte the ATP quantities should be defined before. For more information about calcualted measure, see Configuration Inventory Visibility -> [Calculated measures](https://docs.microsoft.com/en-us/dynamics365/supply-chain/inventory/inventory-visibility-configuration#calculated-measures)

Users can add mutiple calculated measures to calculate ATP quantities, but the total modifiers used in these calculation measures should be less than 8.

## Call the onhand change schedule API
Onhand change schedules are made in the Inventory Visibility service by submitting a POST request to the service's URL, such as /api/environment/{environment-ID}/onhand/changeschedule.

For a onhand change schedule, the request body must contain an organization ID, a product ID, scheduled date and quantitiesbydate. The date should not be ealier than today and later than the end of this schedule period.

***Notice: If the scheduled onhand changes are committed or canceled, user needs to revert the schedule by setting the quantity to a negative value.***

Here is an example of the request body, for reference.
```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand/changeschedule

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

And users can also post bulk requests to service's URL such as /api/environment/{environment-ID}/onhand/changeschedule.




## Call onhand change schedule and ATP Query API
Set **"QueryATP"** option as **true** to query scheduled onhand changes and ATP results.
For more information about calcualted measure, see Reservation configuration.

Here is an example of the request body, for reference.

```json#
Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand/changeschedule/bulk

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

## Query scheduled onhand change and ATP results


Here is an example of the request body, for reference.
```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand/reserve

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
