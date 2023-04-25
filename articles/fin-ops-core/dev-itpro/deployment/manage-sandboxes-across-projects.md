---
# required metadata

title: Manage sandbox environments across implementation projects
description: This article explains how to manage multiple sandbox deployments across implementation projects in Dynamics Lifecycle Services.
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

## Introduction

When implementing Dynamics 365 Finance and Operations apps (Finance and Operations apps), it's crucial to have sandboxes for development, testing, and training purposes. Sandboxes allow for testing modifications of Finance and Operations apps before affecting the production environment. Microsoft provides a production and sandbox environment with the purchase of 20 user licenses for Finance and Operations apps apps. Many customers require more than a single sandbox however and as such additional sandboxes can be purchased from the Microsoft 365 portal.  

## Sandbox addons

Extra sandboxes that are purchased are referred to as Sandbox addons.  Sandbox addons come in various performance levels from Tier 2 through Tier 5 with Tier 5 being the highest performing option.  In the past, these extra sandboxes would be shown in all projects simultaneously, making it difficult to keep track of how many sandboxes were deployed. However, Microsoft is now making changes to better help customers stay within their purchased limits by having sandbox slots disappear across other projects as they're deployed. This article will discuss how to manage sandboxes across implementation projects in Dynamics 365 Finance and Operations apps, including details about the new changes.

## Managing Sandboxes Across Implementation Projects

### Step 1: Determine Your Sandbox Requirements 

The first step in managing sandboxes across implementation projects is to determine your sandbox requirements. You need to understand the number of sandboxes required for development, testing, and training purposes. Microsoft provides a production and sandbox environment each implementation project.  If you only have a single implementation project, then this article won't have any impact for you. However, with multiple implementation projects you'll need to decide how many extra Sandboxes you require for each project. To purchase additional sandboxes, visit the [Purchase services](https://admin.microsoft.com/Adminportal/Home#/catalog) page within the Microsoft 365 admin portal.

### Step 2: Create a Project in Lifecycle Services (LCS) 

Once you have determined your sandbox requirements, create a project in Lifecycle Services (LCS). LCS is a Microsoft Azure-based collaboration portal that provides a unified view of implementation projects. You can use LCS to manage project activities, track progress, and collaborate with other team members.

### Step 3: Deploy Sandboxes to Your Project 

Once you have created a project in LCS, you can start to deploy sandboxes required by that project. Sandboxes are deployed in a first-come, first-served approach.  Let's say, for example, that you have 5 sandbox addons you have purchased, and you have two implementation projects.  If you want them to be split as 3 in one project and 2 in another project, you'll need to deploy 3 in the first project as soon as possible.  These 3 slots will be consumed by the first project and will disappear in the second project.  That will leave you with 2 open sandbox addon slots for deploying in the second project.

### Step 4: Keep Track of Deployed Sandboxes 

To ensure that you're staying within your purchased sandbox limits, it's important to keep track of the sandboxes that have been deployed. In the past, extra sandboxes would be shown in all projects simultaneously, making it difficult to keep track of how many sandboxes were deployed. However, Microsoft is making changes such that as a sandbox slot is deployed, it will disappear across other projects to better help customers stay within their purchased limits. This means that you can only deploy a sandbox to one project at a time. To see which sandboxes have been deployed, go to the **Subscriptions available** page in the implementation project to see the number of deployed sandboxes across all projects.

### Step 5: Remove Deployed Sandboxes 

If you need to deploy a sandbox in another project and are unable or don't desire to purchase more sandbox addons, you must deallocate and delete a previously deployed sandbox.  This will provide back the sandbox addon environment slot across all of your projects at which time you can visit the new project to deploy it.

## Conclusion

Managing sandboxes across implementation projects is an important aspect of Dynamics 365 Finance and Operations apps implementation. By following the steps outlined above, you can ensure that you're staying within your purchased sandbox limits and that you have the appropriate number of sandboxes for your development, testing, and training needs. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
