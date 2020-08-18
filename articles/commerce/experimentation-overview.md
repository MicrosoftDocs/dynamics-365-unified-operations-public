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

Use experimentation to measure the impact of new changes or ideas and avoid making costly updates to your website before understanding their impact. Dynamics 365 Commerce supports A/B testing on pages, modules and fragments. Multi-variate and multi-page testing are currently only supported using fragments and can be achieved as long as they are supported in the third-party service.

## Experimentation journey
The experimentation journey typically begins with creating a hypothesis or the theory that needs to be tested. Dynamics 365 Commerce supports the creation, editing, and management of page and content treatments also known as **variations** within site builder. Integrations with third-party services enable the creation of experiments and treatment assignments. Live event streams from Dynamics 365 Commerce enable the analytics defining experiment results in the third-party service to help support or refute the hypothesis.
![Experimentation user journey](./media/experimentation-user-journey.png "Experimentation user journey")

## Planning considerations
Here are some things to consider before you start:

### Create a hypothesis and measures
Define the assumption on theory you want to validate with the experiment and the corresponding success metrics that you expect the experiment to affect.

### Decide what you want to experiment on
Define the scope of the experiment - full or partial. Think **partial** if you want to target a specific portion of a page and don't want to affect content that isn't part of the experiment. Think **full** if you want to target an entire page or fragment. In this case, a full instance copy of the entire page or fragment is created and content changes across experimentation instances will not be synchronized.

