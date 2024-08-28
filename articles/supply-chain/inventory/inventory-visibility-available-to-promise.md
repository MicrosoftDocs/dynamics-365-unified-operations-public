---
title: Inventory Visibility on-hand change schedules and ATP
description: Learn how to schedule future on-hand changes and calculate available-to-promise (ATP) quantities, including an outline on calculated measures for ATP quantities.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 11/30/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility on-hand change schedules and ATP

[!include [banner](../includes/banner.md)]

This article describes how to set up the *On-hand change schedule* feature to schedule future on-hand changes and calculate available-to-promise (ATP) quantities. ATP is the quantity of an item that's available and can be promised to a customer in the next period. Use of this calculation can greatly increase your order fulfillment capability.

For many manufacturers, retailers, or sellers, it isn't enough just to know what's currently on hand. They must have full visibility into future availability. This future availability should consider future supply, future demand, and ATP.

## Calculated measures for ATP quantities

The *ATP calculated measure* is a predefined calculated measure that's typically used to find the on-hand quantity that's currently available. The *supply quantity* is the sum of quantities for those physical measures that have a modifier type of *addition*, and the *demand quantity* is the sum of quantities for those physical measures that have a modifier type of *subtraction*.

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

## <a name="setup"></a>Turn on and set up on-hand change scheduling and ATP in UI version 2

This section applies when you're using [Inventory Visibility UI version 2](inventory-visibility-ui-version-2.md).

Before you can use ATP, you must set up one or more calculated measures to calculate the ATP quantities. You must also turn on the feature and configure ATP settings in Microsoft Power Apps.

Follow these steps to turn on the *On-hand change schedule* feature in Power Apps and configure the ATP settings.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. On the navigation pane, select **Feature management**.
1. On the **Available to promise** tile, select **Manage**.
1. Set the **Enable feature** option to *True* to turn on the ATP feature.
1. Set the **Schedule for 180 days** option to *True* to support the longer ATP schedule period (180 days).

    > [!IMPORTANT]
    > By default, the ATP feature is limited to seven days. The seven-day ATP and 180-day ATP features are separate and independent of each other. Schedule changes that you create or modify by using the seven-day ATP feature won't take effect when you turn on the 180-day ATP feature. If you've used the seven-day ATP feature and want to migrate to the 180-day feature, we recommend that you delete the old data and repost your on-hand change schedule after you enable the 180-day feature.

1. Set the **Max schedule period (days)** field to the number of days that users can view and submit scheduled on-hand changes. Users who query for stock information will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in the defined period, starting from the current date. The maximum value for this field is 180 days. By default, it's set to 30 days. Therefore, you can schedule changes for up to 30 days from today.

    > [!IMPORTANT]
    > The schedule period includes the current date. Therefore, users can schedule on-hand changes to occur any time from the current date (the day when the change is submitted) through (schedule period – 1) days in the future.

1. In the **Schedule measures** section, set up schedule measures. You can use existing calculated measures as schedule measures, or you can create new ones. When you query Inventory Visibility, the ATP value is provided for defined calculated measures, based on the scheduled changes of component physical measures. In the **Schedule measures** section, select **New on-hand change schedule configuration V2** on the toolbar to add a new calculated measure binding for ATP. The calculated measure is what you want to use to find the currently available on-hand quantity. For information about how to create a calculated measure, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures).

    > [!IMPORTANT]
    > The default ATP calculated formula is for reference. You can modify and add other data sources and physical measures to set up the correct ATP calculation for your business.

1. In the **ATP index set configuration** section, set up your ATP index. The ATP index resembles the *product index hierarchy* that lets you group query results by specific dimensions. For example, if you set *ColorId* and *SizeId* as your ATP index set, query results will be grouped by color and size. You can have multiple index sets.

    > [!IMPORTANT]
    > The default *ColorId* and *SizeId* index is for reference. You can remove dimensions and add other dimensions.

1. Select **Save**.
1. When you've finished configuring all the required settings, select **Update Configuration** under **Admin Settings** on the navigation pane.

