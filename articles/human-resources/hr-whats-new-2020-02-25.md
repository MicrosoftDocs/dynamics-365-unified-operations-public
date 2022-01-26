---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (February 25, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for February 25, 2020.
author: andreabichsel
ms.date: 02/25/2020
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
ms.search.validFrom: 2020-02-25
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (February 25, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This article describes features that are either new or changed in Dynamics 365 Human Resources. Changes apply to build number 8.1.2927. The numbers in parentheses in some headings refer to LCS support numbers for reference.

## Enable Case Management navigation and data management framework (DMF) entity (414754)

This preview feature enables additional navigation to case management cases. You can enable this preview feature in the **Feature Management** workspace. These menu items appear in the **Compliance** workspace of Dynamics 365 Human Resources. With this change, Human Resources can access:

- All cases
- My cases
- My open cases
- My overdue cases
- Cases assigned to me through workflow

Along with these new views into cases, the **Case detail** DMF entity is also available.

## Enable Relationship definitions in global address bBook (414762)

Relationships are now enabled in the global address book. Prior to this week's release, the **Relationship** fact box displayed any system-defined relationships. Now you can define those relationships within the global address book page.

## A position can be removed when active compensation records exist for the position (414568)

With this change, a warning appears when you attempt to delete a position and a worker has an active compensation record for that same position. When this happens, you must update the employee fixed compensation record before removing the position.

## Performance review workflow occasionally adds sign-offs from people who are not part of the process (414171)

This change corrects an issue where additional sign-off participants are added to the performance review.

## Worker position assignment not created in Dataverse when selected on the New Worker dialog (413479)

This change corrects an issue when hiring a new worker and assigning the new hire to a position through the **New worker** dialog. Now the position assignment is reflected in Dataverse.

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

Over the next few weeks, these entity changes will be available in all environments. To manually install the latest Dataverse solution for Human Resources:

1.	Go to the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).

2.	Select **Environments**.

3.	Find the environment you want to upgrade. This should correspond to **Environment name** in the **Common Data Service information** section in the **About** form in Human Resources.

4.	Select the environment to view the environment details.

5.	In the action bar at the top, select **Manage Solutions**. A new browser window will open and navigate to **Dynamics 365 Administration Center** in the context of your environment.

6.	In the **Solution** list, select **Dynamics 365 Human Resources Anchor**.

7.	Select **Upgrade** to apply the latest solution.

## In preview

The following preview features became available on February 3, 2020:

- **Leave and absence preview features** - For more information, see [Leave and absence preview features](hr-leave-and-absence-overview.md?leave-and-absence-preview-features).

- **Benefits management preview feature** - For more information, including known issues, see [Benefits management overview](hr-benefits-management-overview.md).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]