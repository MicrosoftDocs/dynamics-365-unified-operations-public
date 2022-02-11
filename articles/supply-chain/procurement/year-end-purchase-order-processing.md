---
title: Process purchase orders at year end
description: This topic explains how to generate closing entries to the general ledger and against budget reservations at the end of each fiscal year. You can also create opening entries to correctly record the encumbrances and budget reservations when the new fiscal year starts.
author: Henrikan
ms.date: 02/11/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2022-02-01
---

# Process purchase orders at year end

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- What is in preview here? Do we need to enable something in feature management? -->

If you record encumbrances for purchase orders in the general ledger, which includes purchase orders for projects <!-- what includes these POs, the general ledger, the encumbrances, or the purchase orders? -->, you can generate closing entries to <!-- Is "generate ... to" the right phrasing? --> the general ledger and against budget reservations at the end of each fiscal year. At the start of the new fiscal year, you can create opening entries to correctly record the encumbrances and budget reservations. These entries help make sure that the reservations for purchase order encumbrances are correctly recorded on the year-end financial statements and in budget control.

For projects, the account that distributions are assigned to in the new fiscal year is the account that is defined on the **Purchase order year-end process** page in **General ledger**. It is not the account that is defined on the **Ledger posting setup** page in **Project management and accounting**.

If you are in the public sector and are using general budget reservations, see also [Finalize a general budget reservation (Public sector)](/dynamicsax-2012/appuser-itpro/finalize-a-general-budget-reservation-public-sector) and [Carry forward general budget reservation information to a new fiscal year (Public sector)](/dynamicsax-2012/appuser-itpro/carry-forward-general-budget-reservation-information-to-a-new-fiscal-year-public-sector).

In the case of a partially invoiced purchase order, only the amount that has not been invoiced is closed and then reopened in the next fiscal year.

Closing purchase order encumbrances is a separate process from closing a fiscal year, and is usually performed before a fiscal year is closed. For information about closing a fiscal year, see [Fiscal year closing checklist](/dynamicsax-2012/appuser-itpro/fiscal-year-closing-checklist).

> [!NOTE]
> French public sector entities can also create or update commitments in the new fiscal year. For more information, see [(FRA) About commitments (Public sector)](/dynamicsax-2012/appuser-itpro/fra-about-commitments-public-sector) and [(FRA) Process purchase order encumbrances and commitments at year end (Public sector)](/dynamicsax-2012/appuser-itpro/fra-process-purchase-order-encumbrances-and-commitments-at-year-end-public-sector).

## Prerequisites

Before you start this process, make sure that the following prerequisites have been set up. <!-- Which of the following sections are the prerequisites?-->

## Enable budget control

Budget control is often enabled when encumbrances are created for purchase orders. You do not have to enable budget control to use this process, but budget register entries are not created unless you do. The **Process and carry forward budget year-end** option also cannot be used unless budget control is enabled. For more information, see Set up budget control. <!-- Link missing. I suppose it will explain how to do the other things mentioned here, else descriptions are needed. -->

## Enable the encumbrance process

The encumbrance process must be enabled before encumbrances for purchase orders can be recorded in the general ledger, and before you can run the purchase order year-end process successfully. For more information, see Encumber purchase orders. <!-- Link missing. -->

## Set up posting definitions

Open the **Posting definitions** page and set up the following posting definitions in the *Purchasing* module, if they do not already exist:

- **Purchase order year end** – This posting definition is used to reverse encumbrances and outstanding budget reservations for purchase orders in the fiscal year that is ending, and to generate year-end closing entries in the general ledger.
- **Purchase order encumbrances** – This posting definition defines how encumbered amounts are recorded in the general ledger. It is also used in the new fiscal year to reverse year-end closing entries and to re-establish encumbrances in the general ledger.

For more information, see Set up posting definitions. <!-- Link missing. -->

## Assign posting definitions to transaction posting types

Use the **Transaction posting definitions** page to assign posting definitions to the transaction posting definitions that correspond to them. You also select the criteria that originating transactions must meet for a specific posting definition to be used.

Select the following transaction posting types in the Purchasing module, and then follow the steps in Assign posting definitions to transaction posting types:

- **Purchase order year-end close** – Select the posting definition that you created for purchase order year-end.
- **Purchase order** – Select the posting definition that is used for purchase order encumbrances.

## Year-end processing options

