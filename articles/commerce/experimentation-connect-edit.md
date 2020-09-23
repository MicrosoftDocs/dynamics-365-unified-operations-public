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

# Connect an experiment and edit variations

[ ![Experimentation user journey - Connect & Edit](./media/experimentation_connect_edit.svg) ](./media/experimentation_connect_edit.svg#lightbox)

Once the experiment is setup in the third-party service, the next step is to connect it to an entity in Commerce and edit its variations.

## Determine the scope of your experiment
When you connect an experiment in Commerce, you must next define the scope of the experiment. Experiments can be full scope or partial scope. Choose **partial** if you want to target a specific portion of a page. In this case, content changes made to the default page or fragment will be automatically synchronized across variations. Choose **full** if you want to target an entire page or fragment. In this case, separate copies of the default page or fragment are created i.e. content changes will need to be manually synchronized across variations.

## Decide how you want to publish your experiment
Think about whether you want to schedule your experiment to be published in a publish group or directly publish to your live site. This will help you determine where you want to create your experiment.

Read more about [publishing your experiment](experimentation-preview-publish.md).## Connect your experiment
To connect your experiment in Commerce, go to the **Experiments** tab in site builder and click **Connect** to open the *Connect experiment* wizard. This wizard can also be accessed from within a page or fragment editor when in the edit mode, by clicking on **Connect experiment** in the command bar.
> [!NOTE]
> One page can only be connected to one experiment at a time. To connect a page to a different experiment, you will need to first delete the existing experiment.





Next, choose the procedure below that matches the scope of your experiment based on what you decided earlier in the [Identify the goals for your experiment](experimentation-identify.md) stage.

## Edit variations for an experiment with partial scope
1. As a first step in the wizard, choose a page or fragment to be experimented upon.
1. In the next step, set the experimentation scope to **entire** if experimenting on the full entity and to **partial** if experimenting on a small portion of the entity. If you associate your experiment with a page that uses a layout, you will only be able to scope the experiment to the entire page.
    > [!NOTE]
    > Remember to enable the "Experiment on pages or fragments" feature flag if you want to experiment on a full page or fragment.
1. In the final step, click on **Generate variations and exit wizard** to auto-generate the variations. These are nothing but copies of the original page or fragment you previously chose. 
1. In the editor view, use the variations drop-down menu below the command bar to edit each variation based on your original hypothesis. You can also optionally establish a control or base variation to compare to by leaving one of the variations unchanged.
1. Select the module to be experimented on, click on the ellipsis for more options and then click on **Add to experiment**.

## Edit variations for an experiment with entire scope
1. As a first step in the wizard, choose a page or fragment to be experimented upon.
1. In the next step, set the experimentation scope to **entire** if experimenting on the full entity and to **partial** if experimenting on a small portion of the entity. If you associate your experiment with a page that uses a layout, you will only be able to scope the experiment to the entire page.
    > [!NOTE]
    > Remember to enable the "Experiment on pages or fragments" feature flag if you want to experiment on a full page or fragment.
1. In the final step, click on **Generate variations and exit wizard** to auto-generate the variations. These are nothing but copies of the original page or fragment you previously chose. 
1. In the editor view, use the variations drop-down menu below the command bar to edit each variation based on your original hypothesis. You can also optionally establish a control or base variation to compare to by leaving one of the variations unchanged.
