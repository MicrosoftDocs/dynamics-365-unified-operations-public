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

# Connect
Once the experiment is setup in the third-party service, the next step is to associate it with the corresponding experiences in Dynamics 365 Commerce. To do this:
1. Go to the **Experiments** tab in site builder to view the list of experiments from the connector configured above. 
1. Click **Connect** to open the *Connect experiment* wizard. This wizard can also be accessed from within a page or fragment editor when in the edit mode, by clicking on **Connect experiment** in the command bar.
    > [!NOTE]
    > One page can only be connected to one experiment at a time. To connect a page to a different experiment, you will need to first delete the existing experiment.
1. Go through the wizard to choose an entity to be experimented upon and auto-generate the variations as a copy of what already exists. 
    > [!NOTE]
    > Remember to enable the "Experimentation on pages or fragments" feature flag to allow experimentation on pages and fragments. Set the experimentation scope to **entire** if experimentating on the full entity and to **partial** if experimenting on a small portion of the entity.
1. Make the required changes to the variations in the editor view. You can also optionally establish a **control** or base variation to compare to by not making any changes to it.
1. Preview the variations to ensure everything looks good. The editor context will determine which variation you are previewing. If you want to preview a different variation, select the variation in the editor drop down and click preview again.
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