Select one of the following year-end processing options to close purchase order encumbrances in the fiscal year that is ending and to re-encumber them in the new fiscal year.  <!-- Where are these settings? -->

| Option | Closing and opening steps that occur for purchase order encumbrances |
|--- |--- |
| Process and do not carry forward budget – Closing steps | The following steps occur:<ol><li>The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed.</li><li>Year-end closing entries are generated in the general ledger.</li></ol> |
| Process and do not carry forward budget – Opening steps | The following steps occur:<ol><li>Closing entries are reversed.</li><li>Encumbrances are re-established in the general ledger.</li><li>Budget reservations for encumbrances are created for the purchase orders that are being processed.</li></ol> |
| Process and carry forward budget | This option is available only if budget control has been enabled. |
| Process and carry forward budget – Closing steps | The following steps occur:<ol><li>The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed.</li><li>Budget adjustments are created to reduce the budget in the fiscal year that is being closed.</li></ol> |
| Process and carry forward budget – Opening steps | The following steps occur:<ol><li>Closing entries are reversed.</li><li>Encumbrances are re-established in the general ledger.</li><li>Budget reservations for encumbrances are created for the purchase orders that are being processed.</li><li>Budget adjustments are created in the new fiscal year to re-establish the budget register entries that were carried forward from the previous fiscal year.</li></ol> |

## Select purchase orders and run the purchase order year-end process

1. Go to **General ledger \> Periodic \> Fiscal year close \> Purchase order year-end process**.

1. Select **Retrieve purchase orders** in the lower pane to select purchase orders for the year-end process. This opens a query where you can select purchase orders by criteria such as the date, date range, vendor account, purchase order type, purchase order balance, or financial dimensions.

1. Select **OK** on the **Inquiry** page.

1. The results of the query are displayed in the lower pane of the **Purchase order year-end process** page. Select the **Include** check box for each purchase order to include in the year-end processing. Encumbrances for those purchase orders will be reversed in the fiscal year that is ending, and the encumbered amounts will be made available in the new fiscal year. You can select **Include all** from the toolbar to select all of the purchase orders in the list, or select **Exclude all** to clear the selections.

    > [!TIP]
    > You can view the details of a purchase order by selecting **View purchase order**. Select **View subledger journal** <!-- I don't see this. Has it been removed? --> if you want to view the year-end closing and opening entries that will be generated for individual purchase orders.

1. In the **Year-end option** field, select how to process purchase order encumbrances. <!-- We should describe each of the options available here. --> 

1. If you set **Year-end option** to *Process and carry forward budget year-end*, select an **Original budget code**. This code is used for budget adjustments that are made in the closing fiscal year. The code that you select must not have a workflow selected, because the year-end processing would stop for workflow approvals. For more information, see Budget codes (page).<!-- Link missing. -->

1. If you set **Year-end option** to *Process and carry forward budget year-end*, select a **Carry forward budget code**. This code is used for budget adjustments that are made in the new fiscal year. The code that you select must not have a workflow selected, because the year-end processing would stop for workflow approvals.

1. Verify the default values in the **Calendar** and **Fiscal year** fields, and make any changes. You can change the fiscal year value here, but you must use the **Ledger** page to change the selected fiscal calendar.

    You can select the calendar name to open the **Fiscal calendars** page, where you can view a description of the fiscal calendar, and the fiscal years that are included in the fiscal calendar.

1. Verify the default values for the **Closing parameters** fields, and make any changes to the fields that can be changed.

    - The **Accounting date** field indicates the last day of the selected fiscal year. You cannot change this date.
    - The **Type** field is typically set to *Operating* for a period that can be used to record accounting transactions. You can select *Closing* if you are using a closing period to separate the closing entries. For information about how to create closing periods, see Key tasks: Fiscal calendars, fiscal years, and periods. <!-- Link missing. -->
    - If you selected a type of closing, select the closing period to use.

1. Verify the values for the **Opening parameters** fields. These fields cannot be changed.

    - The **Accounting date** field indicates the first day of the opening fiscal year.
    - The **Period** field indicates the first period that has a type of *Operating* in the opening fiscal year. This type of period is used to record accounting transactions.

1. Select **Process when you are ready** to run the purchase order year-end process.

1. If any messages are displayed, make the necessary corrections, and then run the process again for the affected purchase orders.

> [!IMPORTANT]
> Verify the budget register entries that were created in the previous and current fiscal years to help ensure the accuracy of the year-end encumbrance closing process.
