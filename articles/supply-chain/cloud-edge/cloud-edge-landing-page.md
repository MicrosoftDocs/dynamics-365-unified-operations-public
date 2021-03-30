---
# required metadata

title: Use scale units to increase resilience for supply chain management workloads
description: This topic provides information about cloud and edge scale units for manufacturing and warehouse management workloads.
author: cabeln
manager: 
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: cabeln
ms.search.validFrom: 2021-03-10
ms.dyn365.ops.version: 10.0.20
---
 
# Use scale units to increase resilience for supply chain management workloads

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The scale unit capability for Supply Chain Management is made available to you under the terms that govern the use of the service [legal terms for Finance and Operations](https://go.microsoft.com/fwlink/?LinkID=290927).
>
> By enabling cloud and edge scale units, you affirm that you understand that some data that is related to the configuration and processing of cloud and edge scale units might be stored in a data center that is located in the United States. To learn more about the data processing with cloud and edge scale units, see the [**documentation**](cloud-edge-landing-page.md#data-processing-in-the-distributed-hybrid-topology-using-scale-units).

**The core value proposition for scale units:**

Companies that work with manufacturing and distribution must be able to run key business processes 24/7, without interruption and at scale. Cloud and edge scale units enable companies to run key mission-critical manufacturing and warehouse processes without interruption, even when faced with occasional network connectivity or latency issues.

Cloud and edge scale units enable distribution of shop floor and warehouse execution workloads among different environments. This functionality can help improve performance, prevent service interruptions, and maximize uptime. Scale units are provided through add-ins for your supply chain subscription.

- **Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management**
 (*available by 1st of April* 2021)
- **Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management** (*available in the future*)

Workload capabilities are being release on a continuous basis with incremental enhancements.

## Scale units and dedicated workloads

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units":::

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the edge at your local facility premises. Scale units can temporarily be disconnected from the hub environment. When they are connected, scale units receive all the information that is required to run the dedicated processing for assigned workloads.

You can configure your hub environment and  cloud scale units for selected workloads by using the [Scale Unit Manager](https://sum.dynamics.com) portal.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit.
The workload for warehouse management has been released, while the manufacturing execution workload is still in preview.

You can assign multiple workloads per scale unit. (Please refer to [limitations](#limitations-that-apply-during-the-preview-period) in your release)

### Dedicated warehouse management workload capabilities in a scale unit

The warehouse management workload is the first distributed workload for scale units that has been release in general availability.

For warehouse management, scale units deliver the following capabilities:

- Processing of selected wave methods is enabled for sales orders and demand replenishment.
- Warehouse workers can run sales and demand replenishment warehouse work by using the warehouse app.
- Warehouse workers can inquire into on-hand inventory by using the warehouse app.
- Warehouse workers can create and run inventory movements by using the warehouse app.
- Warehouse workers can register purchase orders and do putaway by using the warehouse app.

For more information, see the [warehouse scale unit workload details](cloud-edge-workload-warehousing.md).

### Dedicated manufacturing execution workload capabilities in a scale unit

The first release of the manufacturing workload is in preview at this moment and  delivers the following capabilities:

- Machine operators and shop floor supervisors can access the operational production plan.
- Machine operators can keep the plan up to date by running discrete and process manufacturing jobs.
- The shop floor supervisor can adjust the operational plan.
- Workers can access time and attendance for clock-in and clock-out on the edge, to ensure correct worker pay calculation.

For more information, see the [manufacturing scale unit workload details (in preview)](cloud-edge-workload-manufacturing.md).

## What to consider before enabling the distributed hybrid topology for Supply Chain Management

By enabling the hybrid distributed topology you transition your supply chain management environment in the cloud to functions as a hub that may be supported by additional environments configured as scale units in the cloud or on the edge.

### Prerequisites

Microsoft is in the process of transitioning all cloud environments of SCM from an IaaS model to Service Fabric hosted topology. The move brings better scalability, eases the service management which results in faster deployment and maintenance operations. The service components migrate into the concept of micro services, and the service hosting model [transitions](/virtualization/windowscontainers/about/containers-vs-vm) from VM model to light weight containerized architecture.

Ultimately the same service fabric based containerized service infrastructure will power both cloud and edge instances of the service, be it a hub in the cloud or a scale unit in the cloud or on the edge.

**To onboard to the hybrid topology supporting scale units your project Tenant must have been transitioned to the Service Fabric hosted model.**

Therefore, new environments will be created in Service Fabric. You might have still older existing environments that still run as IaaS until converted. Please note that your planned hub environment must have been converted to Service Fabric. Until then you can create new environments for hub and scale units, which will suffice the requirements – if the LCS project tenant has already been enabled for Service Fabric.

> [!TIP]
> Reach out to your Microsoft contact if you need to inquire about the status of your LCS project tenant.

### Onboarding in two stages

Onboarding to the distributed hybrid topology 

#### Stage 1: Evaluate customization in one-box development environments

Before you begin with onboarding your sandbox or production environments we recommend exploring scale units in a development setup (one-box aka. Tier1 environments) to validate processes, customizations and solutions. In this phase data and customizations will be applied to the one-box environments. One environment takes the role of the hub and the other the role of a scale unit. This setup provides the best way to identify and solve issues. This can also be done using the latest early access (PEAP) build.

For Stage 1, the [scale unit deployment tools for one-box development environments](https://github.com/microsoft/SCMScaleUnitDevTools) should be used. It allows you to configure hub and scale units in one or two separate one-box environments. The tool is provided as binary release and in source code on GitHub. Please study the project Wiki with a step by step guide that describes how the tool is used.

#### Stage 2: Acquire add-ins and deploy in your sandbox and production environments

In order to onboard one of your sandbox or production environment to the new topology you must acquire add-ins for one or more cloud scale units (and in the future also for edge scale units). The add-ins will grant corresponding projects and environments slots in [LCS](https://lcs.dynamics.com/) for the purpose of deploying the scale units environments.

> [!NOTE]
> The scale unit add-ins are not coupled to a limited number of users but can be used by any user in the existing subscription, based on the roles the administrator assigns.

Scale units are offered in multiple SKU and pricing options that you can chose to best match the planned monthly transaction volume and performance requirements.
The entry level SKU is called ‘Basic’, the more performing model is ‘Standard’. Each SKU comes loaded with a certain number of monthly transactions. Additional overage add-ins can be added for each to increase the monthly transaction budget.

:::image type="content" source="media/SKUs-highlevel.png" alt-text="Addins for cloud scale units":::

> [!TIP]
> To identify the best fitting sizing customers shall work with their partner and Microsoft to understand the required monthly transaction size.

The purchase of each scale unit add-ins not only gives you a monthly volume of transactions but also entitlements for a certain number of environment slots in LCS. For each Cloud Scale unit Add-in you are entitled to one new production and one new sandbox slot. In the onboarding process a new LCS projects will be added with these slots. The usage right for the slots is bound to be used as scale units with a cloud hub.

Overage add-ins do not entitle new environments slots.

If you wish to acquire mode sand box environments, you can do so by purchasing additional regular sand box slots, which Microsoft can help you to enable for the hybrid topology as sandbox scale units.

### Data processing when managing scale units

When enabling the your Dynamics 365 environment for the distributed hybrid topology to support cloud and edge scale units, some management services will only be hosted in the United States, similar to LCS. This affects only the transfer and storage of certain administrative and configuration information used by the 'scale unit manager', including:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator and project owner emails used to sign in
- Environment IDs for hub and scale units
- Workload configurations including names and physical address of legal entities and facilities that allows displaying your topology on a geographic map.
- Collected metrics (such as latency and throughput) which are displayed on the map analysis page

Data transferred to and stored in the US data centers will be deleted according to the data retention policies. Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

### Limitations for the current release

In the current release for scale units certain capabilities are not available yet and will be added in incremental releases over time.

- The scale unit add-ins can only be applied if your Lifecycle Services (LCS) project today is managed in a US data center (lcs.dynamics.com). Going forward, when more LCS  projects will be managed in other data regions, support will also be added for those regions.
- The tenant for your LCS project must have already been converted to support the Service Fabric hosting model.
- Management capabilities that help on the movement of workloads are limited. Certain management operations are not supported in a self-service manner and you might need to request support through your partner or Microsoft contact. Examples are certain workload movement between scale units, and temporary ad-hoc movements in disaster scenarios.
- Metrics and measures that may help on selecting the best application for your scale units are not available yet. Please work with your Microsoft contact or implementation partner to select the most beneficial application.

## Onboard to the distributed hybrid topology for Supply Chain Management

### Select your LCS project tenant and the detailed onboarding process

After you have planned on how to onboard to the distributed hybrid topology for supply chain management you will use the [Scale Unit Manager portal](https://aka.ms/SCMSUM)  to commence the onboarding. In the portal navigate to the tab "Dynamics 365 Tenants"where you will find the list of tenants that your account is part of, and where you're an owner or environment admin for an LCS project.

If the tenant that you're looking for isn't in this list, go to [LCS](https://lcs.dynamics.com/v2), and make sure that you're either an environment admin or a project owner of the LCS project for that tenant. Note that only Azure Active Directory (Azure AD) accounts from the selected tenant are authorized to complete the sign-up experience.

> [!NOTE]
> After you apply changes to LCS, it might take up to 30 minutes for the list of tenants to reflect the changes.

For each tenant, the list shows the onboarding status.

:::image type="content" source="media/cloud_edge-EnableHybrid1.png" alt-text="Sign-up option for a tenant":::

Select the **Click here to enable environments** link to request onboarding for the LCS tenant. You must accept the terms. You must also supply a business email address where Microsoft may send communications that are related the onboarding process.

:::image type="content" source="media/cloud_edge-EnableHybrid2.png" alt-text="Sign-up submission for a tenant":::

Microsoft will review your request and inform you about the next steps by sending an email to the address that you supplied on the sign-up form. We will be working closely with you to enable scale units in the hybrid topology for your business scenario.

After the onboarding is complete you will be able to configure scale units and workloads using the portal.

### <a name="scale-unit-manager-portal"></a>Manage cloud scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM), and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale unit and workload management experience":::

To add one or more scale units that are available in your subscriptions, select **Add scale units**.

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Workload creation":::

> [!IMPORTANT]
> The Scale Unit Manager portal in this release doesn't let you reassign workloads tor a different scale unit or back to the hub once  the assignment is made. If you must remove an assignment, reach out to your contact person at Microsoft. The movement of workloads will be added in an upcoming incremental enhancement.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]