---
# required metadata

title: Year-end close
description: This topic describes the required setup and steps for running the general ledger year-end close process. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23 - 07 - 06
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LedgerClosingSheet
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2231
ms.search.scope: AX 7.0.0, Operations, Core
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

This topic describes the required setup and steps for running the general ledger year-end close process. 

At the end of a fiscal year, you must run the year-end close process to transfer opening balances to the new year. Most organizations will run the year-end close process multiple times. The first time would be to get the balances moved into the new fiscal year. The year-end close can then be run again, as many times are required, to move the balances from adjusting entries into the new fiscal year. 

During the year-end close process, there are two types of possible transactions created. An Opening transaction is always generated and is used to create the opening balances in the new fiscal year. The Opening transaction shows the balance sheet ledger account balances in the new fiscal year and balances from the profit and loss ledger account balances in the retained earnings ledger account in the new fiscal year. The Closing transaction is optionally created to bring the balances of the profit and loss accounts down to zero in the fiscal year being closed.

## Prepare to run the yearend close
Before you run the year-end close process, validate the settings for the following: 

On the **Main account** page:

-   Validate the **Main account type** is defined properly for each main account. The Main account type is used to determine whether the balance of the main account will be brought forward as an opening balance or closed into retained earnings in the Opening transaction.
-   The **Opening account** field can be used to transfer the balance of the main account to a new main account during the year-end close. The new main account is entered in the **Opening account** field. Typically this will be used for balance sheet main accounts when the main account is inactivated and a new main account is used for the new fiscal year.

On the **General ledger parameters** page under **Fiscal year close**:

-   The **Delete close of year transactions** option is used to specify whether the system-generated Opening transaction from a previous year-end close should be deleted when the year-end close is run again. If this option is set to **Yes**, the previous Opening transaction is deleted and a new Opening transaction is created based on the current balances. If this option is set to **No**, the previous Opening transaction remains and an additional Opening transaction is created to move the balances forward from adjusting transactions posted after the previous year-end close.
-   The **Create closing transactions during transfer** option is used to create Closing transactions in the fiscal year being closed in order to bring the balances of the profit and loss accounts to zero. If this option is set to **Yes**, both the Opening transaction and Closing transaction is created. If this option is set to **No**, only the Opening transaction is created in the next fiscal year to transfer the balances. The profit and loss account balances remain at the end of the fiscal year.
-   The **Set fiscal year status to permanently closed** option is used to set the fiscal year to a permanently closed status. Use this setting with caution, because all periods with a permanently closed status cannot be reopened, preventing adjustments from being posted to the fiscal year. It's a best practice to set this to **No**.
-   The **Voucher number must be filled in** option is used to define whether a voucher number is required when running the year-end close process. It’s a best practice to require a voucher number in order to easily identify the Opening transaction.

On the **Fiscal calendar** page:

-   The next fiscal year must exist before running the year-end close. The next fiscal year is required in order to create the beginning balances in the opening period.

On the **Ledger calendar** page:

-   Optional: Each fiscal period for the fiscal year being closed can be set to **On hold** to prevent new transactions from being entered. When adjusting entries are identified, the On hold periods can be reopened to post adjusting entries, even if the year-end close process has already been run.

## Define year-end close templates
After the system is configured, the year-end close process can be run. On the **Year-end close** page, a template can be defined for the group of legal entities for which the year-end close process will be run. The template will be reused at each year-end close, but can be modified if your organization changes. 

First, define the **Group name** for the template, and select the fiscal calendar. The group name should identify the group of legal entities included.  For example, the templates may be set up based on geography, with separate groups created for North American legal entities, EMEA legal entities, and APAC legal entities. 

Next, the legal entities can be added to the template. Legal entities can be added by selecting an organizational hierarchy or by selecting the legal entities. If an organizational hierarchy is selected, only legal entities within the hierarchy that use the selected fiscal calendar will be added to the template. If you use legal entities to add to the template, only legal entities with the same fiscal calendar can be added. The same fiscal calendar is required because the year-end close is run by selecting a fiscal year, which can vary from calendar to calendar. 

