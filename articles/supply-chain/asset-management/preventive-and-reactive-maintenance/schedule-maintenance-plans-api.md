---
title: Schedule maintenance plans by using an API
description: Learn how to use the maintenance plan scheduling API in Asset Management to start maintenance plan scheduling from an external system.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/17/2026
ms.custom: 
  - bap-template
---

# Schedule maintenance plans by using an API

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

Preventive maintenance scheduling generates maintenance schedule lines on assets, based on the maintenance plans that you set up on those assets. Usually, a planner runs this process from the **Schedule maintenance plans** dialog or sets it up as a recurring batch job. For more information, see [Schedule maintenance plans](schedule-maintenance-plans.md).

The *maintenance plan scheduling API* lets another system start the same process. For example, a system that records asset counter readings can call the API after it records new readings, instead of waiting for the next scheduled run.

The API is asynchronous. It validates your request, queues a batch job that does the scheduling, and returns the ID of that batch job. To check the result, monitor the batch job, and then review the maintenance schedule lines on the **All maintenance schedule** page (**Asset management** > **Maintenance schedule** > **All maintenance schedule**).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.50 or later.
- The *Maintenance plan scheduling API* feature must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Until you turn on the feature, every call fails.
- The user or service principal that calls the API must have the *Run maintenance plan scheduling service* privilege (`EntAssetMaintenancePlanSchedulingServiceInvoke`) and must have access to the legal entity that's specified in `dataAreaId`. The *Maintenance manager* and *Maintenance clerk* security roles include this privilege.

## Endpoints

The API is a custom service in the `EntAssetServices` service group, which is deployed on both a JSON endpoint and a SOAP endpoint.

| Endpoint | URL |
|---|---|
| JSON | `https://<base URL>/api/services/EntAssetServices/EntAssetMaintenancePlanSchedulingService/scheduleMaintenancePlans` |
| SOAP | `https://<base URL>/soap/services/EntAssetServices?wsdl` |

The `<base URL>` value is the URL of your Supply Chain Management environment. The JSON endpoint accepts the `POST` method and expects a `Content-Type` of `application/json`.

For general information about these endpoints, see [Custom service development](/dynamics365/fin-ops-core/dev-itpro/data-entities/custom-services).

## Authentication

The API uses the same Microsoft Entra ID authentication as other Microsoft finance and operations apps services. Get an access token for your environment URL, and send it in the `Authorization` header of every call.

```http
Authorization: Bearer <access token>
```

