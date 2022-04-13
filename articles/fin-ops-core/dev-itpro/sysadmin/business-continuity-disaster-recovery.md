---
# required metadata

title: Business continuity and disaster recovery
description: This topic describes the business continuity and disaster recovery that Microsoft provides for production instances of Microsoft Dynamics 365 SaaS applications if an Azure region-wide outage occurs.
author: MicroSri
ms.date: 04/13/2022
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

The geo-secondaries are kept synchronized with the primary instance through continuous data replication. There is a small replication latency or lag of up to 15 minutes between the geo-secondaries and the primary instance. For more information, see [Business continuity and disaster recovery (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions).

![Geo-secondaries](media/Finance-and-Operations-apps.png)

For more information about data protection in non-production environments, see [Database movement operations home page](../database/dbmovement-operations.md).

## Planned failover

If Microsoft determines that availability of the primary Azure region is at risk (for example, if there is an impending hurricane), we will notify customers and switch over the environment so that it operates out of the secondary region. There will be a short outage while the environment is configured for the secondary region. However, there will be no data loss, because both Azure regions are online and the replication will be caught up.

## Unplanned failover

If an unanticipated region-wide outage occurs (for example, because of a natural disaster such as an earthquake), and Microsoft determines that the region won't become available within a reasonable amount of time, we will notify customers and switch over the environment so that it operates out of the secondary region. In this case, customers might experience data loss of up to 15 minutes, depending on the nature and timing of the outage.

> [!IMPORTANT]
> While the environment is operating out of the secondary region, the Finance and Operations app environment will have reduced functionality. Financial Reporting and Power BI reporting won't be available. If Financial Reporting is critical for a customer during the disaster, the customer can request restoration of the service to Microsoft through a support ticket.
>
> Additionally, there might be service degradation of non-production instances. Deployments of new non-production environments might be blocked.

## Failback

When Microsoft determines that the primary region is back online and fully operational, we will notify customers and switch over the environments so that they once again operate out of the primary region. The service, including all non-production instances, is fully restored. There will be no data loss.
