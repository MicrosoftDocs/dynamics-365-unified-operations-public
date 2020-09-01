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

# Connect and edit
Once the experiment is setup in the third-party service, the next step is to connect it to an entity in Commerce and edit its variations. To do this:
1. Go to the **Experiments** tab in site builder and click **Connect** to open the *Connect experiment* wizard. This wizard can also be accessed from within a page or fragment editor when in the edit mode, by clicking on **Connect experiment** in the command bar.
    > [!NOTE]
    > One page can only be connected to one experiment at a time. To connect a page to a different experiment, you will need to first delete the existing experiment.
1. As a first step in the wizard, choose a page or fragment to be experimented upon.
1. In the next step, set the experimentation scope to **entire** if experimentating on the full entity and to **partial** if experimenting on a small portion of the entity.
    > [!NOTE]
    > If you want to experiment on entire pages and fragments, remember to enable the "Experiment on pages or fragments" feature flag first.
1. As the final step, click on **Generate variations and exit wizard** to auto-generate the variations as copies of the existing page or fragment. 
1. In the editor view, use the variations drop-down menu below the command bar to edit each variation based on your original hypothesis. You can also optionally establish a **control** or base variation to compare to by leaving it unchanged.
