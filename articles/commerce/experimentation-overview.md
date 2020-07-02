---
# required metadata

title: Commerce Experimentation
description: <fill in>
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


# Run experiments on web pages
## Overview
Web-based experimentation is the process of using controlled experiments such as A/B testing to experiment with variations of webpages and determining which changes result in more conversions, thereby better customer adoption and engagement.

Dynamics 365 Commerce supports the creation, editing, and management of page and content treatments in site builder. Integrations with third-party solution providers enable the creation of experiments and treatment assignments. Event streams from the web storefront support the analytics and reports defining experiment results in the third-party solution.

## Prerequisites

## Create an experiment

## Create webpage variations for the experiment

1. Go to the “Experiments” tab in site builder’s left nav bar.
1. Click “Connect” to link to an experiment in the test connector or the third-party connector.
1. Go through the wizard to choose the page or fragment to be experimented upon and generate the variations. 
    - Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/page-elements-overview) for more information on the page model.
1. Make the required changes to the variations in the WYSIWYG editor. 
    - You can also optionally designate a “control” by not making any changes to it.
> [!NOTE]
> The control in a web experiment refers to the experience that will remain unchanged throughout the duration of the experiment. This helps set the baseline metric for the experiment and identify the “winner”.
1. Preview the variations and click on “Publish” to publish them. Note that this operation will publish all variations that belong to the experiment.
