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

### Set up a calculated measure for ATP quantities

The *ATP calculated measure* is a pre-defined calculated measure. The sum of its addition modifier quantities is the supply quantity and the sum of its subtraction modifier quantities is the demand quantity.

You can add multiple calculated measures to calculate ATP quantities, but the total number of modifiers used in each of these calculated measures should be less than 8. <!-- KFM: Do we mean max of 8 for *each* ATP measure, or a total of 8 *across all* ATP measures? (My edit assumes *each*)-->

For example, you might set up the following calculated measures to calculate various types of ATP values:

- **On-hand-change** = (Supply – Demand)<br>Where:
  - **Supply** = (PhysicalInvent + OnHand + Unrestricted + QualityInspection + Inbound)
  - **Demand** = (ReservPhysical + SoftReservePhysical + Outbound)
- **On-hand-available** = [PhysicalInvent + (OnHand + Unrestricted + QualityInspection + Inbound) – (Reservphysical + SoftReservePhysical + Outbound)]

<!-- KFM: I pulled the above formulas from your comments later in this topic. Are they still correct? Do they work here? -->

For more information about calculated measures, see [Calculated measures](inventory-visibility-configuration.md#calculated-measures)

### Turn on the On-hand change schedule feature and set ATP options

Turn on the *On-hand change schedule* feature in Power Apps and set up the ATP options using the following steps:

1. Sign into Power Apps and open Inventory Visibility.
1. Open the **Configuration** page.
1. On the **Feature management** tab, turn on the *OnhandChangeSchedule* feature.
1. Open the **ATP setting** page.
1. <!-- KFM: It's unclear, but I suppose we do something here to add a new calculated measure and could possibly add several. If so, please describe this process explicitly here. -->
1. Make the following settings:
    - **Data source** – <!-- KFM: Describe this setting and its purpose. I suppose this is the data source where the calculated measures are defined. -->
    - **Calculated measure** – <!-- KFM: Describe this setting and its purpose. Also, is this actually called  **ATP calculated measure**? -->
    - **Schedule period** – Enter the number of days for which users can view and submit scheduled on-hand changes. When users query for stock information, they will get the scheduled on-hand changes and ATP for each day in the period. Enter an integer between 1 and 7. <!-- KFM: I moved several details from the next section to here. Please confirm this edit. -->

    > [!IMPORTANT]
    > The **Schedule period** includes today, which means users can schedule on-hand changes to occur an time from today (the day the change is submitted) to (schedule period – 1) days in the future.

1. Select **Save**. <!-- KFM: I assumed we have a button called **Save** here. True? -->
1. <!-- KFM: If it is possible to add more measures, then we can add the following here: "Continue working until you have added all of the calculated measures you need." -->

## How the on-hand change schedule and ATP calculations work

<!-- KFM: Please confirm my edits to this section. Throughout, we must be careful with the terms "post" (this often means something special in SCM, so I want to avoid that term here other than to refer to the "post method"), "submit" (the word I think we should use for interacting with IV through post or get methods), and "commit" (I am not fully clear on what this means or where we do it). Those are my assumed definitions, which I have used throughout this text. -->

Users submit expected dates and quantities of upcoming on-hand changes to Inventory Visibility, provided the date is within the period defined by the **Schedule period** setting (see [Enable and set up the features](#setup)). When users query for stock information, they will get the scheduled on-hand changes and ATP for each day in that period.

Changes submitted through Inventory Visibility are initially uncommitted and therefore won't affect your "real" on-hand quantities in the system. To commit the changes, users must *commit* the on-hand event and then *revert* the scheduled changes (by committing a negative quantity). For example, if a user submits a scheduled on-hand change to Inventory Visibility with an **Inbound** quantity of *10*, to commit the change, they must commit an on-hand event with an **Inbound** quantity of *10*, and then revert the on-hand change schedule by committing an **Inbound** quantity of *-10* <!-- KFM: Is this reversion made by submitting to IV or by committing in SCM? -->.

When a user queries Inventory Visibility for ATP quantities, the system replies with a data table <!-- KFM: is this best referred to as an array, a table, a result set, or something else? --> that provides the following information for each day during the schedule period:

- **Date** – The date for which the row applies.
- **On-hand** – The on-hand quantity for the specified date. It is calculated based on the current quantities committed in Supply Chain Management. <!-- KFM: Please confirm this formulation. -->
- **Supply** – <!-- KFM: Please provide a short description. -->
- **Demand** – <!-- KFM: Please provide a short description. -->
- **Projected on-hand** – The planed on-hand quantity for the specified date. It equals the current on-hand quantity combined with all of the on-hand change quantities <!--KFM: What do we mean by "on-hand change quantities". Can we express this using the the other terms in this list (eg, "supply", "demand", "planned on-hand", "ATP")? --> scheduled from today to the specified **Date**.
- **ATP** – The minimum projected on-hand quantity available from the specified **Date** until the end of the schedule period, which means that this is the maximum quantity that can be promised on that day.
- **Planed on-hand** – Calculated based on the scheduled quantity changes using the ATP calculated measure specified in the setup. <!-- KFM: This never appears in the tables from the example in the following section. Is it the same as the **Projected on-hand**? I'm not sure what to do with this... -->

For example, if today is 2022/02/01, the schedule period is 7, users can submit scheduled on-hand changes expected to occur from 2022/02/01 to 2022/02/07, and the ATP quantity for 2022/02/03 is calculated based on the ATP quantities from 2022/02/03 to 2022/02/07.

## Example

<!-- KFM: Again, we need to be careful with "Post", "Commit", "Submit", and "revert". I did my best to untangle them here, but we should review this carefully. -->

1. Your system is set up with the following settings on the **ATP setting** page in Power Apps:
    - **Data source** – <!-- KFM: I'm not sure this is needed, but it might complete this example. -->
    - **ATP calculated measure** – You have a calculated measure called *On-hand* (calculated as *On-hand = supply – demand*), and that measure is selected here. <!-- KFM: We could maybe mention that this measure is defined in the data source specified above, if that is the case. -->
    - **Schedule period** – Set to *7*.

1. The following conditions also apply:
    - Today is 2022/02/01.
    - Current on-hand quantity is 20.

1. You submit to Inventory Visibility a scheduled demand with a quantity of 3 for today (2022/02/01). Therefore, the projected on-hand quantity is 17.

1. You query the ATP value and find that the ATP quantity for each day in this period is 17, as shown in the following query result.

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 |  |  | 17 | 17 |
    | 2022/02/04 | 20 |  |  | 17 | 17 |
    | 2022/02/05 | 20 |  |  | 17 | 17 |
    | 2022/02/06 | 20 |  |  | 17 | 17 |
    | 2022/02/07 | 20 |  |  | 17 | 17 |

1. Today (2022/02/01), you submit a scheduled supply with quantity 10 for 2022/02/02. Then you query the quantities, and receive the following information.

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 20 |  | 3 | 17 | 17 |
    | 2022/02/02 | 20 |  |  | 17 | 17 |
    | 2022/02/03 | 20 | 10 |  | 27 | 27 |
    | 2022/02/04 | 20 |  |  | 27 | 27 |
    | 2022/02/05 | 20 |  |  | 27 | 27 |
    | 2022/02/06 | 20 |  |  | 27 | 27 |
    | 2022/02/07 | 20 |  |  | 27 | 27 |

1. Today (2022/02/01), you make the following submissions for the following days:
    - Submit scheduled demand with quantity 15 for 2022/02/04
    - Submit supply with quantity 1 for 2022/02/05
    - Submit scheduled demand with quantity 3 for 2022/02/06

    Then you query the quantities and receive the following results:

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | ---  |
    | 2022/02/01 | 20 |  | 3 | 17 | 12 |
    | 2022/02/02 | 20 |  |  | 17 | 12 |
    | 2022/02/03 | 20 | 10 |  | 27 | 12 |
    | 2022/02/04 | 20 |  | 15 | 12 | 12 |
    | 2022/02/05 | 20 | 1 |  | 13 | 13 |
    | 2022/02/06 | 20 | 3 |  | 16 | 16 |
    | 2022/02/07 | 20 |  |  | 16 | 16 |

1. If the demand order (of quantity 3) for today (2022/02/01) has been committed, you should commit an on-hand change request to increase the on-hand quantity from 10 to 13, and also commit a scheduled demand with quantity -3 to revert the scheduled change. The result is as follows. <!--KFM: Please review my use of "commit" here (I was confused by the original). Who does the "commit" operation, and where/how does this occur? -->

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/01 | 17 |  | 0 | 17 | 12 |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |

1. The next day (2022/02/02), you query the quantities and receive the following results.

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/02 | 17 |  |  | 17 | 12 |
    | 2022/02/03 | 17 | 10 |  | 27 | 12 |
    | 2022/02/04 | 17 |  | 15 | 12 | 12 |
    | 2022/02/05 | 17 | 1 |  | 13 | 13 |
    | 2022/02/06 | 17 | 3 |  | 16 | 16 |
    | 2022/02/07 | 17 |  |  | 16 | 16 |
    | 2022/02/08 | 17 |  |  | 16 | 16 |

    However, two days after that (on 2022/02/04), the supply scheduled for 2022/02/03 still hasn't been committed, which produces the following results:

    | Date | On-hand | Supply | Demand | Projected on-hand | ATP |
    | --- | --- | --- | --- | --- | --- |
    | 2022/02/04 | 17 |  | 15 | 2 | 2 |
    | 2022/02/05 | 17 | 1 |  | 3 | 3 |
    | 2022/02/06 | 17 | 3 |  | 6 | 6 |
    | 2022/02/07 | 17 |  |  | 6 | 6 |
    | 2022/02/08 | 17 |  |  | 6 | 6 |
    | 2022/02/09 | 17 |  |  | 6 | 6 |
    | 2022/02/10 | 17 |  |  | 6 | 6 |

    As you can see, the scheduled (but not committed) on-hand changes do not influence actual on-hand.

## Call the on-hand change schedule API

Users can use the following API URLs to submit on-hand change schedules and query results.

| Path | Method | Description |
| --- | --- | --- |
| `/api/environment/{environment-ID}/on-hand/changeschedule` | `POST` | Create one scheduled on-hand change. |
| `/api/environment/{environment-ID}/on-hand/changeschedule/bulk` | `POST` | Create multiple scheduled on-hand changes. |
| `/api/environment/{environment-ID}/onhand/indexquery` | `POST` | Query by using the `POST` method. |
| `/api/environment/{environment-ID}/onhand` | `GET` | Query by using the `GET` method. |

### Post on-hand change schedules

On-hand change schedules are made by submitting a `POST` request to the relevant Inventory Visibility service URL (as listed previously). You can also submit bulk requests.

For an on-hand change schedule, the request body must contain an organization ID, a product ID, scheduled date, and quantities by date. The scheduled date must be between today and the end of the current schedule period.

> [!NOTE]
> If the scheduled on-hand changes are committed or canceled, you must revert the schedule by setting the quantity to a negative value.

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

You can query scheduled on-hand changes and ATP results by submitting either a `POST` or `GET` request to the appropriate API URL (as listed previously).

In your request, set `QueryATP` to *true* if you want to query scheduled on-hand changes and ATP results.

- If your submitting using the `GET` method, set this parameter in the URL.
- If your submitting using the `POST` method, set this parameter in the request body

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

`https://inventoryservice.{RegionShortName}-il301.gateway.prod.island.powerapps.com/api/environment/{EnvironmentId}/onhand?organizationId=usmf&productId=Bike&SiteId=1&groupBy=ColorId,SizeId&returnNegative=true&QueryATP=true`

This result of this `GET` request is exactly the same as the example `POST` request provided earlier.
