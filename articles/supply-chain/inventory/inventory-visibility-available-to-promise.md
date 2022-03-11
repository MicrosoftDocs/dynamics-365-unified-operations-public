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

This topic describes how to set up the *On-hand change schedule* feature to schedule future on-hand changes and calculate available-to-promise (ATP) quantities. ATP is the quantity of an item that is available and can be promised to a customer in the next period of time, and making use of this calculation can greatly increase your order fulfillment capability.

For many manufactures, retailors, or sellers, just knowing what is currently on-hand isn't sufficient. Companies need full visibility of future availability. This future availability should consider future supply, future demand, and ATP.

## Prerequisites

Before you can use ATP, you must set up a calculated measure for ATP quantities, turn on the feature in Power Apps, and make ATP settings in Power Apps.
 <!-- yirli: order and more than one-->

### Set up a calculated measure for ATP quantities

Before you can use ATP, you must set up one or more  calculated measure to calculate the ATP quantities. You can add multiple calculated measures to calculate ATP quantities, but the total modifiers used in these calculated measures should be less than 8.

For more information about calculated measures, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures)

### Turn on and set up the On-hand change schedule feature

Turn on the *On-hand change schedule* feature in Power Apps using the following steps:

1. Sign into Power Apps and open Inventory Visibility.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnhandChangeSchedule* feature.

Set up your ATP settings by following these steps:

1. Open the **ATP setting** page.
1. Select the calculated measure's **Data Source**, **Calculated Measure** and its **Schedule Period** and save. The **Schedule Period** is an integer from 1 day to 7 days.

<!-- KFM: Where are these settings? Add navigation instructions. -->
<!-- reply from yirli: The aboving is the settings on UI, and I think the deleted sentence is duplicat with the introduction in the top paragraph -->

## On-hand change schedule and ATP calculations
<!-- Questions from yirli: How to name this chapter to introduce how this feature work? -->
<!-- Questions from yirli: I have no idea that how to insert the concept of those explanation for **ATP calculated measure** ，**Schedule period** and **Projected on-hand quantities**  -->

<!--**ATP calculated measure** is a pre-defined calculated measure. The sum of its addition modifier quantities is the supply quantity and the sum of its subtraction modifier quantities is the demand quantity, **On-hand change = supply – demand**. -->

<!-- KFM: The purpose and meaning of this paragraph aren't clear. What is the user supposed to do here? What does the formula mean? -->

<!-- reply from yirli: I insert it to the belowing paragraph, but I'm not quite sure if this is less readable.-->

<!-- **Schedule period** is the period of time during which users can post scheduled on-hand changes. When users query products stock with time, they will get the scheduled on-hand changes and ATP for each day in the period. -->
<!-- KFM: The purpose and meaning of this paragraph aren't clear. What is the user supposed to do here? What does it mean to "query products stock with time"? -->
<!-- reply from yirli: I insert it to the belowing paragraph, but I'm not quite sure if this is less readable. Or I should add a link and explan them seperatly? -->

> [!IMPORTANT]
> The schedule period includes today, which means you can schedule the on-hand changes from today to (schedule period – 1) days in the future.

Users can post on-hand changes with a specific date during an ATP schedule period to plan upcoming on-hand changes. **Schedule period** is the period of time during which users can post scheduled on-hand changes. When users query products stock with time, they will get the scheduled on-hand changes and ATP for each day in the period.

However, these changes are initially uncommitted and won't effected real on-hand quantities. To commit the changes, users must post on-hand to change it and revert the scheduled one's. For example, if users commit an schedule on-hand change with ***inbound*** 10, they should post onhand event with  ***inbound*** 10, and post onhand change schedule with ***inbound*** -10.  
<!-- KFM: The meaning of this sentence isn't clear. -->
<!-- Reply by yirli: Does it became clear to add examples? -->

Users can post scheduled on-hand changes from today to the future ***(scheduled-period - 1)*** days and query them with ATP quantities. The ATP quantities a specific date are calculated by using the minimum projected on-hand quantities from the date to the end of this period. **Projected on-hand quantities** reflect the planed on-hand in the future, which equal current on-hand quantities add all scheduled on-hand change quantities from today to the date. And ***on-hand*** is calculated by current quantities and ***planed on-onhand*** is calculated by schedule quantities change by using same ***ATP calculated measure***. **ATP calculated measure** is a pre-defined calculated measure. The sum of its addition modifier quantities is the supply quantity and the sum of its subtraction modifier quantities is the demand quantity, **On-hand change = supply – demand**.

