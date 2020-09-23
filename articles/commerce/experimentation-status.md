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
There are many steps involved in setting up and running an experiment in Dynamics 365 Commerce. For information on the experimentation lifecycle, see [Experimentation in Dynamics 365 Commerce](experimentation-overview.md).

To learn where an experiment is in the lifecycle, go to the **Experiments** tab in site builder. A list of experiments is diplayed with the status of each experiment in both Commerce and the third-party service that is being used to enable the creation of experiments and variation assignments.

In the **Commerce status** column, the following values may be displayed. 
1. **Draft** - The experiment is connected to a page or fragment in Commerce and is being edited.
1. **Published** - The experiment is ready to go live in Commerce and hasn't been started in the third-party service.
1. **Unpublished** - The experiment is live but isn't visible to website users, even if it's running in the third-party service.
1. **Completed** - The experiment has run its course and a variation was promoted to live for all website users.

Similarly, in the **third-party status** column, the following values may be displayed to indicate what status the experiments are in the third-party service.
1. **Draft** - The experiment is set up in the third-party service but hasn't been started.
1. **Running** - The experiment was started in the third-party service and is collecting data.
1. **Paused** - The experiment is paused and not collecting data. You must resume the experiment for it to collect data again.
1. **Archived** - The experiment has run its course and has been cataloged in the third-party service for future reference.

The image below shows both sets of statuses and how they relate to each other.

[ ![Experimentation statuses](./media/experimentation_statuses.svg) ](./media/experimentation_statuses.svg#lightbox)
