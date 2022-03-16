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

## <a name="setup"></a>Enable and set up the features

Before you can use ATP, you must set up one or more calculated measures to calculate the ATP quantities, turn on the feature in Power Apps, and make ATP settings in Power Apps.

### Set up calculated measures for ATP quantities

The *ATP calculated measure* is a pre-defined calculated measure, typically used to find the currently available on-hand quantity. The sum of its addition modifier quantities is the supply quantity and the sum of its subtraction modifier quantities is the demand quantity.

You can add multiple calculated measures to calculate ATP quantities, but the total number of modifiers used across all ATP calculated measures should be 8 or less.

For example, you might set up the following calculated measure.

- **On-hand-available** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound) – (Reservphysical + SoftReservePhysical + Outbound)

The previous measure can be understood as follows:

- **On-hand-available** = Inbound – Outbound<br>Where:
  - **Inbound** = PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound
  - **Outbound** = ReservPhysical + SoftReservePhysical + Outbound

For more information about calculated measures, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures)

### Turn on the On-hand change schedule feature and set ATP options

Turn on the *On-hand change schedule* feature in Power Apps and set up the ATP options using the following steps:

1. Sign into Power Apps and open Inventory Visibility.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnhandChangeSchedule* feature.
1. Open the **ATP Setting** tab.
1. When you query Inventory Visibility, it will provide a result that includes each of the ATP calculated measures that you add here. Select **Add** to add a new calculated measure to use for ATP.
1. Make the following settings:
    - **Data Source** – Select the data source associated with your calculated measure.
    - **Calculated Measure** – Select the calculated measure (associated with the selected **Data Source**) that you want to use to find the currently available on-hand quantity.
    - **Schedule Period** – Enter the number of days for which users can view and submit scheduled on-hand changes when using the selected **Calculated Measure**. When users query for stock information, they will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in this period, starting with today. Select an integer between 1 and 7.

    > [!IMPORTANT]
    > The **Schedule Period** includes today, which means users can schedule on-hand changes to occur an time from today (the day the change is submitted) to (schedule period – 1) days in the future.

1. Select **Save**.
1. Repeat from step 5 until you have added all of the calculated measures you need for ATP.

## How the on-hand change schedule and ATP calculations work

