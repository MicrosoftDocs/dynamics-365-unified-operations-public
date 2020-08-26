---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 12, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 12, 2020.
author: Darinkramer
manager: AnnBe
ms.date: 02/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-02-07
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (February 12, 2020)

This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2867. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

## Existing entities CompFixedEmpls and HcmPersonImage should be accessible from OData (414178)

With this week's release, the **CompFixedEmpls** and **HcmPersonImage** entities are now public and available via ODAta.

## Delete employment from Common Data Service doesn't work when employment details aren't active (403193)

This change now allows for deleting employment via Common Data Service when no active employment details exist.

## Course registration workflow changes status to complete and errors after second approval (409749)

Course registration workflow has been updated to allow for multiple approvers.

## In preview

The following preview features are available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## Coming soon

### Platform update 32 

Platform update 32 will be available soon. [Find out more information about Platform update 32 here](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-32).

### Updated Common Data Service Solution

A new Common Data Service solution will be available soon with the following changes:

| Description | Change |
| ----------------------------------------- | --- |
| **Job/Position** entity changes | **Compensation region** added</br>**Financial dimensions** added |
| **Worker** entity changes | **Name sequence** added</br>**Works from home** added</br>**Language** added</br>**Seniority date** added</br>**Anniversary date** added</br>**Original hire date** added |
| **Employment** entity changes | **Financial dimensions** added</br>**Termination reason** added</br>**Termination date** renamed from **Transition date**</br>**Probation date** added |
| **Worker address** entity changes | **Street address** added</br>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation |
| New variable compensation setup entities | **Compensation variable plan type**</br>**Compensation variable plan**</br>**Vesting rules**</br>**Compensation variable plan level** |
| New **Worker calendar employment** entity | **Work calendar entity** added |
| New **Payroll position detail** entity | **Payroll position detail** added |
| New **Title** entity | **Title** added. The new **Title** entity will be included in the sync process between Human Resources and Common Data Service. It won't be initially referenced from **Job Position** or **Job** entities. |

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)