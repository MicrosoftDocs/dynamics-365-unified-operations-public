---
title: Multiple Lifecycle Services projects and environments on one Microsoft Entra tenant
description: Learn about how to implement multiple Lifecycle Services projects and production environments on the same Microsoft Entra tenant.
author: sericks007
ms.author: epegors
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.search.form:  
ms.dyn365.ops.version: AX 7.0
---

# Multiple Lifecycle Services projects and environments on one Microsoft Entra tenant

[!include [banner](../../../finance/includes/banner.md)]

For any new cloud project, you instantiate one Microsoft Dynamics Lifecycle Services implementation project on a Microsoft Entra tenant that provides access to one production instance. In rare cases, to handle the requirements of a specific implementation, you might require multiple production instances that run in parallel. By creating multiple Lifecycle Services projects against the same Microsoft Entra tenant, you can have multiple production instances. Here are the most common scenarios where you might need multiple production instances:

- A global implementation's requirements for data residency, latency, or data volume can't be met by one instance.
- Different business units in an organization are implementing the product separately as independent applications.

## Licensing requirements

Every Lifecycle Services implementation project that runs on the same Microsoft Entra tenant must satisfy the minimum licensing requirements. For example, if there are three Lifecycle Services implementation projects on the same Microsoft Entra tenant, a customer must purchase no less than three times the minimum number of subscription licenses. Currently, the minimum license requirement is 20 full user licenses. Therefore, to run three Lifecycle Services implementation projects on the same Microsoft Entra tenant, the customer must purchase at least 60 licenses.

Because the licenses are associated with the Microsoft Entra tenant, the **Subscriptions available** page for every Lifecycle Services project shows the total number of licenses, even though a given Lifecycle Services project can use only the portion of licenses allocated to it. The allocation of licenses to Lifecycle Services projects is described in [Edit the licenses allocated to projects](#edit-the-licenses-allocated-to-projects).

For more information about licensing, download the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## Disadvantages of multiple Lifecycle Services projects

Here are some of the disadvantages to having multiple Lifecycle Services projects:

- Master data isn't shared.
- Intercompany transactions aren't supported.
- Integrations must be configured in each Lifecycle Services project.
- Each Lifecycle Services project requires a separate Bring your own database (BYOD) instance.
- User acceptance testing (UAT) must be done on each instance, even if the code is the same. UAT is required on each instance, because differences can occur across the Lifecycle Services projects, even if they share a code base. One source of differences can be the integration setup and BYOD configuration that must be done separately in each Lifecycle Services project and therefore must be tested in each Lifecycle Services project. There might be data variations, different application configurations per region might affect functionality, and different data centers might support a different set of Azure services.
- Microsoft Azure DevOps must be configured in each Lifecycle Services project. When customizations and code are shared, it makes sense to use the same Azure DevOps project.

## Advantages of multiple Lifecycle Services projects

Having multiple Lifecycle Services projects offers several advantages. Here are some of them:

- You can select data centers for each Lifecycle Services project to provide the best latency experience.
- You can select data centers for each Lifecycle Services project to satisfy statutory requirements for data residency.
- You get more flexibility to schedule servicing operations, such as code deployments and upgrades.
- You can have different stakeholders for the different Lifecycle Services implementation projects.

## Create multiple Lifecycle Services projects

Follow these steps to create another implementation project in your existing organization.

1. On the Lifecycle Services home page, select the plus sign (**+**) button.
1. Select the desired product for the new project.
1. Select **Implementation** as the project type.
1. Enter information about the new implementation project.
1. Select **Create** to finish creating the project. If you already have an existing implementation project in your organization, a message box might prompt you to confirm that you want to create another implementation project. If you receive an error message, your organization might not have the required total license count to support another implementation project.

The newly created implementation project is shown, and you're the owner of it.

## Edit the licenses allocated to projects

Determine how you want to assign licenses across the implementation projects in your organization. Make sure that the number of licenses assigned across all projects doesn't exceed the total license count that you purchased.

After you determine the allocation, open the [Subscription estimator](../lifecycle-services/subscription-estimator.md) tool for each implementation project. Edit the active subscription estimate to apply the desired license allocation for that project.

## Online deployments in China sovereign cloud

If your implementation includes China deployment or rollout, see [finance and operations apps - operated by 21Vianet in China](../../fin-ops/deployment/china-local-deployment.md). This deployment is designed to comply with regulatory requirements in China. The services include a physically separated instance of a cloud service that has a different tenant (Microsoft Entra ID) that 21Vianet operates and transacts.

In this case, a single organization exists in multiple clouds with a different tenant (Microsoft Entra ID). The previously described advantages and disadvantages of multiple Lifecycle Services projects or production environments still apply. However, the licensing requirements and request procedures differ. If you need process assistance, work with your Microsoft account executive or your implementation partners.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
