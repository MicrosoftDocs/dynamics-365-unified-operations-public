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

# Preview and publish your experiment
![Experimentation user journey - Preview & Publish](./media/experimentation_preview_publish.svg "Experimentation user journey - Preview & Publish")
Once you edit the variations in Commerce, follow the steps below to preview and publish them:
1. Click on **Preview** in the top bar to review the variation you are currently working on and ensure everything looks good. If you want to preview a different variation, select it from the variation drop down and click preview again.
1. Click on **Publish** in the top bar to publish all variations that belong to the experiment.
    > [!NOTE]
    > If the page has an unpublished URL, make sure to publish the URL first or it will not be visible to end-users. See more details on how to save, preview and publish a page [here](https://docs.microsoft.com/en-us/dynamics365/commerce/save-preview-publish-page).
    
## Publish experiments with publish groups
Experiment variations created within site builder can also be scheduled for publishing with a publish group. Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/publish-groups) to learn more about publish groups.

Some things to keep in mind:
- When adding a page or fragment to a publish group, any experiments running on it will be removed.
- Within a publish group, you can connect a page or fragment to your experiment either through the **Experiments** tab or the **Pages** / **Fragments** tab as explained in the *Connect and edit* section. 
- Experiments that are already connected to pages in live site, will not be available to pages within publish groups and vice-versa. Similarly, pages that have experiments running on them in live site, cannot be associated with other experiments in publish groups and vice-versa.
- When you publish a publish group, all content within it will be published, whether it has an experiment or not.
- Since publish groups continue to persist even after they have been published to live site, any experiments in them will also persist and limit your ability to associate other experiments to the same page or fragment. To avoid this, make sure to delete any publish groups with persisting experiments first. Similarly, if you want to delete a page or fragment experiment in live site that also exists in publish groups, make sure to first delete it from the publish groups.
