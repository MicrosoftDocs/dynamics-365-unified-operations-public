---
# required metadata

title: Connect an experiment and edit variations
description: This topic describes how to connect an experiment in a third-party service to Dynamics 365 Commmerce, and how to edit variations for the experiment.
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

# Connect an experiment and edit variations

There are many steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. After you've set up your experiment in a third-party service, you'll connect the experiment in Dynamics 365 Commerce and edit the experiment variations.

[ ![Experimentation user journey - Connect & Edit](./media/experimentation_connect_edit.svg) ](./media/experimentation_connect_edit.svg#lightbox)

## Planning considerations

Before you connect your experiment in Commerce, you'll need to make some decisions that impact the way Commerce manages your content.

### Determine the scope of your experiment
When you connect an experiment in Commerce, you are prompted to define the scope of the experiment. Experiments in Commerce are defined as **partial** scope or **full** scope.
- Choose **partial** if you want to target a specific portion of a page for the experiment. Changes you make to the default page or fragment that aren't related to the experiment are automatically synchronized across variations. 
- Choose **full** if you want to target an entire page or fragment. Separate copies of the default page or fragment are created in this scenario. In other words, if you make changes to content that aren't related to the experiment, you'll have to manually synchronize the changes across variations.

### Decide how you want to publish your experiment
You need to decide whether you want to schedule your experiment to be published to your live site in a publish group, or directly publish to your live site. Your choice will dictate where you'll create your experiment.

For more information, refer to the [Preview and publish an experiment](experimentation-preview-publish.md) topic.

## Connect your experiment
To connect your experiment in Commerce, you'll launch the **Connect experiment** wizard. The wizard walks you through the steps required to connect your experiment. When you complete the wizard, your experiment is connected and variations are created and ready to be edited.

To launch the wizard, select the **Experiments** tab in site builder and then select **Connect**. Alternatively, tThe wizard can be accessed from a page or fragment editor. In edit mode, select **Connect experiment** in the command bar.

> [!NOTE]
> A page can only be connected to one experiment at a time. To connect a page to a different experiment, delete the experiment the page is currently connected to.


## Edit your variations
When you exit the wizard, Commerce creates the variations that you defined in the third-party service. Choose the procedure below that corresponds to the scope you chose for your experiment in the [Determine the scope of your experiment](#Determine-the-scope-of-your-experiment) section above.

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
