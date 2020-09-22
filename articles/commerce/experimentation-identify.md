---
# required metadata

title: Identify goals for an experiment
description: This topic describes how to establish the goals for an experiment you'll run on an e-Commerce website in Dynamics 365 Commerce.
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

# Identify goals for an experiment
There are many steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. The first phase in the experimentation lifecycle includes identifying the goals for the experiment and deciding how you want to set up the experiment in Commerce.

[ ![Experimentation user journey - Identify](./media/experimentation_identify.svg) ](./media/experimentation_identify.svg#lightbox)

Identify is the first stage in the experimentation journey where you decide the what and how for your experiment. Here are some things to consider:

## Create a hypothesis and configure metrics
Define the assumption or theory you want to validate with your experiment and the success metrics that you expect it to impact.

## Decide what you want to experiment on
Define the scope of the experiment - full or partial. Choose **partial** if you want to target a specific portion of a page. In this case, content changes made to the default page or fragment will be automatically synchronized across variations. Choose **full** if you want to target an entire page or fragment. In this case, separate copies of the default page or fragment are created i.e. content changes will need to be manually synchronized across variations.

## Decide how you want to publish your experiment
Think about whether you want to schedule your experiment to be published in a publish group or directly publish to your live site. This will help you determine where you want to create your experiment.

Read more about [publishing your experiment](experimentation-preview-publish.md).
