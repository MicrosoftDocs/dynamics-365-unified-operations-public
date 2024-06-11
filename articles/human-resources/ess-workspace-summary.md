---
# required metadata

title: Employee self service workspace summary
description: This article provides an overview of the Employee self service workspace summary feature.
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
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Employee self service workspace summary

Use the **Employee self service workspace summary** feature to get an AI-generated summary of employee time off. This feature is powered by Microsoft Azure OpenAI Service's large language model. It's designed to reduce the time that you must spend viewing the workflow history to find the most important details. Therefore, you can quickly and efficiently approve documents.

This feature has two purposes:

- Increase employees' awareness of their time-off situation, and help them make informed decisions about their time-off plans.
- Optimize employees' time-off use, and prevent the accumulation of unused time off that can create financial liabilities for the organization.

## Prerequisites

### Version requirements

Approval workflow summary requires the latest hotfix for Dynamics 365 Finance version 10.0.38.

### Language requirements

Employee self service workspace summary is supported in the following user-preferred languages: English, Danish, Dutch, French, German, Italian, Japanese, Portuguese (Brazil), Spanish, Chinese (Simplified), Czech, Finnish, Greek, Korean, Norwegian (Bokmal), Polish, Russian, Swedish, Thai, and Turkish.

To use this feature, update your preferred language in Dynamics 365 Finance to one of the preceding languages.

### Role requirements

The user must be assigned an employee role.

## Enable Employee self summary workflow summary

1. In Dynamics 365 Finance, go to **Feature management**.
1. On the **All** tab, search for and select **ESS workspace summary**.
1. Select **Learn more** to learn more about the AI terms.
1. Select **Enable**.

## View summary text

The AI-generated content appears on the **Summary** FastTab. Azure OpenAI is used to generate the results, based on data in Dynamics 365 Finance and the provided prompts. The summary is based on workflow history and includes the following information:

- Submitter
- Approval list
- Workflow completion policy
- Due dates
- Comments
