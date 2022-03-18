---
# required metadata

title: Connect an experiment and edit variations
description: This topic describes how to connect an experiment in a third-party service to Dynamics 365 Commerce, and how to edit variations for the experiment.
author:  sushma-rao 
ms.date: 10/21/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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

This topic describes how to connect your experiment in Commerce and make changes to your variations so that they align with your hypothesis. 

The following diagram shows all of the steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. Additional steps are covered in separate topics.

[ ![Experimentation user journey - Connect & Edit.](./media/experimentation_connect_edit.svg) ](./media/experimentation_connect_edit.svg#lightbox)

After you've [set up your experiment](experimentation-setup.md) in a third-party service, you'll connect the experiment in Dynamics 365 Commerce and edit the experiment variations.

## Planning considerations

Before you connect your experiment in Commerce, you'll need to make some decisions that impact the way Commerce manages your content.

### Determine the scope of your experiment
When you connect an experiment, you are prompted to define the scope of the experiment. Experiments are defined as **partial** scope or **entire** scope.
- Choose **partial** if you want to conduct an experiment on a specific portion of a page. If you select this option, you must identify which modules are included in the experiment. Changes that are made to parts of the default page or fragment that aren't related to the experiment are automatically synchronized across variations.
- Choose **entire** if you want to conduct an experiment on an entire page or fragment. Separate copies of the default page or fragment are created. You won't have to select which modules are included in the experiment because the whole editing surface is available to change. You can add, delete, or re-order modules as needed. However, if any changes are made to the default page or fragment that the experiment is associated with, those changes have to be manually synchronized across all variations.

<!-- not to editors, we're adding an image here to illustrate the difference. it will help.) -->

> [!NOTE]
> If you associate your experiment with a page that uses a layout, you can only scope the experiment as **entire**.

### Decide if you want to schedule when your experiment is published
If you want to schedule when your experiment is published to your live site, make sure the content you want to associate with the experiment is available in a publish group *before* you connect the experiment. 

For more information about publish groups, refer to [Work with publish groups](publish-groups.md).


## Connect your experiment
To connect your experiment, you'll launch the **Connect experiment** wizard. The wizard walks you through the steps required to connect your experiment. When you complete the wizard, your experiment is connected and variations are created and ready to be edited.

To get started connecting your experiment in Commerce site builder, follow these steps.

1. To launch the **Connect experiment** wizard, select **Experiments** in the left navigation pane, and then select **Connect**. Alternatively, you can access the wizard from a page or fragment editor by editing it and selecting **Connect experiment** on the command bar.

    > [!NOTE]
    > A page can only be connected to one experiment at a time. To connect a page to a different experiment, first delete the experiment that the page is currently connected to.

1. Choose the page or fragment you want to run your experiment on.
1. Set the experimentation scope to **partial** or **entire**, based on the choice you made in the [Determine the scope of your experiment](#determine-the-scope-of-your-experiment) section above.
    > [!NOTE]
    > The **Experiment on pages or fragments** feature flag must be enabled if you want to experiment on a full page or fragment. Refer to the [Experimentation in Dynamics 365 Commerce](experimentation-overview.md) topic for more information.
    
1. In the final step of the wizard, select **Generate variations and exit wizard**. Variations are created for the experiment. 

## Edit your variations
When you exit the wizard, variations are created for you. 

Next, you'll edit the variations so they reflect the choices that you need to verify in the experiment hypothesis. Choose one of following procedures that corresponds to the scope you chose for your experiment in the [Determine the scope of your experiment](#determine-the-scope-of-your-experiment) section above.

### Edit variations for experiments with partial scope
Follow these steps if you defined the scope of your experiment as **partial** in the **Connect experiment** wizard.

1. In editor view, use the variations drop-down menu below the command bar to edit each variation based on your original hypothesis. You may also want to establish a control or base variation by leaving one of the variations unchanged.
1. Select the module to be experimented on, select the ellipsis (...), and then select **Add to experiment**.

### Edit variations for experiments with entire scope
If you defined the scope of your experiment as **entire** in the **Connect experiment** wizard, while in editor view, use the variations drop-down menu below the command bar to edit each variation based on your original hypothesis. 

> [!NOTE]
> In either case, you may also want to establish a control or base variation by leaving one of the variations unchanged.

## Previous step
[Set up an experiment](experimentation-setup.md) 


## Next step
[Preview and publish an experiment](experimentation-preview-publish.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]