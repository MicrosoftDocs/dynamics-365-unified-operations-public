---
title: Call off and close rental contracts (preview)
description: Learn how to call off fleet items, receive returns, and close contracts with final invoicing using the best rate calculator.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Call off and close rental contracts (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

When a customer finishes using fleet items, the rental coordinator creates a call-off to stop rental charges. The operations staff receives the fleet item back at the fleet location, and you close the contract with a final invoice. On standard templates, closing includes the best rate calculation (BRC), which bills the customer for the period ladder that the actual rental duration earned.

## Call off fleet items

A call-off indicates that the customer no longer needs the fleet item and wants to return it. Creating a call-off stops the rental billing clock and initiates the return process.

To call off fleet items on a contract, follow these steps:

1. Open the rental contract.
1. On the Action Pane, on the **Rental** tab, in the **Call-offs** group, select **Call-offs**. To call off a single line, select the line, and then select **Call-offs** > **Create** on the lines toolbar.
1. On the **Fleet items** tab, select the lines to call off. Use **Select** for one line, or **Select all**.
1. Set the **Call-off date and time**, which is when the customer stops using the fleet item. It defaults to the current date and time, and the system uses it for final billing calculations. Optionally, enter a **Contact ID** and a **Note line**.
1. Set **Fleet item movement action**, which decides whether the call-off also creates the inbound fleet item movement for the return.
1. On the **Attachments** tab, select the attachments that come back with the fleet item. An attachment that you clear is detached from the line and stays on rent as its own line.
1. Select **OK**. Each called-off line gets the line status *Call-offs*. The system sets its call-off date and invoice-until date to the call-off date, so the line is invoiced up to that date.

The created call-off has a status of *Active*. You can cancel a call-off if the customer changes their mind before the fleet item is returned. Select **Cancel selected call-off** on the Action Pane, or **Call-offs** > **Cancel** for a line, and then select a **Reason code**, which is required. Canceled call-offs have a status of *Canceled*, the line returns to *Active* rental, and an open inbound fleet item movement for the fleet item isn't canceled with the call-off.

If you create an inbound fleet item movement, the contract appears in the **Called off, not returned contracts** tile on the Rental management workspace. This tile opens contract records.

> [!NOTE]
> You can call off individual lines on a contract without calling off the entire contract. This condition is common when customers no longer need some fleet items but want to keep other fleet items on rent.

### Create the return fleet item movement with the call-off

The call-off can create the inbound fleet item movement that brings the fleet item back.

- On the rental template, **Fleet item movement automation on call-off** sets the default: *None* creates no fleet item movement, *Create* creates an inbound fleet item movement that has the status *Request*, and *Create and schedule* creates and schedules it. The fleet item movement gets the template's **Fleet item movement reason for call-off**.
- In the call-off dialog, **Fleet item movement action** starts from that default, and you can change it for this call-off to *None*, *Create*, or *Create and schedule*.
- When the action isn't *None*, each fleet item needs a completed outbound fleet item movement on the contract, and the selected fleet items must be at one location. The dialog lists only the fleet items at the location of the first fleet item that you select, because one inbound fleet item movement collects from one location.
- The **Fleet item movement** group shows the reason code and the from and to locations. You can change **To**.
- If the fleet item movement can't be created, **Fleet item movement action** is set to *None*. Create the fleet item movement afterwards with **Create fleet item movement** on the rental contract.

## Receive returned fleet items

<!--
After the fleet item is called off, the operations staff receives it by using the inbound fleet item movement, on the desktop or in the Dynamics 365 Supply Chain Management mobile app. A fleet item movement that the call-off creates appears in the app after it's scheduled. Learn more about the receiving process in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md), and about the app in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md).
-->

After the fleet item is called off, the operations staff receives it by using the inbound fleet item movement. Learn more about the receiving process in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).

A contract also appears in the **Called off, not invoiced contracts** tile on the workspace as soon as a line is called off, whether or not the fleet items are received. It leaves the tile when the called-off lines are invoiced and closed. This tile is a workspace tile, not a contract status.

## Close a contract with the closing wizard

After the operations staff receives all fleet items and the final billing period is complete, use the contract closing wizard to review and finalize charges.

To close a contract, follow these steps:

1. Open the rental contract.
1. Select **Contract closing** on the Action Pane to launch the contract closing wizard.
1. On the **Select contract lines** step, choose the lines to include in the final invoice. You can select any line that isn't already closed, but the lines you select must all have the same line status and be closable together:
        - You can include lines that are still *Active* when their estimated return dates match, and when the template doesn't use calendar-based invoicing.
    - Lines that are called off must share one call-off date and time.

        On templates that use the best rate calculation, select **Prorate calculation** to calculate the closing amount from each line's active price line, prorated per day, instead of from the daily, weekly, and monthly rates.
