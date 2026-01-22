---
title: Create or update methodologies
description: Lifecycle Services provides methodologies that you can use to ensure a more repeatable and predictable implementation project experience.
author: angelmarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ac723685-f87c-4854-9bb7-b92ccf1094eb
---

# Create or update methodologies

[!include [banner](../includes/banner.md)]

Lifecycle Services for Microsoft Dynamics provides methodologies that you can use to ensure a more repeatable and predictable implementation project experience. You can use one of the provided methodologies or create your own. By using a methodology, you can easily track and report on your progress.

A methodology consists of phases, tasks, and milestones. Each phase can have any number of tasks, some of which are mandatory. When you complete all of the tasks in a phase, you can mark the phase as complete. You can also create a milestone for when you anticipate a phase to be completed. A Lifecycle Services project includes the following methodologies:

- Implementation
- Sure Step
- Learn development
- Migrate and create solutions
- Consume solutions

> [!NOTE]
> A known limitation prevents new changes that are published to the Microsoft Methodology from being pushed to existing projects. Only new projects get these changes.

## Add or update methodologies

A partner or a project administrator can create new methodologies or make changes to an existing methodology for their organization or within the scope of a specific project. Make these additions and changes at the project level or at the organization level. Use the following procedures to create and save a new methodology, update existing methodologies, and when appropriate, promote a new methodology or methodology changes to the organization level.

### Create a new methodology

1. On the Lifecycle Services dashboard, on the right side of the screen, select **Manage methodologies**.
1. On **Manage methodologies**, select the plus sign (+).
1. In **New methodology**, enter a name and description for the new methodology. Select **Confirm**.
1. **Optional:** After you confirm the methodology, promote it to the organization level by selecting the methodology in the grid, and then selecting **Promote**. :::image type="content" source="./media/promotemethodology.jpg" alt-text="Screenshot of the promote methodology option."::: 

    > [!NOTE]
    > You must be an admin in your organization to promote a methodology to the organization level.

### Change or update a methodology

You can make changes to a methodology in two ways. You can append an existing methodology, or you can make changes to a methodology in the scope of a project. From the Lifecycle Services project dashboard, select the methodology that you want to update, and then select **Edit methodology** or **Append methodology**. :::image type="content" source="./media/projectlevelmethodology.jpg" alt-text="Screenshot of the project level methodology options."::: If you select to edit the methodology, you can make the following changes:

- Add a new phase.
- Add a new task.
- Edit a phase or task. (You can edit some phases and tasks. However, Microsoft enforces other phases and tasks, so you can't edit them.)
- Copy a phase or task.
- Reorder phases and tasks.
- Delete a phase or task.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
