---
title: Container activities entity
description: Container activities are used to track the progress of a Shipping Container. 
author: yufeihuang
ms.date: 12/16/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-12-16
ms.dyn365.ops.version: 10.0.25
---

# Container activities entity

[!include [banner](../includes/banner.md)]

Container activities are used to track the progress of shipping containers. A record is created for each leg assigned to the journey template selected at the time of shipping container creation. These records will also be created where the shipping container is created via a data entity.

Information on the progress of an in-transit shipping container is often received from an external source. The container activity entity will allow an external source such as a freight forward to directly update the record, removing the requirement for a manual update of data.

## Container activities (ITMContainerActivityEntity)

You can use this entity to create additional activity records, or a freight forwarder can pass updates for a confirmed **Actual end date**.

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

The tracking control center allows for the update of a specified **Source field**, triggered by an update to a nominated **Target field**. Where both the source and target field values are updated by using the container activity entity, it is the entity value that will be displayed within the target field. This relates to the tracking control records with a **Create type** of *Lead time*.

For cost areas that have a **Create type** of *status update* or *blank* (which is a user-defined value), the system will update the voyage status or target field according to the tracking control configuration.

## Calculated fields

The values of the following fields on a container activity record are determined by the values of other fields. These calculated fields are not included within the data entity, however they will be populated if the prerequisite fields are provided.

- **Estimated days** = **Estimated end date** – **Start date**
- **Actual days** = **Actual end date** – **Start date**
