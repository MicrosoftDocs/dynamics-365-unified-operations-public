---
# required metadata

title: Create a hiring process template in Attract
description: This topic provides information about how to create a hiring process template in Attract.
author: andreabichsel
manager: AnnBe
ms.date: 10/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: AX 8.1

---

# Create a hiring process template in Attract

[!include [banner](includes/banner.md)]

A *hiring process template* contains all the activities that should be included as part of the hiring process for a job. This topic describes the elements of a process template in Microsoft Dynamics 365 Talent: Attract. It also explains how to create a template.

> [!NOTE]
> Template creation is part of the Comprehensive Hiring Add-on for Attract.

## Template management

Organizations can decide whether team members or only admins can create process templates in Attract. To configure template management, go to **Admin Center** \> **Template management**. To let team members create their own templates, turn on template management. If you don't turn on template management, only admins can create templates.

## Default template

Only admins can set the default template. The default template is used if a template isn't selected when a job is created. To set the default template, go to **Admin Center** \> **Template management**. On the card for the template that should be the default template, select the ellipsis button (**...**), and then select **Set as default**.

## Create a process template

Admins, recruiters, and hiring managers can create process templates. A process template consists of *stages* and *activities*. Stages group together one or more activities. By default, every process template has Prospect, Application, and Offer activities. The stages that contain these activities can be renamed. You can add more stages by selecting **+ New Stage**. You can add activities to a stage either by dragging them to the appropriate stage or by double-clicking them in the activity list.

> [!NOTE]
> Stage names are visible to candidates on the **Application status** page. You should consider this fact when you choose names for stages.

To learn more about activities, see [Activities in hiring processes](./activities-attract.md).

Follow these steps to create a hiring process template.

1. Go to **Templates**.
2. Select **New**.
3. In the **Template name** field, enter a name for the template, and then select **Create**.
4. In the **Choose the approval process** list, select **Default** to require approval for a job.
5. Select to enable or disable prospects.
6. Optional: Add or remove stages.

    - To add a stage, select **+ New Stage**.
    - To remove a stage, hover the pointer over the stage, and then select the trash can button that appears.

        > [!NOTE]
        > Prospect, Application, and Offer stages can't be removed, but they can be renamed.

7. Optional: Add or remove activities.

    - To add an activity, drag it from the activity list on the right to the appropriate stage. Alternatively, double-click the activity, and then select the stage to add it to.
    - To remove an activity, expand it, and then select the trash can button on the activity header.

8. Select **Save**.