1. On the **Review contract closing information** step, review the amounts in the **Fleet item** group. To see the best rate calculation (BRC) for a fleet item, select it and then select **Details**, where **Modify periods** lets you correct the period split. The BRC determines the optimal rate based on the actual rental duration. For example, if a customer rented a fleet item for 20 days at a daily rate, the BRC might determine that a weekly and daily combination over the same period results in a lower total cost for the customer. Templates that use calendar-based invoicing or hourly billing are totaled by their own method instead, and the best rate controls are disabled for hourly billing.
1. Review any additional charges:
    - **Fuel charges** – Created when the inbound fleet item movement is received, if **Fuel calculation** or **Diesel calculation** is enabled on the contract and the rental template has a charge line with fee type *Fuel*. The amount of fuel added, recorded in **Fuel level** on the inbound movement, is the quantity. It's priced at the contract's **Fuel price** or **Diesel price**, according to the fuel type of the fleet item model. The rental template supplies the contract's default calculation settings and prices.
    - **Overtime hours** – Based on actual usage hours compared to the shift agreement (single shift, double shift, or continuous).
    - **Damage charges** – When you record damage on a fleet item movement for the contract, a once charge is added to the contract line of the fleet item. The charge is priced from the rental template line that has **Add damage charge to contract** selected. On the invoice, a charge line that has **Damage** selected lists the damage recorded for the fleet item on this contract.
1. Review the **sales tax** on the same **Review contract closing information** step, and record the payment. The step shows the amount to be invoiced, the sales tax on it, and the resulting gross amount, so the figure you take payment against is the figure that the customer is invoiced.
1. Adjust charges if needed. Select the optional final charges to add in **Select final charges** on the **Select contract lines** step. You can also add a one-time charge with **Add Line - Once charge**, or correct the period split of a fleet item with **Details** and **Modify periods**.
1. On the **Finalize** step, choose how to complete the closing. **Generate and post invoice**, **Print invoice**, and **Remove fleet item from contract** are selected by default. Lines are closed and their fleet items removed only when **Generate and post invoice** and **Remove fleet item from contract** are both selected. To create the invoice schedule without posting it, clear **Generate and post invoice** and select **Create invoice schedule only**.
1. Select **Finish**. By using **Generate and post invoice**, you create and post the invoice schedule in the same run. By using **Create invoice schedule only**, you create only the invoice schedule, and you post it separately from the invoice schedules page.

> [!NOTE]
> Resolve all open invoice schedules on the contract before you start the closing wizard.

## Best rate calculation, end to end

The best rate calculation (BRC) ensures a customer is billed for the period ladder they earn, rather than for the period the contract starts on. It runs inside the closing wizard on standard templates, and you can also run it on demand while the fleet item is still out.

### How the calculation works

The calculation takes the rental span, from the start date to the last day you specify, and assigns it to whole months, then whole weeks, then remaining days, using the rates on the contract line. It then promotes the smaller periods upward, but only when the larger period isn't more expensive:

- When the leftover days cost at least as much as one more week, the days become a week.
- When the weeks cost at least as much as one month, the weeks become a month.

Because a period is promoted only when promotion doesn't raise the charge, the result is never worse for the customer than the ladder the contract started on. The same run also derives the start and end service meter unit readings and the hours allowed, so overtime is measured on the same basis as the rate.

### Example: 20 days on a daily rate

A customer takes a fleet item on a daily rate and keeps it for 20 days. The contract line carries the following rates, with a 7-day week and a 28-day month.

| Rate type | Rate |
|---|---|
| Daily | $100 |
| Weekly | $650 |
| Monthly (28-day) | $2,000 |

Billed by the day, 20 days is $2,000. The best rate calculation assigns the span to 2 weeks plus 6 days:

- The 6 leftover days are worth $600, which is less than another week at $650, so they stay as days.
- The 2 weeks are worth $1,300, which is less than a month at $2,000, so they stay as weeks.

The customer is billed 2 weeks plus 6 days, which is $1,900, or $100 less than the daily ladder. If the leftover days were worth $700, the calculation would promote them to a third week.

### Run the calculation from the contract

You don't have to wait for the closing wizard.

- Select **Best rate calculation** on the contract header to create a journal with one line per open contract line and calculate them all. Use **Modify periods** to correct the months, weeks, days, or SMU overtime on a line before anything is committed. The header totals update as you edit.
- Select **Approve initial** to write the recalculated prices back to the contract while the contract stays open and the lines stay active. Use it to true up a long rental mid-term.
- Select **Approve final** to write the prices back, set the line status to *Best rate calculation*, and close the contract. This action is available on contracts only, not on quotations.
- Select a contract line, and then select **Calculator** > **Best rate calculation** on the lines toolbar to recalculate one line. You're prompted for the last day, and the line is always confirmed as final. Use this action when one fleet item comes off a multi-line contract while the rest stays out. The action is available while the line has no open or ordered invoice schedule line.

