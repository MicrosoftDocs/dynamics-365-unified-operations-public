---
# required metadata

title: Experimentation in Dynamics 365 Commerce
description: Enable the creation, editing, and management of page layout and content treatments in site builder. End-to-end experimentation support will be enabled for e-commerce pages, as well as entities within a page.
author:  sushma-rao 
manager: AnnBe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: sushmar
ms.search.validFrom: 2020-09-30
ms.dyn365.ops.version: AX 10.0.13
---

# Preview and publish
Once you edit the variation experiences in Commerce, follow the steps below to preview and publish them:
1. Click on **Preview** to review the variations and ensure everything looks good. The editor context will determine which variation you are previewing. If you want to preview a different variation, select the variation in the editor drop down and click preview again.
1. Click on **Publish** to publish the variations. Note that this single operation will publish all variations that belong to the experiment.
    > [!NOTE]
    > If the page has an unpublished URL, make sure to publish the page URL first or it will not be visible to end-users. See more details on how to save, preview and publish [here](https://docs.microsoft.com/en-us/dynamics365/commerce/save-preview-publish-page).
    
## Using publish groups to publish experiments
Experiment variations created within site builder can be scheduled for publishing within a publish group. You can either create pages or other items within publish groups or add existing ones to them. Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/publish-groups) to learn more about publish groups.

> [!NOTE]
> While adding a page to a publish group, any experiments running on it will be removed.

Some things to keep in mind:
1. You can connect to an experiment either through the **Experiments** tab or the **Pages** / **Fragments** tab as explained above. 
1. Experiments that are already connected to pages in live site, will not be available to pages within publish groups. The same is true for experiments connected to pages within publish groups.
1. When you publish the content in a publish group, all content within it will be published, whether it has an experiment or not.
