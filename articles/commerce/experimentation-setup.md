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

# Setup your experiment
Once a hypothesis and metrics are defined, follow the required steps to create an experiment in the third-party service. These steps will vary from service to service, but the end result will be an experiment with a set of variations to be shown to experiment participants. If the connector is configured properly, the list of experiments and variations from here will surface in site builder within about 5 minutes.

Every experiment needs metrics to measure its impact. Follow the steps below to enable metrics computation in the third-party service using live telemetry events from Dynamics 365 Commerce:
1. Go to the **Pages** tab in site builder's left navigation pane and click on the desired page. 
1. Go to the **Event IDs to track** section in the right property pane of the page or module of interest.
1. Click on **View** to see the list of all event IDs associated and copy the one(s) you want to paste into the third-party service. If you need more than one event ID, view and copy them one by one. 
    - Click [here](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-component-events-diagnostics-troubleshooting#e-commerce-events) to view all available events and attributes, including tracking page views and revenue.
1. Use the event as described in the third-party service to track success metrics for the experiment.
