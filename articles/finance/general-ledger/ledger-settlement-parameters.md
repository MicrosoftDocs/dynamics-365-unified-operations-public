---
title: Ledger settlement parameters
description: Learn about key ledger settlement parameters in Dynamics 365 Finance.
author: courtneicokerdickens-collab
ms.author: courtneic
ms.date: 11/04/2026
ms.topic: concept-article
ms.reviewer: twheeloc
ai-usage: ai-assisted
---

# Ledger settlement parameters

This article describes the ledger settlement parameters in Dynamics 365 Finance, including parameter relationships, expected system behavior, and considerations that might be relevant when evaluating configuration choices.

## Recommendation and prerequisites

Review and enable the ledger settlement parameters that align with your business requirements and intended use of the functionality.

> [!IMPORTANT]
> Validate all configuration changes in a UAT environment before enabling them in production.
> **Permanent configuration change** - Enabling **Partial ledger settlements** is irreversible. Once enabled, it can't be disabled or rolled back.
>
> Enabling **Partial ledger settlements** also permanently enables **Enable advanced awareness options** and **Enable post currency realized gains/losses for ledger settlements**.
None of these three settings can be disabled after **Partial ledger settlements** is enabled.
>
> Enabling this feature also migrates settlement data to new tables. Don't enable **Partial ledger settlements** in production until the configuration is validated in UAT and the appropriate business approval is obtained.

To view the parameters, go to **General ledger** > **Ledger setup** > **General ledger parameters** > **Ledger settlements**.

| Parameter | Required options |
| --- | --- |
| **Enable ledger settlements** | None |
| **Enable advanced awareness options** | **Enable ledger settlements** |
| **Enable post currency realized gains/losses for ledger settlements** | **Enable advanced awareness options** |
| **Enable process automation for ledger settlement** | **Enable advanced awareness options** |
| **Partial ledger settlements** | Enable advanced awareness options and **Enable post currency realized gains/losses for ledger settlements** |
| **Subledger to ledger auto settlement** | **Partial ledger settlements** and its prerequisites |

Once the **Enable advanced awareness options** parameter is enabled, you can enable **Process automation** and **Realized gains/losses** independently based on your business requirements.

**Process automation** is optional and isn't required to use either **Partial ledger settlements** or **Subledger to ledger auto settlement**.


:::image type="content" source="media/ledger-settlement-parameters/advanced-awareness-parameters.png" alt-text="Screenshot of Ledger settlements enabled, with all advanced awareness options parameters set to No.":::


:::image type="content" source="media/ledger-settlement-parameters/ledger-settlement-parameters-accounts-list.png" alt-text="Screenshot of Ledger settlements parameters with advanced awareness, post currency realized gains, and partial settlements set to Yes, and process automation set to No.":::

### Enable ledger settlements

When you enable this feature, you can match and settle eligible ledger debit and credit transactions. You can also reverse existing ledger settlements from the **Ledger settlements** page.  

Select the main accounts that are eligible for ledger settlement in **Ledger settlement accounts**. The account list is maintained at the chart of accounts level and is shared across legal entities that use the same chart of accounts.  

Transactions from these accounts become available for ledger settlement.


### Enable advanced awareness options

When you enable this feature, it connects ledger settlement with year-end close and provides the foundation for other advanced ledger settlement options.  

- **Account and date restrictions** - Manual settlement requires one main account and a date range within one fiscal year. You can't settle transactions across main accounts or fiscal years.  
- **Year-end balances** - For accounts configured for ledger settlement, settled amounts are excluded from the next year's opening balances. Unsettled amounts are carried forward.
- **Detailed carryforward** - The account-level **Keep detail during year-end close** option creates separate opening transactions for unsettled items instead of summarized balances. It's available for **Balance sheet**, **Asset**, and **Liability** account types.  
- **Close and reversal restrictions** - You can't settle or unsettle transactions in a fiscal year for which year-end close has run. You can't reverse year-end close or rerun it with existing entries deleted while its opening transactions are settled in the following year.  

Before enabling:

- Complete marked settlements, because activation clears outstanding marks.
- Review existing cross-year settlements and resolve them before the affected year-end close.
- Plan activation before the first close or after the final close for that fiscal year. Don't enable it between repeated closes.
- This option isn't available with the public sector year-end close process.  

Before you enable partial ledger settlements, you can disable advanced awareness. However, disabling advanced awareness isn't recommended because it can affect period-end close.

### Enable post currency realized gains and losses for ledger settlements

When you enable this parameter, settlement calculates and posts realized exchange gains or losses when accounting or reporting currency amounts differ.

**Before partial ledger settlements**, marked transactions net to zero by using the settlement basis:

