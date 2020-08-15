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


# Experiment on e-commerce pages
## Overview
Web experimentation is the process of using controlled experiments such as A/B tests to present different versions of a page to groups of end-users and validate hypotheses with data. User interactions with each version are tracked to enable making data-informed changes and thereby drive higher conversion rates.

Use experimentation to measure the impact of new changes or ideas and avoid making costly updates to your website before understanding their impact.

## Experimentation journey
The experimentation journey typically begins with creating a hypothesis or the theory that needs to be tested. Dynamics 365 Commerce supports the creation, editing, and management of page and content treatments also known as <b>variations</b> within site builder. Integrations with third-party services enable the creation of experiments and treatment assignments. Live event streams from Dynamics 365 Commerce enable the analytics defining experiment results in the third-party service to help support or refute the hypothesis.

![Experimentation user journey](./media/experimentation-user-journey.png "Experimentation user journey")

> [!NOTE]
> A/B testing on pages, modules and fragments is fully supported in Dynamics 365 Commerce. Multi-variate and multi-page testing can be achieved with fragment-based experimentation, as long as these tests are supported in the third-party service.

## Prerequisites
1. Get the right version of Dynamics 365 Commerce - Upgrade SSK, SDK and Retail Server to version 10.0.13.
1. Setup an experimentation connector - An experimentation connector allows Dynamics 365 Commerce to connect with third-party services to retrieve the list of experiments and determine when to show an experiment to each user. You can either use the sample test connector <available where> or setup a third-party connector purchased from [AppSource](https://appsource.microsoft.com), following instructions [here](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/connectors).
1. Turn on the experimentation feature flags
    1.1 Go to Site Settings -> Features. 
    1.1 Set the "Experimentation" flag to on to enable experiments to be run on modules within a page. Turning this flag off will turn off the experimentation feature and no experiment variations will be shown to end users. 
    1.1 Set the "Experimentation on pages or fragments" flag to enable experiments to be run on a page or fragment. Setting this flag to off will turn off the ability to create new page and fragment experiments.

<Add Images>
<Tenant level flags>

## Create an experiment
Once the connector setup is complete, follow the required steps to create an experiment in the third-party service. The list of experiments from here will be available in site builder within about 5 minutes.

## Create experiment variations
The next step is to associate the experiment with the corresponding web experiences. To do this:
1. Go to the “Experiments” tab on site builder’s left nav bar to view the list of experiments from the connector configured above. 
1. Click “Connect” to open the "Connect experiment" wizard.
1. Go through the wizard to choose an entity to be experimented upon and auto-generate the variations as a copy of what already exists. 
    - Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/page-elements-overview) for more information on page model entities - pages, modules and fragments.
1. Make the required changes to the variations in the editor view. 
    > [!NOTE]
    > You can also optionally establish a "control" or base experience to compare your experiment results against. Designate one of the variations generated as the control by not making any changes to it.
1. Preview the variations and click on “Publish” to publish them. Note that this single operation will publish all variations that belong to the experiment.
<<Note that if this page has an unpublished URL, it will not be visible to the end customers. Make sure to publish the page URL first. Add link to doc on how to publish a page.>>

## Add events to measure experiment success
Every experiment needs metrics that measure its impact. Follow the steps below to enable metrics computation in the third-party service using events from Dynamics 365 Commerce:
1. Go to the “Pages” tab in site builder's left nav bar and click on the desired page. 
1. Click on "Events" in the right property pane of the page or module of interest.
1. View the list of events associated and copy the required event to the clipboard.
    - Click [here](https://docs.microsoft.com) to view all available events and attributes. <add link to Aamir's doc> 
1. Use the event as necessary in the third-party service to track success metrics for the experiment.

## Start the experiment and collect results
Once the variations are setup in Dynamics 365 Commerce, follow the steps below to run the experiment in the third-party service and track user interactions to compute success metrics:
1. Start the experiment in the third-party service so the right variation experiences can be shown to web users.
1. Let the experiment run for a few days/weeks depending on the recommendation from the third-party service.
1. View experiment related data and analytics in the third-party service.
    > [!NOTE]
    > If the experiment is not running in the third-party service, the variation experiences will not be shown i.e. all web users will see the same 'default' version of the page.

## Edit experiment variations
To edit variations in Dynamics 365 Commerce:
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service, unless making a minor change with no significant impact to the experiment results.
1. Pick the variation that needs updating from the drop down just below the experiment name in the editor.
1. Make the required changes, preview the changes and publish. 
    > [!NOTE]
    > The editor context will determine which variation you are previewing. If you want to preview a different variation, select the variation in the editor drop down and click preview again.
1. Go to the third-party service to make changes to the names of the variations.

## Delete experiment variations
To delete variations in Dynamics 365 Commerce:
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service and click on the "Unpublish" button in the top bar.
1. Pick the variation to be deleted from the drop down below the experiment name in the WYSIWYG editor.
1. Click on "Delete" in the top bar to delete the variation and publish as necessary.

## Pick a winning experiment variation
After an experiment completes and has sufficient results to determine whether it was a success or not, the winning experience can be promoted to all users of the website as follows:
1. Go to the “Experiments” tab in site builder's left nav bar and click on the desired experiment.
1. Click "Complete" on the top bar once the experiment has run and gathered sufficient data.
1. Use the analytics generated in the third-party service to pick the variation that performed the best and click "Next".
1. Stop the experiment in the third-party service.
1. Click "Complete" to overwrite the default version of the page and publish the winning variation to all users of the website.

## Use Publish Groups to publish experiment variations 
Experiment variations created within Dynamics 365 Commerce can be published as a unit 

Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/publish-groups) to learn more about publish groups.


## Experiment status within Dynamics 365 Commerce
An experiment in Dynamics 365 Commerce can be in one of the following status:
1. Not Started - The experiment isn't connected to a page or fragment yet.
1. Draft - The experiment is connected to a page or fragment.
1. Published - The experiment is ready to go live once it is started in the third-party service.
1. Unpublished - An experiment that is live isn't visible to users anymore, even if it is running in the third-party service.
1. Completed - The experiment has run its course and the right variation has been promoted to be shown to all users.
