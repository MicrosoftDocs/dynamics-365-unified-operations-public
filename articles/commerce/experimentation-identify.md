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

# Identify
Identify is the first stage in the experimentation journey where you decide the what and how for your experiment. Here are some things to consider:

## Create a hypothesis and metrics
Define the assumption or theory you want to validate with your experiment and the success metrics that you expect it to impact.

## Decide what you want to experiment on
Define the scope of the experiment - full or partial. Think **partial** if you want to target a specific portion of a page and do not want to affect content that is not part of the experiment. Think **full** if you want to target an entire page or fragment. In this case, a new instance copy of the entire page or fragment is created i.e. content changes will not be synchronized across experimentation instances.

## Decide how you want to publish your experiment
Think about whether you want to schedule your experiment to be published in a publish group or directly publish to your live site. This will help you determine where you want to create your experiment.
