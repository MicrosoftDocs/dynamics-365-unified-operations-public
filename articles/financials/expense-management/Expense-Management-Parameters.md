---
# required metadata

title: Expense management parameters
description: The following parameters control the behavior in Expense management.
author: KimANelson
manager: AnnBe
ms.date: 01/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  TrvParameters
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson 
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Expense management parameters
-----------------------------

The parameters control the general behavior in Expense management.

### General

| **Field**                                                | **Description**                                                 |
|----------------------------------------------------------|---------------------------------------------------------------------|
| **Standard rate of mileage**                             | Enter the reimbursement rate for mileage expenses. The rate will be multiplied by the mileage entered on the expense to calculate the amount reimbursed for the travel expense.                       |
|**Personal expenses paid by**                             | Select who is responsible for paying any credit card transaction amounts categorized as personal.                                                                                                     |
|**Display entire expense report on drillback**               | Select this option to display all expenses for an expense report when viewing the details of the original document for a specific voucher that was generated when the expense report was posted.              |
|**Pre-authorization of travel is mandatory**                 | Select this option to require that a travel requisition be submitted and approved before an employee can submit an expense report.                                                                    |
|**Allow editing of distributions before posting**            | Select whether the distributions of an expense report can be edited prior to posting.                                                                                                                 |
|**Evaluate expense management policies**                     | Select when expenses are evaluated to determine if an expense policy has been violated. Expenses can be checked for violations when the expense entry is entered and saved or when the expense is submitted for approval. The policy rules for receipts required will be checked when the expense line is saved.                   |
|**Allow intercompany expense lines**                         | Select whether to allow entry of expenses for other legal entities within an expense report.                                                                                                          |
|**Allow editing the exchange rate for credit card expenses** | Select this option to allow the user to edit the exchange rate for imported credit card expenses.                                                                        |
|**Multi-level hierarchy fields to display**                  | Select which approver fields to display when the expense report workflow assignment type is set to be hierarchy and the hierarchy selection is set to use the Expense multi-level approval hierarchy. When the multi-level approval hierarchy is used for workflow, the selected fields will be displayed and editable in the Expense report. |
|**Enter employee credit card number (July 2017 update)**     | Select whether a 15-or 16-character number can be entered and saved in the **Card ID** field in the **Credit cards** page for an employee.                                                                          |

### Financial

| **Field**                                                            | **Description**     |
|----------------------------------------------------------------------|------------------------------------|
|**Ledger daily journal name**                                         | Select the name of the ledger journal that approved expense reports are posted to.            |
|**Enable tax recovery from expenses**                                  | Select this option to enable expense tax recovery for eligible expenses. This option cannot be enabled if US sales tax and use tax rules are enabled.      |
|**Post cash advances immediately**                                     | Select this option to post an approved cash advance when the process to Pay and transfer is completed. If this option is not selected, the Pay and transfer process will generate an unposted general journal. |
|**Correct accounting date during posting**                             | Select this option to update the accounting date when posting expenses if the current period is on hold or closed. The accounting date will be set to the next open period.   |
|**Allow grouping of transactions based on offset account specified in payment method**      | Select this option to summarize the expense transactions for an expense report, based on the offset account specified in the payment method for the expenses.   
|**Tax included**                                                   | Select this option to include sales tax in the expense amount by default.             |
|**Release encumbrances on closing travel requisitions**            | Select this option to release encumbered funds when an approved travel requisition is closed.                                                                                   |
|**Allow travel requisition submit on budget overrun for budget register and project budget** | Select this option to allow employees to submit travel requisitions for approval that exceed either the allowed budget that is set in the budget register or the allowed budget for a project.            |
|**Allow expense report submit on budget overrun for budget register and project budget**    | Select this option to allow employees to submit expense reports for approval that exceed either the allowed budget that is set in the budget register or the allowed budget for a project.                |
|**Allow expense report approval on budget overrun for budget register only**                | Select this option to allow approvers to approve expense reports that exceed the allowed budget that is set in the budget register.                                                                       |

