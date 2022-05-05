---
title: Scale units in a distributed hybrid topology
description: This topic provides information about cloud and edge scale units for manufacturing and warehouse management workloads.
author: Mirzaab
ms.date: 04/22/2021
ms.topic: article
ms.search.form: ScaleUnitWorkloadsWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mirzaab
ms.search.validFrom: 2021-04-13
ms.dyn365.ops.version: 10.0.19
---

# Scale units in a distributed hybrid topology

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The scale unit capability for Microsoft Dynamics 365 Supply Chain Management is made available to you under the terms that govern the use of the service. For more information, see [Microsoft Dynamics Legal Information](https://go.microsoft.com/fwlink/?LinkID=290927).
>
> When you enable cloud and edge scale units, you will be asked to affirm that you understand that some data that is related to the configuration and processing of cloud and edge scale units might be stored in a data center that is located in the United States. To learn more about data processing for cloud and edge scale units, see the [Data processing during management of scale units](#data-processing-management) section later in this topic.

## Core value proposition for a distributed hybrid topology

Companies that work with manufacturing and distribution must be able to run key business processes 24/7, without interruption and at scale. A distributed hybrid topology enables companies to run key mission-critical manufacturing and warehouse processes without interruption, even when faced with occasional network connectivity or latency issues.

A distributed hybrid topology introduces the concept of *scale units*, which enable distribution of shop floor and warehouse execution workloads among different environments. This functionality can help improve performance, prevent service interruptions, and maximize uptime. Scale units are provided through the following add-ins for your Supply Chain Management subscription:

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management

Workload capabilities are being released on a continuous basis through incremental enhancements.

## Scale units and dedicated workloads

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the [edge](cloud-edge-edge-scale-units-lbd.md), on-premises at your local facility.

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units.":::

Scale units provide resilience, reliability, and scale for the assigned workloads. Edge scale units can be temporarily disconnected from the cloud hub environment, and workers continue to work in the assigned workloads on the edge.

A *workload* is a defined set of business functionality that can be factored out and delegated to a scale unit. Although the workload for warehouse management has been released, the workload for manufacturing execution is still in preview.

You can configure your hub environment and cloud scale units for selected workloads by using the [Scale Unit Manager portal](https://sum.dynamics.com). You can also assign multiple workloads per scale unit. For information about the prerequisites and limitations for cloud scale units in the current release, see the [Prerequisites and limitations for cloud scale units](#cloud-scale-unit-prerequisites) section later in this topic.

### Dedicated warehouse management workload capabilities in a scale unit

The warehouse management workload enables your warehouse operations to scale and run in a resilient environment by using isolated maintenance windows. The warehouse management workload supports most enterprise hub warehouse management processes. For more information, see [Warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md).

### Dedicated manufacturing execution workload capabilities in a scale unit

The manufacturing workload delivers the following capabilities:

- Machine operators and shop floor supervisors can access the operational production plan.
- Machine operators can keep the plan up to date by running discrete and process manufacturing jobs.
- The shop floor supervisor can adjust the operational plan.
- Workers can access time and attendance for clock-in and clock-out on the edge to ensure correct worker pay calculation.

For more information, see [Manufacturing execution workloads for cloud and edge scale units](cloud-edge-workload-manufacturing.md).

## Considerations before you enable the distributed hybrid topology for Supply Chain Management

By enabling the distributed hybrid topology, you transition your Supply Chain Management cloud environment so that it functions as a hub. You can also associate additional environments that are configured as scale units in the cloud or on the edge.

### <a name="cloud-scale-unit-prerequisites"></a>Prerequisites and limitations for cloud scale units

In the current release for scale units, some capabilities aren't yet available but might be added in incremental releases over time.

#### You must be a licensed customer of Supply Chain Management

To onboard to the distributed topology, you must have a license for Supply Chain Management. Your existing cloud environment will become the hub in your hybrid topology. You can declare both sandbox environments and production environments as hub environments, and you can add scale units according to the add-ins that you acquire.

#### Your existing project must be administered via the global commercial version of LCS

Your existing Microsoft Dynamics Lifecyle Services (LCS) project must meet the following version requirements:

- The project must be administered via the global commercial version of LCS at [lcs.dynamics.com](https://lcs.dynamics.com).
- Local versions of LCS (such as [eu.lcs.dynamics.com](https://eu.lcs.dynamics.com) and [fr.lcs.dynamics.com](https://fr.lcs.dynamics.com)) aren't supported.
- Governmental Cloud versions of LCS aren't supported.
- The Mooncake version of LCS isn't supported.

#### Your current production environment must be of the Self-Service type in LCS

Your current production environment must be tagged with the **Self-Service** type in LCS. This type indicates that the tenant of your LCS project has already been converted so that it supports the Azure Service Fabric hosting model.

> [!IMPORTANT]
> Environment types that run as infrastructure as a service (IaaS) aren't supported. These environments are typically tagged with the **Microsoft Managed** type in LCS. If you have environments of this type, work with your Microsoft contact to understand your migration timeline to the **Self-Service** type.

Microsoft is in the process of transitioning all cloud environments of Supply Chain Management from an IaaS model to a topology that is hosted in Service Fabric. This move brings better scalability and helps make service management easier. Therefore, deployment and maintenance operations are faster. Likewise, service components are being migrated to the concept of microservices, and the service hosting model will [transition](/virtualization/windowscontainers/about/containers-vs-vm) from a virtual machine (VM) model to a lightweight containerized architecture.

Ultimately, the same Service Fabric–based containerized service infrastructure will power both cloud and edge instances of the service, regardless of whether an instance is a hub in the cloud, or a scale unit in the cloud or on the edge.

Before you can onboard to the hybrid topology that supports scale units, your project tenant must be transitioned to the Service Fabric–hosted model. Additionally, any environment that will act as a hub must be converted.

> [!TIP]
> To inquire about the status of your LCS project tenant, look up the type of your environment in [LCS](https://lcs.dynamics.com/), or reach out to your partner or Microsoft contact.

#### Local business data (on-premises) environments aren't supported as hubs for scale units

On-premises environments can't function as hubs for scale units. Hub environments must always be cloud hosted.

#### Scale unit management capabilities are limited

Management capabilities that can help with the movement of workloads are limited. Some management operations aren't supported in a self-service manner, and you might have to request support through your partner or Microsoft contact. Examples include some workload movements between scale units and temporary ad-hoc movements in disaster scenarios.

#### Metrics and measurements aren't yet available

Metrics and measures that might help you select the best application for your scale units aren't yet available. Work with your Microsoft contact or implementation partner to select the most beneficial application.

### <a name="data-processing-management"></a>Data processing during management of scale units

When you enable your Dynamics 365 environment to support the distributed hybrid topology for cloud and edge scale units, some management services will be hosted only in the United States, as for LCS. This behavior affects the transfer and storage of some administrative and configuration information that is used by the [Scale Unit Manager portal](https://sum.dynamics.com). Here are some examples:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator and project owner email addresses that are used for sign-in
- Environment IDs for the hub and scale units
- Workload configurations, including the names and physical addresses of legal entities and facilities, so that your topology can be shown on a geographic map
- Collected metrics (such as latency and throughput) that will be shown on the map analysis page to help you select the most beneficial use of your scale units

Data that is transferred to and stored in the US data centers will be deleted according to Microsoft data retention policies. Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Onboard to the distributed hybrid topology for Supply Chain Management

### Try out the distributed hybrid topology

The process of onboarding to the distributed hybrid topology has two stages. During the first stage, you should [try out](cloud-edge-try-out.md) the solution and validate your customizations to make sure that they work in a distributed topology that includes scale units. (You can use existing development environments to do the validation.) You can then continue to the second stage, where you acquire production environments.

## Select your LCS project tenant and the detailed onboarding process

Scale units are offered in multiple stock keeping units (SKUs) and pricing options. Therefore, you can choose the option that best meets your planned monthly transaction volume and performance requirements.

> [!TIP]
> To identify the sizing that best meets your needs, work with your implementation partner and Microsoft to understand the monthly transaction size that you require.

The entry-level SKU is known as *Basic*, and the more performant SKU is known as *Standard*. Each SKU is pre-loaded with a specific number of monthly transactions. However, you can increase the monthly transaction budget by adding overage add-ins for each SKU.

:::image type="content" source="media/SKUs-highlevel.png" alt-text="Add-ins for cloud scale units.":::

> [!NOTE]
> Scale unit add-ins aren't coupled to a limited number of users. They are available to any user in your existing subscription (provided that your administrator has assigned the required user roles to them).

The purchase of each scale unit add-in not only gives you a monthly volume of transactions but also entitles you to a specific number of environment slots in LCS. For each Cloud Scale Unit Add-in, you're entitled to one new production slot and one new sandbox slot. During the onboarding process, a new LCS project will be added that has these slots. The usage rights for the slots are bound so that the slots must be used as scale units that have a cloud hub.

Overage add-ins don't entitle you to new environment slots.

If you want to acquire more sandbox environments, you can purchase additional regular sandbox slots. Microsoft can then help you enable those slots as sandbox scale units for the hybrid topology.


After you've finished planning how you will onboard to the distributed hybrid topology for Supply Chain Management, you will use the [Scale Unit Manager portal](https://aka.ms/SCMSUM) to begin the onboarding process. In the portal, select the **Dynamics 365 Tenants** tab. This tab shows the list of tenants that your account is part of, and where you're an owner or environment admin for an LCS project.

If the tenant that you're looking for isn't in the list, go to [LCS](https://lcs.dynamics.com/v2), and make sure that you're either an environment admin or a project owner of the LCS project for that tenant. Only Azure Active Directory (Azure AD) accounts from the selected tenant are authorized to complete the sign-up experience.

> [!NOTE]
> After you apply changes to LCS, the list of tenants might take up to 30 minutes to reflect the changes.

For each tenant, the list shows the onboarding status.

:::image type="content" source="media/cloud_edge-EnableHybrid1.png" alt-text="List of tenants on the Dynamics 365 Tenants tab.":::

Select **Click here to get started** to request onboarding for the LCS tenant. You must accept the terms. You must also supply a business email address where Microsoft can send communications that are related the onboarding process.

:::image type="content" source="media/cloud_edge-EnableHybrid2.png" alt-text="Sign-up submission for a tenant.":::

Microsoft will review your request and inform you about the next steps by sending an email to the address that you supplied in the sign-up form. Microsoft will be working closely with you to enable scale units in the hybrid topology for your business scenario.

After the onboarding is completed, you can use the port to configure scale units and workloads.

### <a name="scale-unit-manager-portal"></a>Manage scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM), and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale Unit Manager portal, Configure scale units page.":::

To add one or more scale units that are available in your subscriptions, select **Add scale units**.

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Define workloads dialog.":::

#### <a name="manage-workloads"></a>Manage workloads

When one or more workloads are enabled, use the **Manage workloads** option to initiate and manage processes such as those that are listed in the following table.

| Process | Description |
|---|---|
| Pause scale unit communication | Pause pipeline messages between the hub and a scale unit. This process will stop the communication and drain the data pipeline between the hub and scale units. You must run this process before you run a Supply Chain Management servicing operation on either the hub or the scale unit, but you may also use this in other situations. |
| Resume scale unit communication | Resume pipeline messages between the hub and a scale unit. You might have to use this process, for example, after you run a Supply Chain Management servicing operation on either the hub or the scale unit. |
| Upgrade workloads | Sync new functionality between the hub and scale unit workloads. You might have to use this process, for example, when servicing has caused the data exchange queries to change, and/or has added new tables or fields to the workload. |
| Transfer workloads to a scale unit | Schedule a workload that is currently running on the hub to be moved to a scale unit. When this process is run, the synchronization of data will flow, and both the hub and the scale unit will be set to change the ownership of the workload. |
| Transfer scale unit to the hub | Schedule a workload that is currently running on a scale unit to be moved to the hub. When this process is run, the synchronization of data will flow, and both the hub and the scale unit will be set to change the ownership of the workload.
| Emergency transition to hub | <p>Immediately transfer an existing workload to the hub. *This process will change the ownership of only the data that is currently available on the hub.*</p><p><strong>Warning:</strong> This process can cause data loss for unsynchronized data and failure of business processing. Therefore, it should be used only in emergencies, where business processes must be processed on the hub because the scale unit has an outage that can't be mitigated within a reasonable time.</p> |
| Decommission distributed topology | Remove a scale unit deployment and run only on the hub, without workload processing. |

:::image type="content" source="media/sum-manage-workloads.png" alt-text="Scale unit and workload management experience.":::

> [!TIP]
> Over time, incremental enhancements will be added to the Scale Unit Manager experience to help make lifecycle management operations easier. The specific capabilities for the current release are documented in an onboarding handbook that is available to customers who are in the process of onboarding to the distributed hybrid topology for Supply Chain Management. <!-- KFM: Add a link to the handbook when it is published -->

## Feature management considerations for workloads

This section explains some important aspects that you should consider when you install workloads, add features, or remove features in a distributed hybrid topology deployment. Several scenarios can influence whether you will have to run a [workload upgrade](#manage-workloads) after you make changes. However, you will usually have to do so when you update or add new data exchange queries, and/or when you add new tables or fields to a previously installed workload.

### Mandatory features for installing a workload

When you install a workload, the installation process creates a workload definition that contains information about the data tables that are used when data is synced between the two deployments. The creation of a workload definition is automatically handled based on the features that are currently enabled in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). The following table lists the features that must be enabled to generate the workload definitions that are required to run a warehouse or manufacturing workload.

| Mandatory feature | Workload |
|---|---|
| Automatic assigning of the guids on WHS user creation | Warehouse |
| Organization-wide work blocking | Warehouse |
| Shipment wave label details | Warehouse |
| Scale unit support for warehouse app work lists | Warehouse |
| Production floor execution | Manufacturing |

When you deploy a workload by using the [scale unit deployment tools for one-box development environments](https://github.com/microsoft/SCMScaleUnitDevTools) or the [scale unit manager portal](https://sum.dynamics.com), all the mandatory features will automatically be enabled. However, if you do a manual test deployment that is missing one or more mandatory features, the workload installation will fail, and you will receive a message that lists the missing features. You must then manually enable those features and retrigger the workload installation.

### Enabling or disabling features that have data synchronization dependencies

Features that affect the selection of data that is synced between the hub and its scale units also affect how the workload definition is created. Therefore, it's important that these features be enabled before you install the workload. If you enable this type of feature while you're running a workload, you must regenerate the workload definition by running a [workload upgrade](#manage-workloads) after you enable the feature. Likewise, if you disable a feature that has data synchronization dependencies while you're running a workload, you must run a [workload upgrade](#manage-workloads) to remove the relevant data synchronization information from the workload definition.

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