| Marked transactions | Required zero balance |
| --- | --- |
| Same transaction currency | Transaction currency |
| Different transaction currencies | Accounting currency |

Other currency balances can differ. The realized gain or loss posting adjusts eligible accounting or reporting currency differences. Without appropriate adjustments, out-of-balance settlements can prevent year-end close.

Enabling this parameter by itself doesn't generate adjustments for every account. Set **Calculate realized gains and losses** to **Yes** for each applicable settlement account, configure the gain or loss posting accounts. Define the **Ledger settlements** number sequence. Reversing a settlement also reverses its associated realized gain or loss voucher.

### Enable process automation for ledger settlement

When you enable this parameter, you can schedule settlement by using configured accounts, matching criteria, and processing order. Enabling the parameter doesn't create a schedule. To create a schedule, configure a **Ledger settlement** series under **Process automations**.

The matching rules require one debit and one credit with equal accounting currency amounts, the same main account, and the same posting layer. Optional criteria include dates, posting types, financial dimensions, and financial tags. Enabling **Partial ledger settlements** doesn't enable partial or one-to-many matching for scheduled automation.

Automation considers transactions from the start of the current year through its run date and skips transactions that you marked manually. Schedule the final automation run before year-end to include any remaining transactions for the year.

This parameter is optional and can be turned off after **Partial ledger settlements** are enabled.

### Partial ledger settlements

Changes settlement from clearing an entire balanced selection to matching individual debit and credit transaction pairs.

- **Unequal totals are allowed** - Marked debits and credits no longer need to net to zero before settlement.
- **Pairwise processing** - Each settlement links one debit and one credit. Processing continues while eligible amounts remain on both sides; unmatched amounts stay open.
- **Repeated settlement** - A transaction can participate in multiple settlements until its remaining balance is cleared.
- **Balance tracking** - The page shows a **Partially settled** status, remaining amounts in transaction, accounting, and reporting currencies, and settlement history.
- **Reversals** - Reverse individual settlements through **Ledger settlements history**.

For example, a debit of 12,000 can be settled against three credits of 1,000 each. The credits are fully settled, and the debit retains an open balance of 9,000. Year-end close carries the remaining amount forward; subsequent settlement uses the new year's opening transaction, not a cross-year match.

A zero total alone doesn't guarantee full settlement. Eligible debit-credit pairs are still required, and currency differences or pairwise processing can leave residual amounts. Review remaining balances in addition to the selection totals.

### Updated enablement dialog

Review all information in **Enable partial ledger settlements** and its linked documentation before proceeding. 

Before confirming, change all three required acknowledgments to **Yes** to confirm that:

1. Partial ledger settlements can't be disabled or reversed after activation.
1. The two prerequisite parameters are also permanently enabled and can't be disabled.
1. You reviewed the documentation and tested the setting in a non-production environment.

Enter **ENABLE** in the **Confirmation** field, and select **OK** only after full UAT validation and business approval. This change is permanent, not a trial setting.

UAT validation should include partial and repeated settlements, multicurrency residuals, realized gain or loss postings, reversals, year-end carryforward, and downstream reconciliation. Include validation of any automation options you plan to use.


:::image type="content" source="media/ledger-settlement-parameters/enable-partial-ledger-settlements.png" alt-text="Screenshot of the Enable partial ledger settlements dialog with permanence warnings, acknowledgment toggles, and a Confirmation field.":::

### Subledger to ledger auto settlement

Automatically settles the corresponding AR and AP ledger entries when customer or vendor transactions are settled in the subledger. Reversing the subledger settlement also reverses the corresponding ledger settlement.

- **No historical backfill** - Ledger entries aren't automatically settled when the corresponding subledger settlements occurred before the feature was enabled.
- **AR/AP scope** - It doesn't automatically settle other subledger accounts.
- **Account setup** - AR and AP accounts don't need to be listed in **Ledger settlement accounts** for automatic settlement. Add them if you need to view or manually settle your transactions on the **Ledger settlements** page.
- **Read-only in ledger modules** - Any ledger settlements created by this feature are read-only in ledger modules. You can't reverse or modify them in ledger modules. To reverse them, you must reverse the corresponding original subledger settlements.

This feature is triggered by subledger settlement, not by a process automation schedule. You can turn it on or off without changing the permanent partial-settlement configuration.

## References

- [Ledger settlements](ledger-settlements.md)
- [Awareness between ledger settlement and year-end close](awareness-between-ledger-settlement-year-end-close.md)
- [Automate ledger settlements](auto-settle.md)
- [Partial ledger settlements and subledger to ledger auto settlement](ledger-settlements-partial.md)
