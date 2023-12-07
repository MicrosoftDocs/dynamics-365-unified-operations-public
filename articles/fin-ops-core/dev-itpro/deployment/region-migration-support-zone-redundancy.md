# Region migration to support zone redundancy

Microsoft Azure provides multiple regions with the capability of [zone redundancy](/azure/reliability/availability-zones-overview), which enables environments to continue to operate seamlessly even in the event of a data center failure or other unforeseen incidents. Zone redundancy enhances the resilience of the environment and improves overall service continuity. To leverage these capabilities, the environment needs to reside in a [region that supports](/azure/reliability/availability-zones-service-support) zone redundancy.

As part of our commitment to Microsoft Dynamics 365 customers we plan to proactively realign all environments to regions with robust zone redundancy support.

This article answers frequently asked questions about the migration process and the considerations.

## Which Azure geographical regions will be part of this migration?

| **Current (Source)** | **New (Target)** |
| --- | --- |
| Canada East | Canada Central |
| Australia Southeast | Australia East |
| South India | Central India |
| Japan West | Japan East |
| UK West | UK South |

> [!NOTE]
> As part of the migration effort, effective January 2024,the current regions will no longer be available to finance and operations apps customers for new environment provisioning using Lifecycle Services. Microsoft will continue to support all customer environments in their existing regions until the migration is complete for all the environments for their Lifecycle Services project(s).

## What type of environments will be migrated?

We plan to migrate all sandbox and production environments in a Lifecycle Services project. There isn't an impact to data movement or servicing actions if environments in the same Lifecycle Services project are in different regions after a migration.

## What is the timeline for migration completion?  

All the environments in Canada East, Australia Southeast, South India, Japan West and UK West are planned to move to the target regions by end of March 2024.

## What is the integration impact and other considerations for these migrations?

- Prior to migration it's recommended to review integrations or other dependencies that may be sensitive to network latency.
- It is recommended to review all your Azure resources in your current region and assess if they need to be co-located in the new region.

- If your external components don't have any IP dependencies, no action is needed. If your external components don't have dependencies on an explicit inclusion list of IPs or special handling of outbound IP addresses for routing or firewall, no action is required.
- If any of your external components have special handling for the outbound IP addresses to communicate with the AOS, review the configuration. If the PowerPlatformPlex service tag is used, no changes are required. If specific IP ranges are listed we recommend switching to use the service tag. If you need to specify the IP ranges you can find the target region's ranges by using the Service Tag Discovery API or using the downloadable JSON files. For example, an outbound IP address may be explicitly included in a firewall outside your AOS, or an external service may have an allowed list that contains the outbound IP address for your AOS. For more information, see the [Service Tag Documentation](/azure/virtual-network/service-tags-overview), such as how to get the specific IP address ranges for components that don't support Service Tags.
- There isn't a perceived impact on dual-write, virtual entities, or any finance and operations apps add-ins that have dependence on Dataverse.

## What will be the end user experience for customers during this migration?  

End users can expect downtime during our planned migration within the [region's maintenance window](../dev-itpro/lifecycle-services/planned-maintenance-window-faq.md). Duration varies based on the database and storage account size of your environment's storage footprint. Detailed downtime information will be provided in a notification email before the migration.

## How are we notifying customers about migration?  

Customers will be notified about planned migrations for every implementation project or set of environments through email and message center 5-7 business days in advance.

## How will this affect environments with Microsoft Dynamics 365 Commerce Scale Unit (CSU)?

Migration of CSU isn't included with the planned region migration. There is no known impact because of CSU not moving to the new region.
