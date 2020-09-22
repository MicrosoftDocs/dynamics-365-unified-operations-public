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

# Run and monitor your experiment

[ ![Experimentation user journey - Run & Monitor](./media/experimentation_run_monitor.svg) ](./media/experimentation_run_monitor.svg#lightbox)

Once the variations are connected and edited in Commerce, follow the steps below to run the experiment in the third-party service and track user interactions to compute success metrics:
1. Run the experiment in the third-party service so the right variation experiences can be shown to end-users. If the experiment is not running in the third-party service, the experiment variations will not be shown i.e. all end-users will continue to see the existing version of the page.
1. Let the experiment run for however long it takes to gather sufficient data for statistical analyses in the third-party service.
1. Monitor experiment related data and analytics in the third-party service.

## Adjust your experiment
If you need to make changes to variations in Commerce based on the results of your experiment:
1. Go to the **Experiments** tab in site builder and click on the desired experiment. 
1. Pick the variation(s) that needs updating from the variations drop down.
1. Make the required changes, preview and publish them.
1. Go to the third-party service to make any experiment setup related changes.
    > [!NOTE]
    > If the experiment is still active, making changes to the variations in Commerce or the third-party service may significantly impact the experiment results.
