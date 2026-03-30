---
title: Identify a hypothesis and determine metrics for an experiment
description: Learn how to identify the hypothesis and success metrics for an experiment you run on a Microsoft Dynamics 365 Commerce e-commerce site.
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

# Identify a hypothesis and determine success metrics for an experiment

This article explains how to identify the hypothesis and success metrics for an experiment you run on a Microsoft Dynamics 365 Commerce e-commerce site.

The first phase in the experimentation lifecycle includes identifying the hypothesis for the experiment and determining the metrics you track to evaluate success. The following diagram shows all of the steps involved in [setting up and running an experiment](experimentation-overview.md) on an e-commerce website in Dynamics 365 Commerce. Additional steps are covered in separate articles. 

:::image type="content" source="./media/experimentation_identify.svg" alt-text="Screenshot of the experimentation user journey showing the identify step.":::

A hypothesis is a statement where you predict the outcome of the experiment. Many factors go into defining a hypothesis, for example, research about user behavior and website data you collect. With the hypothesis, you define the assumption or theory you want to validate with your experiment. An example of a hypothesis for your experiment might be "*a picture of a white t-shirt on my home page will drive a higher clickthrough rate than a navy sweater during summer months because people want to wear something lightweight and light colored in the summer.*" In that case, you create variations that include a white t-shirt and a navy sweater, and publish both at the same time.

To validate a hypothesis, the success or failure of an experiment should be directly tied to user actions such selecting a link or button. These actions must correspond with events that the partner service tracking the experiment can report. Over time, the percentage of users that take the action is tallied as a metric you can use to generate reports and conduct analyses. To review all of the available events and attributes, see [Commerce component events for diagnostics and troubleshooting](dev-itpro/retail-component-events-diagnostics-troubleshooting.md).

## Previous step
[Experimentation in Dynamics 365 Commerce](experimentation-overview.md)

## Next step
[Set up an experiment](experimentation-setup.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
