---
title: Automate ledger settlements
description: This article provides information about the Automate ledger settlements process.
author: abruer
ms.date: 1/19/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: abruer
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.assetid: 
ms.search.form: 
---

# Automate ledger settlements

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Finance version 10.0.31, the **Automate ledger settlements process** feature is available in the **Feature management** workspace. You can enable the **Automate ledger settlements process** feature only if the **Awareness between ledger settlement and year-end close** feature has been enabled.

Ledger settlement is the process of matching debit and credit transactions in the general ledger. Organizations that perform ledger settlement activities on a recurring schedule can now automate the process. During the automatic ledger settlement process, a debit transaction and a credit transaction can be automatically matched only if their amounts in the accounting currency are equal. For example, a debit amount of $1.00 can be automatically matched to a credit amount of $1.00. However, a debit value of $1.00 can't be automatically matched to two credits, each of which is valued at $0.50. Partial matching of ledger transaction amounts isn't supported.

Ledger settlement automation defines the following details:

- When ledger settlements are run
- What criteria are used to match the debits and credits that can be automatically settled
- What order the ledger settlement information is processed in

## Define the occurrence of ledger settlements

Ledger settlement automation uses the Process automation framework. Different business processes use this framework to define the recurrence of a selected process. For ledger settlements, go to **System administration \> Setup \> Process automations** or **General ledger \> Ledger setup \> Process automations**.

First, select the **Create new process automation** option, and select **Ledger settlements**. A wizard then guides you through the process of setting up the automation.

## General page

On the **General** page of the wizard, enter the name of the ledger settlement occurrence that you're creating. For example, if your matching debits and credits are ledger-settled on Monday, enter a descriptive name such as **LedgerSettle\_Mon**. The name that you enter is shown in the **Automation rule** column on the **Ledger settlements** page.

The remaining settings on the page are generic and define the occurrence pattern for this version of the ledger settlements. For example, if an occurrence is for Monday, you can define it so that it runs weekly, and you can select Monday as the day of the week when it runs. You can also enter an early schedule time, such as 2:00 AM, so that the process automation will be completed before the start of the next business day. We recommend that you schedule the process automation so that it's performed outside your normal working hours. In this way, you help reduce the impact on your accounting staff during the workday.

For more information about the other fields on the **General** page, see the process automation documentation.

## Ledger settlements match criteria page

The next page in the wizard is the **Ledger settlements match criteria** page. It's used to define the main accounts that are included in the process automation occurrence, and the criteria that are used to determine matching debits and credits.

### Account selection

The main accounts that you've previously defined as ledger settlement accounts for the legal entity are shown. (You define main accounts as ledger settlement accounts at **General ledger \> Ledger setup \> General ledger parameters \> Ledger settlements**.)

### Date 

Select this option if the dates of the ledger debit and credit transactions should be considered during the automatic ledger settlements process. When this option is set to **Yes**, enter the **Allowed date difference**. This field is available starting in Microsoft Dynamics 365 Finance version 10.0.32.

## Allowed date difference
Enter the number of days variance for the debit and credit transactions dates. The variance is calculated as the number of days between the debit and credit transaction dates, searching before and after the selected transaction date. A value of 0 specifies that the transaction dates of the debit and credit transactions must match. This field is available when the **Date** field is selected.

### Main account and posting layer

The **Main account** and **Posting layer** values are required match criteria. The **Main account** and **Posting layer** values of the ledger debit transaction and credit transaction must be equal to be matched during the automatic ledger settlement process.

### Posting type

Select the **Posting type** option if the ledger debit and credit transactions must have the same posting type to be matched during the automatic ledger settlement process.

### Financial dimensions

Select the **Financial dimensions** option if the ledger debit and credit transactions must have the same financial dimensions to be matched during the automatic ledger settlement process. When this option is selected, the criteria for financial dimension values must be selected in the **Available financial dimensions** list. The **Available financial dimensions** list doesn't contain the main account dimension, because it's automatically required as part of the match criteria.

### Financial tags
When the **Financial tags** feature has been enabled in the **Feature management** workspace, you can select **Financial tags** as match criteria. Select the **Financial tags** option if the ledger debit and credit transactions must have the same financial tags values to be matched during the automatic ledger settlement process. When this option is selected, the criteria for financial tags values must be selected in the **Available financial tags** list.

