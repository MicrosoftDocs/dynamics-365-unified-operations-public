---
title: Region migration to support zone redundancy FAQ
description: Access frequently asked questions about the migration process and the considerations for supporting zone redundancy.
author: rashmim
ms.author: rashmim
ms.topic: conceptual 
ms.date: 07/03/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Region migration to support zone redundancy FAQ

[!INCLUDE[banner](../includes/banner.md)]

Microsoft Azure provides multiple regions that support [zone redundancy](/azure/reliability/availability-zones-overview). Zone redundancy enables environments to continue to operate seamlessly even when a data center failure or other unforeseen incidents. Zone redundancy enhances the resilience of an environment and helps improve overall service continuity. To use these capabilities, an environment must reside in a [region that supports zone redundancy](/azure/reliability/availability-zones-service-support).

As part of our commitment to Dynamics 365 customers, we plan to proactively migrate all environments to regions that provide robust zone redundancy support.

This article answers frequently asked questions about the migration process and the considerations for supporting zone redundancy.

## Which Azure geographical regions are part of this migration?

| Current (source) | New (target) |
| --- | --- |
| Canada East | Canada Central |
| Australia Southeast | Australia East |
| South India | Central India |
| Japan West | Japan East |
| UK West | UK South |
| China North 2 | China North 3 |
| China East 2 | China North 3 |

> [!NOTE]
> As part of the migration effort, the current regions aren't available to finance and operations apps customers for new sandbox and production environment provisioning using Lifecycle Services. Microsoft continues to support all customer environments in their existing regions until the migration is completed for all environments in customers' Lifecycle Services projects.

## What types of environments are being migrated?

We plan to migrate all sandbox and production environments in a Lifecycle Services project. There's no impact on data movement or servicing actions if environments in the same Lifecycle Services project are in different regions before or after a migration.

## What are the integration impacts and other considerations for this migration?

- Before the migration, we recommend that you review integrations or other dependencies that might be sensitive to network latency.
- We recommend that you review all your Azure resources in your current region and assess whether they must be colocated in the new region.
- If your external components have no IP dependencies, no action is required. If your external components have no dependencies on an explicit inclusion list of IPs or special handling of outbound IP addresses for routing or firewall, no action is required.
- If any of your external components have special handling for the outbound IP addresses to communicate with Application Object Server (AOS), review the configuration. If the PowerPlatformPlex service tag is used, no changes are required. If specific IP ranges are listed, we recommend that you switch to using the service tag. If you must specify the IP ranges, you can find the target region's ranges by using the Service Tag Discovery API or the downloadable JavaScript Object Notation (JSON) files. For example, an outbound IP address might be explicitly included in a firewall outside your AOS instance, or an external service might have an allowed list that contains the outbound IP address for your AOS instance. For more information, such as information about how to get the specific IP address ranges for components that don't support service tags, see the [service tag documentation](/azure/virtual-network/service-tags-overview).
- There's no perceived impact on dual-write, virtual entities, or any finance and operations apps add-ins that have a dependency on Dataverse.
- If you've deployed reports and customized them in Power BI, you can use [Resolve Issues with Power BI](../../dev-itpro/analytics/entity-store-maintenance.md) to republish your reports post-migration. Note that customizations can't be automatically restored after republishing and must be redone manually.

## What's the user experience for customers during this migration?

Users can expect downtime during the planned migration within the [region's maintenance window](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/planned-maintenance-window-faq). The duration varies, depending on the database and storage account size of your environment's storage footprint. Detailed downtime information is provided in a notification email before the migration.

## How is Microsoft notifying its customers about this migration?

Customers are notified about planned migrations for every implementation project or set of environments through email and message center five business days in advance.

## How does this migration affect environments that include Dynamics 365 Commerce Scale Unit?

Migration of Commerce Scale Unit (CSU) isn't included in the planned region migration. There's no known impact, because CSU isn't moving to the new region.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