After the legal entities are added, define the retained earnings main accounts for each legal entity. The **Date of last year end close** field will be updated each time the year end close is run for the legal entity. 

The **Financial dimension** tab is used to define which financial dimensions will be used on the Opening transaction. Note that the settings you are defining are relevant to only the legal entity selected in the **Legal entities** grid. You will repeat the setup for each legal entity in the grid. 

The **Transfer balance sheet dimensions** is used to define whether the financial dimensions on transactions posted to balance sheet accounts should be maintained on the Opening transaction. It’s a best practice to set this option to **Yes**. The **Transfer profit and loss dimensions** is used to define which financial dimensions on transactions posted to profit and loss account will be transferred to the retained earnings main account. First, identify the financial dimensions relevant to the selected legal entity. This would include any financial dimensions posted against during the year, even if the financial dimension is not part of an active account structure. Next, define each dimension as either **Close single** or **Close all**.  The default is **Close all**, which maintains the original financial dimension values from posted transactions and uses them for creating the opening balances for the retained earnings account. Separate retained earnings beginning balances will be created for each unique combination of financial dimension values. If **Close single** is selected, all transactions posted with that financial dimension will be summarized into a retained earnings beginning balance for the dimension value entered in the field after **Close single**. For example, assume that all transactions for the fiscal year were posted with the account structure of Main account - Department. On the Department financial dimension on the template, **Close single** is selected and 100 is the value entered. If the total income of all transactions posted to departments 200, 300, and 400 is $100,000, one opening balance will be created for Retained earnings - 100. If you select **Close single** and leave the financial dimension value blank, all transactions will post to retained earnings with that dimension value being blank. 

The year-end close process doesn’t adhere to account structures. This is because account structures can change throughout a fiscal year and it's not always possible to identify the relevant account structure due to those changes.  When opening transactions are created, the balances will be brought forward with financial dimensions as defined in the year end close template. The beginning balances entries could include financial dimensions no longer in the current account structure and segment combinations that are no longer valid in the current account structure. If your organization wants to exclude a financial dimension for the retained earning beginning balance, set the financial dimension to be **Close single** and leave the dimension value empty.

## Run the yearend close process
After the year-end close templates are created, the year-end close process is initiated by choosing **Run fiscal year** on the Action Pane. Either select all or a subset of legal entities from the template for which to run the year-end close. When running the year-end close for the first time in a fiscal year, you will likely choose all the legal entities to create beginning balances for all the legal entities. If you're running the year-end close again, you may choose to run the process for only the legal entities for which adjusting entries were posted. 

Select the fiscal year that you would like to run the year end close process against. If more than one closing period exists for the last period of the fiscal year, the **Period name** field will become available so you can select which closing period to post the Closing transaction, if setup is defined to create the Closing transaction. 

Enter a voucher number, which or may not be required, depending on the setup in General ledger parameters. The same voucher number will be used for all the legal entities selected for the year end close process. The voucher number is not generated using a number sequence. It’s a best practice to enter a voucher number, even if it’s not required. Entering a voucher number makes it easier to find the Opening transaction in the new fiscal year. If a voucher number isn’t entered, the voucher will be blank for the Opening transaction. 

If you would like to reverse a previous year end close for the selected fiscal year, set **Undo previous close** to **Yes**. The year-end close will be reversed, but the process can be rerun at any time. If you reverse a year-end close, the **Date of last year end close** will be unavailable. 

The year-end close process defaults to run in batch mode. It’s a best practice to run the process in batch mode, to allow the user to return to other activities. After the year end close process is complete, the **Date of last year end close** will be updated with the session date.

For more information, see [Close the general ledger at period end](close-general-ledger-at-period-end.md).

