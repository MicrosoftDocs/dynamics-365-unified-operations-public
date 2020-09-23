---
# required metadata

title: Preview and publish an experiment
description: This topic describes how to preview and publish an experiment from Dynamics 365 Commerce.
author:  sushma-rao 
manager: AnnBe
ms.date: 10/01/2020
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

# Preview and publish an experiment

There are many steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. This topic describes how to preview and publish your experiment in Commerce.

[ ![Experimentation user journey - Preview & Publish](./media/experimentation_preview_publish.svg) ](./media/experimentation_preview_publish.svg#lightbox)

After you edit your variations, you'll preview your variations and then publish the experiment.

## Preview variations
You can preview your variations and continue editing them until they look the way you want them to.

1. In editor view in site builder, use the variations drop-down menu below the command bar to select the content you want to preview. 
1. Select **Preview** in the top bar. A preview of what the content will look like when it's published is displayed.
1. To preview a different variation, select it from the variation drop-down and select **Preview** again.

## Publish your experiment
If you aren't using a publish group to schedule when your experiment goes live and you want to publish immediately, select **Publish** in the top bar. All variations that belong to the experiment will be published.
    
    > [!IMPORTANT]
    > If the page has an unpublished URL, you must first publish the URL or it won't be visible to your website users. For more details, refer to the [Save, preview, and publish a page](save-preview-publish-page) topic.
    
### Publish experiments with publish groups
Variations created in site builder can be scheduled for publishing with a publish group. For more information on publish groups, refer to the [Work with publish groups](publish-groups.md) topic.

Some things to keep in mind:
- When adding a page or fragment to a publish group, any experiments running on it will be removed.
- Within a publish group, you can connect a page or fragment to your experiment either through the **Experiments** tab or the **Pages** / **Fragments** tab as explained in the *Connect and edit* section. 
- Experiments that are already connected to pages in live site, will not be available to pages within publish groups and vice-versa. Similarly, pages that have experiments running on them in live site, cannot be associated with other experiments in publish groups and vice-versa.
- When you publish a publish group, all content within it will be published, whether it has an experiment or not.
- Since publish groups continue to persist even after they have been published to live site, any experiments in them will also persist and limit your ability to associate other experiments to the same page or fragment. To avoid this, make sure to delete any publish groups with persisting experiments first. Similarly, if you want to delete a page or fragment experiment in live site that also exists in publish groups, make sure to first delete it from the publish groups.
