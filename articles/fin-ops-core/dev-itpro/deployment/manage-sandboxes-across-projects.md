---
# required metadata

title: Manage sandbox environments across implementation projects
description: This article explains how to manage multiple sandbox deployments across implementation projects in Microsoft Dynamics Lifecycle Services.
author: laneswenka
ms.date: 04/25/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Admin
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Manage sandbox environments across implementation projects

[!include[banner](../includes/preview-banner.md)]

Management of sandboxes across implementation projects is an important aspect of the implementation of finance and operations apps. By following the steps that are outlined in this article, you can ensure that you stay within your purchased sandbox limits.

When you implement finance and operations apps, it's crucial that you have the appropriate number of sandboxes for your development, testing, and training purposes. Sandboxes let you test modifications to finance and operations apps before you affect your production environment. Microsoft provides one production environment and one sandbox environment with the purchase of 20 user licenses for finance and operations apps. However, many customers require more than one sandbox. Therefore, you can purchase more sandboxes from the Microsoft 365 portal.

## Sandbox add-ons

The extra sandboxes that you purchase are referred to as sandbox add-ons. Sandbox add-ons come in different performance levels, from Tier 2 through Tier 5. Tier 5 is the highest-performing option. In the past, sandbox add-ons were shown in all projects simultaneously. Therefore, it was difficult to keep track of how many sandboxes were deployed. To help you stay within your purchased limits, Microsoft is changing this behavior. Sandbox slots now disappear from other projects as they're deployed.

## Managing sandboxes across implementation projects

This section explains the steps that you can take to manage sandboxes across implementation projects.

### Step 1: Determine your sandbox requirements

The first step in managing sandboxes across implementation projects is to determine your sandbox requirements. You must understand the number of sandboxes that are required for development, testing, and training purposes. Microsoft provides one production environment and one sandbox environment for each implementation project. If you have only one implementation project, this article won't have any impact for you. If you have multiple implementation projects, you must decide how many extra sandboxes you require for each project. To purchase additional sandboxes, visit the [Purchase services](https://admin.microsoft.com/Adminportal/Home#/catalog) page in the Microsoft 365 admin portal.

### Step 2: Create a project in Lifecycle Services

After you've determined your sandbox requirements, create a project in Microsoft Dynamics Lifecycle Services. Lifecycle Services is an Azure-based collaboration portal that provides a unified view of implementation projects. You can use Lifecycle Services to manage project activities, track progress, and collaborate with other team members.

### Step 3: Deploy sandboxes to your project

After you've created a project in Lifecycle Services, you can start to deploy the sandboxes that are required for the project. Sandboxes are deployed by using a first-come, first-served approach. For example, you've purchased five sandbox add-ons, and you have two implementation projects. If you want to have three sandboxes in one project and two in the other project, deploy three sandbox add-ons to the first project as soon as possible. These three sandbox add-on slots will be consumed by the first project and will disappear from the second project. The remaining two open sandbox add-on slots are then available for deployment to the second project.

### Step 4: Keep track of deployed sandboxes

It's important that you keep track of the sandboxes that you've deployed. In the past, extra sandboxes were shown in all projects simultaneously. Therefore, it was difficult to keep track of how many of the sandboxes were deployed. Now, when a sandbox is deployed, it disappears from view in your other projects. To help you stay within your purchased limits, only sandboxes that are available for deployment are shown.

You can deploy a sandbox to only one project at a time. To view which sandboxes have been deployed, go to the **Subscriptions available** page in the implementation project. The **Subscriptions available** page shows the number of deployed sandboxes across all projects.

### Step 5: Remove deployed sandboxes

If you must deploy a sandbox to another project, and you can't or don't want to purchase more sandbox add-ons, you must deallocate and delete a previously deployed sandbox. The sandbox add-on slot will then become available across all your projects, and you can select the new project that you want to deploy it to.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