## View the results of a ledger settlement automation

After the ledger settlement automation series is created, the occurrences for each ledger settlement are shown in the process automation weekly view. Additionally, the status of each occurrence is shown. The following statuses are used:

- **Scheduled** – The automation is scheduled, but it hasn't yet run.
- **Executing** – The automation is currently running.
- **Error** – The automation has run, but an error occurred. You can view the errors by selecting the **View results** button.
- **Completed** – The automation has successfully run. You can view the settlement results on the **Ledger settlements** page.

To view the matching results, go to **General ledger \> Periodic tasks \> Ledger settlements**. The **Automation rule** field on the **Ledger settlements** page shows the name of the automated ledger settlement scheduled task that was used to settle the transaction. Unsuccessful settlement attempts won't update the **Automation rule** value. If you manually reverse a transaction that was previously successfully settled by the automation process, the **Automation rule** value will be removed.

The **Date settled** field for the matched records shows the date when the automation process was performed.

## Editing a ledger settlement automation

The Process automation framework lets you edit the series and the occurrences that are created for the ledger settlement. The series can be edited from either the **Process automation** page or the process automation weekly view. For example, if the manager decides to perform ledger settlement on Wednesday instead of Monday, they can find an occurrence in the weekly view and select **View/Edit – Series**.

If you edit a series, you're prompted to specify whether the change should be made to all existing occurrences or only to new occurrences. Historical occurrences that already have a status of **Completed**, or that ended in an **Error** status, won't be changed.

You can also add a new occurrence or change an existing occurrence. For example, the next ledger settlement occurrence is scheduled to run Wednesday, January 1, but this date is a holiday. You can change the occurrence from either the **Process automation** page or the process automation weekly view. A page is opened that shows the schedule details and match criteria. Here, you can edit the scheduled time and date. You can also edit the match criteria, if changes are required. 

You can also disable an occurrence or a series. To disable an occurrence and suspend processing for it, select it in the process automation weekly view, and then select **Disable**. You can disable a series on the **Process automation** page.

## Security for ledger settlement automation

The **Maintain ledger settlements automation series settings** duty has been added to the Accounting manager and Accounting supervisor roles, and the **View ledger settlements automation series settings** duty has been added to the Accountant, Accounting manager, and Accounting supervisor roles for ledger settlement automations. These duties are the default security settings, but they can be changed based on your organization's requirements.

## General ledger parameters for ledger settlement automation

The **Settlement typical balance** field indicates the order that the automatic ledger settlement will be processed in. To set up or view the **Settlement typical balance** value, go to **General ledger \> Setup \> General ledger parameters**, and select the **Ledger settlements** tab.

If **Debit** is selected, the automated ledger settlement process starts on the debit side and searches for corresponding credits. If **Credit** is selected, the automated ledger settlement process starts on the credit side and searches for the corresponding debits. This option should reflect the main account's typical balance.

## Processing a ledger settlement automation

When the automation is run, the system selects ledger transactions for the main accounts that are defined for the process automation series. It orders the transactions by date, by using a date range from the start of the fiscal year to the date when the process automation is run. It matches based on the specified match criteria. The absolute values of the accounting currency amounts of the debit and the credit must match to be settled.

The Automate ledger settlements feature will run the automation for transactions that are dated from the first day of the fiscal year to the current date when the occurrence runs. For fiscal years that end on December 31, you might have to adjust the execution date of your occurrence to ensure that it's run in December. For example, automation is set to run on the first day of every month. This automation will be run on December 1, 2022, and is scheduled to run on January 1, 2023. It is recommeded to change the January 1, 2023 occurrence to December 31, 2022. This change will ensure that the transactions that are dated December 2 through 31 will be considered for automatic settlement.

While a main account is being processed by an occurrence of a ledger settlement automation, you can't display it in the **Ledger settlements** page. You must wait until the automation process is completed. We recommend that you schedule the process automation to run outside working hours, to help prevent conflicts.

The automation process will include all transactions that meet the criteria, except transactions that have been manually marked for settlement on the **Ledger settlements** page.

## Reversal of transactions that are settled by the automation process

You can reverse a settlement that was made by the automated ledger settlement process. When a transaction that was settled by the automation process is reversed, the **Automation rule** value will be removed.
