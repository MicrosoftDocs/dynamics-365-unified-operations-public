---
# required metadata

title: Configure skills
description: You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job.
author: twheeloc
ms.date: 06/05/2026
ms.topic: how-to
# optional metadata

ms.search.form: HcmSkill, HcmSkillGapProfile, HcmSkillMapping, HcmSkillType, HcmEmployeeDevelopmentWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: c2ce94c0-933d-4edb-822c-7f0e7b49e4ee
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Configure skills

You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job.

Examples of skills you can track include:

- Supervisory – Ability to supervise the work of others.
- Leadership – Ability to lead employees and business domains.
- Planning – Ability to look ahead, to form vision statements, and to see them through.
- HTML – Ability to write HTML code.

If you didn't already set up skill types and rating models, add them before creating skills.

The following people can enter skills for a worker:

- Workers can enter skills for themselves in Employee self-service. These skills require manager approval.
- Managers can enter skills for their workers. You can create a workflow that autoapproves these skills.

## Create a skill type

Skill types are categories that individual skills fall under, such as Administration or Sales.

1. In the **Employee development** workspace, select **Links**.

1. Under **Competency setup**, select **Skill types**.

1. Select **New**.

1. Complete the following fields:

   - **Skill type**: Enter a name for the skill type.
   - **Description**: Enter a description for the skill type.

1. Select **Save**.

## Create a rating model

Rating models help you evaluate a person's actual level of skill, the level they should work to achieve, or the level of skill required for a job. Assign a factor to each level in a rating model.

1. In the **Employee development** workspace, select **Links**.

1. Under **Competency setup**, select **Rating models**.

1. Select **New**.

1. Complete the following fields:

   - **Rating**: Enter a name for the rating model, such as **Skills**.
   - **Description**: Enter a description for the rating model, such as **Skill ratings**.

1. In the **Levels** section, select **New**. For each level you want to add, complete the following fields:

   - **Level**: Enter a name for the level.
   - **Description**: Enter a description for the level.
   - **Factor**: Enter a factor value from 0-9. Factors help normalize the scores of skills that use different rating models. Each level must have a unique factor. Levels with higher factor values carry more weight in a rating model.

   Continue adding levels as necessary. You can enter up to 10 levels for each rating model.

1. Select **Save**.

## Create a skill

Before you can assign a skill, or create a skill-mapping search or skill profile, enter information about the skills on the **Skills** page. For each skill, select a skill type and a rating model.

1. In the **Employee development** workspace, select **Links**.

1. Under **Competency setup**, select **Skills**.

1. Select **New**.

1. Complete the following fields:

   - **Skill**: Enter a name for the skill.
   - **Description**: Enter a description for the skill.
   - **Rating**: Select the rating model you want to use for this skill.
   - **Skill type**: Select from the list of skill types.

1. Select **Save**.

## See also

[Enter skills](hr-develop-enter-skills.md)<br>
[Map skills](hr-develop-map-skills.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
