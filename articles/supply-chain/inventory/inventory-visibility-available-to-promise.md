---
title: Inventory Visibility on-hand change schedules and available to promise
description: This topic describes how to schedule future on-hand changes and calculate available-to-promise (ATP) quantities.
author: yufeihuang
ms.date: 05/11/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2022-03-04
ms.dyn365.ops.version: 10.0.26
---

# Inventory Visibility on-hand change schedules and available to promise

[!include [banner](../includes/banner.md)]

This topic describes how to set up the *On-hand change schedule* feature to schedule future on-hand changes and calculate available-to-promise (ATP) quantities. ATP is the quantity of an item that is available and can be promised to a customer in the next period. Use of this calculation can greatly increase your order fulfillment capability.

For many manufacturers, retailers, or sellers, it isn't enough just to know what is currently on hand. They must have full visibility into future availability. This future availability should consider future supply, future demand, and ATP.

## <a name="setup"></a>Enable and set up the features

Before you can use ATP, you must set up one or more calculated measures to calculate the ATP quantities. You must also turn on the feature and configure ATP settings in Microsoft Power Apps.

### Set up calculated measures for ATP quantities

The *ATP calculated measure* is a predefined calculated measure that is typically used to find the on-hand quantity that is currently available. The *supply quantity* is the sum of quantities for those physical measures that have a modifier type of *addition*, and the *demand quantity* is the sum of quantities for those physical measures that have a modifier type of *subtraction*.

You can add multiple calculated measures to calculate multiple ATP quantities. However, the total number of distinct physical measures across all ATP calculated measures should be less than nine.

> [!IMPORTANT]
> A calculated measure is a composition of physical measures. Its formula can include only physical measures without duplicates, not calculated measures.

For example, you set up the following calculated measure:

**On-hand-available** = (*PhysicalInvent* + *OnHand* + *Unrestricted* + *QualityInspection* + *Inbound*) – (*ReservPhysical* + *SoftReservePhysical* + *Outbound*)

The sum (*PhysicalInvent* + *OnHand* + *Unrestricted* + *QualityInspection* + *Inbound*) represents supply, and the sum (*ReservPhysical* + *SoftReservePhysical* + *Outbound*) represents demand. Therefore, the calculated measure can be understood in the following way:

**On-hand-available** = *Supply* – *Demand*

You can add another calculated measure to calculate the **On-hand-physical** ATP quantity.

**On-hand-physical** = (*PhysicalInvent* + *OnHand* + *Unrestricted* + *QualityInspection* + *Inbound*) – (*Outbound*)

There are eight distinct physical measures across those two ATP calculated measures: *PhysicalInvent*, *OnHand*, *Unrestricted*, *QualityInspection*, *Inbound*, *ReservPhysical*, *SoftReservePhysical*, and *Outbound*.

For more information about calculated measures, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures).

### Turn on the On-hand change schedule feature and configure ATP settings

Follow these steps to turn on the *On-hand change schedule* feature in Power Apps and configure the ATP settings.

1. Sign in to Power Apps, and open Inventory Visibility.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *OnhandChangeSchedule* feature.
1. Select the **ATP Setting** tab.
1. When you query Inventory Visibility, it will provide a result that includes each ATP calculated measure that you add here. Select **Add** to add a new calculated measure for ATP.
1. Set the following fields:

    - **Data Source** – Select the data source that is associated with the calculated measure.
    - **Calculated Measure** – Select the calculated measure that is associated with the selected data source, and that you want to use to find the currently available on-hand quantity.
    - **Schedule Period** – Enter the number of days that users can view and submit scheduled on-hand changes when the selected calculated measure is used. Users who query for stock information will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in this period, starting with the current date. Select an integer between 1 and 7.

    > [!IMPORTANT]
    > The schedule period includes the current date. Therefore, users can schedule on-hand changes to occur any time from the current date (the day when the change is submitted) through (schedule period – 1) days in the future.

1. Select **Save**.
1. Repeat steps 5 through 7 until you've added all the calculated measures that you require for ATP.
1. When you've finished configuring all the required settings, select **Update Configuration**.

For more information, see [Complete and update the configuration](inventory-visibility-configuration.md).

## How the on-hand change schedule and ATP calculations work

