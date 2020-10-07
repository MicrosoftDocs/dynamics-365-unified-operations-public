---
# required metadata

title: Cloud and Edge
description: Cloud and Edge scale units for manufacturing and warehouse management workloads
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

Cloud and edge scale units enable shop floor and warehouse execution workloads to be distributed among different environments, which can help improve performance, prevent service interruptions, and maximize up time. This functionality is provided by the following add-ins:

- Cloud Scale Unit Add-in for Dynamics 365 Supply Chain Management
- Edge Scale Unit Add-in for Dynamics 365 Supply Chain Management

Companies working with manufacturing and distribution must be able to execute key business processes 24/7, without interruption and at scale. But complications may arise due to issues ranging from basic connectivity (such as provider outages, Azure outages, unreliable connections, or network latency) to multiple business processes competing for the same system resources. Cloud and edge features enable companies to execute key mission-critical manufacturing and warehouse processes without interruption, even in situations such as these.

## Public preview information

> [!IMPORTANT]
> As a preview feature, services related to cloud and edge scale unit are currently available in limited geographies. By enabling cloud and edge scale units, you are affirming that you understand that some data related to the configuration and processing of cloud and edge scale units may be performed in a data center located in the USA. By enabling cloud and edge scale units, you agree to these [Terms and Conditions](https://go.microsoft.com/fwlink/?linkid=2105274). To learn more about cloud and edge scale units please consult the [documentation](https://aka.ms/scmcne).
>
> Your privacy is important to us. To learn more read our [Privacy Statement](https://aka.ms/privacy).

> [!NOTE]
> Microsoft is committed to providing software that is usable by persons of all abilities. As a preview feature, the user experience for the cloud and edge scale unit manager is still being developed. Some usability and accessibility work remains. We welcome your feedback on how we can improve our user experiences.

> [!IMPORTANT]
> The preview for cloud and edge scale units is available for existing customers of Supply Chain Management starting in October 2020.
>
> You must be part of the early access program (also known as PEAP) for Supply Chain Management to get access to the October preview release 10.0.15 / PU 39 for deployment in your LCS environment. You can join the PEAP program if you already are a member of the broader  [Dynamics Insider Program](https://experience.dynamics.com/insider) and then by selecting the specific program called "Finance & Operations: Preview early access program (PEAP)".

> [!IMPORTANT]
> To sign up to the cloud and edge preview for Supply Chain Management, your organization must already have a live Supply Chain Management cloud environment.
>
> The scale-unit capabilities are currently in public preview. When signing up, you must use a user account on the specific tenant and also be a project owner or an environment admin in LCS for an active Dynamics 365 LCS project in that tenant.
>
> When you sign up for the preview, you will select the tenant and go through the sign up steps. As soon as we can allocate preview capacity, we will send you an email with the provisioning details and the promotion codes for two environments (a cloud hub and a scale unit) for the respective LCS project. You will then be able to deploy the two environments as tier 2 sandbox environments. Those are valid 60 days from creation date of the promo code.
>
> After you confirm your sign up with Microsoft, one of the environments will be configured to function as a cloud hub the other as a scale unit. You can then configure the scale units and deploy select warehouse management and manufacturing workloads using the [Scale Unit Manager portal](https://sum.dynamics.com).
>
> Preview environments will be deleted automatically after 60 days, or sooner if they appear to not be in use. After your preview environment has been deleted, you may sign up and queue for a new preview deployment.
>
> Go to the [Scale Unit Manager portal](https://sum.dynamics.com) to sign up for the preview.

> [!WARNING]
> Certain business functionality is not fully supported in the public preview when using workloads scale units. See the sections for more details about the functional workloads.

The preview provides you with one environment that functions as a cloud based hub of your Supply Chain Management environment and one environment that will function as a cloud scale unit. For the preview, both environment will be hosted in a data center in northern USA.

You will also be able to use Local Business Data (LBD) to configure an on-premises environment as an edge scale unit for the cloud hub you received as part of the preview program.

## Scale units and dedicated workloads

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with Scale Units":::

Scale units extend your central Supply Chain Management cloud hub environment by adding dedicated processing capacity. Scale units can run in the cloud or on the edge at your local facility premises. Scale units are always connected to the cloud hub environment and receive all information to run the dedicated processing for assigned workloads.

:::image type="content" source="media/cloud_edge-previewoptions.png" alt-text="Scale unit options with public preview":::

With the public preview, we offer an opportunity to experience configurations of a cloud hub environment with selected workloads on a cloud scale unit, which you can configure using the Scale Unit Manager portal. Preview participants who have access to an LBD on-premises environment can configure it as an edge scale unit.  

The preview features two kinds of workloads, and you can assign one of each per scale unit. A workload is a defined set of business functionality that can be factored out and delegated to a scale unit. As of today, two types of workloads are supported:

- Manufacturing execution
- Warehouse management

### Dedicated manufacturing workload capabilities in a scale unit

Within manufacturing execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable machine operators and shop floor supervisors to access the operational production plan.
- Enable machine operators to keep the plan current by executing discrete and process manufacturing jobs.
- Enable the shop floor supervisor to adjust the operational plan.
- Enable workers to access time and attendance for clock-in and clock-out on the edge to ensure correct worker pay calculation.

Review the [manufacturing scale unit workload details](cloud-edge-workload-manufacturing.md) for more information.

### Dedicated warehouse management workload capabilities in a scale unit

For warehouse execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable selected wave methods processing, for sales orders and demand replenishment.
- Enable warehouse workers to execute sales and demand replenishment warehouse work using the warehouse app.
- Enable warehouse workers to perform inquiries into on-hand inventory using the warehouse app.
- Enable warehouse workers to create and execute inventory movements using the warehouse app.
- Enable warehouse worker to register purchase orders and conduct put away using the warehouse app.

Review the [warehouse scale unit workload details](cloud-edge-workload-warehousing.md) for more information.

## Onboard scale units for your Supply Chain Management environment

### Deploy of the preview for cloud and edge scale units

The following diagram shows the sign-up and provisioning flow for the public preview of cloud and edge scale units.

:::image type="content" source="media/cloud_edge-previewsignup.png" alt-text="Diagram of the preview sign-up steps":::

### Select your LCS project tenant and the detailed preview process

In the public preview, the [Scale Unit Manager portal](https://sum.dynamics.com) shows the list of tenants that your account is part of and where you are an owner or environment admin for an LCS project. It also shows the sign-up status for each tenant.

:::image type="content" source="media/cloud_edge-Signup1.png" alt-text="Screen shot showing the 'Sign up' option for a tenant.":::

Select the **Sign up now!** button to sign up your LCS tenant to participate in the preview. You must accept the terms and supply a business email address where we can send you communications related the preview sign-up process.

:::image type="content" source="media/cloud_edge-Signup2.png" alt-text="Screen shot showing the sign up submission for a tenant.":::  

Microsoft will review your request and inform you about the next steps.  

Once you have been granted access to the preview program, you will receive two promo codes for your LCS project. You can now deploy two environments in LCS using these promo codes. The environments must be using PEAP release 10.0.15 or later. Once completed, please reply in email so we can prepare one of those environments to become the Supply Chain Management cloud hub and the other to be a cloud scale unit in your preview deployment. We will then let you know once this configuration step is completed.

Now you can start configuring scale units and workloads in your preview environment using the Scale Unit Manager portal.

### Manage cloud scale units and workloads

Access the Scale Unit Manager portal and sign in with your tenant account. On the **Configure scale units** page, you can add a hub environment if it isn't already listed. Then you can select the hub that you want to configure with scale units and workloads.

:::image type="content" source="media/cloud_edge-Manage.png" alt-text="Screen shot showing the scale unit and workload management experience.":::  

Select **Add scale units** to add one or more scale units that are available in your topology. In preview, you should see the cloud scale unit that you have deployed from one of the promo codes that you received as part of the preview program.

> [!IMPORTANT]
> In the public preview, the Scale Unit Manager portal shows the cloud scale unit that you received as part of the preview program. Any edge scale unit that you created based on an LBD configuration can't be managed in the Scale Unit Manager portal yet. For configuration details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md)

On the **Defined workloads** tab, use the **Create workload** button to add a warehouse-execution or manufacturing-execution workload to one of your scale units. For each workload, you must specify the context of the processes that will be owned by the workload. For warehouse execution workloads, the context is a specific warehouse in a specific site and legal entity. For manufacturing execution workloads, the context is a specific site in a legal entity.  

:::image type="content" source="media/cloud_edge-DefineWorkload.png" alt-text="Screen shot showing the the creation of a workload.":::  

> [!CAUTION]
> Please be aware that the Scale Unit Manager portal in the preview doesn't let you remove workloads from scale units or unassign a scale unit from a hub once the assignment is made. If you need to remove an assignment, please reach out to your preview program management contact.

### Create an edge scale unit using your custom on-premises hardware appliance
  
In the public preview, you can create on-premises edge scale units on your custom hardware using the LBD environments. For details, see [Deploy custom edge scale units on custom hardware using LBD](cloud-edge-edge-scale-units-lbd.md).