### Per diem

| **Field**                             | **Description**             |
|---------------------------------------|--------------------------------------------------------------------------------------|
|**Minimum hours for per diem**           | Enter the default minimum number of hours that an employee must work in a day to be eligible to receive a per diem for travel-related expenses.  This value is only used as a default value for the Minimum hours field on per diem rate tiers.                                                                                      |
|**Meal percent**                          | Enter the default percentage of the per diem for meals that is used on the first and last days of the travel-related expense when the **Calculate meal reduction by** field is set to either **Meal type per day** or **Number of meals per day**. The work day on the first and last days may be shorter than a standard work day. Therefore, the amount of the per diem on these days may differ from the standard amount. If the percent is set to 0, then the first and last day deductions will be 0.00. |
|**Hotel percent**                        | Enter the default percentage of the per diem for hotels that is used on the first and last days of the travel-related expense. The work day on the first and last days may be shorter than a standard work day. Therefore, the amount of the per diem on these days may differ from the standard amount. If the percent is set to 0, then the first and last day deductions will be 0.00.                                              |
|**Other percent**                        | Enter the default percentage of the per diem for miscellaneous expenses that is used on the first and last days of the travel-related expense. The work day on the first and last days may be shorter than a standard work day. Therefore, the amount of the per diem on these days may differ from the standard amount. If the percent is set to 0, then the first and last day deductions will be 0.00.                                                                                                     |
|**Reduction in percentage for breakfast** | Enter the amount that the per diem is reduced for breakfast. For example, if an employee receives a complimentary breakfast, you may want to reduce the amount of the per diem by 10 percent.                               |
|**Reduction in percentage for lunch**    | Enter the amount that the per diem is reduced for lunch. For example, if an employee receives a complimentary lunch, you may want to reduce the amount of the per diem by 15 percent.                                       |
|**Reduction in percentage for dinner**   | Enter the amount that the per diem is reduced for dinner. For example, if an employee receives a complimentary dinner, you may want to reduce the amount of the per diem by 25 percent.                                     |
|**Calculate meal reduction by**         | Select how the system should calculate the per diem meal reduction by selecting if the reduction is based on the meal type per trip or per day, or if the reduction is based on the number of meals allowed per day.|
|**Per diem rounding**                  | Select the type of rounding that is used for per diem expenses. If you select normal rounding, any per diem expense that has an amount of 0.50 is rounded up to 1.00, and any per diem expense that has an amount that is less than 0.50 is rounded down to 0.00.                                                                                              |
|**Base per diem calculation on**         | Select whether a per diem amount is based on a calendar day or a 24-hour period.       |

### Fax cover pages

| **Field**                      | **Description**            |
|--------------------------------|-----------------------------------------------------------------------------|
| **Instructions**                   | Enter the instructions that employees must follow when they create a cover page for a fax that is used to send receipts that are related to an expense report. Click the **Translations** button to enter language-specific text that will be displayed based on the user language. |
|**User ID (Bar code information)** | Select this option to store an employee’s unique identifier in the bar code that is used on the cover page of the fax.                 |
|**Bar code**                      | Select the bar code that is used on the cover page of the fax. Bar codes 39 and 128 are supported with Expense management.               |

### Anti-corruption

| **Field**                             | **Description**      |
|---------------------------------------|------------------------------------------------------------------------|
|**Display anti-corruption attestation**   | Select this option to display the anti-corruption text when creating a new expense report. Specific expense categories can then be enabled that will require the anti-corruption attestation to be selected on the expense report. For example, a gift category related to a government official expense may require the employee to confirm that the expense meets company policy related to government officials. |
|**Anti-corruption message for submitter** | Enter the text that will be displayed to the employee when creating a new expense report. Click the **Translations** button to enter language specific text that will be displayed based on the user language.         |
|**Anti-corruption message for approver**  | Enter the text that will be displayed to the approver when creating a new expense report. Click the **Translations** button to enter language specific text that will be displayed based on the user language.        |
