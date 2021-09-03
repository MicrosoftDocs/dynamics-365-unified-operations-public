---
title: Scale units in a distributed hybrid topology
description: This topic provides information about cloud and edge scale units for manufacturing and warehouse management workloads.
author: cabeln
ms.date: 04/22/2021
ms.topic: article
# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: cabeln
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

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management (*available April 2021*)
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management (*available soon*)

Workload capabilities are being released on a continuous basis through incremental enhancements.

## Scale units and dedicated workloads

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the edge, on-premises at your local facility.

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units.":::

Scale units provide resilience, reliability, and scale for the assigned workloads. Edge scale units can be temporarily disconnected from the cloud hub environment, and workers continue to work in the assigned workloads on the edge.

A *workload* is a defined set of business functionality that can be factored out and delegated to a scale unit. Although the workload for warehouse management has been released, the workload for manufacturing execution is still in preview.

You can configure your hub environment and cloud scale units for selected workloads by using the [Scale Unit Manager portal](https://sum.dynamics.com). You can also assign multiple workloads per scale unit. For information about the prerequisites and limitations for cloud scale units in the current release, see the [Prerequisites and limitations for cloud scale units](#cloud-scale-unit-prerequisites) section later in this topic.

### Dedicated warehouse management workload capabilities in a scale unit

The warehouse management workload is the first distributed workload for scale units that has been released for general availability.

For warehouse management, scale units deliver the following capabilities:

- The system can process selected wave methods for sales orders and demand replenishment.
- Warehouse workers can run sales and demand replenishment warehouse work by using the Warehouse Management mobile app.
- Warehouse workers can inquire into on-hand inventory by using the Warehouse Management mobile app.
- Warehouse workers can create and run inventory movements by using the Warehouse Management mobile app.
- Warehouse workers can register purchase orders and do putaway by using the Warehouse Management mobile app.

For more information, see [Warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md).

### Dedicated manufacturing execution workload capabilities in a scale unit

The first release of the manufacturing workload is currently in preview and delivers the following capabilities:

- Machine operators and shop floor supervisors can access the operational production plan.
- Machine operators can keep the plan up to date by running discrete and process manufacturing jobs.
- The shop floor supervisor can adjust the operational plan.
- Workers can access time and attendance for clock-in and clock-out on the edge to ensure correct worker pay calculation.

For more information, see [Manufacturing execution workloads for cloud and edge scale units](cloud-edge-workload-manufacturing.md).

## Considerations before you enable the distributed, hybrid topology for Supply Chain Management

By enabling the distributed, hybrid topology, you transition your Supply Chain Management cloud environment so that it functions as a hub. You can also associate additional environments that are configured as scale units in the cloud or on the edge.

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

When you enable your Dynamics 365 environment to support the distributed, hybrid topology for cloud and edge scale units, some management services will be hosted only in the United States, as for LCS. This behavior affects the transfer and storage of some administrative and configuration information that is used by the [Scale Unit Manager portal](https://sum.dynamics.com). Here are some examples:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator and project owner email addresses that are used for sign-in
- Environment IDs for the hub and scale units
- Workload configurations, including the names and physical addresses of legal entities and facilities, so that your topology can be shown on a geographic map
- Collected metrics (such as latency and throughput) that will be shown on the map analysis page to help you select the most beneficial use of your scale units

Data that is transferred to and stored in the US data centers will be deleted according to Microsoft data retention policies. Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Onboarding in two stages

The process of onboarding to the distributed, hybrid topology has two stages. During the first stage, you must validate customizations to ensure that they work in the distributed topology that has scale units. Sandbox and production environments are moved only during the second stage.

### Stage 1: Evaluate customizations in one-box development environments

Before you start to onboard your sandbox or production environments, we recommend that you explore scale units in a development setup, such as a one-box environment (also known as a tier-1 environment), so that you can validate processes, customizations, and solutions. During this stage, data and customizations will be applied to the one-box environments. One environment takes the role of the hub, and the other takes the role of a scale unit. This setup provides the best way to identify and fix issues. The latest early access (PEAP) build can also be used to complete this stage.

For stage 1, you should use the [scale unit deployment tools for one-box development environments](https://github.com/microsoft/SCMScaleUnitDevTools). These tools let you configure hub and scale units in one or two separate one-box environments. The tools are provided as a binary release and in source code on GitHub. Study the project wiki, which includes a [Step by step usage guide](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide) that describes how the tools are used.

### Stage 2: Acquire add-ins, and deploy in your sandbox and production environments

To onboard one of your sandbox or production environments to the new topology, you must acquire add-ins for one or more cloud scale units (and, in the future, for edge scale units). The add-ins will grant corresponding project and environment slots in [LCS](https://lcs.dynamics.com/) so that the scale unit environments can be deployed.

> [!NOTE]
> The scale unit add-ins aren't coupled to a limited number of users but can be used by any user in the existing subscription, based on the roles that the administrator assigns.

Scale units are offered in multiple stock keeping units (SKUs) and pricing options. Therefore, you can choose the option that best meets your planned monthly transaction volume and performance requirements.

The entry-level SKU is known as *Basic*, and the more performant SKU is known as *Standard*. Each SKU is pre-loaded with a specific number of monthly transactions. However, you can increase the monthly transaction budget by adding overage add-ins for each SKU.

:::image type="content" source="media/SKUs-highlevel.png" alt-text="Add-ins for cloud scale units.":::

> [!TIP]
> To identify the sizing that best meets your needs, work with your partner and Microsoft to understand the monthly transaction size that you require.

The purchase of each scale unit add-in not only gives you a monthly volume of transactions but also entitles you to a specific number of environment slots in LCS. For each Cloud Scale Unit Add-in, you're entitled to one new production slot and one new sandbox slot. During the onboarding process, a new LCS project will be added that has these slots. The usage rights for the slots are bound so that the slots must be used as scale units that have a cloud hub.

Overage add-ins don't entitle you to new environment slots.

If you want to acquire more sandbox environments, you can purchase additional regular sandbox slots. Microsoft can then help you enable those slots as sandbox scale units for the hybrid topology.

## Onboard to the distributed, hybrid topology for Supply Chain Management

### Select your LCS project tenant and the detailed onboarding process

After you've finished planning how you will onboard to the distributed, hybrid topology for Supply Chain Management, you will use the [Scale Unit Manager portal](https://aka.ms/SCMSUM) to begin the onboarding process. In the portal, select the **Dynamics 365 Tenants** tab. This tab shows the list of tenants that your account is part of, and where you're an owner or environment admin for an LCS project.

If the tenant that you're looking for isn't in the list, go to [LCS](https://lcs.dynamics.com/v2), and make sure that you're either an environment admin or a project owner of the LCS project for that tenant. Only Azure Active Directory (Azure AD) accounts from the selected tenant are authorized to complete the sign-up experience.

> [!NOTE]
> After you apply changes to LCS, the list of tenants might take up to 30 minutes to reflect the changes.

For each tenant, the list shows the onboarding status.

:::image type="content" source="media/cloud_edge-EnableHybrid1.png" alt-text="List of tenants on the Dynamics 365 Tenants tab.":::

Select **Click here to get started** to request onboarding for the LCS tenant. You must accept the terms. You must also supply a business email address where Microsoft can send communications that are related the onboarding process.

:::image type="content" source="media/cloud_edge-EnableHybrid2.png" alt-text="Sign-up submission for a tenant.":::

Microsoft will review your request and inform you about the next steps by sending an email to the address that you supplied in the sign-up form. Microsoft will be working closely with you to enable scale units in the hybrid topology for your business scenario.

After the onboarding is completed, you can use the port to configure scale units and workloads.

### <a name="scale-unit-manager-portal"></a>Manage cloud scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM), and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale unit and workload management experience.":::

To add one or more scale units that are available in your subscriptions, select **Add scale units**.

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Workload creation.":::

> [!TIP]
> Over time, incremental enhancements will be added to the Scale Unit Manager experience to help make lifecycle management operations easier. The specific capabilities for the current release are documented in an onboarding handbook that is available to customers who are in the process of onboarding to the distributed, hybrid topology for Supply Chain Management. <!-- KFM: Add a link to the handbook when it is published -->

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
