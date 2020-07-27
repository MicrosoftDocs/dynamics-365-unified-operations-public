---
# required metadata

title: Stay compliant wtih user licensing requirements
description: This topic provides information about to to stay compliant with the user licensing requirements for Dynamics 365 Finance and Operations apps.
author: peakerbl 
manager: AnnBe
ms.date: 07/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30 
ms.dyn365.ops.version: AX 7.0
---

# Stay compliant with user licensing requirements

[!include [banner](../includes/banner.md)]

This topic provides an overview for how customers can stay compliant with the user licensing requirements for Dynamics 365 for the Finance and Operation purpose-built applications. e.g. Finance, Supply Chain Management and Commerce.

The license requirements for a user are determined by the assigned security role(s) for the user. Security roles are built based on a hierarchy of sub-roles, duties, privileges and directly referenced securable objects. Please refer to the [Role-based security](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/role-based-security) content for more details.

Licensing requirements for users are determined on the organization/tenant level. This topic is focused on the requirements for a single environment. For multi-environment it will be required to analyze the requirements across environments.

Each securable object is assigned a licensing requirement, e.g. None, Team members, Activity or Operations. Operations indicates that a full user license will be required. Some privileges are identified as unique for a specific full user license and will require that the user has been assigned either a base or attach license for that specific license. This is covered more in details below in the User license estimator report section.

There are several Dynamics 365 for Finance and Operations tools that can be used to assure that the actual licensing is compliant with the expected licensing requirements:

## Users - Roles for selected user fact box (System administration > Users)

While assigning roles to users it is possible to view license requirements for each role in the **Roles for selected user** fact box.

![](RackMultipart20200727-4-1hd145q_html_b6c4073e3333aec2.png)

The maximum license requirement determines the actual licensing requirement for a user. If any license requirement is identified as Operations, it will be necessary to use the User License estimator report to determine the full user licensing requirements.

## View permissions form (System administration > Security > Configure security)

While configuring security, it is possible to select any permission reference, e.g. a role or duty, and click **View permissions** to see all currently included permissions and their licensing requirements:

![](RackMultipart20200727-4-1hd145q_html_dd990d8bf2d69a10.png)

The required license level is displayed in the header of the form.

## User license counts report (System administration > Inquiries > License)

The User license count report is used to get a count of required licenses per license type, e.g. Team members, Activity and Operations:

![](RackMultipart20200727-4-1hd145q_html_69fc72f2ee09400c.png)

It can also provide details for each user and the licensing requirements for each assigned role. The users are listed under the maximum license type. If the license requirement is identified as Operations, it will be required to use the [User License estimator report](#UserLicenseEstimatorReport) to determine the specific full user licensing requirements.

The history version of the report will provide total counts per date, without any details.

Note: These reports are dependent on the **Named user license count reports processing** batch job. To verify when the batch was last run, see the **Batch job history** form.

## User license estimator report (System administration > Inquiries > License reports)

The User license estimator report is used to get a count of specific licensing requirements for a user that has been identified as requiring an Operations license type in the above tools. The report only includes these users. Users who have not been assigned a privilege requiring a specific full user license, will be shown without any of the specific full user licenses marked, and will be compliant with any full user license assigned. An example is a user that has been assigned the Database management administrator role and no other roles requiring an Operations license type:

![](RackMultipart20200727-4-1hd145q_html_bcec2c5d638a821e.png)

Based on the licensing guide this user is compliant with any full user license:

Admin rights apply across Finance, Supply Chain Management, and Commerce applications. For example, if you have a Finance license, you have the admin rights for Finance, as well as Supply Chain Management, and Commerce applications.

There are several roles, provided by Microsoft and custom, where this may be true, based on the included privileges. In the report these users will appear without any specific license indicated. For example:

![](RackMultipart20200727-4-1hd145q_html_f0d2ccc736124f30.png)

On the other hand, for a user who has been assigned privileges that require a specific full user license, that license will be indicated:

![](RackMultipart20200727-4-1hd145q_html_cc5aa18f1453d756.png)

In the above example the user must have a base license for Dynamics 365 Supply Chain Management.

For a user who has been assigned privileges that together require more than one specific full user license, those licenses will be indicated accordingly:

![](RackMultipart20200727-4-1hd145q_html_bb5a2ccb2df2c442.png)

In such cases, the user must have a base license for one of the licenses, as well as an attach license for all other full user licenses required. In the example above, the user must have either a base license for Finance plus an attach license for Supply Chain Management, or a base license for Supply Chain Management plus an attach license for Finance.

The totals per specific full-user counts are not divided into base vs. attach.

Note: Total counts per specific full-user license and evaluation of custom privileges are included from platform version 10.1.13. The report is not able to separate between base and attach license requirements and will only list total full user licenses requirements.

## Additional resources:

For information for how to buy and license Dynamics 365, please refer to the [Microsoft Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544&amp;clcid=0x409).

For information for how to assign licenses to users in the Microsoft 365 admin center, please refer to [Assign licenses to users](https://docs.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide).

Additional user licenses are required when multiple implementation projects exists for the same tenant, for details please refer to [Multiple LCS projects and production environments on one Azure AD tenant](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/implement-multiple-projects-aad-tenant#licensing-requirements)
