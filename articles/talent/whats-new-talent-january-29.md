---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 31, 2019)
description: This topic describes features that are new or changed in Microsoft Dynamics 365 Talent for January 31, 2019.
author: andreabichsel
manager: tfehr
ms.date: 01/31/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-01-29
ms.dyn365.ops.version: Talent

---

# What's new or changed in Dynamics 365 Talent (January 31, 2019)

This topic describes features that are either new or changed in Dynamics 365 Talent.

**Build 8.1.2128**

## Core HR Changes

### Time off taken on leave people card doesn't consider leave plan dates

For leave plans that don’t run on a calendar year, the **Taken** card now displays time off taken in the plan-defined leave year. For example, if an organization’s leave year is June 1 through May 30 and an employee has taken three days off in December, the **Taken** card on January 15, will display three days. 

### Accrual amounts not matching tier date basis

New Leave and absence options in **Human resources** parameters enable customers to determine when employees’ months of service date are effective. The date is the end of the month for some organizations, but for others it could be the start of the next month. For example, one organization might award time off on December 31, while another might on January 1. This option will allow you to choose when the award should occur. 

### Worker hire actions are stuck in "Workflow complete" state

Changes have been made to correct an issue where a few workflows finished with a "Workflow complete" status. New workflows should now move to a "Completed" state when the workflow finishes. Any workflows in a workflow completed status will be transitioned to an error status to allow for updating or removal. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]