### Trace how the invoice amount was calculated

Approved journals are kept, and journals that are never approved are deleted. The **Best rate calculation journal** page, which you open with **Journal** on the **Best rate calculation** page, holds exactly the set of decisions that were committed. Each journal line shows the period and price before the run next to the recalculated period and price, and the journal header reconciles the recalculated total against what is already invoiced and paid.

Each price line also stores a **Best rate calculation status** (blank, *Closed*, or *Created*) that shows whether the line was untouched, closed by a best rate calculation, or created by one. Together, the journal and this status let you show a customer which split and which meter readings produced the invoice, including long after the contract closed.

### See the sales tax on a rate estimate

The journal header prices the recalculation with tax, not only net. It shows the amount still to be invoiced with the sales tax on that amount. It also shows the total sales tax across the journal with the resulting gross amount, so a recalculation that changes the period ladder shows what the customer is asked to pay. Select **Details** next to **Sales tax** to open the sales tax breakdown for the journal.

The system calculates the tax from the tax groups on the contract, at the current date. Learn more in [How tax groups are determined](understand-rental-financial-integration.md#how-tax-groups-are-determined).

### Reverse a per-line calculation

Select a contract line, and then select **Calculator** > **Last calculation** on the lines toolbar to review the last per-line calculation and reverse it. It's available only while the line has no open or ordered invoice schedule line. The reversal deletes the price line that the calculation created, restores the previous price line and the previous line status, and marks the meter reading as unprocessed. Use it when the calculation used the wrong last day or the wrong meter reading, before the amounts are invoiced. It doesn't reverse amounts that are already posted, and it can't reach a calculation that was made from the header journal.

### Charges that close with the rental

The closing figures also include the charges identified during the return:

- **Overtime hours** – If the customer used the fleet item for more hours than the shift agreement allowed, the extra hours are charged at the overtime rate. For example, if 40 hours were allowed on a weekly rental and 51 hours were put on the fleet item, 11 hours are overtime. Learn more in [Overtime at closing](#overtime-at-closing).
- **Fuel charges** – The amount of fuel added, recorded in **Fuel level** on the received inbound fleet item movement, charged at the contract's **Fuel price** or **Diesel price**. The rental template supplies the default prices and **Fuel calculation** or **Diesel calculation** settings; the contract's settings determine whether the charge applies.
- **Damage charges** – Once charges that are added to the contract line of the fleet item when damage is recorded on a fleet item movement for the contract. They're priced from the rental template line that has **Add damage charge to contract** selected.

> [!TIP]
> Review the proposed split before you approve it. The calculation is a proposal that **Modify periods** lets you correct, but a final approval closes the contract.

### Overtime at closing

The best rate calculation measures overtime on the same basis as the rate. Usage runs up to the meter reading recorded when the fleet item is received back on the inbound fleet item movement, or, if the fleet item hasn't been received, to the latest reading recorded during the contract. The hours allowed come from the hours allowance on the daily, weekly, and monthly prices, multiplied by the days, weeks, and months in the calculation, less any stand-down hours. Usage above the hours allowed is overtime, charged at the overtime rate, and the final invoice includes the overtime that hasn't been invoiced yet.

The **Overtime billing method** on the contract line decides how much overtime is left for the closing:

- *End of contract* – The closing bills the overtime for the whole rental. These lines have no approval step, so the overtime goes straight onto the final invoice.
- *Period* – Overtime was billed for each invoice period during the rental, so the closing bills only the rest.
- *Last reading* – Overtime was billed up to the latest reading in each invoice period, so the closing bills the usage after the last billed reading.

Learn more in [Invoice rental contracts](invoice-rental-contracts.md#handle-overtime-charges).

## Remove a fleet item from a contract line

Use **Remove fleet item** to take the fleet items off a contract line and close the line at a date and time that you choose, without a call-off. It's available while the contract is *Active*, the line isn't *Closed*, and the line has an active fleet item.

Before you start, post or delete every invoice schedule that isn't invoiced for the line, for an attachment linked to it, or for a charge line under it.

To remove the fleet items from a line, follow these steps:

1. Open the rental contract, and select the line in the **Lines** grid.
1. Select **Fleet item** > **Remove fleet item** on the lines toolbar.
1. In **Remove fleet item and attachments**, check **Invoiced until**, and set **Close date/time**. It can't be earlier than **Invoiced until** or the invoice-from date of the line.
1. Select **OK**.

The system removes every fleet item on the line and on its attached lines, and closes those lines at that date and time. A fleet item that's on no other active contract line returns to the agreement status *Available*, and its physical status comes from the inbound fleet item movement when you receive it.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md)
