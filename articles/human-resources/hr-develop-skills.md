---
# required metadata

title: Configure skills
description: You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job.
author: twheeloc
ms.date: 03/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmSkill, HcmSkillGapProfile, HcmSkillMapping, HcmSkillType, HcmEmployeeDevelopmentWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 3361
ms.assetid: c2ce94c0-933d-4edb-822c-7f0e7b49e4ee
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Configure skills

> [!IMPORTANT]
> The functionality noted in this article is currently available for Human Resources customers on the Finance infrastructure.  


You can track your worker's skills in Dynamics 365 Human Resources. You can also specify the skills that are required for a specific job.

Examples of skills you can track include:

- Supervisory – Ability to supervise the work of others.
- Leadership – Ability to lead employees and business domains.
- Planning – Ability to look ahead, to form vision statements, and to see them through.
- HTML – Ability to write HTML code.

If you haven't already set up skill types and rating models, you'll need to add some before creating skills.

The following people can enter skills for a worker:

- Workers can enter skills for themselves in Employee self-service. These skills require manager approval.
- Managers can enter skills for their workers. You can create a workflow that auto-approves these skills.

## Create a skill type

Skill types are categories that individual skills fall under, such as Administration or Sales.

1. In the **Employee development** workspace, select **Links**.

2. Under **Competency setup**, select **Skill types**.

3. Select **New**.

4. Complete the following fields:

   - **Skill type**: Enter a name for the skill type.
   - **Description**: Enter a description for the skill type.

5. Select **Save**.

## Create a rating model

Rating models help evaluate a person's actual level of skill, the level they should work to achieve, or the level of skill required for a job. Each level in a rating model is assigned a factor.

1. In the **Employee development** workspace, select **Links**.

2. Under **Competency setup**, select **Rating models**.

3. Select **New**.

4. Complete the following fields:

   - **Rating**: Enter a name for the rating model, such as **Skills**.
   - **Description**: Enter a description for the rating model, such as **Skill ratings**.

5. In the **Levels** section, select **New**. For each level you want to add, complete the following fields:

   - **Level**: Enter a name for the level.
   - **Description**: Enter a description for the level.
   - **Factor**: Enter a factor value from 0-9. Factors help normalize the scores of skills that use different rating models. Each level must have a unique factor. Levels with higher factor values carry more weight in a rating model.

   Continue adding levels as necessary. You can enter up to 10 levels for each rating model.

6. Select **Save**.

## Create a skill

Before you can assign a skill, or create a skill-mapping search or skill profile, you must enter information about the skills on the **Skills** page. For each skill, you can select a skill type and a rating model.

1. In the **Employee development** workspace, select **Links**.

2. Under **Competency setup**, select **Skills**.

3. Select **New**.

4. Complete the following fields:

   - **Skill**: Enter a name for the skill.
   - **Description**: Enter a description for the skill.
   - **Rating**: Select the rating model you want to use for this skill.
   - **Skill type**: Select from the list of skill types.

5. Select **Save**.

## See also

[Enter skills](hr-develop-enter-skills.md)<br>
[Map skills](hr-develop-map-skills.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
