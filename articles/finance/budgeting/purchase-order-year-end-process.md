---
title: Purchase order year-end close
description: Learn about the required steps for running the purchase order year-end process. 
author: music727
ms.author: music727 
ms.topic: article
ms.date: 09/25/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 09/25/2024

---

# Purchase order year-end close

[!include [banner](../includes/banner.md)]

This article describes the required steps and setup for running the purchase order year-end process.

If you record encumbrances for purchase orders in the general ledger, which includes purchase orders for projects, you can generate closing entries to the general ledger and against budget reservations at the end
of each fiscal year. At the start of the new fiscal year, you can create opening entries to correctly record the encumbrances and budget reservations. These entries make sure that the reservations for purchase
order encumbrances are correctly recorded on the year-end financial statements and in a budget control.

See more about [Purchase order encumbrances](https://learn.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/about-purchase-order-encumbrances).

For projects, the account that distributions are assigned to in the new fiscal year is the account that is defined in the **Purchase order year-end process** form in the General ledger module. It is not the 
account that is defined in the **Ledger posting setup** form in the Project management and accounting module.

For public sector organizations using general budget reservations, see [Finalize a general budget reservation](/dynamicsax-2012/appuser-itpro/finalize-a-general-budget-reservation-public-sector) and
[Carry forward general budget reservation information to a new fiscal year (Public sector)](/dynamicsax-2012/appuser-itpro/carry-forward-general-budget-reservation-information-to-a-new-fiscal-year-public-sector).

> [!NOTE]
> General budget reservations are available only if the *Public Sector* configuration key is enabled.

In the case of a partially invoiced purchase order, only the amount that hasn't been invoiced is closed and then reopened in the next fiscal year.


Closing purchase order encumbrances is a separate process to closing a fiscal year and is usually performed before a fiscal year is closed. For information about closing a fiscal year, see [Year-end close](year-end-close.md).


> [!NOTE]
> (FRA) French public sector entities can also create or update commitments in the new fiscal year. For more information, see [(FRA) About commitments (Public sector)](dynamicsax-2012/appuser-itpro/fra-about-commitments-public-sector) and [(FRA) Process purchase order encumbrances and commitments at year end (Public sector)](https://learn.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/fra-process-purchase-order-encumbrances-and-commitments-at-year-end-public-sector).


## Prerequisites

Before starting purchase order year-end process, the following prerequisites must be set up.

### Enable budget control
Budget control is often enabled when encumbrances are created for purchase orders. You don't have to enable budget control to use this process, but budget register entries are not created unless it is done. 
The **Process and carry forward budget year-end option** can't be used unless budget control is enabled. For more information, see [Set up budget control](budget-control-overview-configuration.md).

### Enable the encumbrance process
The encumbrance process must be enabled before encumbrances for purchase orders can be recorded in the general ledger, and before you can run the purchase order year-end process successfully. For more information,
see [Encumber purchase orders](/dynamicsax-2012/appuser-itpro/encumber-purchase-orders).

### Set up posting definitions
Go to **Posting definitions** and set up the following posting definitions in the **Purchasing** module, if needed:

  - **Purchase order year end** – This posting definition is used to reverse encumbrances and outstanding budget reservations for purchase orders in the fiscal year that is ending, and to generate year-end closing
 entries in the general ledger.
  - **Purchase order encumbrances** – This posting definition defines how encumbered amounts are recorded in the general ledger. It is also used in the new fiscal year to reverse year-end closing entries and to
re-establish encumbrances in the general ledger.

For more information, see [Posting definitions](posting-definitions.md).

### Assign posting definitions to transaction posting types

Use the **Transaction posting definitions** to assign posting definitions to the transaction posting definitions that correspond to them. You can also select the criteria that originating transactions must meet
for a specific posting definition to be used.

Select the following transaction posting types in the **Purchasing**, and then follow the steps in the [Posting definitions](posting-definitions.md) page:

  - **Purchase order year-end close** – Select the posting definition created for purchase order year-end.
  - **Purchase order** – Select the posting definition used for purchase order encumbrances.

## Year-end processing options
Select one of the following year-end processing options to close purchase order encumbrances in the fiscal year that is ending and to re-encumber them in the new fiscal year.

> [!NOTE]
> The year-end processing option selected is used for encumbrances on all of the purchase orders selected. If the **Public Sector** configuration key is enabled, you can override this selection and
> substitute a different year-end processing option for specific funds that you select on the **Funds** page.

| **Option**| **Closing and opening steps that occur for purchase order encumbrances** |
|------|------------------------------------------------------------|
|**Process and do not carry forward budget**| **Closing steps:** <ol><li>The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed. <li> Year-end closing
entries are generated in the general ledger.</li></ol> **Opening steps:** <ol><li> Closing entries are reversed. <li> Encumbrances are re-established in the general ledger. <li> Budget reservations for 
encumbrances are created for the purchase orders that are being processed.</li></ol>|
|**Process and carry forward budget**| > [!NOTE] <br> > This option is available only if the **Budget control** is enabled. <br><br> **Closing steps:** <ol><li> The remaining encumbrances in the general ledger 
and outstanding budget reservations for encumbrances are reversed. <li> Year-end closing entries are generated in the general ledger. <li> Budget adjustments are created to reduce the budget in the fiscal year
that is being closed. </li></ol> **Opening steps:** <ol><li> Closing entries are reversed. <li> Encumbrances are re-established in the general ledger. <li> Budget reservations for encumbrances are created for the
purchase orders that are being processed. <li> Budget adjustments are created in the new fiscal year to re-establish the budget register entries that were carried forward from the previous fiscal year. </li></ol>|

## Select purchase orders and run the purchase order year-end process

1. Click **General ledger** > **Periodic** > **Fiscal year close** > **Purchase order year-end process**.
2. Click **Retrieve purchase orders** in the lower pane to select purchase orders for the year-end process. This will open a query form where you can select purchase orders by criteria such as the date, date
range, vendor account, purchase order type, purchase order balance, or financial dimensions.
3. Click **OK** in the **Inquiry**.
4. The results of the query are displayed in the lower pane of the **Purchase order year-end process** page. Select the **Include** checkbox for each purchase order to include in the year-end processing.
Encumbrances for those purchase orders are reversed in the fiscal year that is ending, and the encumbered amounts will be available in the new fiscal year. Click **Include all** to select all of the purchase
orders in the list or click **Exclude all** to clear the selections.

> [!TIP]
> You can view the details of a purchase order by clicking **View purchase order**. You can also select **View subledger journal** to see the year-end closing and opening entries that will be generated for individual
> purchase orders.

5. In the **Year-end option** field, select how to process purchase order encumbrances.
6. If you chose the **Process and carry forward budget** year-end option, select an original budget code. This code is used for budget adjustments that are made in the closing fiscal year. The code that you choose
 must not have a workflow selected, because the year-end processing would stop for workflow approvals. 
7. Select a carry forward budget code, if you selected the **Process and carry forward budget** year-end option. This code is used for budget adjustments that are made in the new fiscal year. The code that you
select must not have a workflow selected, because the year-end processing would stop for workflow approvals.
8. Verify the default values in the **Calendar** and **Fiscal year** fields and make any changes. You can change the fiscal year value here, but you must use the **Ledger** form to change the selected fiscal
9. calendar.
10. You can click the calendar name to open the **Fiscal calendars** form, where you can view a description of the fiscal calendar, and the fiscal years that are included in the fiscal calendar.
11. Verify the default values for the **Closing** parameters fields and make any changes needed to the fields.
- The **Accounting date** field indicates the last day of the selected fiscal year. You cannot change this date.
- The **Type** field is typically set to **Operating** for a period that can be used to record accounting transactions. You can select **Closing** if you are using a closing period to separate the closing entries. 
- If you selected a type of **Closing**, select the closing period to use.

10. Verify the values for the **Opening parameters** fields. These fields can't be changed.
- The **Accounting date** field is the first day of the opening fiscal year.
- The **Period** field is the first period that has a type of **Operating** in the opening fiscal year. This type of period is used to record accounting transactions.

11. Click **Process** when you are ready to run the purchase order year-end process.
12. If any messages are displayed, make the necessary corrections, and then run the process again for the affected purchase orders.

> [!IMPORTANT]
> Verify the budget register entries that were created in the previous and current fiscal years to ensure the accuracy of the year-end encumbrance closing process. You can view the budget register entries on the
> **Budget register entries** page.

