---
title: Preview and publish an experiment
description: Learn how to preview and publish an experiment in Microsoft Dynamics 365 Commerce.
author: sushma-rao 
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-09-30
ms.custom: 
  - bap-template
---

# Preview and publish an experiment

This article describes how to preview and publish your experiment in Microsoft Dynamics 365 Commerce after you [connect your experiment and edit your variations](experimentation-connect-edit.md). The following diagram shows all of the steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. Additional steps are covered in separate articles.

:::image type="content" source="./media/experimentation_preview_publish.svg" alt-text="Screenshot of the experimentation user journey showing the preview and publish step.":::

## Preview your experiment variations
You can preview your variations and continue editing them until they look the way you want.

To preview your experiment variations in Commerce site builder, follow these steps:

1. From the variations drop-down menu, select the content you want to preview.
1. On the command bar, select **Preview**. You see a preview of what the content looks like when published.
1. To preview a different variation, select it from the variation drop-down menu and select **Preview** again.

## Publish your experiment
If you're not using a publish group to schedule when your experiment goes live and you want to publish immediately, select **Publish** in the command bar. All variations that belong to the experiment are published.

> [!IMPORTANT]
> If the page has an unpublished URL, you must first publish the URL or it isn't visible to your website users. For details, see [Save, preview, and publish a page](save-preview-publish-page.md).
    
### Use publish groups to schedule when your experiment goes live
You can schedule variations created in site builder for publishing by using a publish group. Within a publish group, you can connect a page or fragment to your experiment by selecting **Experiments** in the left navigation pane. You can also connect a page or fragment to your experiment by selecting **Pages** or **Fragments** and following the instructions in [Connect an experiment and edit variations](experimentation-connect-edit.md). For information about publish groups, see [Work with publish groups](publish-groups.md).

When you use publish groups with experiments, be aware of these important considerations.
- When you add a page or fragment that has an experiment running on it to a publish group, the experiment is removed from the page or fragment in the publish group.
- Experiments that are connected to pages in a live site aren't available to pages within publish groups and vice-versa. Similarly, pages that have experiments running on them in a live site aren't available to other experiments in publish groups and vice versa.
- When you publish or schedule a publish group, all content in the publish group is published, regardless of whether there's an experiment associated with the publish group.
- Because a publish group continues to persist after it's published to a live site, experiments in the publish group also persist. Therefore, you can't associate other experiments with the same page or fragment. To avoid this limitation, delete any publish groups with persisting experiments. Similarly, if you want to delete an experiment in a live site that also exists in a publish group, delete it from the publish group first.

### Force variations for testing

After you publish the experiment, you can add the experiment ID and variation ID to the default page URL to force a variation for testing or automation purposes. For example, if the default page URL is `https://fabrikam.com/modern/homepage`, you can force a variation with a URL like `https://fabrikam.com/modern/homepage?exp=18012910471|18024360464`. Get the experiment ID and variation ID for your experiment variation from the preview URL in the **Preview** experience.

## Previous step
[Connect and edit an experiment](experimentation-connect-edit.md)

## Next step
[Run and monitor an experiment](experimentation-run-monitor.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
