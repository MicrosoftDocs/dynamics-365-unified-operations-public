---
# required metadata

title: Experimentation in Dynamics 365 Commerce
description: Enable the creation, editing, and management of page layout and content treatments in site builder. End-to-end experimentation support will be enabled for e-commerce pages, as well as entities within a page.
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
1. Setup test connector or purchase and setup third-party connector - terms need explaining. <add link to Sam's doc>
1. Turn on feature flags - needs description + images. 

## Create an experiment
Once the third-party connector setup is complete, follow the necessary steps to create an experiment in the third-party service. The list of experiments from here will be pulled into site builder to help with associating the required web experiences.

## Create webpage variations for the experiment
1. Go to the “Experiments” tab on site builder’s left nav bar to view the list of experiments from either the test connector or the third-party connector. 
1. Click “Connect” to open up the "Connect experiment" wizard.
1. Go through the wizard to choose an entity to be experimented upon and auto-generate the required number of variations. 
    - Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/page-elements-overview) for more information on page model entities - pages, modules and fragments.
1. Make the required changes to the variations in the WYSIWYG editor. You can also optionally designate a “control” by not making any changes to it.
    > [!NOTE]
    > The control in a web experiment refers to the experience that will remain unchanged throughout the duration of the experiment. This helps set the baseline metric for the experiment and identify the 'winner'.
1. Preview the variations and click on “Publish” to publish them. Note that this single operation will publish all variations that belong to the experiment.

## Discover events to measure experiment success
1. Go to the “Pages” tab in site builder's left nav bar and click on the desired page. 
1. Click on "Events" in the right property pane of the page or module of interest.
1. View the list of events associated and copy the required event to the clipboard.
1. Use the event as necessary in the third party service to track success metrics for the experiment.

## Editing webpage variations
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service and click on the "Unpublish" button in the top bar.
1. Pick the variation that needs updating from the drop down below the experiment name in the WYSIWYG editor.
1. Make the required changes, preview the changes and publish.

## Deleting webpage variations
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service and click on the "Unpublish" button in the top bar.
1. Pick the variation to be deleted from the drop down below the experiment name in the WYSIWYG editor.
1. Click on "Delete" in the top bar to delete the variation and publish as necessary.

## Running the experiment and viewing results
1. Start the experiment in the third-party service so the right variation experiences can be shown to web users.
1. Let the experiment run for a few days/weeks depending on the recommendation from the third-party service.
1. View experiment related data and analytics in the third-party service.
    > [!NOTE]
    > If the experiment is not running in the third-party service, the variation experiences will not be shown i.e. all web users will see the same 'default' version of the page.

## Picking a winning webpage variation
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment.
1. Click "Complete" on the top bar once the experiment has run and gathered sufficient data.
1. Use the analytics generated in the thir-party service to pick a winner and click "Next".
1. Click "Complete" to promote the 'winning' experience to the web storefront.
1. Stop the experiment in the third-party service.
