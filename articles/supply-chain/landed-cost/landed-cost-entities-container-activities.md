---
title: Container activities entity
description: Learn about container activities, which are used to track the progress of shipping containers with a table that defines various names. 
author: lisascholz91
ms.author: lisascholz
ms.topic: article
ms.date: 05/27/2022
ms.reviewer: kamaybac
ms.search.form:
---

# Container activities entity

[!include [banner](../includes/banner.md)]

Container activities are used to track the progress of shipping containers. A record is created for each leg that is assigned to the journey template that is selected at the time of shipping container creation. Records are also created when the shipping container is created via a data entity.

Information about the progress of an in-transit shipping container is often received from an external source. The container activities entity enables an external source such as a freight forwarder to directly update the record. Therefore, no manual update of data is required.

## Container activities (ITMContainerActivityEntity)

You can use the container activities entity (`ITMContainerActivityEntity`) to create additional activity records. Alternatively, a freight forwarder can pass updates for a confirmed **Actual end date** value.

| Name | Mapping | Data type | Key | Mandatory |
|---|---|---|---|---|
| Actual end date | ITMContainerActivityTable.ActualEndDate | Datetime | No | No |
| Mode of delivery | ITMContainerActivityTable.DlvModeId | Nvarchar(10) | No | No |
| Estimated end date | ITMContainerActivityTable.EsimatedDate | Datetime | No | No |
| Line number | ITMContainerActivityTable.LineNum | Numeric(32, 16) | **Yes** | No |
| Notes | ITMContainerActivityTable.Notes | nvarchar(MAX) | No | No |
| Activity | ITMContainerActivityTable.ShipActivityId | Nvarchar(10) | No | **Yes** |
| Shipping container | ITMContainerActivityTable.ShipContainerId | Nvarchar(20) | **Yes** | **Yes** |
| Voyage | ITMContainerActivityTable.ShipId | Nvarchar(20) | **Yes** | **Yes** |
| Leg | ITMContainerActivityTable.ShipLegId | Nvarchar(20) | No | **Yes** |
| Service provider | ITMContainerActivityTable.ShipServiceProvider | Nvarchar(20) | No | No |
| Temperature | ITMContainerActivityTable.ShipTemperature | Numeric(32, 6) | No | No |
| Vessel | ITMContainerActivityTable.ShipVesselId | Nvarchar(20) | No | No |
| Start date | ITMContainerActivityTable.StartDate | Datetime | No | No |

## Tracking control

The tracking control center enables an update of a specified source field to be triggered by an update of a specified target field. If both the value of the source field and the value of the target field are updated by using the container activities entity, the target field will show the entity value. This behavior is related to tracking control records that have a **Create type** value of *Lead time*.

For cost areas that have a **Create type** value of *Status update* or *Blank* (which is a user-defined value), the system will update the voyage status or target field according to the tracking control configuration.

## Calculated fields

The values of the following fields in a container activity record are calculated based on the values of other fields. Although these calculated fields aren't included in the data entity, they will be set if the fields that the calculations are based on are provided.

- **Estimated days** = **Estimated end date** – **Start date**
- **Actual days** = **Actual end date** – **Start date**