### Decide how you want to publish your experiment
If you want to schedule your experiment to be published in a [publish group](#publish-experiment-variations-with-publish-groups) or directly [publish to your live site](#create-experiment-variations).

## Prerequisites
1. Get the right version of Dynamics 365 Commerce - Upgrade your store starter kit,  online channel extensibility SDK and Commerce scale unit to version 10.0.13.
1. Setup an experimentation connector - An experimentation connector allows Dynamics 365 Commerce to connect with third-party services to retrieve the list of experiments and determine when to show an experiment to each user. You can either use the sample test connector <available where??> or setup a third-party connector purchased from [AppSource](https://appsource.microsoft.com), following instructions [here](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/connectors).
1. Turn on the experimentation feature flags in Site Settings -> Features.
    - Set the **Experimentation** flag to on to enable creating experiment variations of modules within a page, without affecting or copying other content that is not part of the experiment. This ensures that ongoing content updates outside the experiment stay in sync during the experiment lifecycle. Disabling this will stop all experiments from being shown to users, and remove all editing functions within site builder.
    - Set the **Experimentation on pages or fragments** flag to on to enable experiments to be run on a page or fragment. This mode creates a full instance copy of the entire page or fragment for all modules within it.  Use this mode when you want to test comprehensive content changes, or where synchronizing ongoing content changes across instances is not a concern. Disabling it will prevent creation and editing of new experiments on pages and fragments.

<Tenant level flags???>

## Configure an experiment
Once the third-party connector setup is complete, follow the required steps to create an experiment in the third-party service. These steps will vary from service to service, but the end result will be one or more experiments with a set of variations to be shown to experiment participants. If the connector is configured properly, the list of experiments and variations from here will surface in site builder within about 5 minutes.

Every experiment needs metrics to measure its impact. Follow the steps below to enable metrics computation in the third-party service using live telemetry events from Dynamics 365 Commerce:
1. Go to the **Pages** tab in site builder's left navigation pane and click on the desired page. 
1. Click on **Events** in the right property pane of the page or module of interest.
1. View the list of events associated and copy the required one to the clipboard.
    - Click [here](https://docs.microsoft.com) to view all available events and attributes. <add link to Aamir's doc> 
1. <<Tracking page views and revenue??>>
1. Use the event as necessary in the third-party service to track success metrics for the experiment.

## Create experiment variations
The next step is to associate the experiment with the corresponding experiences in Dynamics 365 Commerce. To do this:
1. Go to the **Experiments** tab in site builder to view the list of experiments from the connector configured above. 
1. Click **Connect** to open the *Connect experiment* wizard. This wizard can also be accessed from within a page or fragment editor when in the edit mode, by clicking on **Connect experiment** in the command bar.
    > [!NOTE]
    > One page can only be connected to one experiment at a time. To connect a page to a different experiment, you will need to first delete the existing experiment.
1. Go through the wizard to choose an entity to be experimented upon and auto-generate the variations as a copy of what already exists. 
    > [!NOTE]
    > Remember to enable the "Experimentation on pages or fragments" feature flag to allow experimentation on pages and fragments. Set the experimentation scope to **entire** if experimentating on the full entity and to **partial** if experimenting on a small portion of the entity.
1. Make the required changes to the variations in the editor view. You can also optionally establish a **control** or base variation to compare to by not making any changes to it.
1. Preview the variations to ensure everything looks good. The editor context will determine which variation you are previewing. If you want to preview a different variation, select the variation in the editor drop down and click preview again.
1. Click on **Publish** to publish the variations. Note that this single operation will publish all variations that belong to the experiment.
    > [!NOTE]
    > If the page has an unpublished URL, make sure to publish the page URL first or it will not be visible to end-users. See more details on how to save, preview and publish [here](https://docs.microsoft.com/en-us/dynamics365/commerce/save-preview-publish-page).
    
## Publish experiment variations with Publish Groups
Experiment variations created within site builder can be scheduled for publishing within a publish group. You can either create pages or other items within publish groups or add existing ones to them. Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/publish-groups) to learn more about publish groups.

> [!NOTE]
> While adding a page to a publish group, any experiments running on it will be removed.

Some pointers to keep in mind:
1. You can connect to an experiment either through the **Experiments** tab or the **Pages** / **Fragments** tab as explained above. 
1. Once an experiment is connected in Live site, it will not be available within publish groups and the other way around.
1. When you click **Publish** to publish the content in a publish group, all content inside of it will be published, whether it has an experiment or not.

## Launch and monitor the experiment
Once the variations are setup in Dynamics 365 Commerce, follow the steps below to run the experiment in the third-party service and track user interactions to compute success metrics:
1. Start the experiment in the third-party service so the right variation experiences can be shown to end-users.
    > [!NOTE]
    > If the experiment is not running in the third-party service, the variation experiences will not be shown i.e. all end-users will see the same 'default' version of the page.
1. Let the experiment run for a few days/weeks depending on how long it takes to gather sufficient data for statistical analyses in the third-party service.
1. View experiment related data and analytics in the third-party service.

## Edit experiment variations
To edit variations in Dynamics 365 Commerce:
1. Go to the **Experiments** tab in site builder and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service, unless making a minor change with no significant impact to the experiment results.
1. Pick the variation that needs updating from the drop down just below the experiment name in the editor.
1. Make the required changes, preview and publish them.
1. Go to the third-party service to make changes to the names of the variations.

## Delete experiment variations
To delete variations in Dynamics 365 Commerce:
1. Go to the **Experiments** tab in site builder and click on the desired experiment. 
1. If the experiment is running and/or already published, stop the experiment in the third-party service and click on the **Unpublish** button in the top bar.
1. Pick the variation to be deleted from the drop down below the experiment name in the editor.
1. Click on **Delete** in the top bar to delete the variation and publish as necessary.

## Promote a winning experiment variation
After an experiment completes and has sufficient results to determine whether it was a success or not, the winning experience can be promoted to all users of the website as follows:
1. Go to the **Experiments** tab in site builder and click on the desired experiment.
1. Click **Complete** on the top bar once the experiment has run and gathered sufficient data.
1. Use the analytics generated in the third-party service to pick the variation that performed the best and click **Next**.
1. Stop the experiment in the third-party service.
1. Click **Complete** to overwrite the default version of the page and publish the winning variation to all users of the website.

## Check the status of an experiment
The **Experiments** tab in site builder shows the following states in the **Commerce status** field to help you quickly see what state your experiment is in:
1. Not Started - The experiment isn't connected to a page or fragment yet.
1. Draft - The experiment is connected to a page or fragment.
1. Published - The experiment is ready to go live once it is started in the third-party service.
1. Unpublished - An experiment that is live isn't visible to users anymore, even if it is running in the third-party service.
1. Completed - The experiment has run its course and the right variation has been promoted to be shown to all users.

Similarly you can also use the **third-party status** field to understand the state of your experiment in the third-party service. 