Learn more in [Complete and update the configuration](inventory-visibility-configuration.md).

### Turn on and set up on-hand change scheduling and ATP in UI version 1

This section applies when you're using [Inventory Visibility UI version 1](inventory-visibility-ui-version-2.md).

Follow these steps to turn on the *On-hand change schedule* feature in Power Apps and configure the ATP settings.

1. Sign in to Power Apps, and open the **Inventory Visibility** app.
1. Open the **Configuration** page.
1. On the **Feature Management** tab, turn on the *Available to promise* feature.
1. Select the **ATP Setting** tab.
1. When you query Inventory Visibility, it will provide a result that includes each ATP calculated measure that you add here. Select **Add** to add a new calculated measure for ATP.
1. Set the following fields:

    - **Data Source** – Select the data source that's associated with the calculated measure.
    - **Calculated Measure** – Select the calculated measure that's associated with the selected data source, and that you want to use to find the currently available on-hand quantity.
    - **Schedule Period** – Enter the number of days that users can view and submit scheduled on-hand changes when the selected calculated measure is used. Users who query for stock information will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in this period, starting with the current date. Select an integer between 1 and 7.

    > [!IMPORTANT]
    > The schedule period includes the current date. Therefore, users can schedule on-hand changes to occur any time from the current date (the day when the change is submitted) through (schedule period – 1) days in the future.

1. Select **Save**.
1. Repeat steps 5 through 7 until you've added all the calculated measures that you require for ATP.
1. When you've finished configuring all the required settings, select **Update Configuration**.

## How the on-hand change schedule and ATP calculations work

An *on-hand change schedule* establishes expected dates and quantities of scheduled on-hand changes. You can submit an on-hand change schedule to Inventory Visibility, provided that the dates are within the period that's defined by the **Schedule period** setting (see the [Enable and set up the features](#setup) section of this article). Users who query for stock information will get the on-hand quantity, scheduled on-hand changes, and ATP for each day in that period.

Scheduled changes are initially uncommitted and therefore don't affect your actual on-hand quantities in the system. To commit the changes, you must submit an *on-hand change event*, which updates the actual available on-hand quantity. You must then revert the scheduled change by submitting an on-hand change schedule for a matching negative quantity.

For example, you place an order for 10 bikes and expect it to arrive tomorrow. Therefore, you submit an on-hand change schedule that has an inbound quantity of 10 and is dated for tomorrow. When the order arrives the next day, you add the bikes to your physical on-hand inventory. You must then commit the change to your system to update the actual on-hand quantity. To commit the change, you submit an on-hand change event that has an inbound quantity of 10. You then revert the scheduled change by submitting an on-hand change schedule that has an inbound quantity of -10.

When you query Inventory Visibility for on-hand and ATP quantities, it returns the following information for each day in the schedule period:

- **Date** – The date that the result applies to. The time zone is Coordinated Universal Time (UTC).
- **On-hand quantity** – The actual on-hand quantity for the specified date. This calculation is made according to the ATP calculated measure that's configured for Inventory Visibility.
- **Scheduled supply** – The sum of all scheduled inbound quantities that haven't become physically available for immediate consumption or shipment as of the specified date.
- **Scheduled demand** – The sum of all scheduled outbound quantities that haven't been consumed or shipped as of the specified date.
- **ATP quantity** – The minimum projected on-hand quantity that's available from the specified date through the end of the schedule period. This quantity includes all scheduled quantity adjustments. It's the maximum quantity that can be promised on the current date for delivery or consumption on that day.

For example, if the current date is February 1, 2022, and the schedule period is 7, users can submit scheduled on-hand changes that are expected to occur from February 1 through February 7, 2022. In this case, the ATP quantity for February 3, for example, is calculated based on the on-hand quantity for that day and the scheduled quantities from February 3 through February 7.

## Example

The following example shows how a series of scheduled quantity changes affects the on-hand and ATP quantities that Inventory Visibility reports. It also shows how to commit a scheduled change, how a committed schedule change affects the results, and what can occur if you don't commit a scheduled change.

