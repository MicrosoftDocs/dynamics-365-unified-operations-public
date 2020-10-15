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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: cabeln
ms.search.validFrom: 2020-09-23
ms.dyn365.ops.version: 10.0.15
---
 
# Cloud and edge scale units for manufacturing and warehouse management workloads

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Cloud and edge scale units enable distribution of shop floor and warehouse execution workloads among different environments. This functionality can help improve performance, prevent service interruptions, and maximize uptime. It's provided by the following add-ins:

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management

Companies that work with manufacturing and distribution must be able to run key business processes 24/7, without interruption and at scale. Cloud and edge scale units enable companies to run key mission-critical manufacturing and warehouse processes without interruption, even when faced with occasional network connectivity or latency issues.

## Public preview information

The preview provides one environment that functions as a cloud-based hub of your Dynamics 365 Supply Chain Management environment and one environment that functions as a cloud scale unit.

<!-- You will also be able to use Local Business Data (LBD) to configure an on-premises environment as an edge scale unit for the hub you received as part of the preview program.-->

### Preview availability

The preview for cloud and edge scale units becomes available for existing customers of Supply Chain Management in October 2020.

To access the October preview release 10.0.15/Platform update 39 for deployment in your [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2) environment, you must be part of the preview early access program (also known as PEAP) for Supply Chain Management. You can join PEAP if you're already a member of the broader [Dynamics Insider Program](https://experience.dynamics.com/insider). Just select the specific program that is named "Finance & Operations: Preview early access program (PEAP)."

> [!IMPORTANT]
> The scale unit capability for Supply Chain Management is made available only if you agree to the [Preview Terms and Conditions](https://go.microsoft.com/fwlink/?linkid=2105274).

### Data processing for the preview

During the public preview, some management services will only be hosted in the United States. However, when the feature becomes generally available, these management services will be available in all geographies supported by Supply Chain Management. This affects the transfer and storage of administrative information used by the scale unit manager, including:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator emails used to sign in
- Environment IDs for hub and scale units
- Workload configurations
- Collected metrics (such as latency and throughput) which are displayed on the map analysis page

Data transferred to and stored in the US data centers will be deleted when your preview environments are shut down.

### Sign up for the preview

To sign up for the cloud and edge preview for Supply Chain Management, your organization must already have a live Supply Chain Management cloud environment.

The scale unit capabilities are currently in public preview. When you sign up, you must use a user account on the specific tenant. You must also be a project owner or an environment admin in LCS for an active Dynamics 365 LCS project in that tenant.

When you sign up for the preview, you will select a tenant and go through the sign-up steps. As soon as Microsoft can allocate preview capacity, we will send you an email that includes the provisioning details and the promotion (promo) codes for two environments (a hub and a scale unit) for the appropriate LCS project. You will then be able to deploy the two environments as tier-2 sandbox environments. Those environments will be valid 60 days from the creation date of the promo codes. You should not use the two environments until the step that is described in the next paragraph is completed.

After you confirm with Microsoft that the two environments have been deployed by using the promo codes, one of the environments will be configured to work as a hub, and the other will be configured to work as a scale unit. You can then configure the scale units and deploy selected warehouse management and manufacturing workloads by using the [Scale Unit Manager portal](https://aka.ms/SCMSUM).

Preview environments will automatically be deleted after 60 days. However, they might be deleted sooner if it appears that they aren't being used. After your preview environments have been deleted, you can sign up and queue up for a new preview deployment.

To sign up for the preview, go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM).

### Limitations that apply during the preview period

> [!IMPORTANT]
> For the initial phase of the preview program for this feature, Microsoft is supporting only hubs that have cloud scale units, not hubs that have edge scale units. Edge scale units are installed on-premises and are expected to become available during an upcoming phase of the program.

Because cloud and edge scale units are a preview feature, services that are related to them are currently available in limited countries and regions. By enabling cloud and edge scale units, you affirm that you understand that some data that is related to the configuration and processing of cloud and edge scale units might be stored in a data center that is located in the United States. By enabling cloud and edge scale units, you also agree to the [Preview Terms and Conditions](https://go.microsoft.com/fwlink/?linkid=2105274). To learn more about cloud and edge scale units, see the [documentation](https://aka.ms/scmcne).

Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://aka.ms/privacy).

> [!IMPORTANT]
> Some business functionality isn't fully supported in the public preview when workloads are used on scale units. For more information about the functional workloads, see the sections later in this topic.

## Scale units and dedicated workloads

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with scale units":::

Scale units extend your central Supply Chain Management hub environment by adding dedicated processing capacity. Scale units can run in the cloud. Alternatively, they can run on the edge at your local facility premises. Scale units can temporarily be disconnected from the hub environment. When they are connected, scale units receive all the information that is required to run the dedicated processing for assigned workloads.

:::image type="content" source="media/cloud_edge-previewoptions.png" alt-text="Scale unit options in the public preview":::

For the public preview, you can configure a hub environment with selected workloads on a cloud scale unit by using the Scale Unit Manager portal. Preview participants who have access to a Local Business Data (LBD) on-premises environment can also configure the LBD environment as an edge scale unit.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit. Currently, the preview features two types of workloads:

- Manufacturing execution
- Warehouse management

You can assign one of each type of workload per scale unit. 

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

## Onboard scale units for your Supply Chain Management environment

### Deploy the preview for cloud and edge scale units

The following illustration shows the sign-up and provisioning flow for the public preview for cloud scale units.

:::image type="content" source="media/cloud_edge-previewsignup.png" alt-text="Preview sign-up steps":::

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
> When you configure cloud scale units, you can [do all the required steps in the Scale Unit Manager portal](#manage-cloud-scale-units-and-workloads-using-the-scale-unit-manager-portal).
<!-- >
> If want to use edge scale units with your preview deployment, you must do all scale unit configuration in the user interface on the hub as described in [Configure the hub environment for use with edge scale units](cloud-edge-edge-scale-units-lbd.md#configure-the-hub-environment). You can't use Scale Unit Manager portal if you include an edge scale unit. -->

### Manage cloud scale units and workloads by using the Scale Unit Manager portal

Go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM), and sign in by using your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. You can then select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Scale unit and workload management experience":::

To add one or more scale units that are available in your topology, select **Add scale units**. In the preview, you should see the cloud scale unit that you deployed from one of the promo codes that you received as part of the preview program.

<!-- > [!IMPORTANT]
> In the public preview, the Scale Unit Manager portal shows the cloud scale unit that you received as part of the preview program. Any edge scale unit that you created based on an LBD configuration can't be managed in the Scale Unit Manager portal yet. For configuration details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md) -->

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse management or manufacturing execution workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse management workloads, the context is a specific warehouse in a specific site and legal entity. For manufacturing execution workloads, the context is a specific site in a legal entity.

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Workload creation":::

> [!IMPORTANT]
> The Scale Unit Manager portal in the preview doesn't let you remove workloads from scale units or unassign a scale unit from a hub after the assignment is made. If you must remove an assignment, reach out to your contact person for preview program management.

<!-- ### Create an edge scale unit using your custom on-premises hardware appliance

In the public preview, you can create on-premises edge scale units on your custom hardware using the LBD environments. For details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md). -->
