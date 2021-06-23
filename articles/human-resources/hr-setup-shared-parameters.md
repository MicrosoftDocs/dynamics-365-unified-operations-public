---
# required metadata

title: Configure shared parameters
description: You must set up shared parameters for records that are shared across companies, such as Position records. This article explains how to set up Human resources parameters across legal entities.
author: andreabichsel
ms.date: 06/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmSharedParameters, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 51891
ms.assetid: c7d8f58c-d78a-4035-abbf-2b0ce16109fe
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure shared parameters

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You must set up shared parameters for records that are shared across companies, such as Position records. This article explains how to set up Human resources parameters across legal entities.

Some types of records, such as Position records, are shared across companies. For these records, you must set up shared parameters. For example, you use the **Human resources shared parameters** page to set up Human resources parameters across legal entities. 

On the **Human resources shared parameters** page, parameters are grouped into areas, based on their functionality. 

### Settings
On the **Identification** tab, you must select the identification types that represent the identification numbers that are listed on the page. You must set up identification types before you can enter identification information for workers. Information about the Social Security number, national ID number, alien ID number, and personal ID code is maintained on the **Identification type** page. To define a new identification type or review the list of existing types, click **Personnel management** &gt; **Links tab** &gt; **Setup** &gt; **Identification types**. You can enter a simple code and description. 

On the **Number sequences** tab, you can select the number sequences that are used for the following records: Personnel number, Position, User request ID, I-9 document, Applicant, Discussion, Benefit ID, and Personnel action (if this record type is enabled). To maintain number sequence references and codes, use the **Number sequences** list page. To find this page, use the page search feature. 

On the **Positions** tab, indicate whether new positions are available for assignment by default:

- **Always** – You can assign workers to new positions when positions are created. When positions are created, the **Available for assignment** date and time on the **General** tab of the **Position** page are automatically set to the creation date and time.
- **Never** – You can't assign workers to new positions when positions are created. If you select this option, you must open the **Position** page for each new position as it becomes available, and then, on the **General** tab, enter the **Available for assignment** date to enable worker assignment.

On the **Advanced access** tab, you can restrict access to certain information or links.

- **Restrict access to worker information** – Turning on this option will restrict users' ability to view employee information for only those legal entities they have access to and employees with employments in those legal entities.
  
  Once this feature is turned on you will need to set the appropriate permissions for each user that needs to have their view restricted. To do this, navigate to the **Users** page.  Select a user and select a role for the user.  The **Assign organizations** option will become enabled.  Select **Assign organizations**.  Within the new page, select **Grant access to specific organizations individually**.  Select the organizations that the user should have access to.  You will need to do this for every role that the user has, including the system user role.  
  
  > [!Note]
  > The companies that the user has access to must match across all of their roles.
     
- **Enable cross-company compensation view** –  Compensation for employees is assigned per legal entity of employment.  Sometimes an employee can be employed in multiple legal entities at the same time.  When this feature is on, compensation for each legal entity will display in ESS/MSS without having to change legal entities. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
