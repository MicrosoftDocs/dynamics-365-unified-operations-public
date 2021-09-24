---
title: Integrate with third-party manufacturing execution systems
description: This topic explains how you can integrate Suppl Chain Management with a third-party manufacturing execution system (MES)
author: t-benebo
ms.date: 09/24/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-09-24
ms.dyn365.ops.version: 10.0.23
---

# Integrate with third-party manufacturing execution systems

[!include [banner](../includes/banner.md)]

Some manufacturing organizations that use Supply Chain Management use the native functionality in Dynamics 365 to control their manufacturing activities for machines, equipment, and personnel. However, other manufacturing organizations, especially those that have advanced manufacturing requirements, use a third-party manufacturing execution system (MES) instead. Organizations might choose a third-party MES solution because, for example, it's specifically tailored to their vertical industry.

In the integrated solution, data exchange is fully automated and occurs in near real time. Therefore, data is kept current in both systems, and no manual data entry is required. For example, when material consumption is registered in the MES, the integration ensures that the same consumption is also registered in Dynamics 365. Therefore, up-to-date inventory records are available to other important processes, such as planning and sales.

The solution makes it faster, easier, and cheaper for Supply Chain Management users to integrate with third-party MESs. It offers the following features:

- Business events and interfaces that support [key manufacturing execution processes](#processes-available-for-mes-integration)
- A centralized dashboard where you can track the event processing history, and troubleshoot and fix processes that fail

The following illustration shows a typical collection of business events, processes, and messages that are exchanged in an integrated solution.

![Typical integration scenario.](media/3p-mes-scenario.png "Typical integration scenario.")

## Turn on the MES integration feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Production control*
- **Feature name:** *Manufacturing execution systems integration*

## Processes available for MES integration

You can enable any or all of the following processes for integration.

| Process name | Description |
|---|---|
| Release production orders and production order status change business events | This process provides a business event that the MES can listen to, to get information about the production orders that should be produced. Reference data that is related to the production order is expected to be shared from Supply Chain Management to the MES through Open Data Protocol (OData) or data entities. |
| Start production order | This process provides Supply Chain Management with information about production orders that are being started by using the MES. It ensures that both systems have an up-to-date view of all manufacturing activities. |
| Report produced or scrapped quantity | This process provides Supply Chain Management with information about the good and error quantities that are reported on a production job by using the MES. It ensures that shop floor supervisors have an up-to-date view of production plan progress. |
| Report material consumption | This process provides Supply Chain Management with information from the MES about the quantities of materials that are consumed. It makes up-to-date inventory records available to other important processes, such as planning and sales. |
| Report time consumed for the operation | This process provides Supply Chain Management with information about the time that is used for a specific operation. |
| End production order | This process informs Supply Chain Management that the MES has updated a production order to its final status of *Ended*. This status indicates that no more quantities will be produced on the production order. |

## Monitor incoming messages

To monitor the incoming messages to the system, open the **Manufacturing execution systems integration** page. There, you can view, process, and troubleshoot issues.

## Call the API

To call any of the APIs, send a `POST` request to the following endpoint URL:<br>`/api/services/SysMessageServices/SysMessageService/SendMessage`

Send a request body similar to the following, replacing the values for *_companyId*, *_messageType* and *_messageContent* as needed. See the next section for details about the various message types supported by the API and how to design their content.

```json
{
    "_companyId": "USMF",
    "_messageQueue": "JmgMES3P",
    "_messageType": "ProdProductionOrderReportFinished",
    "_messageContent":
    "{\"ProductionOrderNumber\": \"P000123\", \"ReportFinishedLines\": [{\"ItemNumber\": \"A0001\", \"ReportedGoodQuantity\": 10, \"ReportAsFinishedDate\": \"2021-01-01\"}]}"
}
```

## API message types and content

The following subsections describe each type of message that can be exchanged though the MES integration API.

### Start production order message

The start production order message is named `ProdProductionOrderStart` and supports the fields listed in the following table.

| Field name | Status | Type |
|---|---|---|
| `ProductionOrderNumber` | Mandatory | String |
| `StartedQuantity` | Optional | Real |
| `StartedDate` | Optional | Date |
| `AutomaticBOMConsumptionRule` | Optional | Enum (FlushingPrincip \| Always \| Never) |

### Report as finished message

The report as finished message is named `ProdProductionOrderReportFinished` and supports the fields listed in the following table.

| Field name | Status | Type |
|---|---|---|
| `ProductionOrderNumber` | Mandatory | String |
| `ReportFinishedLines` | Mandatory | A list of lines (at least one), each of which contains the payload described in the following table. |

Each line in the `ReportFinishedLines` section of the `ProdProductionOrderReportFinished` message supports the fields listed in the following table.

| Field name | Status | Type |
|---|---|---|
| `LineNumber` | ???? | Real |

...

### Material consumption (picking list) message

...

### Time used for operation (route card) message

...

### End production order message

...