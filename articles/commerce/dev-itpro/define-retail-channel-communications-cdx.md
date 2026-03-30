---
title: Commerce Data Exchange and commerce channel communications
description: This article provides an overview of Commerce Data Exchange and its components.
author: josaw1
ms.date: 02/13/2026
ms.topic: overview
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.assetid: 179b1629-ac90-4cfb-b46a-5bda56c4f451
ms.custom: 
  - bap-template
---

# Commerce Data Exchange and commerce channel communications

[!include [banner](../includes/banner.md)]

This article provides an overview of Commerce Data Exchange and its components. It explains the part that each component plays in the transfer of data between Microsoft Dynamics 365 Commerce headquarters and channels.

Commerce Data Exchange is a system that transfers data between headquarters and channels, such as online stores or brick-and-mortar stores. The database that stores data for a channel is separate from the Commerce database. The channel database holds only the data that is required for transactions. You configure primary data in headquarters and distribute it to channels. Transactional data is created in the point of sale (POS) system or the online store, and then uploaded to headquarters. Data distribution is asynchronous. In other words, the process of gathering and packaging data at the source occurs separately from the process of receiving and applying data at the destination. For some scenarios, such as price and inventory lookups, data must be retrieved in real time. To support these scenarios, Commerce Data Exchange also includes a service that enables real-time communication between headquarters and a channel.

## Async Service

Microsoft SQL Server change tracking on the Commerce database is used to determine the data changes that you must send to channels. Based on a distribution schedule, headquarters packages that data and saves it to central storage (Azure blob storage). A separate batch process uses the Commerce Data Exchange: Async Client library to insert this data package into the channel database.

[![Async Service.](./media/async-300x239.png)](./media/async.png)

### Commerce scheduler

Scheduler jobs are the mechanism for distributing data to and from locations. Jobs are made up of subjobs, which specify the tables and table fields that contain the data to distribute. Headquarters includes predefined scheduler jobs and subjobs that meet the replication requirements of most organizations. The following types of predefined jobs are created:

- **Download jobs** – Download jobs send data that changed from headquarters to channel databases. SQL Server change tracking tracks modifications to records.
- **Upload jobs (P jobs)** – Upload jobs pull sales transactions from a channel into the Commerce database. P jobs upload data incrementally. When a P job runs, the Async Client library checks the replication counter for records that it already received from a location. A record is uploaded only if its replication counter is more than the largest value that it found. P jobs don't update data that was previously uploaded.

You use the distribution schedule to run the data transfer, either manually or by scheduling a batch job in headquarters. A distribution schedule can contain one or more channel data groups, and one or more scheduler jobs. To ensure that the scheduler jobs run smoothly, don't rename the "Default" database configured for the instance, and don't create a second database. Microsoft manages all non-Commerce Scale Unit databases, and only one default database is expected.

## Real-time Service

Commerce Data Exchange: Real-time Service is an integrated service that provides real-time communication between headquarters and channels. Real-time Service enables individual POS computers and online stores to retrieve specific data from headquarters in real time. Although you can perform most key operations in the local channel database, the following scenarios require direct access to the data that is stored in headquarters:

- Issuing and redeeming gift cards
- Redeeming loyalty points
- Issuing and redeeming credit memos
- Creating and updating customer records
- Creating, updating, and completing sales orders
- Receiving inventory against a purchase order or transfer order
- Performing inventory counts
- Retrieving sales transactions across stores and completing return transactions

[![Real-time Service.](./media/rts.png)](./media/rts.png)

A predefined Real-time Service profile is created.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
