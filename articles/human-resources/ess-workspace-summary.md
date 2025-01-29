---
# required metadata

title: Employee self service leave summary
description: This article provides an overview of the Employee self service leave summary feature.
author: jcart
ms.date: 01/17/2025
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

# Employee self service leave summary
The **Employee self service leave summary** feature is enabled by default in Dynamics 365 Human Resources version 10.0.39. 

Use the **Employee self service leave summary** feature to get an AI-generated summary of employee time off. This feature is powered by Microsoft Azure OpenAI Service's large language model and is designed to reduce the time that you spend reviewing the different screens containing time off information and calculating time off that may be subject to forfeiture.
This feature has two purposes:

- Increase employees' awareness of their time-off situation, and help them make informed decisions about their time-off plans.
- Optimize employees' time-off use, and provide insight into the accumulation of unused time off that can create financial liabilities for the organization.

## Country/region and language requirements
For information about the languages that this Copilot feature was validated for, see [Explore Copilot features by geography and languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although the feature can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience.

### Version requirements

Employee self service leave summary requires the latest PQU on Dynamics 365 Finance and Operations versions 10.0.39 and 10.0.40. 

### Role requirements

To use this feature, the user must be assigned an employee role in Dynamics 365 Human Resources or Dynamics 365 Finance.

## Summary by Copilot

The **Summary by Copilot** field appears in the **My information** tab of the **Employee self service** workspace. The summary includes the current time off balances for leave types with a carry forward rule associated. It also includes the time off subject to forfeiture based on current time off balances and upcoming time off requests.  

##See also
[Employee self service leave summary FAQ](ess-transp-faq.md)
