---
# required metadata

title: Create departments and include them in the department hierarchy
description: A department is an operating unit that represents a category or functional area of an organization. A department is responsible for a specific area of the organization, such as sales, accounting, or human resources. 
author: twheeloc
ms.date: 06/05/2026
ms.topic: how-to
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

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

A department is an operating unit that represents a category or functional area of an organization. A department is responsible for a specific area of the organization, such as sales, accounting, or human resources. Use departments to report on functional areas. Departments might have profit and loss responsibility.

A department might include a group of cost centers. Assign positions to departments. To create a department, select **Human Resources** > **Departments** > **Department**. The following table describes the available fields.

| Field               | Description                |
|---------------------|-----------------------------------------------------------------------------------------------|
| **Name**                | Enter a name for the department.                                                                |
| **Department number**   | A default value might be generated automatically if you assign a number sequence code to the **Organization number** reference on the **Number sequences** page.            |
| **Search name**         | Enter a name or acronym that you can use to search for the department.                       |
| **Memo**                | Enter any additional information here.                                                          |
| **In hierarchy**        | A selected check box indicates that the department is included in the department hierarchy. For information about how to add a department to the department hierarchy, see the information later in this article. |
| **DUNS number**  | DUNS stands for Data Universal Number System. This is a nine-digit number that is issued by Dun & Bradstreet.   |
| **Manager**   | Enter the persona that manages the department.                                                                                  |
| **Addresses**           | Add the address information for the department. For example, add the mailing address for the building that the department is located in.                                  |
| **Contact information** | Add contact information for the department. For example, add a telephone number for the service desk in the department.            |

To add a department to the department hierarchy, follow these steps:

1. Select **Human Resources** > **Departments** > **Department hierarchy**.
1. Select **Edit**, and then select the organization that the department should be under.
1. Select **Insert**, and select **Department** in the list.
1. In the list of departments that appears, select the department to add to the hierarchy.
1. Save your changes. You receive a message that a draft version of the hierarchy is created.
1. When you're ready, select **Publish** in the hierarchy designer. You can enter an effective date that indicates when the hierarchy should be published. For example, to add a new department at the beginning of the next calendar year, set the effective date to January 1 of the new calendar year. The changes to the hierarchy take effect on that date.

## Steps for creating a department

For a step-by-step procedure to create a new department, see [Define new departments](./hr-personnel-define-departments.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
