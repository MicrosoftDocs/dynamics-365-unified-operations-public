---
# required metadata

title: Preview capabilities for cloud and edge scale units for manufacturing and warehouse management
description: This topic provides information about capabilities in preview for cloud and edge scale units for manufacturing and warehouse management.
author: cabeln
manager: 
ms.date: 10/03/2021
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
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.19
---
 
# Cloud and edge scale unit capabilities in preview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The distributed hybrid topology for supply chain management will bring cloud and edge scale units in different delivery models and more workload capabilities are added as iterative enhancements.
This article lists the functionality that is available in preview.

||Cloud scale unit|Edge scale unit (on LBD hardware) |Edge scale unit (on your Azure Stack Hub) |Edge scale unit (Edge as a service) |
|--------------|---------|---------|---------|---------|
|**Warehouse**     |Released |***Preview***  |...to be announced |...to be announced |
|**Manufacturing** |***Preview***  |***Preview***  |...to be announced |...to be announced |

## Public preview information

For any preview participation we recommend to onboard through two stages.

1. **Stage 1:** In the first stage we recommend exploring scale units in a development setup (one-box aka. Tier1 environments) to validate processes, customizations and solutions. In this phase data and customizations will be applied to the one-box environments. One environment takes the role of the hub and the other the role of a scale unit. This setup provides the best way to identify and solve issues.

   For this stage, the scale unit deployment tools for one-box development environments should be used. It allows you to configure hub and scale units in one or two separate one-box environments. The tool is provided as binary release and in source code on [GitHub](https://github.com/microsoft/SCMScaleUnitDevTools). Please study the project Wiki with a step by step guide that describes how the tool is used.

1. **Stage 2:** The second stage is open to select customers with implementation projects, and it follows completion of Step 1. Microsoft may provide two new (60 days time limited) sandbox Tier 2 environments in the LCS implementation project. Stage 2 requires sign-up through the [Scale unit manager portal](https://sum.dynamcis.com) by the LCS project owner. Potential changes to customizations found in Stage 1 shall then be applied to these sandbox Tier 2 environments.
To succeed with this step we like to setup a meeting with you to understand how we can help you best in the configuration process and help you succeed.

As part of the preview program you will also be able to configure an [edge scale unit](#preview-for-edge-scale-units) and connect it to your your preview hub. You may do that in an on-premises appliance you may own.

### Preview availability

The preview for cloud and edge scale units is available for existing customers of Supply Chain Management.

To access the preview capabilities you must be part of the preview early access program  for Supply Chain Management, also known as PEAP program. You can join program if you're already a member of the broader [Dynamics Insider Program](https://experience.dynamics.com/insider). Just select the specific program that is named "Finance & Operations: Preview early access program (PEAP)."

> [!IMPORTANT]
> By enabling preview capabilities for cloud and edge scale units, you also agree to the [Cloud + Edge Preview for Finance and Operations terms](https://Aka.ms/SCMCnETerms). To learn more about cloud and edge scale units, see the [documentation](https://aka.ms/scmcne).
>
> Your privacy is important to Microsoft. To learn more, read our [Privacy Statement](https://aka.ms/privacy).

### Data processing for the preview

Some management services will only be hosted in the United States, which corresponds to the information in Live Cycle Service projects, which typically are stored in US data center. This affects the transfer and storage of administrative information used by the scale unit manager, including:

- Your tenant names and IDs
- Your LCS project IDs
- Administrator emails used to sign in
- Environment IDs for hub and scale units
- Workload configurations
- Collected metrics (such as latency and throughput) which are displayed on the map analysis page, when this capability lights up in the preview.

Data transferred to and stored in the US data centers will be deleted when your preview environments are shut down.

### Sign up for the preview In Stage 2 for cloud hosted environments

To sign up for **Stage 2** in the preview, your organization must already have a live Supply Chain Management cloud environment which includes a LCS implementation project is running on the service fabric topology. This is required such that environments slots can be allocated for the preview.

To sign up, you must use a user account on the specific tenant. And you must also be a project owner or an environment admin in LCS for an active Dynamics 365 LCS project in that tenant.

The sign up for functionality still in preview goes through the same experience that you use to enable the hybrid distributed topology. In the sign-up process first select a tenant where above requirements is fulfilled, and go through the sign-up steps. As soon as Microsoft can allocate preview capacity, we will send you an email and invite you to a closer collaboration. We will require a meeting with you to understand the best way to support you with the preview capabilities.

:::image type="content" source="media/cloud_edge-EnableHybrid1.png" alt-text="Sign-up option for a tenant":::

:::image type="content" source="media/cloud_edge-EnableHybrid2.png" alt-text="Agree to terms an privacy statement":::

In the process we may provide you with provisioning details and the promotion (promo) codes for two environments (a hub and a scale unit) for the appropriate LCS project. You will then be able to deploy the two environments as tier-2 sandbox environments. Those environments will be valid 60 days from the creation date of the promo codes. You should not use the two environments until the step that is described in the next paragraph is completed. But we will guide you through all the steps.

After you confirm with Microsoft that the two environments have been deployed by using the promo codes, one of the environments will be configured to work as a hub, and the other will be configured to work as a scale unit. You can then configure the scale units and deploy selected warehouse management and manufacturing workloads by using the [Scale Unit Manager portal](https://aka.ms/SCMSUM).

The preview environments from the promo codes will automatically be deleted after 60 days. However, they might be deleted sooner if it appears that they aren't being used. After your preview environments have been deleted, you can sign up and queue up for a new preview deployment.

To request participation in **Stage 2** of the preview, go to the [Scale Unit Manager portal](https://aka.ms/SCMSUM).

## Capabilities lighting up in preview

### Preview for the manufacturing execution workload

For manufacturing execution, scale units deliver the following capabilities in the configured workload:

- Machine operators and shop floor supervisors can access the operational production plan.
- Machine operators can keep the plan up to date by running discrete and process manufacturing jobs.
- The shop floor supervisor can adjust the operational plan.
- Workers can access time and attendance for clock-in and clock-out on the edge, to ensure correct worker pay calculation.

For more information, see the [manufacturing scale unit workload details](cloud-edge-workload-manufacturing.md).

### Preview for edge scale units

Preview participants who have access to a Local Business Data (LBD) on-premises environment will be able to configure an edge scale unit and deploy workloads.

For details, see [Deploy custom edge scale units on custom hardware using LBD deployment](cloud-edge-edge-scale-units-lbd.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]