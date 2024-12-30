---
title: Purchase order year-end close
description: Learn about the required steps for running the purchase order year-end process.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 10/15/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 09/25/2024

---

# Purchase order year-end close

[!include [banner](../includes/banner.md)]

This article describes the required steps and setup for running the purchase order year-end process.

The purchase order year-end process lets organizations that use the **Budget** module transfer open purchase orders during the year-end closing. During this transfer, the closing year budget is released (or reversed) in budget registries, and new lines are created in the next open period. The accounting dates and financial distribution dates on the purchase order are updated.

If you record encumbrances for purchase orders in the general ledger, including purchase orders for projects, you can generate closing entries in the general ledger and against budget reservations at the end of each fiscal year. At the start of the new fiscal year, you can create opening entries to correctly record the encumbrances and budget reservations. These entries ensure that the reservations for purchase order encumbrances are correctly recorded on the year-end financial statements and in budget control. Learn more in [About purchase order encumbrances](/dynamicsax-2012/appuser-itpro/about-purchase-order-encumbrances).

For projects, the account that distributions are assigned to in the new fiscal year is the account that is defined on the **Purchase order year-end process** page in the **General ledger** module. It isn't the account that is defined on the **Ledger posting setup** page in the **Project management and accounting** module.

For public sector organizations that use general budget reservations, go to [Finalize a general budget reservation (Public sector)](/dynamicsax-2012/appuser-itpro/finalize-a-general-budget-reservation-public-sector) and [Carry forward general budget reservation information to a new fiscal year (Public sector)](/dynamicsax-2012/appuser-itpro/carry-forward-general-budget-reservation-information-to-a-new-fiscal-year-public-sector).

> [!NOTE]
> General budget reservations are available only if the **Public Sector** configuration key is enabled.

In the case of a partially invoiced purchase order, only the amount that hasn't been invoiced is closed and then reopened in the next fiscal year.

The closing of purchase order encumbrances and the closing of a fiscal year are separate processes. Purchase order encumbrances are usually closed before a fiscal year is closed. Learn more about how to close a fiscal year in [Year-end close](../general-ledger/year-end-close.md).

> [!NOTE]
> (FRA) French public sector entities can also create or update commitments in the new fiscal year. Learn more in [(FRA) About commitments (Public sector)](/dynamicsax-2012/appuser-itpro/fra-about-commitments-public-sector) and [(FRA) Process purchase order encumbrances and commitments at year end (Public sector)](/dynamicsax-2012/appuser-itpro/fra-process-purchase-order-encumbrances-and-commitments-at-year-end-public-sector).

## Prerequisites

Before you start the purchase order year-end process, the following prerequisites must be set up.

### Enable budget control

Budget control is often enabled when encumbrances are created for purchase orders. You don't have to enable budget control to use this process. However, budget register entries are created only if budget control is enabled.

The **Process and carry forward budget** year-end option can be used only if budget control is enabled. Learn more in [Budget control overview](budget-control-overview-configuration.md).

### Enable the encumbrance process

The encumbrance process must be enabled before encumbrances for purchase orders can be recorded in the general ledger, and before you can successfully run the purchase order year-end process. For more information, see [Encumber purchase orders](/dynamicsax-2012/appuser-itpro/encumber-purchase-orders).

### Set up posting definitions

On the **Posting definitions** page, set up the following posting definitions in the **Purchasing** module, as required:

- **Purchase order year end** – This posting definition is used to reverse encumbrances and outstanding budget reservations for purchase orders in the fiscal year that is ending, and to generate year-end closing entries in the general ledger.
- **Purchase order encumbrances** – This posting definition defines how encumbered amounts are recorded in the general ledger. It's also used in the new fiscal year to reverse year-end closing entries and reestablish encumbrances in the general ledger.

Learn more in [Posting definitions](../general-ledger/posting-definitions.md).

### Assign posting definitions to transaction posting types

Use the **Transaction posting definitions** page to assign posting definitions to the transaction posting definitions that correspond to them. You can also define the criteria that originating transactions must meet before a specific posting definition can be used.

Select the following transaction posting types in the **Purchasing** module, and then follow the steps on the [Posting definitions](../general-ledger/posting-definitions.md) page:

- **Purchase order year-end close** – Select the posting definition that was created for purchase order year end.
- **Purchase order** – Select the posting definition that is used for purchase order encumbrances.

## Year-end processing options

Select one of the following year-end processing options to close purchase order encumbrances in the fiscal year that is ending, and to re-encumber them in the new fiscal year.

> [!NOTE]
> The year-end processing option that you select is used for encumbrances on all the selected purchase orders. If the **Public Sector** configuration key is enabled, you can override your selection and substitute a different year-end processing option for specific funds that you select on the **Funds** page.

