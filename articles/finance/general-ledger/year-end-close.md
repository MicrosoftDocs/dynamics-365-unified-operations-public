---
# required metadata

title: Year-end close
description: This topic describes the required setup and steps for running the general ledger year-end close process. 
author: kweekley
ms.date: 07/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerClosingSheet
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Year-end close

[!include [banner](../includes/banner.md)]

This topic describes the required setup and steps for running the general ledger year-end close process. 

At the end of a fiscal year, you must run the year-end close process to transfer opening balances to the new year. Most organizations will run the year-end close process multiple times. The first time would be to get the balances moved into the new fiscal year. The year-end close can then be run again, as many times as required, to move the balances from adjusting entries into the new fiscal year. 

During the year-end close process, there are two types of possible transactions created. An Opening transaction is always generated and is used to create the opening balances in the new fiscal year. The Opening transaction shows the balance sheet ledger account balances in the new fiscal year and balances from the profit and loss ledger account balances in the retained earnings ledger account in the new fiscal year. The Closing transaction is optionally created to bring the balances of the profit and loss accounts down to zero in the fiscal year being closed.

## Prepare to run the year-end close
Before you run the year-end close process, validate the settings for the following: 

On the **Main account** page:

- Validate the **Main account type** is defined properly for each main account. The Main account type is used to determine whether the balance of the main account will be brought forward as an opening balance or closed into retained earnings in the Opening transaction.
- The **Opening account** field can be used to transfer the balance of the main account to a new main account during the year-end close. The new main account is entered in the **Opening account** field. Typically this will be used for balance sheet main accounts when the main account is inactivated and a new main account is used for the new fiscal year.

On the **General ledger parameters** page under **Fiscal year close**:

- The **Delete existing year-end entries when re-closing the year** option is used to specify whether the system-generated Opening transaction from a previous year-end close should be deleted when the year-end close is run again. If this option is set to **Yes**, the previous Opening and optional Closing transactions are deleted and a new Opening or Closing transaction is created based on the current balances. If this option is set to **No**, the previous Opening and optional transaction remains and an additional Opening or Closing transaction is created to move the balances forward from adjusting transactions posted after the previous year-end close.

- The **Create closing transactions during transfer** option is used to create Closing transactions in the fiscal year being closed in order to bring the balances of the profit and loss accounts to zero. If this option is set to **Yes**, both the Opening transaction and Closing transaction is created. If this option is set to **No**, only the Opening transaction is created in the next fiscal year to transfer the balances. The profit and loss account balances remain at the end of the fiscal year.

- The **Set fiscal year status to permanently closed** option is used to set the fiscal year to a permanently closed status. Use this setting with caution, because all periods with a permanently closed status cannot be reopened, preventing adjustments from being posted to the fiscal year. It's a best practice to set this to **No**.

- The **Voucher number must be filled in** option removed. A voucher is required when running the year-end close process. The voucher number is manually entered at the time of running the year-end close.

On the **Fiscal calendar** page:

- The next fiscal year must exist before running the year-end close. The next fiscal year is required in order to create the beginning balances in the opening period.

On the **Ledger calendar** page:

- Optional: Each fiscal period for the fiscal year being closed can be set to **On hold** to prevent new transactions from being entered. When adjusting entries are identified, the On hold periods can be reopened to post adjusting entries, even if the year-end close process has already been run.

On the **Year-end close template setup** page: 

With the **General ledger year-end enhancements** feature enabled, the setup of the year-end close template has been separated from running the year-end close. The template can be defined under **General ledger – Ledger setup - Year-end close template setup** or it can be accessed from the year-end close process. 

With the feature

## Define year-end close templates
After the system is configured, the year-end close process can be run. On the **Year-end close template setup** page, a template can be defined for the group of legal entities for which the year-end close process will be run. The template will be reused at each year-end close, but can be modified if your organization changes. 

First, define the **Group name** for the template, and select the fiscal calendar. The group name should identify the group of legal entities included. When determining the groups of legal entities, remember that only legal entities with the same fiscal calendar selected can be included within the same group. For example, the templates may be set up based on geography, with separate groups created for North American legal entities, EMEA legal entities, and APAC legal entities. 

Next, the legal entities can be added to the template. Legal entities can be added by selecting an organizational hierarchy or by selecting the legal entities. If an organizational hierarchy is selected, only legal entities within the hierarchy that use the selected fiscal calendar will be added to the template. If you use legal entities to add to the template, only legal entities with the same fiscal calendar can be added. The same fiscal calendar is required because the year-end close is run by selecting a fiscal year, which can vary from calendar to calendar. 

After the legal entities are added, define the retained earnings main accounts for each legal entity.  

The **Financial dimension** tab is used to define which financial dimensions will be used on the Opening transaction. Note that the settings you are defining are relevant to only the legal entity selected in the **Legal entities** grid. You will repeat the setup for each legal entity in the grid. 

The **Transfer balance sheet dimensions** is used to define whether the financial dimensions on transactions posted to balance sheet accounts should be maintained on the Opening transaction. It’s a best practice to set this option to **Yes**. The setting for the balance sheet dimensions does not impact existing balances in the retained earnings ledger accounts. That is determined by the profit and loss dimensions defined in the next section. For example, fiscal year 2019 was the first year closed and the Department and Cost center were selected for closing, using Close all.  A separate retained earnings account was created for each combination of Department and Cost center.  When running the year-end close for fiscal year 2020, the retained earnings from the previous year will remain exactly as posted, even if the balance sheet dimensions option is set to No. Posted balances to retained earnings from previous year-end closes are never changed. 

