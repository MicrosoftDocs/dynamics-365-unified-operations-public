---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.25 
description: This article describes features that are either new or changed in the Dynamics 365 Human Resources version 10.0.25 preview release.
author: twheeloc
ms.date: 01/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2022-01-31 
ms.dyn365.ops.version: 10.0.25

---

# Preview of Dynamics 365 Human Resources 10.0.25 (April 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.25. This version has a build number of 10.0.1149 and is available as 
follows:

- **Preview of release**: January 2022
- **General availability of release (self-update)**: March 2022
- **General availability of release (auto-update)**: April 2022

The 10.0.25 release brings the first wave of capabilities in the infrastructure merge. During the infrastructure merge, Microsoft Dynamics 365 Human Resources will be merged
with the finance and operations infrastructure. However, it will continue to be licensed as an independent application, like Dynamics 365 Finance and Dynamics 365 Supply Chain 
Management. For more information about the infrastructure merge, see [Dynamics 365 Human Resources infrastructure merge FAQ](../../human-resources/hr-infrastructure-merge-faq.md).

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was 
initially published. If you want to use or turn off any of these features, you must do that in 
[feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

   | Feature name | Overview | Release status |
   |--------------|----------|----------------|
   | Years of service calculation | A setup option lets you select the date that is used for the **Years of service** calculation. For more information, see [Configure Human resources parameters](../../human-resources/hr-setup-parameters.md#general).| Generally available |
   | Workflow experience enhancements | New **Submit** and **Approve** buttons were added to the **Application** page. For more information, see [Workflow system overview](../../fin-ops-core/fin-ops/organization-administration/overview-workflow-system.md).| Generally available | 
   | Print performance reviews | You can print performance reviews in PDF format. For more information, see [Performance management](../../human-resources/hr-develop-performance-management-overview.md). | Generally available | 
   | Custom links in **Manager self service** | You can create custom links that appear in the **Related links** section of **Manager self service**. For more information, see [Create custom links in Manager self service](../../human-resources/hr-employee-manager-self-service-custom-links.md). | Generally available | 
   | Cross company compensation view | Users can view compensation plans in **Manager self service** across all legal entities, without having to switch companies. For more information, see [Employee and Manager self service overview](../../human-resources/hr-employee-manager-self-service-overview.md). | Generally available | 
   | Configure multiple compensation levels by job\*&dagger; | Jobs now support multiple compensation levels. For more information, see [Personnel jobs](../../human-resources/hr-personnel-jobs.md). | Preview | 
   | Task Management\* | You can create checklists and tasks for the onboarding, offboarding, and transition process. For more information, see [Task management](../../human-resources/hr-task-mgmt.md). | Preview | 
   | Streamlined employee entry | This feature provides an updated user experience on the existing **Worker** page. For more information, see [Streamlined employee entry](../../talent/streamlined-employee-entry.md). | Preview | 
  
\* This feature must be turned on before the **Human resources user experience enhancements** feature.

&dagger; This feature can't be disabled after it's enabled.

## Human resource user experience enhancements

| Feature name | More information | 
|--------------|----------| 
| Delete employment | You can delete the employment of an employee. | 
| Job families | You can track a group of jobs that involve similar work, and that require similar training, skills, knowledge, and expertise. For more information, see [Personnel jobs](../../human-resources/hr-personnel-jobs.md). | 
| Additional employment fields | The following fields were added: **Employment category**, **Employment type**, and **Employment status**. For more information see, [Set up employment categories](../../human-resources/hr-benefits-setup-employment-categories.md).| 
| **Workers without employment** page | A page shows a list of workers who don't have an employment record. For more information, see [Workers without employment](../../human-resources/hr-personnel-workers-without-employment.md).| 
| Position dimension user experience update | There is an enhanced user experience for assigning position dimensions per legal entity. For more information, see [Human resources personnel](../../human-resources/hr-personnel-positions.md). | 
| Address changes in **Personnel management** workspace | This feature provides a count of all address changes that occurred during a specified number of days, as defined on the **Human resources parameters** page. For more information, see [Personnel management workspace](../../human-resources/hr-personnel-personnel-management-workspace.md#address-changes-tile).| 
| Expiring records in **Personnel management** workspace | This feature provides a list of items that have expired or will expire for certificates, identifications, probations, screenings, or tests. For more information, see [Personnel management workspace](../../human-resources/hr-personnel-personnel-management-workspace.md#expiring-records-tab). | 
| **Position hierarchy validation** page | A check is done for circular references in the position line hierarchy. | 
| Country specific payroll information | Additional payroll fields are available on the **Worker employment** page, depending on the country/region of the legal entity where the workers are employed. | 
| Compliance reporting enhancements | Additional reporting options are available for EEO-1, Vets 4212, and OSHA300a. | 
| Updates to the **Personnel management** workspace | Updates have been made to track address changes and expiring records. Additionally, new tabs list worker and position actions. | 

## Known issues

| Issue summary | More information | Work around |
|--------------|----------|----------------|
|The Multiple level compensation feature| When the **Configure multiple compensation levels by job** feature is enabled, users will experience the following issues when transferring an employee: <br>	To a position that has a **Step compensation** level, the **Compensation level** drop-down list does not display the compensation levels associated to the position. <br>	To a position that has a **Grade** or **Band compensation level**, the user will receive an error that the values are out of range and the compensation level cannot be found.| Enable the Human resources user experience enhancements in **Feature management**.| 
|Error - 'Can't display visual' in **Employee development** workspace| When a user selects **Analytics** in the **Employee development** workspace, the user will receive an error.   | This is fixed in release 10.0.26. |
| Task link in **Onboarding**, **Offboarding** and **Transitions** **Task setup** is displaying incorrect information| When creating a task that uses a **Task link type** of  **Worker details**, the page incorrectly displays additional information in the drop-down list. | The issue is cosmetic. Page links can still be selected.|
| Offboarding checklists task due dates are off by one day when terminating through worker slide | When terminating a worker, and the user selects an **Offboarding** checklist in the **Terminate worker** slider, the tasks are created with a due date one day earlier than they should.|Do not assign an **Offboarding** checklist in the **Terminate worker** slider. Go to the **Checklists** menu item on the **Worker** page. Select to apply a checklist and use the termination date as the target date.|
|**Personnel management** workspace needs to be updated to add checklist information to the cards| In the **Personnel management** workspace, the employee cards need to be updated to indicate the following information: <br>	No checklist applied <br>	Tasks outstanding <br>	Overdue tasks |Go to the **Task management** workspace to view this information|
|Error 'The parent node failed in Business process' in the **Human resources** workspace| When a user creates a task on the fly in the **Business Process** workspace, and then changes the **Due date** filter, the user will receive an error.| Refresh the page after creating a new task on the fly.|
|Custom controls render incorrectly when using compressed visual sizing.|In **User options**, if the user has selected the **Compressed** visual size, rather than the **Standard** size, some of the custom controls may render incorrectly.| Select to view **Standard size** in the **User options-Visual tab**. |