An *on-hand change schedule* establishes expected dates and quantities of scheduled on-hand changes. You can submit an on-hand change schedule to Inventory Visibility, provided that the dates are within the period that is defined by the **Schedule period** setting (see the [Enable and set up the features](#setup) section). Users who query for stock information will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in that period.

Scheduled changes are initially uncommitted and therefore don't affect your actual on-hand quantities in the system. To commit the changes, you must submit an *on-hand change event*, which updates the actual available on-hand quantity. You must then revert the scheduled change by submitting an on-hand change schedule for a matching negative quantity.

For example, you place an order for 10 bikes and expect it to arrive tomorrow. Therefore, you submit an on-hand change schedule that has an inbound quantity of 10 and is dated for tomorrow. When the order arrives the next day, you add the bikes to your physical on-hand inventory. You must then commit the change to your system to update the actual on-hand quantity. To commit the change, you submit an on-hand change event that has an inbound quantity of 10. You then revert the scheduled change by submitting an on-hand change schedule that has an inbound quantity of -10.

When you query Inventory Visibility for on-hand and ATP quantities, it returns the following information for each day in the schedule period:

- **Date** – The date that the result applies to. The time zone is Coordinated Universal Time (UTC).
- **On-hand quantity** – The actual on-hand quantity for the specified date. This calculation is made according to the ATP calculated measure that is configured for Inventory Visibility.
- **Scheduled supply** – The sum of all scheduled inbound quantities that haven't become physically available for immediate consumption or shipment as of the specified date.
- **Scheduled demand** – The sum of all scheduled outbound quantities that haven't been consumed or shipped as of the specified date.
- **ATP quantity** – The minimum projected on-hand quantity that is available from the specified date through the end of the schedule period. This quantity includes all scheduled quantity adjustments. It's the maximum quantity that can be promised on the current date for delivery or consumption on that day.

For example, if the current date is February 1, 2022, and the schedule period is 7, users can submit scheduled on-hand changes that are expected to occur from February 1 through February 7, 2022. In this case, the ATP quantity for February 3, for example, is calculated based on the on-hand quantity for that day and the scheduled quantities from February 3 through February 7.

## Example

The following example shows how a series of scheduled quantity changes affects the on-hand and ATP quantities that Inventory Visibility reports. It also shows how to commit a scheduled change, how a committed schedule change affects the results, and what can occur if you don't commit a scheduled change.

The results in this example show a *projected on-hand* value. This value incorporates all scheduled updates for illustration purposes but isn't actually reported when you query Inventory Visibility.

1. The following settings are configured for your system on the **ATP setting** page in Power Apps:

    - **ATP calculated measure** – You have a calculated measure that is named *On-hand*. It's calculated as *On-hand = Supply – Demand*. You select that measure here.
    - **Schedule period** – You select *7*.

1. The following conditions also apply:

    - The current date is February 1, 2022.
    - The current on-hand quantity is 20.

1. For the current date (February 1, 2022), you submit a scheduled demand quantity of 3 to Inventory Visibility. Therefore, the projected on-hand quantity is 17. The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-01 | 20 | | 3 | 17 | 17 |
    | 2022-02-02 | 20 | | | 17 | 17 |
    | 2022-02-03 | 20 | | | 17 | 17 |
    | 2022-02-04 | 20 | | | 17 | 17 |
    | 2022-02-05 | 20 | | | 17 | 17 |
    | 2022-02-06 | 20 | | | 17 | 17 |
    | 2022-02-07 | 20 | | | 17 | 17 |

1. On the current date (February 1, 2022), you submit a scheduled supply quantity of 10 for February 3, 2022. The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-01 | 20 | | 3 | 17 | 17 |
    | 2022-02-02 | 20 | | | 17 | 17 |
    | 2022-02-03 | 20 | 10 | | 27 | 27 |
    | 2022-02-04 | 20 | | | 27 | 27 |
    | 2022-02-05 | 20 | | | 27 | 27 |
    | 2022-02-06 | 20 | | | 27 | 27 |
    | 2022-02-07 | 20 | | | 27 | 27 |

1. On the current date (February 1, 2022), you submit the following scheduled quantity changes:

    - Demand quantity of 15 for February 4, 2022
    - Supply quantity of 1 for February 5, 2022
    - Supply quantity of 3 for February 6, 2022

    The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-01 | 20 | | 3 | 17 | 12 |
    | 2022-02-02 | 20 | | | 17 | 12 |
    | 2022-02-03 | 20 | 10 | | 27 | 12 |
    | 2022-02-04 | 20 | | 15 | 12 | 12 |
    | 2022-02-05 | 20 | 1 | | 13 | 13 |
    | 2022-02-06 | 20 | 3 | | 16 | 16 |
    | 2022-02-07 | 20 | | | 16 | 16 |

1. On the current date (February 1, 2022), you ship the scheduled demand quantity of 3. Therefore, you must commit this change so that it's reflected in your actual on-hand quantity. To commit the change, you submit an on-hand change event that has an outbound quantity of 3. You then revert the scheduled change by submitting an on-hand change schedule that has an outbound quantity of -3. The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-01 | 17 | | 0 | 17 | 12 |
    | 2022-02-02 | 17 | | | 17 | 12 |
    | 2022-02-03 | 17 | 10 | | 27 | 12 |
    | 2022-02-04 | 17 | | 15 | 12 | 12 |
    | 2022-02-05 | 17 | 1 | | 13 | 13 |
    | 2022-02-06 | 17 | 3 | | 16 | 16 |
    | 2022-02-07 | 17 | | | 16 | 16 |

1. On the next day (February 2, 2022), the schedule period shifts forward by one day. The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-02 | 17 | | | 17 | 12 |
    | 2022-02-03 | 17 | 10 | | 27 | 12 |
    | 2022-02-04 | 17 | | 15 | 12 | 12 |
    | 2022-02-05 | 17 | 1 | | 13 | 13 |
    | 2022-02-06 | 17 | 3 | | 16 | 16 |
    | 2022-02-07 | 17 | | | 16 | 16 |
    | 2022-02-08 | 17 | | | 16 | 16 |

1. However, two days later (February 4, 2022), the supply quantity of 10 that was scheduled for February 3 still hasn't arrived. The following table shows the result.

    | Date | On-hand | Scheduled supply | Scheduled demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022-02-04 | 17 | | 15 | 2 | 2 |
    | 2022-02-05 | 17 | 1 | | 3 | 3 |
    | 2022-02-06 | 17 | 3 | | 6 | 6 |
    | 2022-02-07 | 17 | | | 6 | 6 |
    | 2022-02-08 | 17 | | | 6 | 6 |
    | 2022-02-09 | 17 | | | 6 | 6 |
    | 2022-02-10 | 17 | | | 6 | 6 |

    As you see, the scheduled (but not committed) on-hand changes don't affect the actual on-hand quantity.

## <a name="api-urls"></a>Submit change schedules, change events, and ATP queries through the API

You can use the following application programming interface (API) URLs to submit on-hand change schedules, change events, and queries.

| Path | Method | Description |
| --- | --- | --- |
| `/api/environment/{environmentId}/onhand/changeschedule` | `POST` | Create one scheduled on-hand change. |
| `/api/environment/{environmentId}/onhand/changeschedule/bulk` | `POST` | Create multiple scheduled on-hand changes. |
| `/api/environment/{environmentId}/onhand` | `POST` | Create one on-hand change event. |
| `/api/environment/{environmentId}/onhand/bulk` | `POST` | Create multiple change events. |
| `/api/environment/{environmentId}/onhand/indexquery` | `POST` | Query by using the `POST` method. |
| `/api/environment/{environmentId}/onhand` | `GET` | Query by using the `GET` method. |

For more information, see [Inventory Visibility public APIs](inventory-visibility-api.md).

### Create one on-hand change schedule

An on-hand change schedule is created by submitting a `POST` request to the relevant Inventory Visibility service URL (see the [Submit change schedules, change events, and ATP queries through the API](#api-urls) section). You can also submit bulk requests.

An on-hand change schedule can be created only if the scheduled date is between the current date and the end of the current schedule period. The datetime format should be *year-month-day* (for example, **2022-02-01**). The time format must be accurate only to the day.

This API creates a single on-hand change schedule.

```txt
Path:
    /api/environment/{environmentId}/onhand/changeschedule
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        id: string,
        organizationId: string,
        productId: string,
        dimensionDataSource: string, # optional
        dimensions: {
            [key:string]: string,
        },
        quantitiesByDate: {
            [datetime:datetime]: {
                [dataSourceName:string]: {
                    [key:string]: number,
                },
            },
        },
    }
```

The following example shows sample body content without `dimensionDataSource`.

```json
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
    "quantitiesByDate":
    {
        "2022-02-01": // today
        {
            "pos":{
                "inbound": 10
            }
        }
    }
}
```

### Create multiple on-hand change schedules

This API can create multiple records at the same time. The only differences between this API and the single-event API are the `Path` and `Body` values. For this API, `Body` provides an array of records. The maximum number of records is 512. Therefore, the on-hand change schedule bulk API can support up to 512 scheduled changes at a time.

```txt
Path:
    /api/environment/{environmentId}/onhand/changeschedule/bulk
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    [
        {
            id: string,
            organizationId: string,
            productId: string,
            dimensionDataSource: string,
            dimensions: {
                [key:string]: string,
            },
            quantityDataSource: string, # optional
            quantitiesByDate: {
                [datetime:datetime]: {
                    [dataSourceName:string]: {
                        [key:string]: number,
                    },
                },
            },
        },
        ...
    ]
```

The following example shows sample body content.

```json
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
        "quantitiesByDate":
        {
            "2022-02-01": // today
            {
                "pos":{
                    "inbound": 10
                }
            }
        }
    },
    {
        "id": "id-car-0002",
        "organizationId": "usmf",
        "productId": "Car",
        "dimensions": {
            "SiteId": "1",
            "LocationId": "11",
            "ColorId": "Red",
            "SizeId": "Small"
        },
        "quantitiesByDate":
        {
            "2022-02-05":
            {
                "pos":{
                    "outbound": 10
                }
            }
        }
    }
]
```

### Create on-hand change events

On-hand change events are made by submitting a `POST` request to the relevant Inventory Visibility service URL (see the [Submit change schedules, change events, and ATP queries through the API](#api-urls) section). You can also submit bulk requests.

> [!NOTE]
> On-hand change events aren't unique to the ATP functionality but are part of the standard Inventory Visibility API. This example has been included because events are relevant when you work with ATP. On-hand change events resemble on-hand change reservations, but event messages must be sent to a different API URL, and events use `quantities` instead of `quantityByDate` in the message body. For more information about the on-hand change events and other features of the Inventory Visibility API, see [Inventory Visibility public APIs](inventory-visibility-api.md#create-one-onhand-change-event).

The following example shows a request body that contains a single on-hand change event.

```json
{
    "id": "id-bike-0001",
    "organizationId": "usmf",
    "productId": "Bike",
    "dimensions": {
        "SiteId": "1",
        "LocationId": "11",
        "SizeId": "Big",
        "ColorId": "Red"
    },
    "quantities": {
        "pos": {
            "inbound": 10.0
        }
    }
}
```

## Query the scheduled on-hand changes and ATP results

You can query scheduled on-hand changes and ATP results by submitting either a `POST` request or a `GET` request to the appropriate API URL (see the [Submit change schedules, change events, and ATP queries through the API](#api-urls) section).

In your request, set `QueryATP` to *true* if you want to query scheduled on-hand changes and ATP results.

- If you're submitting the request by using the `GET` method, set this parameter in the URL.
- If you're submitting the request by using the `POST` method, set this parameter in the request body.

> [!NOTE]
> Regardless of whether the `returnNegative` parameter is set to *true* or *false* in the request body, the result will include negative values when you query for scheduled on-hand changes and ATP results. These negative values will be included because, if only demand orders are scheduled, or if supply quantities are less than demand quantities, the scheduled on-hand change quantities will be negative. If negative values weren't included, the results would be confusing. For more information about this option and how it works for other types of queries, see [Inventory Visibility public APIs](inventory-visibility-api.md#query-with-post-method).

```txt
Path:
    /api/environment/{environmentId}/onhand/indexquery
Method:
    Post
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Body:
    {
        dimensionDataSource: string, # Optional
        filters: {
            organizationId: string[],
            productId: string[],
            siteId: string[],
            locationId: string[],
            [dimensionKey:string]: string[],
        },
        groupByValues: string[],
        returnNegative: boolean,
    }
```

The following example shows how to create a request body that can be submitted to Inventory Visibility by using the `POST` method.

```json
{
    "filters": {
        "organizationId": ["usmf"],
        "productId": ["Bike"],
        "siteId": ["1"],
        "LocationId": ["11"]
    },
    "groupByValues": ["ColorId", "SizeId"],
    "returnNegative": true,
    "QueryATP":true
}
```

### GET method example

```txt
Path:
    /api/environment/{environmentId}/onhand
Method:
    Get
Headers:
    Api-Version="1.0"
    Authorization="Bearer $access_token"
ContentType:
    application/json
Query(Url Parameters):
    groupBy
    returnNegative
    [Filters]
```

The following example shows how to create a request URL as a `GET` request.

```txt
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand?organizationId=usmf&productId=Bike&SiteId=1&LocationId=11&groupBy=ColorId,SizeId&returnNegative=true&QueryATP=true
```

The result of this `GET` request is exactly the same as the result of `POST` request in the previous example.

### Query result example

Both the previous query examples might produce the following reply. For this example, the system is configured with the following settings:

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