For example, if today is 2022/02/01, the schedule period is 7, users can post scheduled on-hand change from 2022/02/01 to 2022/02/07. And the ATP quantities on 2022/02/03 are are calculated by using the minimum projected on-hand quantities from 2022/02/03 to 2022/02/07. <!-- KFM: Is this the same as the "Schedule period" mentioned above? If so, we should use the same term. --> <!-- Reply by yirli: Does it became clear to add examples? --> The ATP quantities for a specific day are the minimum projected on-hand quantities that are available from that day until the end of this period, which means that these are the maximum quantities that can be promised on that day.

## Example

1. Your system is set up with the following settings:
    - You have a calculated measure called *On-hand*(On-hand = supply – demand) and have set it as the **ATP calculated measure**.
  <!-- KFM: Why is this formula here? Is it supposed to be the same as the similar formula given earlier? -->
  <!-- PEPLY from yirli: Not exactly, the formula before is a concept that on-hand = supply - demand. But the customer can set its' own calculated measure name with different element of formula, like **onhand-available**(onhand-available = PhysicalInvent + onhand + unrestricted + qualityinspection + inbound - reservphysical - softreservephysical -outbound), for this calculated measure, the **onhand** is ***onhand-available***, **supply** is  ***PhysicalInvent + onhand + unrestricted + qualityinspection + inbound***, and **demand** is ***reservphysical + softreservephysical + outbound***. We set this formula to simply the example by asummming there is a calculated measure named **on-hand**, and physical measures named **sypply** and **demand**. Or Should I use **onhand = inbound - outboud** to distinguish them。-->
    - **Schedule period** is set to *7*.

1. The following conditions also apply:
    - Today is 2022/02/01.
    - Current on-hand quantity is 20.

1. You post a scheduled demand with a quantity of 3 for today (2022/02/01). Therefore, the projected on-hand quantity is 17.

1. You query the ATP value and find that the ATP quantity for each day in this period is 17, as shown in the following table.

    | Date | On-hand| Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 |  |  | 17 | 17 |
    | 2022/02/04 | 20 |  |  | 17 | 17 |
    | 2022/02/05 | 20 |  |  | 17 | 17 |
    | 2022/02/06 | 20 |  |  | 17 | 17 |
    | 2022/02/07 | 20 |  |  | 17 | 17 |

1. Today (2022/02/01), you post a scheduled supply with quantity 10 for 2022/02/02. Then you query the quantities, and receive the following information. <!--KFM: Throughout this procedure, it isn't clear whether the user is acting on the day specified or acting "today" but specifying the date specified. ->
   <!-- Reply by yirli: I try to explain that "acting "today" but specifying the date specified", could you please give me some suggestions to make it clear?-->

    | Date | On-hand| Supply | Demand | Projected on-hand| ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 | 10 |  | 27 | 27 |
    | 2022/02/04 | 20 |  |  | 27 | 27 |
    | 2022/02/05 | 20 |  |  | 27 | 27 |
    | 2022/02/06 | 20 |  |  | 27 | 27 |
    | 2022/02/07 | 20 |  |  | 27 | 27 |

1. Today (2022/02/01), you make the following postings for the following days:
    - Post scheduled demand with quantity 15 for 2022/02/04
    - Post supply with quantity 1 for 2022/02/05
    - Post scheduled demand with quantity 3 for 2022/02/06

    Then you query the quantities and receive the following results:

    | Date | On-hand| Supply | Demand | Projected on-hand| ATP |
    | --- | --- | --- | --- | --- | ---  |
    | 2022/02/01 | 20 |  | 3 | 17 | 12 |
    | 2022/02/02 | 20 |  |  | 17 | 12 |
    | 2022/02/03 | 20 | 10 |  | 27 | 12 |
    | 2022/02/04 | 20 |  | 15 | 12 | 12 |
    | 2022/02/05 | 20 | 1 |  | 13 | 13 |
    | 2022/02/06 | 20 | 3 |  | 16 | 16 |
    | 2022/02/07 | 20 |  |  | 16 | 16 |

