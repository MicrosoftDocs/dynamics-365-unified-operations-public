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
1. Check and update to the "right" e-commerce product versions.
1. Setup test connector or purchase and setup third-party connector - terms need explaining.
1. Turn on feature flags - needs description + images. Also explain event discoverability here.

## Create an experiment
Once the third-party connector setup is complete, follow the necessary steps to create an experiment in the third-party service. The list of experiments from here will be pulled into site builder to help with associating the required web experiences.

## Create webpage variations for the experiment
1. Go to the “Experiments” tab on site builder’s left nav bar to view the list of experiments from the test connector or the third-party connector. 
1. Click “Connect” to open up the "Connect experiment" wizard.
1. Go through the wizard to choose an entity to be experimented upon and auto-generate the required number of variations. 
    - Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/page-elements-overview) for more information on pages, modules and fragments.
1. Make the required changes to the variations in the WYSIWYG editor. You can also optionally designate a “control” by not making any changes to it.
    > [!NOTE]
    > The control in a web experiment refers to the experience that will remain unchanged throughout the duration of the experiment. This helps set the baseline metric for the experiment and identify the “winner”.
1. Preview the variations and click on “Publish” to publish them. Note that this operation will publish all variations that belong to the experiment.

## Editing and deleting webpage variations
Go to the “Pages” tab in site builder's left nav bar and open the desired page with variations that needs updating. 

## Running the experiment and viewing results
1. Start the experiment in the third-party service so the right variation experiences can be shown to web users.
1. Let the experiment run for a few days/weeks depending on the recommendation from the third-party service.
1. View experiment related data and analytics in the third-party service.

<Note: When a web request comes in for a published page participating in an experiment, our system will use the connector to ask the third-party service which variation of the page to show to each user.  If the experiment is not running in the third-party service, all users will only see the default version of the page. <need to define what the default is>

## Picking a winning webpage variation
1. Pick a winner and promote it.
1. Complete the experiment in Commerce.
1. Stop the experiment in the third-party service.