The **Transfer profit and loss dimensions** is used to define which financial dimensions on transactions posted to profit and loss account will be transferred to the retained earnings main account. First, identify the financial dimensions relevant to the selected legal entity. This would include any financial dimensions posted against during the year, even if the financial dimension is not part of an active account structure. Next, define each dimension as either **Close single** or **Close all**.  The default is **Close all**, which maintains the original financial dimension values from posted transactions and uses them for creating the opening balances for the retained earnings account. Separate retained earnings beginning balances will be created for each unique combination of financial dimension values. If **Close single** is selected, all transactions posted with that financial dimension will be summarized into a retained earnings beginning balance for the dimension value entered in the field after **Close single**. For example, assume that all transactions for the fiscal year were posted with the account structure of Main account - Department. On the Department financial dimension on the template, **Close single** is selected and 100 is the value entered. If the total income of all transactions posted to departments 200, 300, and 400 is $100,000, one opening balance will be created for Retained earnings - 100. If you select **Close single** and leave the financial dimension value blank, all transactions will post to retained earnings with that dimension value being blank. 

## Run the year-end close process
After the year-end close templates are created, the year-end close process is initiated on the **Year-end close** page (**General ledger – Period close – Year-end close**). You can add new year-end close templates, or modify existing templates, before running the year-end close by selecting the **Year-end close template setup** button, which opens the setup page for the templates.  

Select the year-end close template and then choose **Run year-end close** on the Action Pane. Either select all or a subset of legal entities from the template for which to run the year-end close. When running the year-end close for the first time in a fiscal year, you will likely choose all the legal entities to create beginning balances for all the legal entities. If you're running the year-end close again, you may choose to run the process for only the legal entities for which adjusting entries were posted.

Select the fiscal year that you would like to run the year end close process against. If more than one closing period exists for the last period of the fiscal year, the **Period name** field will become available so you can select which closing period to post the Closing transaction, if setup is defined to create the Closing transaction. 

Enter a voucher number. The same voucher number will be used for all the legal entities selected for the year end close process. The voucher number is not generated using a number sequence.

The year-end close process runs in batch mode so you can return to other activities. 

The year-end close process doesn’t adhere to account structures. This is because account structures can change throughout a fiscal year and it's not always possible to identify the relevant account structure due to those changes. When opening transactions are created, the balances will be brought forward with financial dimensions as defined in the year end close template. The beginning balances entries could include financial dimensions no longer in the current account structure and segment combinations that are no longer valid in the current account structure. If your organization wants to exclude a financial dimension for the retained earning beginning balance, set the financial dimension to be **Close single** and leave the dimension value empty.

After the process is complete, a record will be created for each legal entity/fiscal year combination.  You will only see records for legal entities for which you have access. The record includes the system date/time of when the process was run and a direct link to the voucher(s) created for the year end close. 

Illustration

If the year end close is rerun, you will see one or multiple records for each legal entity/fiscal year depending on the GL parameters:
•	If the GL parameter Delete existing year-end entries when re-closing the year is set to Yes, the voucher for the previous year-end close will be deleted.  The record will be marked as Reversed, stamped with the Reversed date/time, and the link to the Voucher number removed.  A new record will be created for the new voucher created when the year-end close is complete.
•	If the GL parameter Delete existing year-end entries when re-closing the year is set to no, the record for the previous year-end close remains, along with the link to the voucher. A new record will be created each time the year-end close is run again, along with a link to the new vouchers.
	Reverse the year-end close process
A year end close can be reversed from the Year end close page. Select the record for the legal entity and fiscal year that needs to be reversed and select the Reverse year-end close button. The reversal will delete all opening and closing vouchers created for the fiscal year. The record will be marked as Reversed, stamped with the Reversed date/time, and the link to the Voucher number removed. The reversal of the year end close will also run via batch processing. 
An option, Show reversed, is available above the grid to hide or show the records for reversed year-end close processes.  After running the Reverse year-end close process, you may need to mark Show reversed to see the record. Additional filters can be used to view

Illustration

If the year end close is rerun, you will see one or multiple records for each legal entity/fiscal year depending on the GL parameters:
•	If the GL parameter Delete existing year-end entries when re-closing the year is set to Yes, the voucher for the previous year-end close will be deleted.  The record will be marked as Reversed, stamped with the Reversed date/time, and the link to the Voucher number removed.  A new record will be created for the new voucher created when the year-end close is complete.
•	If the GL parameter Delete existing year-end entries when re-closing the year is set to no, the record for the previous year-end close remains, along with the link to the voucher. A new record will be created each time the year-end close is run again, along with a link to the new vouchers.

## Reverse the year-end close process

A year end close can be reversed from the Year end close page. Select the record for the legal entity and fiscal year that needs to be reversed and select the Reverse year-end close button. The reversal will delete all opening and closing vouchers created for the fiscal year. The record will be marked as Reversed, stamped with the Reversed date/time, and the link to the Voucher number removed. The reversal of the year end close will also run via batch processing. 
An option, Show reversed, is available above the grid to hide or show the records for reversed year-end close processes.  After running the Reverse year-end close process, you may need to mark Show reversed to see the record. Additional filters can be used to view

Illustration

For more information, see [Close the general ledger at period end](close-general-ledger-at-period-end.md) and [Close the fiscal year](tasks/close-fiscal-year.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