You can submit an *on-hand change schedule* (which establishes expected dates and quantities of scheduled on-hand changes) to Inventory Visibility, provided the dates are within the period defined by the **Schedule period** setting (see [Enable and set up the features](#setup)). When you query for stock information, they will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in this period.

Scheduled changes are initially uncommitted and therefore won't affect your "real" on-hand quantities in the system. To commit the changes, you must submit an *on-hand change event* (which updates the actual available on-hand quantity) and then *revert* the scheduled change (by submitting an *on-hand change schedule* for a matching negative quantity).

For example, if you place an order for 10 bikes, which you expect to arrive tomorrow, you could than submit an on-hand change *schedule* with an **Inbound** quantity of *10* dated for tomorrow. The next day, when the order arrives, you add the bikes to your physical on-hand inventory and must therefore commit the change to your system to update the actual on-hand quantity. To commit the change, submit an *on-hand change event* with an **Inbound** quantity of *10*, and then revert the scheduled change by submitting an *on-hand change schedule* with an **Inbound** quantity of *-10*.

When you query Inventory Visibility for on-hand and ATP quantities, it returns the following information for each day in the schedule period:

- **Date** – The date for which the result applies.
- **On-hand quantity** – The actual on-hand quantity for the specified date. This calculation made according to the *ATP calculated measure* configured for Inventory Visibility.
- **Scheduled inbound** – The total sum of all scheduled incoming quantities that haven't become physically available for immediate consumption or shipment as of the specified **Date**.
- **Scheduled outbound** – The total sum of all scheduled outbound quantities that haven't been consumed or shipped as of the specified **Date**.
- **ATP quantity** – The minimum projected on-hand quantity available from the specified **Date** until the end of the schedule period, including all scheduled quantity adjustments. This is the maximum quantity that can be promised today for delivery or consumption on that day.

For example, if today is 2022/02/01 and the schedule period is 7, users can submit scheduled on-hand changes expected to occur from 2022/02/01 to 2022/02/07, and the ATP quantity for (for example) 2022/02/03 is calculated based on the on-hand quantity for that day and the scheduled quantities from 2022/02/03 to 2022/02/07.

## Example

The following example shows how a series of scheduled quantity changes affects the on-hand and ATP quantities reported by Inventory Visibility. It also shows how to commit a scheduled change and how that affects the results, and what can happen if you don't commit a scheduled change.

The example results here show a value for *projected on-hand*, which incorporates all scheduled updates for illustration purposes, but which is not actually reported when you query Inventory Visibility.

1. Your system is set up with the following settings on the **ATP setting** page in Power Apps:
    - **ATP calculated measure** – You have a calculated measure called *On-hand* (calculated as *On-hand = Inbound – Outbound*), and that measure is selected here.
    - **Schedule period** – Set to *7*.

1. The following conditions also apply:
    - Today is 2022/02/01.
    - Current on-hand quantity is 20.

1. You submit to Inventory Visibility a scheduled outbound quantity of 3 for today (2022/02/01). Therefore, the projected on-hand quantity is 17.The result is as follows.

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 |  |  | 17 | 17 |
    | 2022/02/04 | 20 |  |  | 17 | 17 |
    | 2022/02/05 | 20 |  |  | 17 | 17 |
    | 2022/02/06 | 20 |  |  | 17 | 17 |
    | 2022/02/07 | 20 |  |  | 17 | 17 |

1. Today (2022/02/01), you submit a scheduled inbound quantity of 10 for 2022/02/02. The result is as follows.

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 | 10 |  | 27 | 27 |
    | 2022/02/04 | 20 |  |  | 27 | 27 |
    | 2022/02/05 | 20 |  |  | 27 | 27 |
    | 2022/02/06 | 20 |  |  | 27 | 27 |
    | 2022/02/07 | 20 |  |  | 27 | 27 |

1. Today (2022/02/01), you submit the following scheduled quantity changes:
    - Outbound quantity of 15 for 2022/02/04
    - Inbound quantity of 1 for 2022/02/05
    - Outbound quantity of 3 for 2022/02/06

    The result is as follows.

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | ---  |
    | 2022/02/01 | 20 |  | 3 | 17 | 12 |
    | 2022/02/02 | 20 |  |  | 17 | 12 |
    | 2022/02/03 | 20 | 10 |  | 27 | 12 |
    | 2022/02/04 | 20 |  | 15 | 12 | 12 |
    | 2022/02/05 | 20 | 1 |  | 13 | 13 |
    | 2022/02/06 | 20 | 3 |  | 16 | 16 |
    | 2022/02/07 | 20 |  |  | 16 | 16 |

1. You ship the scheduled outbound quantity of 3 on 2022/02/01, so you must commit this change so it is reflected in your actual on-hand quantity. To commit the change, submit an *on-hand change event* with an outbound quantity of *3*, and then revert the scheduled change by submitting an *on-hand change schedule* with an outbound quantity of *-3*. The result is as follows.

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 17 |  | 0 | 17 | 12 |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |

1. The next day (2022/02/02), the schedule period shifts one day forward and the results are as follows.

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |
    | 2022/02/08 | 17 |  |  | 16 | 16 |

    However, two days after that (on 2022/02/04), the inbound quantity of 10 scheduled for 2022/02/03 still hasn't arrived, which produces the following results:

    | Date | On-hand | Scheduled inbound | Scheduled outbound | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/04 | 17 |  | 15 | 2 | 2 |
    | 2022/02/05 | 17 | 1 |  | 3 | 3 |
    | 2022/02/06 | 17 | 3 |  | 6 | 6 |
    | 2022/02/07 | 17 |  |  | 6 | 6 |
    | 2022/02/08 | 17 |  |  | 6 | 6 |
    | 2022/02/09 | 17 |  |  | 6 | 6 |
    | 2022/02/10 | 17 |  |  | 6 | 6 |

    As you can see, the scheduled (but not committed) on-hand changes do not influence actual on-hand.

## Submit change schedules, change events, and ATP queries through the API

You can use the following API URLs to submit on-hand change schedules, change events, and queries.

| Path | Method | Description |
| --- | --- | --- |
| `/api/environment/{environment-ID}/on-hand/changeschedule` | `POST` | Create one scheduled on-hand change. |
| `/api/environment/{environment-ID}/on-hand/changeschedule/bulk` | `POST` | Create multiple scheduled on-hand changes. |
| `/api/environment/{environmentId}/onhand` | `POST` | Create one on-hand change event |
| `/api/environment/{environmentId}/onhand/bulk` | `POST` | Create multiple change events |
| `/api/environment/{environment-ID}/onhand/indexquery` | `POST` | Query by using the `POST` method. |
| `/api/environment/{environment-ID}/onhand` | `GET` | Query by using the `GET` method. |

For more information, see [Inventory Visibility public APIs](inventory-visibility-api.md).

### Submit on-hand change schedules

On-hand change schedules are made by submitting a `POST` request to the relevant Inventory Visibility service URL (as listed previously). You can also submit bulk requests.

To submit an on-hand change schedule, the request body must contain an organization ID, a product ID, scheduled date, and quantities by date. The scheduled date must be between today and the end of the current schedule period.

#### Example request body containing a single update

Here is an example of a request body containing a single update.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/changeschedule

# Method
Post

# Header
# Replace {access_token} with the one from your security service
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
        "SizeId": "Small"
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

#### Example request body containing multiple (bulk) updates

Here is an example of a request body containing multiple (bulk) updates.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/changeschedule/bulk

# Method
Post

# Header
# replace {access_token} with the one from your security service
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
            "SizeId": "Small"
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
            "SizeId": "Small"
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

### Submit on-hand change events

On-hand change events are made by submitting a `POST` request to the relevant Inventory Visibility service URL (as listed previously). You can also submit bulk requests.

To submit an on-hand change event, the request body must contain an organization ID, a product ID, scheduled date, and quantities by date. The scheduled date must be between today and the end of the current schedule period.

Note that the event request uses `quantities` instead of `quantityByDate`.

Here is an example of a request body containing a single event.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand

# Method
Post

# Header
# Replace {access_token} with the one from your security service
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
        "SizeId": "Big",
        "ColorId": "Red",
    },
    "quantities": {
        "pos": {
            "inbound": 10.0
        }
    }
}
```

## Query the scheduled on-hand changes and ATP results

You can query scheduled on-hand changes and ATP results by submitting either a `POST` or `GET` request to the appropriate API URL (as listed previously).

In your request, set `QueryATP` to *true* if you want to query scheduled on-hand changes and ATP results.

- If your submitting using the `GET` method, set this parameter in the URL.
- If your submitting using the `POST` method, set this parameter in the request body

> [!NOTE]
> Whether `returnNegative` is set true or false, the result will return negative values when query the scheduled on-hand changes and ATP results. Because if only demand orders are scheduled or supply quantities are less than demand quantities, the scheduled on-hand change quantities will be negative. Without returning this value, the result will be very confusing. <!-- KFM: add a link to the API topic -->

### POST method example

Here is an example of how to create a request body to be submitted to Inventory Visibility using the `POST` method.

```json
# Url
# replace {RegionShortName} and {EnvironmentId} with your value
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/on-hand/indexquery

