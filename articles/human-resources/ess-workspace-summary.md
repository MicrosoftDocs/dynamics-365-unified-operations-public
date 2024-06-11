---
# required metadata

title: Employee self service workspace summary
description: This article provides an overview of the Employee self service workspace summary.
author: jcart
ms.date: 06/11/2024
ms.topic: overview
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.collection: bap-ai-copilot
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Employee self service workspace summary

Use the Employee self service workspace summary feature to get an AI-generated summary of the employee time off. This feature is powered by Microsoft Azure OpenAI’s large language model and is designed to reduce
the time that you spend viewing the workflow history for the most important details so you can approve documents quickly and efficiently.

This feature has two purposes:

- Increase employees’ awareness of their time off situation and help them make informed decisions about their time off plans.
- Optimize the employee's time off utilization and prevent the accumulation of unused time off that can create financial liabilities for the organization.

## Prerequisites

Version requirements

Approval workflow summary requires the latest hotfix on Dynamics 365 Finance version 10.0.38.

Language requirements

Employee self service summary is supported in the following user preferred languages: English, Danish, Dutch, French, German, Italian, Japanese, Portugues (Brazil), Spanish, Chinese (Simplified), Czech, Finnish, 
Greek, Korean, Norwegian (Bokmal), Polish, Russion, Swedish, Thai and Turkish.

Update your preferred language in Dynamics 365 Finance to one of the above languages if you want to use this feature.

Role requirements

The user must be assigned as an employee role.

Enable Approval workflow summary

1. In Dynamics 365 Finance open the Feature management workspace.
2. On the All tab, search for and select ESS workspace summary.
3. Select Learn more to learn more about the AI terms.
4. Select Enable.

**View summary text**

The AI-generated content appears on the Summary fastTab. Azure OpenAI is used to generate the results, based on data in Dynamics 365 Finance and the provided prompts. The summary is based on workflow history 
including the submitter, approval list, workflow completion policy, due dates, and comments of the same workflow document type.
