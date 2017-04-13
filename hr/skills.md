---
# required metadata

title: Align workforce skills with business needs
description: You can track the skills that workers, applicants, or contact persons have, or should have, to fulfill their roles effectively. You can also specify the skills that are required for a specific job.
author: rschloma
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmSkill, HcmSkillGapProfile, HcmSkillMapping, HcmSkillType
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3361
ms.assetid: c2ce94c0-933d-4edb-822c-7f0e7b49e4ee
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Align workforce skills with business needs

You can track the skills that workers, applicants, or contact persons have, or should have, to fulfill their roles effectively. You can also specify the skills that are required for a specific job.

Examples of skills you can track include the following:
-   Supervisory – Ability to supervise the work of others.
-   Leadership – Ability to lead employees and business domains.
-   Planning – Ability to look ahead, to form visions, and to see them through.
-   HTML – Ability to write HTML code.

Before you can assign a skill to a person or a job, create a skill-mapping search, or create a skill profile, you must enter information about the skills on the **Skills** page. For each skill, you can select a skill type and a rating model.

## Rating models
Rating models help evaluate a person's actual level of skill, the level they should work to achieve, or the level of skill that is required for a job. You can enter up to 10 levels for a rating model.  Each level in a rating model is assigned a factor.  The factor value will be used to normalize the scores of skills that use different rating models.  The factor must be a number between 0-9 and each level must have a unique factor.  Levels with higher factor values carry more weight in a rating model.

## Specify job skills
When you enter information about a job, you can specify the skills that a person should have to perform the work required for the job.  In addition you can specify the desired level for each skill as well the level of importance of the skill. Different jobs can require different levels of importance for the same skill.

## Enter skills for workers, applicants, or contacts
You can enter target skills or actual skills for workers, applicants, or contacts. A target skill is a skill that a person plans to achieve. An actual skill is a skill that a person currently has.

## Skill mapping and Skill mapping profiles
You can create a skill-mapping search to find a worker, applicant, or contact person who is qualified to perform a specific type of task. Skill-mapping searches look across skills, education, certificates, positions of trust and project experience and return a results that match the criteria entered.  For example, it might be useful to know which workers in your organization earned their CPA.

Skill-mapping profiles allow you to find current employees or candidates with qualifications that directly correspond to business needs.  For example, you could create a skill-mapping profile for an open position in your organization. By creating a profile for a particular job and copying the skills, education and certificates from that job to the profile, you can quickly search workers, applicants and contact persons who match one or more of the criteria entered on the profile and view a list of the candidates whose skills most closely match the skills required for the job.

>**Note**
>Only workers, applicants, and contact persons who are selected to be included in skill mapping searches can be displayed in a skill-mapping results list, or included in a skill profile. To include a worker, applicant, or contact person in skill mapping searches, set the **Include in skill mapping** selection to Yes in the following pages:

> + Worker
> + Employee
> + Applicant
> + Contacts

## Skill gap analysis and skill profile analysis
You can create a skill profile analysis to view a list of the competencies of a worker, applicant, or contact person as of a specific date. You can create a skill gap analysis to compare a person’s skills and the skills that are required for a specific job.  



See also
--------

[Human resources](index.md)

