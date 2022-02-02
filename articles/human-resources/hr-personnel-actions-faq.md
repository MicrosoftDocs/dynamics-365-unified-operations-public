---
# required metadata

title: Personnel actions FAQ
description: This topic contains answers to questions that you might have if your organization uses personnel actions.
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: HcmPositionActionDetail, HcmPersonnelManagementWorkspace
# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Personnel actions FAQ


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic contains answers to questions that you might have if your organization uses personnel actions. Personnel actions are additional steps that you must complete when you perform certain personnel-related tasks. 

Examples of tasks that might require personnel actions are:
 - When you create new positions. 
 - Modify existing position values. 
 - Hire new workers. 
 - Transfer workers. 
 - Change worker compensation. 
 - Change position assignments. 
 - Terminate workers.

> [!NOTE]
> Personnel actions are available only if the **Enable worker actions** and **Enable position actions** fields have been set to **Yes**, in the **Personnel actions** tab on the **Human resources shared parameters** page. 

## How can I tell if my organization requires personnel actions?
Personnel actions are required by your organization if you are asked to select a personnel action when you create new positions, change existing positions, hire new workers, transfer workers, change worker compensation, change position assignments, terminate workers, or enter leave for workers. 

## What is the difference between a position action and a worker action?
There are two types of personnel actions:

- **Position** action – A position action is performed on existing positions or new positions. For example, a position action might be required if you change a value on an existing position or if you create a new seasonal position. 

- **Worker** action – A worker action is performed on existing employees or new employees. For example, a worker action might be required when a new employee is hired or an existing employee is promoted. 

## What do the statuses of the personnel actions mean?
Personnel actions can have the following statuses:

- **Draft** – If workflow is used, the action hasn't been submitted. If workflow isn't used, the action hasn't been completed.
- **In review** – The personnel action has been submitted to workflow, but the workflow is not completed.
- **Approved waiting** – The workflow is completed, but the changes are still in process. **Canceled** – The workflow was canceled or the personnel action was recalled. **Rejected** – The action request was rejected by the approver.
- **Processing action** – The action request has been approved and the changes are being processed.
- **Workflow complete**  – The workflow is completed and the changes have been processed. **Failed** – The workflow failed because the information is out of date. Click **Reactivate** to display the latest information and continue.
- **Completed** – The position was successfully created or modified, or the employee was successfully hired, transferred, or terminated, or had their compensation changed. **Error** – A problem occurred other than information being out of date. Open the **Personnel actions message log** to determine the cause of the error.
- **Denied** – The action request was denied by the approver.

## Can I delete a personnel action?
Yes, you can delete personnel actions that have a status of **Draft**, **Error**, **Failed**, or **Canceled**. You can delete personnel actions that have a status of **Completed** only if you've set the **Allow deleting completed worker actions** option to **Yes** on the **Human resources shared parameters** page.

## What is the fastest way to check the status of a personnel action request?
Open any of the **Personnel action** list pages and select a personnel action.

## What should I do if a personnel action request fails?
If a personnel action request fails, follow these steps to resolve the error and resubmit the request:

> 1. On the **Action Pane**, click the **Error text** button to view the message text that describes the problem.
> 
> 2. On the **Action Pane**, click **Reactivate** to load the latest information and set the status of the personnel action back to **Draft**.
> 
> 3. Resolve the error, and then click **Complete** or **Submit**.

## What happens to a personnel action that uses workflow when the final approval is completed?
If there are no errors, the personnel action becomes read-only. (You can view the history on the **All worker actions** list page, but you can't change the personnel action.) When the status of a  personnel action is **Completed**, the position or worker record has already been updated. To view the changes that were performed, open the **Positions** or **Workers** list page.

## Why do I receive the following error when I enter a non-zero value in the Pay rate field? "The value is out of its valid range – it much be between 0.00 and 0.00"
You receive this message because the **Level** field on the **Job** page is blank for the job that is associated with the selected position.

To resolve this error, follow these steps:

> 1. On the **Worker position assignments** page, click on **Position** field.  
> 2. Click the **Job** field value to open the **Job** page.
> 3. On the Action pane, click **Edit**.
> 4. Click the **Compensation** tab.
> 5. In the **Level** field, select a level.
> 6. Close the **Job** page.
> 7. Close the **Position** page.
> 8. Return to the **Compensation** tab on the **Worker** page, select **Fixed compensation**.  Select **New** and enter the employee's position in the **Position** field.  Enter a value in the **Plan** field, and then enter the employee's compensation in the **Pay rate** field.

## Why can't I change the effective date on the header of the Worker action page?
You can't change the effective date because the field is populated with the most logical date for the action type.

For example:

- The effective date in the header of a **Terminate a worker** action is the date you entered in the **Termination date** field.
- The effective date of a **Hire a worker** action is the date that you entered in the **Employment start date** field.
- The effective date of a **Transfer a worker** action is the date that you entered in the **Assignment start date** field for the worker.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
