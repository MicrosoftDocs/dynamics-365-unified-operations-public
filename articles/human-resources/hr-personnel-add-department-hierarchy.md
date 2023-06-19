---
# required metadata

title: Create departments and include them in the department hierarchy
description: A department is an operating unit that represents a category or functional area of an organization. A department is responsible for a specific area of the organization, such as sales, accounting, or human resources. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HierarchyDesigner, OMOperatingUnit, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 5dbc62fc-0184-4c0e-9856-e735fc68799e
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Create departments and include them in the department hierarchy


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

A department is an operating unit that represents a category or functional area of an organization. A department is responsible for a specific area of the organization, such as sales, accounting, or human resources. You can use departments to report on functional areas. Departments might have profit and loss responsibility.

A department might include a group of cost centers. Positions can be assigned to departments. To create a department, click **Human Resources** &gt; **Departments** &gt; **Department**. The following table describes the fields that are available.

| Field               | Description                                                                                                                                                                                                       |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Name**                | Enter a name for the department.                                                                                                                                                                                  |
| **Department number**   | A default value might be generated automatically if a number sequence code is assigned to the **Organization number** reference on the **Number sequences** page.                                                 |
| **Search name**         | Enter a name or acronym that can be used to search for the department.                                                                                                                                            |
| **Memo**                | Enter any additional information here.                                                                                                                                                                            |
| **In hierarchy**        | A selected check box indicates that the department is included in the department hierarchy. For information about how to add a department to the department hierarchy, see the information later in this article. |
| **DUNS number**         | DUNS stands for Data Universal Number System. This is a nine-digit number that is issued by Dun & Bradstreet.                                                                                                     |
| **Manager**             | Enter the persona that manages the department.                                                                                                                                                                    |
| **Addresses**           | Add the address information for the department. For example, add the mailing address for the building that the department is located in.                                                                          |
| **Contact information** | Add contact information for the department. For example, add a telephone number for the service desk in the department.                                                                                           |

To add a department to the department hierarchy, follow these steps.

1.  Click **Human Resources** &gt; **Departments** &gt; **Department hierarchy**.
2.  Click **Edit**, and then select the organization that the department should be under.
3.  Click **Insert**, and select **Department** in the list.
4.  In the list of departments that appears, select the department to add to the hierarchy.
5.  Save your changes. You receive a message that a draft version of the hierarchy has been created.
6.  When you're ready, click **Publish** in the hierarchy designer. You can enter an effective date that indicates when the hierarchy should be published. For example, to add a new department at the beginning of the next calendar year, set the effective date to January 1 of the new calendar year. The changes to the hierarchy will take effect on that date.

## Steps for creating a department
Refer to the [Define new departments](./hr-personnel-define-departments.md) article for the step-by-step procedure for creating a new department. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
