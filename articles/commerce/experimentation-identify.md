---
# required metadata

title: Identify a hypothesis and determine metrics for an experiment
description: This topic describes how to establish the hypothesis and success metrics for an experiment you'll run on an e-Commerce website in Dynamics 365 Commerce.
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

# Identify a hypothesis and determine success metrics for an experiment
There are many steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. The first phase in the experimentation lifecycle includes identifying the hypothesis for the experiment and determining the metrics you'll track to evaluate success.

[ ![Experimentation user journey - Identify](./media/experimentation_identify.svg) ](./media/experimentation_identify.svg#lightbox)

Before you set up the experiment in a third-party service and connect it to Dynamics 365 Commerce, you need to define exactly what you want to test and then decide which metrics to track during the experiment to intepret the results. 

A hypothesis is a statement where you predict the outcome of the experiment. Many factors go into defining a hypothesis, for example, research about user behavior and website data you've collected. With the hypothesis, you'll define the assumption or theory you want to validate with your experiment. An example of a hypothesis for your experiment may be "*a picture of a white t-shirt on my home page will drive more clickthroughs on my site than a navy sweater during summer months because people want to wear something lightweight and light color in the summer.*" In that case, you'll create variations that include a white t-shirt and a navy sweater, and publish both at the same time.

Metrics you collect during the experiment track how your website users respond to the variations. Choose which metrics to track based on what you believe will give you the best insight into determining whether your hypothesis is valid. In the example above, you may choose to track bounce rate or conversion rate. 

## Previous topic
[Experimentation in Dynamics 365 Commerce](experimentation-overview.md)


## Next topic
[Set up an experiment](experimentation-setup.md)
