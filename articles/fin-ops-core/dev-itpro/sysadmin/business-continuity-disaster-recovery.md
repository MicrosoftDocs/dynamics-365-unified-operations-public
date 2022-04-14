---
# required metadata

title: Business continuity and disaster recovery
description: This topic describes the business continuity and disaster recovery that Microsoft provides for production instances of Microsoft Dynamics 365 SaaS applications if an Azure region-wide outage occurs.
author: MicroSri
ms.date: 04/14/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sriknair
ms.search.validFrom: 2021-07-31
---

# Business continuity and disaster recovery

[!include[banner](../includes/banner.md)]

Microsoft provides business continuity and disaster recovery for production instances of Dynamics 365 software as a service (SaaS) applications if a Microsoft Azure region-wide outage occurs.

Customers who have purchased the appropriate licenses can deploy a production instance of a Finance and Operations app. For more information, see [Cloud deployment overview](../deployment/cloud-deployment-overview.md).

For production environments, replicas of the different storage services (Azure SQL Database and file storage) are established in the secondary region at the time of deployment. These replicas are known as *geo-secondaries*.

The geo-secondary replicas are kept synchronized with the primary instance through continuous data replication. There is a small replication latency, or lag—typically less than a few minutes—between the primary data sources and their corresponding geo-secondary replicas. For more information, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions).

![Geo-secondaries](media/geo-secondary-replicas.png)

For more information about data protection in non-production environments, see [Database movement operations home page](../database/dbmovement-operations.md).

As seen in the preceding diagram, similar to data storage services, compute infrastructure is also provisioned in both regions in such a way that it can handle the traffic volume in case of an environment or region-level failover. In order to provide region-level resiliency VMSS is configured with 5-level fault domains to handle transient issues caused due to faulty hardware, etc. and automatically load balance the traffic and results in an experience where customers barely see a blip with no data loss. The following sections describe the different types of failovers that are possible and how Microsoft manages service continuity in either of these situations. 

Finance and Operations apps adhere to the Microsoft Business Continuity and Disaster Recovery (BCDR) standard that requires each online service to have a BCDR plan reviewed, updated, and tested at least annually. Microsoft Cloud Business Continuity and Disaster Recovery Plan Validation Report is made available to customers on [Service Trust Portal](https://servicetrust.microsoft.com/).

If the outage is caused due to issues with underlying services, caused due to faulty hardware or network outage etc., and Microsoft has determined that the region won't become available within a reasonable amount of time, Microsoft will notify the customers and switch over the traffic to route to the secondary region instances. Recovery Point Objective (RPO) here is small and up to a few seconds or couple of minutes. 

In the event of an unanticipated region-wide outage, such as a natural disaster that affects the entire Azure region, and Microsoft has determined that the region won't become available within a reasonable amount of time, Microsoft will notify customers and switch over the traffic to route to the secondary instances. In this case, it's possible that customers might experience a data loss of up to 15 minutes, depending on the nature and timing of the outage. RPO here is small and up to a few seconds or couple of minutes. 

Recovery Time Objective (RTO) varies depending on the nature of the impact and could be from 4 to 10 hours. 

The applicable service will be operated in limited mode on failover. Update maintenance cannot be triggered in failover mode. 

## Failback 

Microsoft will notify customers and switch back the environments to operate out of the primary region when it determines that the primary region is back online and is fully operational. Users connected to the systems will experience a brief interruption of up to a few minutes and batch service can be unavailable for up to 25 minutes. The service, including all non-production instances, will be fully restored. There will be no data loss during the failback process.  

## Responsibilities for disaster recovery 

The following table describes responsiblities for disaster recovery.

| Microsoft's responsibilities | Customer's responsibilities |
|------|------|
| Microsoft enables geo-redundancy and automatic back-up of SQL and Azure storage at the time of deployment of the primary production instance. | None |
| Microsoft has AOS images available from regional repository to restore compute. We maintain the compute infrastructure to meet RTO. |None |
|On outage, Microsoft determines within region failover needs to be executed then we don’t need customer consent, as there will not be data loss, but if a cross-region failover needs to be executed for the customer and there could be a data loss up to five seconds. For details, see Azure SQL Database Geo-Restore here: [Azure SQL Database Geo-Restore](https://azure.microsoft.com/blog/azure-sql-database-geo-restore/)<br><br>In the event of a data loss, Microsoft will send a request to the customer asking for its sign-off on a failover.  |   Customer must provide written sign-off to trigger the failover in the event of data loss. |
|When a failover occurs, the applicable service works in limited mode. Update maintenance can't be triggered in failover mode. | Customer can't request package deployments or other regular maintenance requests in failover mode. |
| Microsoft fails back to the production instance in the primary Azure region when the datacenter becomes operational. Normal operations are resumed. Notification will be published to customers, and they may experience brief interruptions or disconnects during this window, but will not need to take a full downtime. | None |
|None | Customers should plan disaster recovery for external resources not provisioned by Microsoft. |