The results in this example show a *projected on-hand* value. This value incorporates all scheduled updates for illustration purposes but isn't actually reported when you query Inventory Visibility.

1. The following settings are configured for your system on the **ATP setting** page of the Inventory Visibility app in Power Apps:

    - **Schedule measures** – A calculated measure that's named *On-hand* is added here. It's calculated as *On-hand* = *Supply* – *Demand*.
    - **Max schedule period (days)** – The value is set to *7*.
    - **ATP index set configuration** – *ColorId* and *SizeId* are added here.

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
| `/api/environment/{environmentId}/onhand/exactquery` | `POST` | Exact query by using the `POST` method. |

Learn more in [Inventory Visibility public APIs](inventory-visibility-api.md).

### Create one on-hand change schedule

An on-hand change schedule is created by submitting a `POST` request to the relevant Inventory Visibility service URL. You can also submit bulk requests.

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
    "quantitiesByDate": {
        "2022-02-01": {
            "pos": {
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
        "quantitiesByDate": {
            "2022-02-01": {
                "pos": {
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
        "quantitiesByDate": {
            "2022-02-05": {
                "pos": {
                    "outbound": 10
                }
            }
        }
    }
]
```

### Create on-hand change events

On-hand change events are made by submitting a `POST` request to the relevant Inventory Visibility service URL (see the start of the [Submit change schedules, change events, and ATP queries through the API](#api-urls) section).

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

In your request, set `QueryATP` to *true* if you want to query scheduled on-hand changes and ATP results. By default, the query returns all ATP-related data from today. You can specify `ATPFromDate` and `ATPToDate` to narrow the results. (The "to" and "from" dates just filter the result. They don't affect how ATP is calculated.)

- If you're submitting the request by using the `GET` method, set this parameter in the URL.
- If you're submitting the request by using the `POST` method, set this parameter in the request body.

> [!NOTE]
> Regardless of whether the `returnNegative` parameter is set to *true* or *false* in the request body, the result will include negative values when you query for scheduled on-hand changes and ATP results. These negative values will be included because, if only demand orders are scheduled, or if supply quantities are less than demand quantities, the scheduled on-hand change quantities will be negative. If negative values weren't included, the results would be confusing. For more information about this option and how it works for other types of queries, see [Inventory Visibility public APIs](inventory-visibility-api.md#query-with-post-method).

### Query by using the POST method

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

The following example shows how to create an index query request body that can be submitted to Inventory Visibility by using the `POST` method.

```json
{
    // OnHand Index Query fields
    "filters": {
        "organizationId": ["usmf"],
        "productId": ["Bike"],
        "SiteId": ["1"],
        "LocationId": ["11"]
    },
    "groupByValues": ["ColorId", "SizeId"],
    "returnNegative": true,

    // ATP related fields
    "QueryATP":true,
    "ATPFromDate": "2022-02-01",
    "ATPToDate": "2022-02-10",
}
```

### Query by using the GET method

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

The following example shows how to create an index query request URL as a `GET` request.

```txt
https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand?organizationId=usmf&productId=Bike&SiteId=1&LocationId=11&groupBy=ColorId,SizeId&returnNegative=true&QueryATP=true&ATPToDate=2022-02-01&ATPToDate=2022-02-10
```

The result of this `GET` request is exactly the same as the result of the `POST` request in the previous example.

### Exact query by using the POST method

To set up an exact query, add ATP-related fields to the query body. Learn more in [Exact query by using the post method](inventory-visibility-api.md#exact-query-with-post-method).

```json
{
    // Exact query fields
    // ...

    // ATP related fields
    "QueryATP":true,
    "ATPFromDate": "2022-02-01",
    "ATPToDate": "2022-02-10",
}
```

### Query result example

Any of the previous query examples might produce the following reply. For this example, the system is configured with the following settings:

- **ATP calculated measure:** *iv.onhand = pos.inbound – pos.outbound*
- **Schedule period:** *7*

Here's an example of the reply body.

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