1. If the demand order for today (2022/02/01) has been committed <!--KFM: Which demand order? Committed by whom/when? --><!-- The demand 3 on 2022/02/01, which is line 1, colomn 4. It should be committed by customer themself, but I am wondering that there may be the situation that the customer has his/her partner and the order is committed by them. So I add the specific date, will it be clearer? -->, you should post an on-hand change request to increase the on-hand quantity from 10 to 13, and also post a scheduled demand with quantity -3 to revert the scheduled change. The result is as follows.

    | Date | On-hand| Supply | Demand | Projected on-hand| ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 17 |  | 0 | 17 | 12 |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |

1. The next day (2022/02/02), the result becomes that shown in the following table.

    | Date | On-hand| Supply | Demand | Projected on-hand| ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |
    | 2022/02/08 | 17 |  |  | 16 | 16 |

    However, two days after that (on 2022/02/04), the supply scheduled for 2022/02/03 still hasn't been committed, which produces the following results:

    | Date | On-hand| Supply | Demand | Projected on-hand| ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/04 | 17 |  | 15 | 2 | 2 |
    | 2022/02/05 | 17 | 1 |  | 3 | 3 |
    | 2022/02/06 | 17 | 3 |  | 6 | 6 |
    | 2022/02/07 | 17 |  |  | 6 | 6 |
    | 2022/02/08 | 17 |  |  | 6 | 6 |
    | 2022/02/09 | 17 |  |  | 6 | 6 |
    | 2022/02/10 | 17 |  |  | 6 | 6 |

    Scheduled on-hand changes will not influence actual on-hand.
    <!--KFM: How is the connected to the rest of this step/procedure? -->
    <!-- Reply by yirli: I did not really understand this comment. The aboving chapter explain how ATP works by exmaples, and the following step introduces how to use this feature by calling ATP.-->

## Call the on-hand change schedule API

Users can use the following API to posting on-hand change schedules and query results.

| Path                                                           | Method | Description                              |
| ---                                                            | ---   | ---                                       |
| /api/environment/{environment-ID}/on-hand/changeschedule     | Post  |Create one scheduled on-hand change        |
| /api/environment/{environment-ID}/on-hand/changeschedule/bulk| Post  |Create multiple scheduled on-hand changes  |
| /api/environment/{environment-ID}/onhand/indexquery          | Post  |Query by using the post method             |
| /api/environment/{environment-ID}/onhand                     | Get   |Query by using the get method              |

### Post on-hand change schedules

On-hand change schedules are made by submitting a POST request to the Inventory Visibility service URL (which resembles `/api/environment/{environment-ID}/on-hand/changeschedule`). You can also post bulk requests.

For an on-hand change schedule, the request body must contain an organization ID, a product ID, scheduled date, and quantities by date. The scheduled date must be between today and the end of the current schedule period.

> [!NOTE]
> If the scheduled on-hand changes are committed or canceled, you must revert the schedule by setting the quantity to a negative value.

Here is an example of the request body.

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
        "2022/02/01": // today
        {
            "pos":{
                "inbound": 10,
            },
        },
    },
}
```

And users can also post bulk requests to service's URL such as `/api/environment/{environment-ID}/onhand/changeschedule/bulk`.

Here is an example of the request body.

```json
# Url
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
            "2022/02/01": // today
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

## Query the scheduled on-hand changes and ATP results

Users can query scheduled on-hand changes and ATP results from both post method `/api/environment/{environment-ID}/onhand/indexquery` and get mothod `/api/environment/{environment-ID}/onhand`.

Set **"QueryATP"** option as **true** to query scheduled on-hand changes and ATP results. For post method, it can be set in the request's body. And for get mehtod, it can be set in the url.
<!--KFM: Introduction is needed. What does this example show? -->
<!--KFM: Where is this setting? -->
<!--Reply by yirli: I am not sure it is clear enough-->

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/indexquery

# Method
Post

# Header
# replace {access_token} with the one get from security service
Api-version: "1.0"
Content-Type: "application/json"
Authorization: "Bearer {access_token}"

# Body
{
    "filters": {
        "organizationId": ["usmf"],
        "productId": ["Bike"],
        "siteId": ["1"],
        "LocationId": ["11"],
    },
    "groupByValues": ["ColorId", "SizeId"],
    "returnNegative": true,
    "QueryATP":true,
}
```

And here is an example of the get request body, for reference.

```json
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand?organizationId=usmf&productId=Bike&SiteId=1&groupBy=ColorId,SizeId&returnNegative=true&QueryATP=true
```

This get request is exactly the same as the sample post request provided earlier.
