---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 18, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 18, 2020.
author: andreabichsel
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2020-02-18
ms.dyn365.ops.version: Human Resources

---
# What's new or changed in Dynamics 365 Human Resources (February 18, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2903. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Platform update 32 

Platform update 32 is now available. For more information, see [What's new or changed in Platform update 32 for Finance and Operations (February 2020)](../fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32.md).

## Search values are remembered when changing view options in streamlined employee form (383833)

The new **Worker** form now remembers  search values when you change the view options and apply changes.

## Compensation management summary tiles in preview feature redirect to wrong form (401861)

Fixed and variable compensation management tiles now display the correct records in the new **Worker** form. Applies only to the streamlined employee form preview feature. You can enable this preview feature in **Feature management**. For more information, see [Manage features](hr-admin-manage-features.md).

## Empty Status field for some leave request records in Dataverse (414915)

This change corrects an issue in Dataverse when the **Status** field in a leave request is set to **Review**. Dataverse now reflects the status.

## Skill gap analysis only possible for assigned job (411390)

You can now do a skill gap analysis on any job defined in Human Resources.

## System currency doesn't sync from Dataverse to Human Resources in new environments (418011)

The system currency in Dataverse can now sync to Human Resources.

## In preview

- [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features)

- [Benefits management preview features](hr-benefits-management-overview.md)

## Coming soon

### Updated Dataverse solution

A new Dataverse solution will be available soon with the following changes:

| Description | Change |
| ----------------------------------------- | --- |
| **Job/Position** entity changes | **Compensation region** added</br>**Financial dimensions** added |
| **Worker** entity changes | **Name sequence** added</br>**Works from home** added</br>**Language** added</br>**Seniority date** added</br>**Anniversary date** added</br>**Original hire date** added |
| **Employment** entity changes | **Financial dimensions** added</br>**Termination reason** added</br>**Termination date** renamed from **Transition date**</br>**Probation date** added |
| **Worker address** entity changes | **Street address** added</br>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation |
| New variable compensation setup entities | **Compensation variable plan type**</br>**Compensation variable plan**</br>**Vesting rules**</br>**Compensation variable plan level** |
| New **Worker calendar employment** entity | **Work calendar entity** added |
| New **Payroll position detail** entity | **Payroll position detail** added |
| New **Title** entity | **Title** added. The new **Title** entity will be included in the sync process between Human Resources and Dataverse. It won't be initially referenced from **Job Position** or **Job** entities. |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]