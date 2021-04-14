---
title: Use scale units to increase resilience for supply chain management workloads
description: This topic provides information about cloud and edge scale units for manufacturing and warehouse management workloads.
author: cabeln
ms.date: 04/13/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: cabeln
ms.search.validFrom: 2021-04-13
ms.dyn365.ops.version: 10.0.19
---
 
# Use scale units to increase resilience for supply chain management workloads

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The scale unit capability for Supply Chain Management is made available to you under the terms that govern the use of the service [legal terms for Finance and Operations](https://go.microsoft.com/fwlink/?LinkID=290927).
>
> By enabling cloud and edge scale units, you affirm that you understand that some data that is related to the configuration and processing of cloud and edge scale units might be stored in a data center that is located in the United States. To learn more about the data processing with cloud and edge scale units, see the [data processing documentation](#data-processing-when-managing-scale-units).

## The core value proposition for scale units

Companies that work with manufacturing and distribution must be able to run key business processes 24/7, without interruption and at scale. Cloud and edge scale units enable companies to run key mission-critical manufacturing and warehouse processes without interruption, even when faced with occasional network connectivity or latency issues.

Cloud and edge scale units enable distribution of shop floor and warehouse execution workloads among different environments. This functionality can help improve performance, prevent service interruptions, and maximize uptime. Scale units are provided through the following add-ins for your Supply Chain Management subscription:

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management (*available in April 2021*)
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management (*available soon*)

Workload capabilities are being release on a continuous basis with incremental enhancements.

## Scale units and dedicated workloads

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the edge, on-premises at your local facility.

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units":::

Scale units provide resilience, reliability, and scale for the assigned workloads. Edge scale units can be temporarily disconnected from the cloud hub environment and workers continue with the work in the assigned workloads on the edge.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit.
The workload for warehouse management has been released, while the manufacturing execution workload is still in preview.

You can configure your hub environment and  cloud scale units for selected workloads by using the [Scale Unit Manager portal](https://sum.dynamics.com). You can also assign  multiple workloads per scale unit. See also the [prerequisites and limitations for cloud scale units](#cloud-scale-unit-prerequisites) for the current release.

### Dedicated warehouse management workload capabilities in a scale unit

The warehouse management workload is the first distributed workload for scale units that has been release in general availability.

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

## What to consider before enabling the distributed hybrid topology for Supply Chain Management

By enabling the hybrid distributed topology, you transition your cloud supply chain management environment to functions as a hub. And you may associate additional environments that are configured as scale units in the cloud or on the edge.

<a name="cloud-scale-unit-prerequisites"></a>

### Prerequisites and limitations for cloud scale units

In the current release for scale units, certain capabilities are not yet available and may be added in incremental releases over time.

#### You must be a licensed customer of Dynamics 365 Supply Chain Management

To onboard to the distributed topology, you must have a license for Dynamics 365 Supply Chain Management. Your existing cloud environment will become the hub in your hybrid topology. You can declare both sandbox and production environments as hub environments and add scale units according to the add-ins you acquire.  

#### Your existing project must be administered via the global commercial version of LCS

Your LCS project must meet the following version requirements:

- Your existing project must be administered via the global commercial version of Lifecycle Services (LCS) at [lcs.dynamics.com](https://lcs.dynamics.com).
- Local versions of LCS are not supported (such as [eu.lcs.dynamics.com](https://eu.lcs.dynamics.com) or [fr.lcs.dynamics.com](https://fr.lcs.dynamics.com)).
- Governmental Cloud versions of LCS are not supported.
- The Mooncake version of LCS is not supported.

#### Your current production environment must be of type "Self-Service" in LCS

Your current production environment must be of type "Self-Service" in LCS. This indicates that the tenant of your LCS project has already been converted to support the Service Fabric hosting model.

> [!IMPORTANT]
> Environment types running as infrastructure as a service (IaaS) are not supported. These are typically are tagged as "Microsoft Managed" in LCS.
>
> If you have this type of environment, please work with your Microsoft contact to understand your migration timeline to "Self-Service".

Microsoft is in the process of transitioning all cloud environments of Supply Chain Management from an IaaS model to a Service Fabric hosted topology. This move brings better scalability and eases service management, which results in faster deployment and maintenance operations. Likewise, service components are migrating to the concept of micro services, and the service hosting model will [transition](https://docs.microsoft.com/virtualization/windowscontainers/about/containers-vs-vm) from a virtual machine (VM) model to a light-weight containerized architecture.

Ultimately the same Service Fabric based containerized service infrastructure will power both cloud and edge instances of the service, be it a hub in the cloud or a scale unit in the cloud or on the edge.

To onboard to the hybrid topology that supports scale units, your project tenant must have been transitioned to the Service Fabric hosted model. Also, any environment that shall act as a hub must have been converted.

> [!TIP]
> To inquire about the status of your LCS project tenant, look up the type of your environment in [LCS](https://lcs.dynamics.com/) or reach out to your partner or Microsoft contact.

#### Local Business Data (on-premises) environments are not supported as hubs for Scale Units

On-premises environments cannot function as a hub for scale units. Hub environments must always be cloud hosted.

#### Limited scale unit management capabilities

Management capabilities to help with the movement of workloads are limited. Certain management operations are not supported in a self-service manner and you might need to request support through your partner or Microsoft contact. Examples include certain workload movements between scale units and temporary ad-hoc movements in disaster scenarios.

#### Metrics and measurements

Metrics and measures that may help with selecting the best application for your scale units are not available yet. Please work with your Microsoft contact or implementation partner to select the most beneficial application.

### Data processing when managing scale units

When enabling your Dynamics 365 environment to support the distributed hybrid topology for cloud and edge scale units, some management services will only be hosted in the United States, similar to LCS. This affects the transfer and storage of certain administrative and configuration information used by the Scale Unit Manager portal, including:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator and project owner emails used to sign in
- Environment IDs for hub and scale units
- Workload configurations including names and physical address of legal entities and facilities that allows displaying your topology on a geographic map.
- Collected metrics (such as latency and throughput) which will be displayed on the map analysis page to help you selecting the most beneficial use of your scale units.

Data transferred to and stored in the US data centers will be deleted according to our data retention policies. Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Onboarding in two stages

Onboarding to the distributed hybrid topology goes through two stages. In the first stage, the customizations must be validated to work in the distributed topology with scale units. Only in the second stage can sandbox and production environments be moved.

### Stage 1: Evaluate customization in one-box development environments

Before you begin with onboarding your sandbox or production environments, we recommend exploring scale units in a development setup (such as a one-box (also known as tier-1) environment) to validate processes, customizations, and solutions. In this phase, data and customizations will be applied to the one-box environments. One environment takes the role of the hub and the other the role of a scale unit. This setup provides the best way to identify and solve issues. This can also be done using the latest early access (PEAP) build.

For Stage 1, you should use the [scale unit deployment tools for one-box development environments](https://github.com/microsoft/SCMScaleUnitDevTools). It allows you to configure hub and scale units in one or two separate one-box environments. The tool is provided as a binary release and in source code on GitHub. Study the project wiki, which includes a [Step by step usage guide](https://github.com/microsoft/SCMScaleUnitDevTools/wiki/Step-by-step-usage-guide) that describes how the tool is used.

### Stage 2: Acquire add-ins and deploy in your sandbox and production environments

To onboard one of your sandbox or production environments to the new topology, you must acquire add-ins for one or more cloud scale units (and in the future also for edge scale units). The add-ins will grant corresponding project and environment slots in [LCS](https://lcs.dynamics.com/) for deploying the scale units environments.

> [!NOTE]
> The scale unit add-ins are not coupled to a limited number of users but can be used by any user in the existing subscription, based on the roles the administrator assigns.

Scale units are offered in multiple SKUs and pricing options that you can chose to best match the planned monthly transaction volume and performance requirements.

The entry level SKU is called *Basic*, the more performing model is *Standard*. Each SKU comes loaded with a specific number of monthly transactions. Additional overage add-ins can be added for each to increase the monthly transaction budget.

:::image type="content" source="media/SKUs-highlevel.png" alt-text="Add-ins for cloud scale units":::

> [!TIP]
> To identify the best sizing fit, work with your partner and Microsoft to understand your required monthly transaction size.

The purchase of each scale unit add-in not only gives you a monthly volume of transactions, but also entitlements for a specific number of environment slots in LCS. For each Cloud Scale unit Add-in, you are entitled to one new production and one new sandbox slot. In the onboarding process, a new LCS project will be added with these slots. The usage rights for the slots are bound to be used as scale units with a cloud hub.

Overage add-ins do not entitle new environments slots.

If you wish to acquire more sandbox environments, you can do so by purchasing additional regular sandbox slots, which Microsoft can help you to enable for the hybrid topology as sandbox scale units.

## Onboard to the distributed hybrid topology for Supply Chain Management

### Select your LCS project tenant and the detailed onboarding process

After you have planned on how to onboard to the distributed hybrid topology for supply chain management, you will use the [Scale Unit Manager portal](https://aka.ms/SCMSUM) to commence the onboarding. In the portal, navigate to the tab **Dynamics 365 Tenants**, where you will find the list of tenants that your account is part of, and where you're an owner or environment admin for an LCS project.

If the tenant that you're looking for isn't in this list, go to [LCS](https://lcs.dynamics.com/v2) and make sure that you're either an environment admin or a project owner of the LCS project for that tenant. Only Azure Active Directory (Azure AD) accounts from the selected tenant are authorized to complete the sign-up experience.

> [!NOTE]
> After you apply changes to LCS, it might take up to 30 minutes for the list of tenants to reflect the changes.

For each tenant, the list shows the onboarding status.

:::image type="content" source="media/cloud_edge-EnableHybrid1.png" alt-text="Sign-up option for a tenant":::

Select the **Click here to get started** link to request onboarding for the LCS tenant. You must accept the terms. You must also supply a business email address where Microsoft may send communications that are related the onboarding process.

:::image type="content" source="media/cloud_edge-EnableHybrid2.png" alt-text="Sign-up submission for a tenant":::

Microsoft will review your request and inform you about the next steps by sending an email to the address that you supplied on the sign-up form. We will be working closely with you to enable scale units in the hybrid topology for your business scenario.

After the onboarding is complete, you will be able to configure scale units and workloads using the portal.

### <a name="scale-unit-manager-portal"></a>Manage cloud scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM) and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale unit and workload management experience":::

To add one or more scale units that are available in your subscriptions, select **Add scale units**.

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Workload creation":::

> [!Tip]
> Over time, incremental enhancements will be added to the Scale Unit Manager experience to ease lifecycle management operations. The specific capabilities for the current release are documented in an onboarding handbook which is available to customers in the process of onboarding to the distributed hybrid topology for supply chain management. <!-- KFM: Add a link to the handbook when it is published -->

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
