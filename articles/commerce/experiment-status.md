---
# required metadata

title: Review the status of an experiment
description: This topic explains what status an experiment has in the experimentation lifecycle in Dynamics 365 Commerce . 
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

# Review the status of an experiment

To learn where an experiment is in the lifecycle, go to the Experiments page in site builder. A list of experiments is diplayed with the status of each experiment in both Commerce and the third-party service.
The **Experiments** tab in site builder shows the following statuses in the **Commerce status** field to help you quickly see what state your experiment is in:
1. Draft - The experiment is connected to a page or fragment in Commerce and is being edited.
1. Published - The experiment is ready to go live, once it is started in the third-party service.
1. Unpublished - An experiment that is live isn't visible to users anymore, even if it is running in the third-party service.
1. Completed - The experiment has run its course and the right variation has been promoted to be shown to all users.

Similarly you can also use the **third-party status** field to understand the state of your experiment in the third-party service:
1. Draft - The experiment is setup in the third-party service but hasn't started yet.
1. Running - The experiment has started and is collecting data.
1. Paused - The experiment is paused and not collecting data. You will need to resume it so it starts collecting data again.
1. Archived - The experiment has run its course and has been cataloged for future reference.

Below is an image that shows both sets of statuses and how they relate to each other:

[ ![](./media/experimentation_statuses.svg) ](./media/experimentation_statuses.svg#lightbox)