To set up authentication, including registering an application for service-to-service calls, see [Service endpoints overview](/dynamics365/fin-ops-core/dev-itpro/data-entities/services-home-page#authentication).

## Request

The JSON body contains a single `_request` object. The following example shows the smallest request that the API accepts. This request schedules every maintenance plan in the legal entity.

```json
{
    "_request": {
        "dataAreaId": "usmf",
        "periodLength": 3,
        "periodUnit": "Month"
    }
}
```

### Legal entity and scheduling period

The following table lists the required fields.

| Field | Type | Description |
|---|---|---|
| `dataAreaId` | String | The ID of the legal entity where you schedule the maintenance plans. |
| `periodLength` | Integer | The number of period units to schedule ahead. The value must be greater than zero. |
| `periodUnit` | String | The unit for `periodLength`. Valid values are `Day`, `Week`, `Month`, `Quarter`, and `Year`. |

`periodLength` and `periodUnit` correspond to the **Period** and **Period frequency** fields, respectively, in the **Schedule maintenance plans** dialog. For example, a `periodLength` value of `3` and a `periodUnit` value of `Month` create maintenance schedule lines for the next three months.

### Work order options

The fields listed in the following table are optional. The default value for each of them is `false`.

| Field | Type | Description |
|---|---|---|
| `autoCreateWorkOrders` | Boolean | Set this field to `true` to automatically create work orders for maintenance plan lines where the **Auto create** check box is selected. This field corresponds to the **Auto create if specified in the line** option in the dialog. |
| `oneWorkOrderPerScheduleLine` | Boolean | Set this field to `true` to create a separate work order for every maintenance schedule line. |

To group maintenance schedule lines into work orders, set one or more of the following Boolean fields to `true`.

| Field | Groups by |
|---|---|
| `groupScheduleLinesByMaintenancePlan` | Maintenance plan |
| `groupScheduleLinesByAssetType` | Asset type |
| `groupScheduleLinesByAsset` | Asset |
| `groupScheduleLinesByFunctionalLocation` | Functional location |
| `groupScheduleLinesByJobTypeCategory` | Job type category |
| `groupScheduleLinesByJobType` | Job type |
| `groupScheduleLinesByJobTypeVariant` | Job type variant |
| `groupScheduleLinesByTrade` | Trade |
| `groupScheduleLinesByDate` | Date |

The work order options follow the same rules as the dialog:

- You can use `oneWorkOrderPerScheduleLine` and the grouping fields only when `autoCreateWorkOrders` is `true`.
- You can't combine `oneWorkOrderPerScheduleLine` with any grouping field.

### Filters

The fields listed in the following table are optional. Use them to limit scheduling to some of the maintenance plans in the legal entity. If you omit all filter fields, the batch job schedules every maintenance plan in the legal entity, the same as a full recurring batch run.

| Field | Type | Description |
|---|---|---|
| `maintenancePlanIds` | Array of strings | Schedule only the maintenance plans that have these IDs, on both assets and functional locations. |
| `assetIds` | Array of strings | Limit maintenance plans on assets to these assets. |
| `assetTypeIds` | Array of strings | Limit maintenance plans on assets to assets of these asset types. |
| `functionalLocationIds` | Array of strings | Limit maintenance plans on functional locations to these functional locations. |
| `functionalLocationTypeIds` | Array of strings | Limit maintenance plans on functional locations to functional locations of these types. |

The asset filters don't limit maintenance plans on functional locations, and the functional location filters don't limit maintenance plans on assets. For example, a request that contains only `assetIds` still schedules every maintenance plan on a functional location in the legal entity. To limit both, also use `maintenancePlanIds`.

If you combine `maintenancePlanIds` with another filter, or combine two filters of the same kind, a maintenance plan must match at least one value in each of those fields.

> [!IMPORTANT]
> The API doesn't check whether filter values exist. If you send an asset ID that doesn't exist or that you misspelled, the call still succeeds, but no maintenance plans are scheduled for that value. If a filter list contains an empty string, it matches no records. For example, `"assetIds": [""]` schedules no maintenance plans on assets, but still schedules maintenance plans on functional locations. To skip a filter, leave the field out. Validate your IDs before you call the API, and compare the maintenance schedule lines that are created with what you expect.

### Batch options

The fields listed in the following table are optional.

| Field | Type | Description |
|---|---|---|
| `batchGroupId` | String | The batch group that the batch job runs in. If you omit this field, the job runs in the default batch group. If the batch group doesn't exist, the call fails. |
| `taskDescription` | String | The description of the batch job on the **Batch jobs** page. The default description is *Maintenance plan scheduling (API)*. |

## Response

The response includes the ID of the batch job that the API queues.

| Field | Type | Description |
|---|---|---|
| `batchJobId` | Integer | The ID of the batch job that runs maintenance plan scheduling. Use this value to find the job in **System administration** > **Inquiries** > **Batch jobs**. |

```json
{
    "$id": "1",
    "batchJobId": 5637148796
}
```

The platform's JSON serializer adds a `$id` reference number to each object in the response. It isn't part of the API's contract. Use `batchJobId` to identify the batch job.

A successful response means only that the API queues the batch job, not that scheduling is finished.

## Examples

The following examples use IDs from the *USMF* demo company.

### Schedule a maintenance plan for one asset

This example schedules the `EX-PM` maintenance plan for asset `EX-101` for the next six months. Without `maintenancePlanIds`, the request would also schedule every maintenance plan on a functional location.

```json
{
    "_request": {
        "dataAreaId": "usmf",
        "periodLength": 6,
        "periodUnit": "Month",
        "maintenancePlanIds": ["EX-PM"],
        "assetIds": ["EX-101"]
    }
}
```

### Schedule maintenance plans and group work orders by asset

This example schedules two maintenance plans for the next six months, turns on automatic work order creation, groups the work orders by asset, and sets a custom description for the batch job.

The batch job creates work orders only for maintenance plan lines that are set up to create them.

```json
{
    "_request": {
        "dataAreaId": "usmf",
        "periodLength": 6,
        "periodUnit": "Month",
        "autoCreateWorkOrders": true,
        "groupScheduleLinesByAsset": true,
        "maintenancePlanIds": ["EX-PM", "GEN-PM"],
        "taskDescription": "EX-PM and GEN-PM, next six months"
    }
}
```

## Errors

If a request isn't valid, the API returns an error and doesn't queue a batch job. The API returns the messages in the following table with HTTP status code 500.

| Message | Cause |
|---|---|
| The '*feature name*' feature is not enabled. | The *Maintenance plan scheduling API* feature is turned off in feature management. |
| A maintenance plan scheduling request is required. | The `_request` value is `null`. |
| A legal entity is required. | The `dataAreaId` field is missing or blank. |
| The legal entity '*value*' does not exist. | The `dataAreaId` field doesn't match a legal entity in the environment. |
| The legal entity '*value*' is not available to the current user. | The caller doesn't have access to the legal entity that's specified in `dataAreaId`. |
| The scheduling period length must be greater than zero. | The `periodLength` field is zero or negative. |
| A scheduling period unit is required. | The `periodUnit` field is missing or blank. |
| The scheduling period unit must be Day, Week, Month, Quarter, or Year. | The `periodUnit` field contains a value that isn't valid. |
| The scheduling period is too large to produce a valid end date. | The combination of `periodLength` and `periodUnit` produces a date beyond the range that the system supports. |
| Work order options cannot be used when automatic work order creation is turned off. | `oneWorkOrderPerScheduleLine` or a grouping field is set to `true`, but `autoCreateWorkOrders` is `false` or omitted. |
| Schedule line grouping cannot be combined with one work order per schedule line. | Both `oneWorkOrderPerScheduleLine` and a grouping field are set to `true`. |
| The batch group '*value*' does not exist. | The `batchGroupId` field doesn't match a batch group in the environment. |

The platform can also reject a request before the API runs:

- **HTTP status code 400** – The body doesn't contain a `_request` object, or a field has the wrong type, such as text in `periodLength`.
- **HTTP status code 401** – The caller doesn't have the *Run maintenance plan scheduling service* privilege. The message includes *Entry point security access denied*.

## Usage considerations

- **Each run replaces the open maintenance schedule lines.** For each asset and maintenance plan that the request covers, the batch job deletes the maintenance schedule lines that don't have a work order yet, and then creates new lines for the requested period. If you request a shorter period than an earlier run, the lines after the new period are removed.
- **Each call queues its own batch job.** If another system sends two requests a few seconds apart, the API queues two batch jobs, and both run. The API doesn't detect duplicate requests.

## Related information

- [Schedule maintenance plans](schedule-maintenance-plans.md)
- [Maintenance plans](maintenance-plans.md)
- [Preventive maintenance overview](preventive-maintenance-overview.md)
- [Custom service development](/dynamics365/fin-ops-core/dev-itpro/data-entities/custom-services)