# Method
Post

# Header
# replace {access_token} with the one from your security service
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

### GET method example

Here is an example of how to create a request URL as a `GET` request.

```txt
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand?organizationId=usmf&productId=Bike&SiteId=1&groupBy=ColorId,SizeId&returnNegative=true&QueryATP=true
```

This result of this `GET` request is exactly the same as the example `POST` request provided earlier.

### Query result example

Either of the query examples provides previously might result in the following reply. For this example, the system is configured as follows.

- **ATP calculated measure:** *iv.onhand = pos.inbound – pos.outbound*
- **Schedule period:** *7*

Here is an example of the reply body.

```json
[
    {
        "quantitiesByDate": {
            "2022-02-02T00:00:00": {
                "pos": {
                    "outbound": 5,
                    "inbound": 0,
                },
                "iv": {
                    "onhand": -5,
                },
            },
            "2022-02-06T00:00:00": {
                "pos": {
                    "inbound": 7,
                    "outbound": 0,
                },
                "iv": {
                    "onhand": 7,
                },
            }
        },
        "atpQuantities": {
            "2022-02-01T00:00:00Z": {
                "iv": {
                    "onhand": 5.0
                }
            },
            "2022-02-02T00:00:00Z": {
                "iv": {
                    "onhand": 5.0
                }
            },
            "2022-02-03T00:00:00Z": {
                "iv": {
                    "onhand": 5.0
                }
            },
            "2022-02-04T00:00:00Z": {
                "iv": {
                    "onhand": 5.0
                }
            },
            "2022-02-05T00:00:00Z": {
                "iv": {
                    "onhand": 5.0
                }
            },
            "2022-02-06T00:00:00Z": {
                "iv": {
                    "onhand": 12.0
                }
            },
            "2022-02-07T00:00:00Z": {
                "iv": {
                    "onhand": 12.0
                }
            }
        },
        "productId": "Bike ",
        "dimensions": {
            "ColorId": "Red",
            "SizeId": "Big",
            "siteid": "1",
            "locationid": "11"
        },
        "quantities": {
            "pos": {
                "inbound": 10.0,
                "outbound": 0,
            },
            "iv": {
                "onhand": 10.0,
            }
        }
    }
]
```

