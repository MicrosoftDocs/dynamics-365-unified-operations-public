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
ms.custom: 24211
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Manage sandbox environments across implementation projects

[!include[banner](../includes/preview-banner.md)]

Managing sandboxes across implementation projects is an important aspect of finance and operations apps implementation. By following the steps outlined in this article, you can ensure that you're staying within your purchased sandbox limits.

When implementing Microsoft Dynamics 365 finance and operations apps, it's crucial to have the appropriate number of sandboxes for your development, testing, and training purposes. Sandboxes allow you to test modifications of finance and operations apps before affecting your production environment. Microsoft provides one production and one sandbox environment with the purchase of 20 user licenses for finance and operations apps. Many customers require more than one sandbox, therefore, you can purchase more sandboxes from the Microsoft 365 portal.  

## Sandbox add-ons

The extra sandboxes that you purchase are referred to as sandbox add-ons. Sandbox add-ons come in various performance levels, from Tier 2 through Tier 5, with Tier 5 being the highest performing option. In the past, sandbox add-ons would be shown in all projects simultaneously and made it difficult to keep track of how many sandboxes were deployed. Microsoft is now making changes to help you stay within you purchased limits by having sandbox slots disappear across other projects as they're deployed. 

## Managing sandboxes across implementation projects

The following sections explain the steps you can to take to manage sandboxes across implementation projects.

### Step 1: Determine your sandbox requirements 

The first step in managing sandboxes across implementation projects is to determine your sandbox requirements. You need to understand the number of sandboxes that are required for development, testing, and training purposes. Microsoft provides one production and one sandbox environment for each implementation project. If you only have a single implementation project, then this article won't have any impact for you. If you have multiple implementation projects, you'll need to decide how many extra sandboxes you require for each project. To purchase additional sandboxes, visit the [Purchase services](https://admin.microsoft.com/Adminportal/Home#/catalog) page within the Microsoft 365 admin portal.

### Step 2: Create a project in Lifecycle Services 

Once you have determined your sandbox requirements, create a project in Lifecycle Services. Lifecycle Services is a Microsoft Azure-based collaboration portal that provides a unified view of implementation projects. You can use Lifecycle Services to manage project activities, track progress, and collaborate with other team members.

### Step 3: Deploy sandboxes to your project 

After you have created a project in Lifecycle Services, you can start to deploy the sandboxes that are required for the project. Sandboxes are deployed with a first-come, first-served approach. For example, let's say you have five sandbox add-ons that you have purchased, and you have two implementation projects. If you want to have three sandboxes in one project and two in another project, deploy three sandbox add-ons in the first project as soon as possible. These three sandbox add-on slots are consumed by the first project and will disappear from the second project. The remaining two open sandbox add-on slots are then available to deploy in the second project.

### Step 4: Keep track of deployed sandboxes 

It's important to keep track of the sandboxes that you have deployed. In the past, extra sandboxes were shown simultaneously in all projects. This made it difficult for you to keep track of how many of the sandboxes were deployed. Now, when a sandbox is deployed, it disappears from view in your other projects. Only sandboxes that are available to be deployed display to help you stay within your purchased limits. You can only deploy a sandbox to one project at a time. To see which sandboxes have been deployed, go to the **Subscriptions available** page in the implementation project. The **Subscriptions available** page shows the number of deployed sandboxes across all projects.

### Step 5: Remove deployed sandboxes 

If you need to deploy a sandbox in another project, and are unable or don't desire to purchase more sandbox add-ons, you must deallocate and delete a previously deployed sandbox. This will make the sandbox add-on slot available across all of your projects so you can select the new project where you want to deploy it.
 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
