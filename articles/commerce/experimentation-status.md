---
title: Review the status of an experiment
description: Learn how to review the status an experiment in the Microsoft Dynamics 365 Commerce experimentation lifecycle. 
author:  sushma-rao 
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-09-30
ms.custom: 
  - bap-template
---

# Review the status of an experiment

This article explains how to review the status of an experiment in the Microsoft Dynamics 365 Commerce experimentation lifecycle.

Setting up and running an experiment in Microsoft Dynamics 365 Commerce involves many steps. For more information about the experimentation lifecycle, see [Experimentation in Dynamics 365 Commerce](experimentation-overview.md).

To see where an experiment is in the lifecycle, select **Experiments** in the left navigation pane of Commerce site builder. You see a list of experiments with the status of each experiment in both Commerce and the partner service that you use to enable the creation of experiments, assign variations, and analyze data.

In the **Commerce status** column, you see the following values. 
- **Draft** - You connect the experiment to a page or fragment in Commerce and you're editing it.
- **Published** - The experiment variations are ready to display on your website. If the experiment is running in the partner service, website users see a variation of the page or fragment as selected by the partner service.
- **Unpublished** - The experiment is no longer available on your website. Website users only see the default version of the page or fragment even if the experiment is running in the partner service.
- **Completed** - The experiment ran and a variation was promoted to live for all website users.

Similarly, in the **third-party status** column, you see the following values that indicate what status the experiments are in the partner service.
- **Draft** - You set up the experiment in the partner service but didn't start it.
- **Running** - You started the experiment in the partner service and it's collecting data.
- **Paused** - The experiment is paused and not collecting data. You must resume the experiment for it to collect data again.
- **Archived** - The experiment ran and the partner service cataloged it for future reference.

The following diagram shows both sets of statuses and how they relate to each other.

:::image type="content" source="./media/experimentation_statuses.svg" alt-text="Screenshot of experimentation statuses showing Commerce and third-party status relationships.":::

[!INCLUDE[footer-include](../includes/footer-banner.md)]
