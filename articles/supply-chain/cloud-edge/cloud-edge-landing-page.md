---
# required metadata

title: Cloud and edge scale units for manufacturing and warehouse management workloads
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
 
# Cloud and edge scale units for manufacturing and warehouse management workloads

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The scale unit capability for Supply Chain Management is made available only if you agree to the [legal terms for Finance and Operations](https://go.microsoft.com/fwlink/?LinkID=290927).
>
> By enabling cloud and edge scale units, you affirm that you understand that some data that is related to the configuration and processing of cloud and edge scale units might be stored in a data center that is located in the United States. To learn more about the data processing with cloud and edge scale units, see the [documentation](cloud-edge-landing-page.md#data-processing-in-the-distributed-hybrid-topology-using-scale-units).

Cloud and edge scale units enable distribution of shop floor and warehouse execution workloads among different environments. This functionality can help improve performance, prevent service interruptions, and maximize uptime. It's provided by the following add-ins:

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management

Companies that work with manufacturing and distribution must be able to run key business processes 24/7, without interruption and at scale. Cloud and edge scale units enable companies to run key mission-critical manufacturing and warehouse processes without interruption, even when faced with occasional network connectivity or latency issues.

## Scale units and dedicated workloads

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units":::

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the edge at your local facility premises. Scale units can temporarily be disconnected from the hub environment. When they are connected, scale units receive all the information that is required to run the dedicated processing for assigned workloads.

You can configure your hub environment and  cloud scale units for selected workloads by using the [Scale Unit Manager](https://sum.dynamics.com) portal.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit. Currently, the preview features two types of workloads:

- Manufacturing execution
- Warehouse management

You can assign multiple workloads per scale unit. (Please refer to [limitations](#limitations-that-apply-during-the-preview-period) in your release)

### Dedicated manufacturing execution workload capabilities in a scale unit

For manufacturing execution, cloud and edge scale units deliver the following capabilities, even when the edge units aren't connected to the cloud:

- Machine operators and shop floor supervisors can access the operational production plan.
- Machine operators can keep the plan up to date by running discrete and process manufacturing jobs.
- The shop floor supervisor can adjust the operational plan.
- Workers can access time and attendance for clock-in and clock-out on the edge, to ensure correct worker pay calculation.

For more information, see the [manufacturing scale unit workload details](cloud-edge-workload-manufacturing.md).

### Dedicated warehouse management workload capabilities in a scale unit

For warehouse management, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Processing of selected wave methods is enabled for sales orders and demand replenishment.
- Warehouse workers can run sales and demand replenishment warehouse work by using the warehouse app.
- Warehouse workers can inquire into on-hand inventory by using the warehouse app.
- Warehouse workers can create and run inventory movements by using the warehouse app.
- Warehouse workers can register purchase orders and do putaway by using the warehouse app.

For more information, see the [warehouse scale unit workload details](cloud-edge-workload-warehousing.md).

## How to enable the distributed hybrid topology for Supply Chain Management

By enabling the hybrid distributed topology you transition your supply chain management environment in the cloud to functions as a hub that may be supported by additional environments configured as scale units in the cloud or on the edge.

### Onboarding steps

 Before you begin with onboarding your sandbox or production environments we recommend exploring scale units in a development setup (one-box aka. Tier1 environments) to validate processes, customizations and solutions. In this phase data and customizations will be applied to the one-box environments. One environment takes the role of the hub and the other the role of a scale unit. This setup provides the best way to identify and solve issues. This can also be done using the latest early access (PEAP) build. 

In order to onboard one of your sandbox or production environment to the new topology you can acquire add-ins for one or more cloud scale units and going forward also for edge scale units. The add-ins will grant corresponding projects and environments slots in [LCS](https://lcs.dynamics.com/) for the purpose of deploying the scale units environments.
For this stage, the scale unit deployment tools for one-box development environments should be used. It allows you to configure hub and scale units in one or two separate one-box environments. The tool is provided as binary release and in source code on GitHub. Please study the project Wiki with a step by step guide that describes how the tool is used.

You may also participate in the preview program for to experience incremental enhancements to be release in upcoming releases. Find more information on how to [experience the capabilities in preview](cloud-edge-preview-components.md).



### Data processing in the distributed hybrid topology using scale units

When enabling the your Dynamics 365 environment for the distributed hybrid topology to support cloud and edge scale units, some management services will only be hosted in the United States, similar to LCS. This affects only the transfer and storage of certain administrative and configuration information used by the 'scale unit manager', including:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator and project owner emails used to sign in
- Environment IDs for hub and scale units
- Workload configurations including names and physical address of legal entities and facilities that allows displaying your topology on a geographic map.
- Collected metrics (such as latency and throughput) which are displayed on the map analysis page

Data transferred to and stored in the US data centers will be deleted according to the data retention policies. Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://aka.ms/privacy).

### Limitations for the current release
 


## DELETE -Onboard scale units for your Supply Chain Management environment

### Select your LCS project tenant and the detailed preview process

In the public preview, the [Scale Unit Manager portal](https://aka.ms/SCMSUM) shows the list of tenants that your account is part of, and where you're an owner or environment admin for an LCS project.

If the tenant that you're looking for isn't in this list, go to [LCS](https://lcs.dynamics.com/v2), and make sure that you're either an environment admin or a project owner of the LCS project for that tenant. Note that only Azure Active Directory (Azure AD) accounts from the selected tenant are authorized to complete the sign-up experience.

> [!NOTE]
> After you apply changes to LCS, it might take up to 30 minutes for the list of tenants to reflect the changes.

For each tenant, the list shows the sign-up status.

:::image type="content" source="media/cloud_edge-Signup1.png" alt-text="Sign-up option for a tenant":::

Select the **Click here to sign up** link to sign up your LCS tenant to participate in the preview. You must accept the terms. You must also supply a business email address where Microsoft can send communications that are related the preview sign-up process.

:::image type="content" source="media/cloud_edge-Signup2.png" alt-text="Sign-up submission for a tenant":::

Microsoft will review your request and inform you about the next steps by sending an email to the address that you supplied on the sign-up form.

After you've been granted access to the preview program, you will receive two promo codes for your LCS project. You can now use those promo codes to deploy two environments in LCS. The environments must use PEAP release 10.0.15 or later. When you've finished applying the promo codes, notify Microsoft (as instructed), so that we can finish enabling the environments for the preview features. Microsoft will let you know when this configuration step is completed.

You can now start to configure scale units and workloads in your preview environment.

> [!IMPORTANT]
> When you configure cloud scale units, you can [do all the required steps in the Scale Unit Manager portal](#scale-unit-manager-portal).
<!-- 
> If want to use edge scale units with your preview deployment, you must do all scale unit configuration in the user interface on the hub as described in [Configure the hub environment for use with edge scale units](cloud-edge-edge-scale-units-lbd.md#configure-the-hub-environment). You can't use Scale Unit Manager portal if you include an edge scale unit. -->

### <a name="scale-unit-manager-portal"></a>Manage cloud scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM), and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale unit and workload management experience":::

To add one or more scale units that are available in your topology, select **Add scale units**. In the preview, you should see the cloud scale unit that you deployed from one of the promo codes that you received as part of the preview program.

<!--  [!IMPORTANT]
> In the public preview, the Scale Unit Manager portal shows the cloud scale unit that you received as part of the preview program. Any edge scale unit that you created based on an LBD configuration can't be managed in the Scale Unit Manager portal yet. For configuration details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md) -->

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management or manufacturing execution workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity. For manufacturing execution workloads, the context is a specific site in a legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Workload creation":::

> [!IMPORTANT]
> The Scale Unit Manager portal in the preview doesn't let you remove workloads from scale units or unassign a scale unit from a hub after the assignment is made. If you must remove an assignment, reach out to your contact person for preview program management.

<!-- ### Create an edge scale unit using your custom on-premises hardware appliance

In the public preview, you can create on-premises edge scale units on your custom hardware using the LBD environments. For details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md). -->


[!INCLUDE[footer-include](../../includes/footer-banner.md)]