---
title: Automate ledger settlements
description: This article provides information about the Automate ledger settlements process. Organizations that perform ledger settlement activities on a recurring schedule can now automate the process of matching debit and credit transactions in the general ledger.
author: abruer
ms.date: 
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

In Microsoft Dynamics 365 Finance version 10.0.31, the **Automate ledger settlements process** feature is available in the **Feature management** workspace. To enable the **Automate ledger settlements process** feature, the **Awareness between ledger settlement and year-end close** feature must be enabled.

Ledger settlement is the process of matching debit and credit transactions in the general ledger. Organizations that perform ledger settlement activities on a recurring schedule can now automate the process of matching debit and credit transactions in the general ledger. The debit and credit transaction’s accounting currency amounts must equal to be automatically matched during the automatic ledger settlements process.  For example, a debit amount of **$1.00** can be automatically matched to a credit amount of **$1.00**. However, a debit value of **$1.00** will not be automatically matched to two credits valued at **$0.50** each. Partial matching of ledger transaction amounts is not supported. 

Ledger settlements automations define the following details: 

-	When ledger settlements are run 
-	What criteria are used to match the debits and credits that can be automatically settled 
-	What order that the ledger settlement information will be processed

## Define the occurrence of ledger settlements 

Ledger settlements automations use the Process automation framework. Different business processes use this framework to define the recurrence of a selected process. For ledger settlements, the automation can be accessed at **System administration > Setup > Process automations** or **General ledger > Ledger setup >Process automations**. 

First, use the **Create new process automation** option, and select **Ledger settlements**. A wizard then guides you through the process of setting up the automation.

## General page 

On the **General** page of the wizard, enter the name of the ledger settlements occurrence that you're creating. For example, if you ledger settle your matching debits and credits on Monday, enter a descriptive name such as **LedgerSettle_Mon**. The name that you enter is shown in the **Automation rule** column in the **Ledger settlements** page. 

The remaining settings on the page are generic and are used to define the occurrence pattern for this version of the ledger settlements. For example, if an occurrence is for Monday, you can define it so that it runs weekly, and you can select Monday as the day of the week when it runs. You can also enter an early schedule time, such as 2:00 AM, so that the process automation will be completed before the start of the next business day. It is recommended to schedule the process automation to be performed outside of your normal working hours, to reduce the impact to your accounting staff during the workday.

For more information about the other fields on the **General** page, see the process automation documentation.

## Ledger settlements match criteria page 

The next page in the wizard is the **Ledger settlements match criteria** page. It's used to define the main accounts that will be included in this process automation occurrence and the criteria used for determining matching debits and credits.  

### Account selection 
The main accounts that you’ve previously defined as ledger settlement accounts for this legal entity will be displayed. (**General ledger > Ledger setup > General ledger parameters > Ledger settlements**)

### Main account and posting layer 

The Main account and Posting layer values are required match criteria. The Main account and Posting layer of the ledger debit transaction and credit transaction must equal to be matched during the automatic ledger settlements process. 

### Posting type 

Select this option if the ledger debit and credit transactions must have the same posting type in order to be matched during the automatic ledger settlements process.  
### Financial dimensions 

Select this option if the ledger debit and credit transactions must have the same financial dimensions in order to be matched during the automatic ledger settlements process. When selected, the financial dimension value criteria must be selected from the **Available financial dimensions** list. 
The **Available financial dimensions** list does not contain the main account dimension because it is automatically required as part of the match criteria.  

## View the results of a ledger settlements automation

After the ledger settlement automation series is created, the occurrences for each ledger settlement are shown in the process automation weekly view.  
Additionally, the status of each occurrence is shown. The following statuses are used: 

-	Scheduled – The automation is scheduled, but it hasn't yet run. 
- Executing – The automation is currently running. 
- Error – The automation has run, but an error occurred. You can view the errors by selecting the **View results** button. 
- Completed – The automation has successfully run. You can view the settlement results on the **Ledger settlements** form. 

To view the matching results, go to **General ledger > Periodic tasks > Ledger settlements**.  The **Automation rule** field on the **Ledger settlements** form will display the name of the automated ledger settlement scheduled task that was used to settle the transaction. Unsuccessful attempts to settle will not update the **Automation rule** value. If you manually reverse a transaction that was previously successfully settled by the automation process, the **Automation rule** value will be removed. 

The **Date settled** for the matched records displays the date that the automation process was performed.
 
## Edit a ledger settlement automation

The Process automation framework lets you edit the series and the occurrences that are created for the ledger settlement. The series can be edited from either the **Process automation** page or the process automation weekly view. For example, if the manager decides to perform ledger settlement on Wednesday instead of Monday, they can find an occurrence in the weekly view and select **View/Edit – Series**. If you edit a series, the system prompts you to specify whether the change should be made to all existing occurrences or only to new occurrences. Historical occurrences that already have a status of **Completed**, or that ended in an **Error** status won't be changed. 

You can also add a new occurrence or change an existing occurrence. For example, the next ledger settlement occurrence is scheduled to run Wednesday, January 1, but this date is a holiday. You can change the occurrence from either the process automation weekly view or the Process automation page. A page is opened that shows the schedule details and match criteria. Here, you can edit the scheduled time and date. You can also edit the match criteria, if changes are required. 
You can also disable an occurrence or a series. To disable an occurrence and suspend processing for it, select it in the process automation weekly view, and then select **Disable**. You can disable a series on the **Process automation** page. 

## Security for ledger settlements automation 

The **Maintain ledger settlements automation series settings** duty has been added to the Accounting manager and Accounting supervisor roles, and the **View ledger settlements automation series settings** have been added to the Accountant, Accounting manager and Accounting supervisor roles for ledger settlement automations. These duties are the default security settings, but they can be changed based on your organization's requirements.  

## General ledger parameters for ledger settlements automation 

The Settlement typical balance field indicates the order that the automatic ledger settlement will be processed. To set up or view the Settlement typical balance, go to **General ledger > Setup > General ledger parameters > Ledger settlements** tab. 
When **Debit** is selected, the automated ledger settlement process will start with the debit side and search for corresponding credits. When **Credit** is selected, the automated ledger settlement process will start with the credit side and search for the corresponding debits. This option should typically reflect the main account's typical balance. 

## Processing ledger settlements automation 

When the automation is run, the system will select ledger transactions for the main accounts that are defined for the process automation series. It will order the transactions by date, using a date range from the start of the fiscal year to the date that the process automation is run. It will match based on the specified match criteria. The absolute values of the accounting currency value of the debit and the credit must match to settle. 
 
While a main account is being processed by an occurrence of a ledger settlement automation, you cannot display it in the **Ledger settlements** page. You will need to wait until the automation process is complete. We recommend scheduling the process automation to run outside of working hours to avoid conflicts. 
 
The automation process will include transactions that meet the criteria, except if they have been manually marked for settlement from the **Ledger settlements** page. 

## Reversal of transactions settled by the automation process 

You can reverse a settlement that was made by the automated ledger settlement process. When a transaction that was settled by the automation process is reversed, the Automation rule indicator will be removed.

