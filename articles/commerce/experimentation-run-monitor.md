---
title: Run and monitor an experiment
description: Learn how to run and monitor an experiment in a partner app and change variations as needed in Microsoft Dynamics 365 Commerce.
author: sushma-rao 
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2020-09-30
ms.custom: 
  - bap-template
---

# Run and monitor an experiment

This article describes how to run and monitor an experiment in a partner app and change variations as needed in Microsoft Dynamics 365 Commerce. 

Before you complete the steps in this article, first [publish](experimentation-preview-publish.md) your experiment in Commerce. 

The following diagram shows all of the steps involved in setting up and running an experiment on an e-commerce website in Dynamics 365 Commerce. Additional steps are covered in separate articles.

:::image type="content" source="./media/experimentation_run_monitor.svg" alt-text="Screenshot of the experimentation user journey showing the run and monitor step.":::

After you publish your variations, you complete all of the steps in Commerce to run your experiment. The next step is determining which variation to show to each user when they request a page. The partner service makes that determination, but first you have to activate the experiment within the service. Since the steps for activating an experiment vary from service to service, follow the instructions included with your service or provider. If the experiment isn't activated, users see only the default version of the page (no variations are displayed).

Keep the experiment running long enough to gather data for statistically valid results. Use the partner service to monitor the experiment-related data and analytics while the experiment is running.

## Adjust your variations
If you need to modify your variations, follow the steps in this section.

> [!IMPORTANT]
> If you make changes to a live experiment in Commerce or the partner service, you might significantly affect your results. Consider letting the experiment run its course and then creating a new experiment for major changes.

1. In Commerce site builder, select **Experiments** in the left navigation pane, and then select the experiment. 
1. Select the variation you want to update from the drop-down menu.
1. Make any needed changes, and then preview and publish the variations. For more information, see [Preview and publish an experiment](experimentation-preview-publish.md).
1. Go to the partner service to make any experiment setup-related changes.
  
## Previous step
[Preview and publish an experiment](experimentation-preview-publish.md)

## Next step
[Promote a variation and complete an experiment](experimentation-review-complete.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
