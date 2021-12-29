---
# required metadata

title: Process purchase orders at year end
description: 
author: TaylorVH 
ms.date: 2/01/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 267074
ms.assetid: 1d293b3a-2fa2-418d-9347-78c2809d67fe
ms.search.region: global
# ms.search.industry: 
ms.author: v-savanh
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2022-02-01

---

# Process purchase orders at year end

[!include [banner](../includes/banner.md)]

If you record encumbrances for purchase orders in the general ledger, which includes purchase orders for projects, you can generate closing entries to the general ledger and against budget reservations at the end of each fiscal year. At the start of the new fiscal year, you can create opening entries to correctly record the encumbrances and budget reservations. These entries help make sure that the reservations for purchase order encumbrances are correctly recorded on the year-end financial statements and in budget control.

For projects, the account that distributions are assigned to in the new fiscal year is the account that is defined in the Purchase order year-end process form in General ledger. It is not the account that is defined in the Ledger posting setup form in Project management and accounting.

If you are in the public sector and are using general budget reservations, see also Finalize a general budget reservation (Public sector) and Carry forward general budget reservation information to a new fiscal year (Public sector).

In the case of a partially invoiced purchase order, only the amount that has not been invoiced is closed and then reopened in the next fiscal year.

Closing purchase order encumbrances is a separate process from closing a fiscal year, and is usually performed before a fiscal year is closed. For information about closing a fiscal year, see Fiscal year closing checklist.

> [!Note]
> (FRA) French public sector entities can also create or update commitments in the new fiscal year. For more information, see (FRA) About commitments (Public sector) and (FRA) Process purchase order encumbrances and commitments at year end (Public sector).

### Prerequisites
Before you start this process, make sure that the following prerequisites have been set up.

## Enable budget control
Budget control is often enabled when encumbrances are created for purchase orders. You do not have to enable budget control to use this process, but budget register entries are not created unless you do. The Process and carry forward budget year-end option also cannot be used unless budget control is enabled. For more information, see Set up budget control.

## Enable the encumbrance process
The encumbrance process must be enabled before encumbrances for purchase orders can be recorded in the general ledger, and before you can run the purchase order year-end process successfully. For more information, see Encumber purchase orders.

## Set up posting definitions
Open the Posting definitions form to set up the following posting definitions in the Purchasing module, if they do not already exist:

Purchase order year end – This posting definition is used to reverse encumbrances and outstanding budget reservations for purchase orders in the fiscal year that is ending, and to generate year-end closing entries in the general ledger.

Purchase order encumbrances – This posting definition defines how encumbered amounts are recorded in the general ledger. It is also used in the new fiscal year to reverse year-end closing entries and to re-establish encumbrances in the general ledger.

For more information, see Set up posting definitions.

Assign posting definitions to transaction posting types
Use the Transaction posting definitions form to assign posting definitions to the transaction posting definitions that correspond to them. You also select the criteria that originating transactions must meet for a specific posting definition to be used.

Select the following transaction posting types in the Purchasing module, and then follow the steps in Assign posting definitions to transaction posting types:

Purchase order year-end close – Select the posting definition that you created for purchase order year-end.

Purchase order – Select the posting definition that is used for purchase order encumbrances.

## Year-end processing options
Select one of the following year-end processing options to close purchase order encumbrances in the fiscal year that is ending and to re-encumber them in the new fiscal year.

|     Option                                     	|     Closing and opening steps that occur for purchase   order encumbrances    	|
|------------------------------------------------	|-------------------------------------------------------------------------------	|
|     Process and do not carry forward budget  –  Closing steps    	|    1.  The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed. <br> 2. Year-end closing entries are generated in the general ledger. <br>                                             	|
|      Process and do not carry forward budget  –  Opening steps                                      	|   1. Closing entries are reversed.   <br>  2.  Encumbrances are re-established in the general ledger.     <br>  3. Budget reservations for encumbrances are created for the purchase orders that are being processed.        	|
|     Process and carry forward budget           	|     This option is available only if budget control has   been enabled.       	|
|     Process and carry forward budget  –  Closing steps                                     	|    1. The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed.     <br> 2. Budget adjustments are created to reduce the budget in the fiscal year that is being closed.                                           	|
|    Process and carry forward budget  –  Opening steps                                     	|        <br>  1.  Closing entries are reversed.  <br>  2. Encumbrances are re-established in the general ledger.     <br>  1. Budget reservations for encumbrances are created for the purchase orders that are being processed. <br>  3. Budget adjustments are created in the new fiscal year to re-establish the budget register entries that were carried forward from the previous fiscal year.	|

## Select purchase orders and run the purchase order year-end process

1. Click General ledger > Periodic > Fiscal year close > Purchase order year-end process.

2. Click Retrieve purchase orders in the lower pane to select purchase orders for the year-end process. This opens a query form where you can select purchase orders by criteria such as the date, date range, vendor account, purchase order type, purchase order balance, or financial dimensions. For more information, see Inquiry (form).

3. Click OK in the Inquiry form.

4. The results of the query are displayed in the lower pane of the Purchase order year-end process form. Select the Include check box for each purchase order to include in the year-end processing. Encumbrances for those purchase orders will be reversed in the fiscal year that is ending, and the encumbered amounts will be made available in the new fiscal year. You can click Include all to select all of the purchase orders in the list, or click Exclude all to clear the selections.

> [!TIP]
> You can view the details of a purchase order by clicking View purchase order. You can also click View subledger journal to view the year-end closing and opening entries that will be generated for individual purchase orders.

5. In the Year-end option field, select how to process purchase order encumbrances.

6. Select an original budget code, if you selected the Process and carry forward budget year-end option. This code is used for budget adjustments that are made in the closing fiscal year. The code that you select must not have a workflow selected, because the year-end processing would stop for workflow approvals. For more information, see Budget codes (form).

7. Select a carry forward budget code, if you selected the Process and carry forward budget year-end option. This code is used for budget adjustments that are made in the new fiscal year. The code that you select must not have a workflow selected, because the year-end processing would stop for workflow approvals. For more information, see Budget codes (form).

8. Verify the default values in the Calendar and Fiscal year fields, and make any changes. You can change the fiscal year value here, but you must use the Ledger form to change the selected fiscal calendar.

   You can click the calendar name to open the Fiscal calendars form, where you can view a description of the fiscal calendar, and the fiscal years that are included in the fiscal calendar.

9. Verify the default values for the Closing parameters fields, and make any changes to the fields that can be changed.

  - The Accounting date field indicates the last day of the selected fiscal year. You cannot change this date.

  - The Type field is typically set to Operating for a period that can be used to record accounting transactions. You can select Closing if you are using a closing period to separate the closing entries. For information about how to create closing periods, see Key tasks: Fiscal calendars, fiscal years, and periods.

  - If you selected a type of Closing, select the closing period to use.

10. Verify the values for the Opening parameters fields. These fields cannot be changed.

 - The Accounting date field indicates the first day of the opening fiscal year.

 - The Period field indicates the first period that has a type of Operating in the opening fiscal year. This type of period is used to record accounting transactions.

11. Click Process when you are ready to run the purchase order year-end process.

12. If any messages are displayed, make the necessary corrections, and then run the process again for the affected purchase orders.

> [!IMPORTANT]
> Verify the budget register entries that were created in the previous and current fiscal years to help ensure the accuracy of the year-end encumbrance closing process. 
