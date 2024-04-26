---
title: Multiple LCS projects and environments on one Microsoft Entra tenant
description: Learn about how to implement multiple LCS projects and production environments on the same Microsoft Entra tenant.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 02/03/2022
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-05-30
ms.search.form:  
ms.dyn365.ops.version: AX 7.0
---

# Multiple LCS projects and environments on one Microsoft Entra tenant

[!include [banner](../../../finance/includes/banner.md)]

For any new cloud project, one Microsoft Dynamics Lifecycle Services (LCS) implementation project is instantiated on a Microsoft Microsoft Entra tenant that provides access to one production instance. In rare cases, to handle the requirements of a specific implementation, you might require multiple production instances that run in parallel. By creating multiple LCS projects against the same Microsoft Entra tenant, you can have multiple production instances. Here are the most common scenarios where multiple production instances might be required:

- A global implementation's requirements for data residency, latency, or data volume can't be met by one instance.
- Different business units in an organization are implementing the product separately as independent applications.

## Licensing requirements

Every LCS implementation project that runs on the same Microsoft Entra tenant must satisfy the minimum licensing requirements. For example, if there are three LCS implementation projects on the same Microsoft Entra tenant, a customer must purchase no less than three times the minimum number of subscription licenses. Currently, the minimum license requirement is 20 full user licenses. Therefore, to run three LCS implementation projects on the same Microsoft Entra tenant, the customer must purchase at least 60 licenses.

Because the licenses are associated with the Microsoft Entra tenant, the **Subscriptions available** page for every LCS project will show the total number of licenses, even though a given LCS project can use only the portion of licenses that has been allocated to it. The allocation of licenses to LCS projects is described in [Edit the licenses allocated to projects](#edit-the-licenses-allocated-to-projects).

Users who access multiple environments in parallel must be licensed separately for each environment. A user can only be assigned one license for each product for each Microsoft Entra tenant. Even though the Microsoft 365 admin center allows a user to only be assigned one license for each product for each Microsoft Entra tenant, the customer is still required to activate a separate license for each LCS project that the user will access. For additional information about licensing, download the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544&clcid=0x409).

## Disadvantages of multiple LCS projects

Here are some of the disadvantages to having multiple LCS projects:

- Master data isn't shared.
- Intercompany transactions aren't supported.
- Integrations must be configured in each LCS project.
- Each LCS project requires a separate Bring your own database (BYOD) instance
- User acceptance testing (UAT) must be done on each instance, even if the code is the same. UAT is required on each instance, because differences can occur across the LCS projects, even if they share a code base. One source of differences can be the integration setup and BYOD configuration that must be done separately in each LCS project and therefore must be tested in each LCS project. Additionally, there might be data variations, different application configurations per region might affect functionality, and different data centers might support a different set of Azure services.
- Microsoft Azure DevOps must be configured in each LCS project. When customizations and code are shared, it makes sense to use the same Azure DevOps project.

## Advantages of multiple LCS projects

There are also advantages to having multiple LCS projects. Here are some of them:

- Data centers can be selected per LCS project to provide the best latency experience.
- Data centers can be selected per LCS project to satisfy statutory requirements for data residency.
- There is more flexibility to schedule servicing operations, such as code deployments and upgrades.
- It is possible to have different stakeholders for the different LCS implementation projects.

## Create multiple LCS projects

Follow these steps to create an additional implementation project in your existing organization.

1. On the LCS home page, select the plus sign (**+**) button.
2. Select the desired product for the new project.
3. Select **Implementation** as the project type.
4. Enter information about the new implementation project.
5. Select **Create** to finish creating the project. If you already have an existing implementation project in your organization, a message box might prompt you to confirm that you want to create an additional implementation project. If you receive an error message, your organization might not have the required total license count to support an additional implementation project.

The newly created implementation project is shown, and you will be the owner of it.

## Edit the licenses allocated to projects

Determine how you want to assign licenses across the implementation projects in your organization, to ensure that the number of licenses that are assigned across all projects doesn't exceed the total license count that the customer purchased.

After the allocation has been determined, open the [Subscription estimator](../lifecycle-services/subscription-estimator.md) tool for each implementation project, and edit the active subscription estimate to apply the desired license allocation for that project.

## Online deployments in China sovereign cloud

If your implementation includes China deployment/rollout, see [finance and operations apps - operated by 21Vianet in China](../../fin-ops/deployment/china-local-deployment.md). This deployment is designed to comply with regulatory requirements in China. The services include a physically separated instance of a cloud service that has a different tenant (Microsoft Entra ID) that is operated and transacted by 21Vianet.

In this case, there is a single organization in multiple clouds with a different tenant (Microsoft Entra ID). The previously described advantages and disadvantages of multiple LCS projects or production environments still apply. However, the licensing requirements and request procedures differ. If you require process assistance, work with your Microsoft account executive or your implementation partners.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]