| Option | Closing and opening steps that occur for purchase order encumbrances |
|---|---|
| Process and do not carry forward budget | <p><strong>Closing steps:</strong></p><ol><li>The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed.</li><li> Year-end closing entries are generated in the general ledger.</li></ol><p><strong>Opening steps:</strong></p><ol><li>Closing entries are reversed.</li><li> Encumbrances are reestablished in the general ledger.</li><li>Budget reservations for encumbrances are created for the purchase orders that are being processed.</li></ol> |
| Process and carry forward budget | <p><strong>Note:</strong> This option is available only if budget control is enabled.</p><p><strong>Closing steps:</strong></p><ol><li>The remaining encumbrances in the general ledger and outstanding budget reservations for encumbrances are reversed.</li><li>Year-end closing entries are generated in the general ledger.</li><li>Budget adjustments are created to reduce the budget in the fiscal year that is being closed.</li></ol><p><strong>Opening steps:</strong></p><ol><li>Closing entries are reversed.</li><li>Encumbrances are reestablished in the general ledger.</li><li>Budget reservations for encumbrances are created for the purchase orders that are being processed.</li><li>Budget adjustments are created in the new fiscal year to reestablish the budget register entries that were carried forward from the previous fiscal year.</li></ol> |

## Prepare for a purchase order year-end process

> [!NOTE]
> Before you can run the purchase order year-end process, the **Include carry forward amount** parameter must be enabled on the **Budget funds available** tab in the budget control configuration. 

To enable purchase orders to be retrieved during the purchase order year-end process, the following conditions should be met:

- Purchase orders have a **Confirmed** state, or they have reserved budget values (encumbrance).
- A purchase order is open or partially invoiced.
- The purchase order approval workflow is completed.
- No draft invoices exist for the purchase order. If a draft invoice exists, it must be deleted or posted before you start the year-end process.
- The purchasing status is **Backorder** or **Received**.
- The last accounting event for the purchase order is in the fiscal year that is selected during the purchase order year end. For example, if **2023** is selected, the accounting date of the last accounting event must be in 2023. Otherwise, the purchase order is excluded.
- Both the current fiscal year period and the next fiscal year period are open.

## Select purchase orders and run the purchase order year-end process

1. Go to **General ledger** \> **Periodic** \> **Fiscal year close** \> **Purchase order year-end process**.
2. In the lower pane, select **Retrieve purchase orders**.
3. In the query dialog box that appears, define criteria for the purchase orders that you want to include in the year-end processing. Criteria include the date, date range, vendor account, purchase order type, purchase order balance, and financial dimensions. When you're finished, select **OK**.

> [!NOTE]
> If the feature **Enable non-retriavable purchase orders form for purchase order year-end process** is enabled, users can validate the reason why specific purchase order is not available for a POYE processing in the **Non-retriavable purchase orders** form.
> The following conditions are checked and should be met for the order to be available to be processed during purchase order year-end process:
> - Purchase order status should be Confirmed but not fully invoiced (no draft invoices should exist as well).
> - Approval status must be Approved.
> - Accounting date should be in the fiscal year for which POYE is run.
> - Last accouting event date of the PO should be in the year for which POYE is run.
> - PO should be budget controlled or have ecumbrances enabled.\
> ![Non-retriavable purchase orders](.budgeting/media/Non-retrievable-purchase-orders.png)

4. On the **Purchase order year-end process** page, the lower pane shows the results of the query. To include only specific purchase orders from the query results in the year-end processing, select the **Include** checkbox for each one. To include all the purchase orders from the query results, select **Include all**. To clear the selection of all purchase orders, select **Exclude all**. Encumbrances for the selected purchase orders are reversed in the fiscal year that is ending. The encumbered amounts will then be available in the new fiscal year.

    > [!TIP]
    > You can view the details of a purchase order by selecting **View purchase order**. You can also select **View subledger journal** to view the year-end closing and opening entries that will be generated for individual purchase orders.

5. In the **Year-end option** field, select how purchase order encumbrances should be processed.
6. If you selected the **Process and carry forward budget** year-end option, select an original budget code. This code is used for budget adjustments that are made in the closing fiscal year. No workflow must be selected for the selected code. Otherwise, the year-end processing will stop for workflow approvals.
7. If you selected the **Process and carry forward budget** year-end option, select a carry-forward budget code. This code is used for budget adjustments that are made in the new fiscal year. No workflow must be selected for the selected code. Otherwise, the year-end processing will stop for workflow approvals.
8. Review the default values in the **Calendar** and **Fiscal year** fields. You can change the selected fiscal year directly on this page. However, to change the selected fiscal calendar, you must use the **Ledger** page.
9. You can select the calendar name to open the **Fiscal calendars** page. There, you can view a description of the fiscal calendar. You can also view the fiscal years that are included in the fiscal calendar.
10. Review the default values of the **Closing parameters** fields, and make any changes that are required.

    - The **Accounting date** field specifies the last day of the selected fiscal year. You can't change the value.
    - The **Type** field is typically set to **Operating** for a period that can be used to record accounting transactions. If you're using a closing period to separate the closing entries, you can select **Closing**.
    - If you selected **Closing** as the type, select the closing period to use.

11. Review the values of the **Opening parameters** fields. These values can't be changed.

    - The **Accounting date** field specifies the first day of the opening fiscal year.
    - The **Period** field specifies the first period that has a type of **Operating** in the opening fiscal year. This type of period is used to record accounting transactions.

12. When you're ready to run the purchase order year-end process, select **Process**.
13. If you receive any messages, make the required corrections. Then run the process again for the affected purchase orders.

> [!IMPORTANT]
> Review the budget register entries that were created in the previous and current fiscal years to ensure the accuracy of the year-end encumbrance closing process. You can view the budget register entries on the **Budget register entries** page.
