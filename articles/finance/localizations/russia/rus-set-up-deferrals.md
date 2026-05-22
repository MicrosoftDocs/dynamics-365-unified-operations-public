---
title: Set up deferrals (Russia)
description: Learn how to set up deferrals for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 05/12/2026
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-06-28
---

# Set up deferrals (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to set up deferrals for Russia in Microsoft Dynamics 365 Finance.

Deferrals are expense types that are stored differently in general accounting principles and tax accounting principles. To use the deferral functionality, you must complete the following setup:

- [Write-off methods](#write-off-methods)
- [Value models](#create-value-models)
- [Posting profiles](#post-profiles)
- [Sequence of calculation](#create-a-sequence-of-calculation)
- [Deferrals groups](#create-deferrals-groups)
- [General ledger parameters](#set-up-general-ledger-parameters)
- [Deferrals](#create-and-configure-deferrals)

## Write-off methods

To create write-off methods for deferred expenses, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals setup** \> **Writing off methods**.
1. On the Action Pane, select **New** to create a write-off method for deferred expenses.

    The following table describes the fields on the **Writing off methods** page.

    | Field | Description |
    |---|---|
    | Writing off method | Enter the code for the write-off method. |
    | Name | Enter a description of the write-off method. |
    | Type | Select the type of write-off: **Linear** – Evenly divide the write-off amount across all intervals in the defined period. **Manual** – Manually enter either a percentage of the total or the amount to write off in each period, depending on the calculation type that you select in the **Calculation type** field. On the **Manual schedules** page, you can set up a different percentage for each write-off period. On the **Writing off sum** page, you can set up a different amount for each write-off period. **Linear with factor** – Multiply the calculated result by a calculated factor. |
    | Writing off period | Select the write-off period for the deferred expense: Month, Quarter, Half-Yearly, Years |
    | Calculation period | Select the calculation period for the deferred expense: **Month** – The deferrals write-off calculation is done proportionately over the number of months in the given period. **Day** – The deferrals write-off calculation is done proportionately over the number of days in the given period. This option lets you calculate the deferred expense write-off amount for an incomplete reporting period, based on the number of calendar days in the period. **Period** – The calculation is done proportionately for the number of periods that are defined in the **Writing off period** field. |
    | Calculation type | If you selected **Manual** in the **Type** field, select the calculation type for the manual write-off: **Percent** – A percentage of the total is written off in each period. You manually enter this percentage on the **Manual schedules** page. **Amount** – An amount is written off. On the **Writing off sum** page, you can set up a separate amount for each write-off period. |
    | Round-off | Enter the round-off value for the deferred expense write-off amount. |

1. If you selected **Manual** in the **Type** field and **Amount** in the **Calculation type** field, on the Action Pane, select **Manual schedules** to create write-off schedules.

:::image type="content" source="../media/rus-set-up-deferral-01.png" alt-text="Screenshot of the Writing off methods page.":::

## Create value models

To create value models, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals setup** \> **Value models**.
1. On the Action Pane, select **New** to create value models for deferrals accounting.

    The following table describes the fields on the **Value models** page.

    | Field         | Description                                               |
    |---------------|-----------------------------------------------------------|
    | Model number  | Enter the deferrals model to associate with the deferral. |
    | Name          | Enter a name for value model.                             |
    | Posting layer | Select a posting layer for the value model.               |

1. On the Action Pane, select **Deferrals groups** to set up deferrals groups that are related to the selected value model.

:::image type="content" source="../media/rus-set-up-deferral-02.png" alt-text="Screenshot of the Value models page.":::

## Post profiles

To post profiles, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals setup** \> **Posting profiles**.
1. On the Action Pane, select **New** to create posting profiles for deferred expenses.

    The following table describes the fields on the **Deferrals posting profiles** page.

    | Field | Description |
    |---|---|
    | Posting profile | Enter a name for the posting profile. |
    | Description | Enter a description of the posting profile. |
    | Writing off | Select this option to set up ledger accounts that are used to write off the value of the asset. |
    | Disposal | Select this option to set up ledger accounts that are used to dispose of the asset. |
    | Receipt | Select this option to set up ledger accounts that are used to post receipt transactions for deferrals. |
    | Groupings | Select the grouping method for the deferred expense profile: **All** – The **Main account** and **Offset account** fields are applicable to all deferrals. **Value model** – The **Main account** and **Offset account** fields are applicable to the value model that is selected in the **Account/Group number** field. **Group** – The **Main account** and **Offset account** fields are applicable to the deferrals group that is selected in the **Account/Group number** field. **Table** – The **Main account** and **Offset account** fields are applicable to the deferral that is selected in the **Account/Group number** field. |
    | Account/Group number | Select a value model, deferrals group, or deferral, depending on the value that you selected in the **Groupings** field. |
    | Main account | Select the main account for write-off posting or deferred expense disposal. |
    | Offset account | Select the offset account for write-off posting or deferred expense disposal. |
    | Post value | Select the value to post: Remaining amount, Initial amount, Amount written off. **Note:** This field is available only if you select the **Disposal** option. |

:::image type="content" source="../media/rus-set-up-deferral-03.png" alt-text="Screenshot of the Deferrals posting profiles page.":::

## Create deferrals groups

To create deferrals groups, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals** \> **Deferrals groups**.
1. On the Action Pane, select **New** to create groups for deferred expenses.

    The following table describes the fields on the **Deferrals groups** page.

    | Field | Description |
    |---|---|
    | Deferrals group | Enter the identification code for the deferrals group. |
    | Name | Enter the name of the deferrals group. |
    | Model number | Select the deferral model number. |
    | Model name | The name of the value model. |
    | Writing off method | Select the write-off method for the deferrals. |
    | Writing off time | Enter the write-off period for the deferrals. |
    | Beginning date of writing off | Select the start date for the write-off. |
    | Disposal date | Select the date of disposal. |
    | Posting profile | Select the posting profile for the transactions. |
    | VAT offset method for deferrals | Select the value-added tax (VAT) deduction method for deferrals: **Standard** – Use the standard VAT deduction method to process incoming VAT for factures that are related to deferrals. **Proportionate** – Use the proportional VAT deduction method to process incoming VAT for factures that are related to deferrals. |

The deferrals group that is set up has a one-to-one (1:1) relation to value model that is related to the posting profiles setup.

:::image type="content" source="../media/rus-set-up-deferral-04.png" alt-text="Screenshot of the Deferrals groups page.":::

## Create a sequence of calculation

You use the **Standard expenses sequence** and **Counter setup** pages to create calculation sequences that are used to create deferrals for vendor invoices.

> [!NOTE]
> Before you can set up the calculation sequence and counters, you must set up expense codes on the **Expense and income codes** page.

To create a sequence of calculation, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals setup** \> **Sequence of calculation**.
1. On the Action Pane, select **New** to set up revenue or expense calculation sequences.

    The following table describes the fields on the **Standard expenses sequence** page.

    | Field             | Description                                                             |
    |-------------------|-------------------------------------------------------------------------|
    | Sequence          | Enter the sequence number.                                              |
    | Description       | Enter a description of the calculation sequence.                        |
    | Channel           | Select the deferral output format for the calculation results.          |
    | Channel reference | Select the deferred expense group to record the calculation results to. If necessary, you can create deferrals for the bookkeeping accounting and tax accounting models at the same time by separating them with commas.|

    :::image type="content" source="../media/rus-set-up-deferral-05.png" alt-text="Screenshot of the Standard expenses sequence page.":::

1. On the Action Pane, select **Counters** to open the **Counter setup** page.
1. On the Action Pane, select **New** to create counters for the calculation sequence.

    The following table describes the fields on the **Counter setup** page.

    > [!NOTE]
    > You must select an expense code. When you use the periodic process to generate deferrals, the expense code that is specified for a counter is used to generate deferrals for vendor invoices that have the same expense code.

    | Field | Description |
    |---|---|
    | Sequence | Select the calculation sequence code. |
    | Description | Enter a name for the counter. |
    | Expense code | Select an expense code. |
    | Description | The description of the expense code. |
    | Line number | Enter a unique line number. |
    | Operator | Select the mathematical or logical operator for the calculation sequence: **+ (plus sign)** – Add the values in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field. The resulting value is used for the calculation sequence. **– (minus sign)** – Subtract the values in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field. The resulting value is used for the calculation sequence. **\* (asterisk)** – Multiply the values in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field. The resulting value is used for the calculation sequence. **/ (slash)** – Divide the values in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field. The resulting value is used for the calculation sequence. **Min** – Use the minimum value in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field for the calculation sequence. **Max** – Use the maximum value in the range that is defined by the **From** and **To** fields for the line type that is selected in the **Line type** field for the calculation sequence. |
    | Line type | Select a line type. |
    | From | Select the first value in the range of values that is used for the calculation sequence. |
    | To | Select the last value in the range of values that is used for the calculation sequence. |
    | Register field | Select the register field to use for the calculation sequence. **Note:** This field is available only if you selected **Register** in the **Channel** field on the **Standard expenses sequence** page. |
    | Table field | Select a table field. **Note:** This field is available only if you selected **Ratio** in the **Channel** field on the **Standard expenses sequence** page. |
    | Field ID | The identification number of the register field. |
    | Note | Enter an optional comment about the counter setup. |

    :::image type="content" source="../media/rus-set-up-deferral-06.png" alt-text="Screenshot of the Counter setup page.":::
    
    If you want to create a sequence of calculations to generate a deferrals master record, on the last line, in the **Output** field, specify **Data output**. The value of this line is the amount of the generated deferral.
    
The following table provides detailed instructions about how to fill in the **From**, **To**, **Period types**, and **Index** fields depending on the value in the **Line type** field.
    
| Line type          | Description                                                                                                                                                                                                                                                                  |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Register           | Select a register in the **From** field or a range of registers in the **From** and **To** fields.                                                                                                                                                                         |
| Line type          | Select a line number in the **From** field.                                                                                                                                                                                                                                  |
| Rates              | Select a rate code in the **From** field.                                                                                                                                                                                                                                    |
| Constant           | Enter a constant in the **From** field.                                                                                                                                                                                                                                      |
| Price              | The price from the source document that is generated in the transaction will be selected. The **From** and **To** fields are not editable.                                                                                                                        |
| Quantity           | The transaction will be selected from the quantity in the generated source document.                                                                                                                                                                                       |
| Expense            | Select a range of expense or income codes in the **From** and **To**   fields to calculate the amount of expenses and income. The range can consist   of a single code.                                                                                                      |
| Debit activity     | Select a range of accounts in the **From** and **To** fields on which the amount of debit activity will be calculated. The amount will be calculated   for the period defined in the **Period** types and **Index** fields. The   range can consist of a single account.   |
| Credit activity    | Select a range of accounts in the **From** and **To** fields on which the amount of credit activity will be calculated. The amount will be calculated   for the period defined in the **Period types** and **Index** fields. The range can consist of a single account. |
| Debit balance      | Select a range of accounts in the **From** and **To** fields on which the   amount of debit balance will be calculated. The amount will be calculated for   the period defined in the **Period types**  and **Index** fields. The range can consist of a single account.   |
| Credit balance     | Select a range of accounts in the **From** and **To** fields on which the   amount of credit balance will be calculated. The amount will be calculated   for the period defined in the **Period types** and **Index** fields. The   range can consist of a single account.   |
| Deferral write-off | Select a deferrals group in the **From** field to calculate the planned   write-off of deferrals in the current period.                                                                                                                                                      |

1. To copy the counter settings from one calculation sequence to another, on the Action Pane, select **Copy counter** to open the **Copy aisle** dialog.

    The following table describes the fields in the **Copy aisle** dialog.

    | Field                                       | Description                                                |
    |---------------------------------------------|------------------------------------------------------------|
    | Sequence (in the **Copy from** section)     | Select the sequence to copy the counter settings from.     |
    | Expense code (in the **Copy from** section) | Select the expense code to copy the counter settings from. |
    | Sequence (in the **Copy to** section)       | Select the sequence to copy the counter settings to.       |
    | Expense code (in the **Copy to** section)   | Select the expense code to copy the counter settings to.   |

## Set up General ledger parameters

To set up General ledger parameters, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **Deferrals** tab, set the fields by using the information in the following table.

    | Field                           | Description |
    |---------------------------------|-------------|
    | Posting profile                 | Select the posting profile that is used by default. The posting profile is automatically shown on the deferral voucher when it's registered. |
    | Round-off                       | Define the default round-off amount for the deferral write-off methods. For example, if you enter **0.01**, values are rounded to two decimal places. |
    | Expense and income code         | Select default expense and income codes. |
    | Worker                          | Select a default worker. |
    | Base value model                | Select a default value model. |
    | VAT offset method for deferrals | Select a default VAT offset method for deferrals. |

    :::image type="content" source="../media/rus-set-up-deferral-07.png" alt-text="Screenshot of the Deferrals tab on the General ledger parameters page.":::

1. On the **Number sequences** tab, in the **Number sequence code** field, select the number sequence code for the **Deferral ID** reference.

    :::image type="content" source="../media/rus-set-up-deferral-08.png" alt-text="Screenshot of the Number sequences tab on the General ledger parameters page.":::

1. Go to **General ledger** \> **Journal setup** \> **Journal names**.
1. On the Action Pane, select **New** to create a journal of the **Deferrals** type to work with deferrals.
1. In the **Name** field, enter the name of the journal.
1. In the **Description** field, enter a short description of the journal.
1. In the **Journal type** field, select **Deferrals**.
1. In the **Voucher series** field, select the number sequence that is used for voucher numbering.

    :::image type="content" source="../media/rus-set-up-deferral-09.png" alt-text="Screenshot of the Journal names page.":::

## Create and configure deferrals

Deferrals can be created manually, or they can be automatically generated by using a periodic operation. Learn more in [Create or generate deferrals (Russia)](rus-create-generate-deferrals.md).

To create and configure deferrals, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Deferrals** \> **Deferrals**.
1. You can use the **Deferrals** page to manually create deferrals, or to review and work with deferrals.

    The following table describes the fields on the **Deferrals** page.

    | Field | Description |
    |---|---|
    | Deferral ID | The identification code for the deferral. This code is updated according to the configured number sequence. |
    | Name | Enter a name for the deferral. |
    | Comment | Enter a detailed description of the deferral. |
    | Date attached | Select the creation date of the deferral. |
    | Table name | The name of the table that provides the source data that is used to generate the deferral. |
    | Reference | The identifier of the data table that provides the source data that is used to generate the deferral. |
    | Expense code | Select the expense code for the deferral. |
    | VAT offset method for deferrals | Select the VAT deduction method for deferrals: **Standard** – Process the incoming VAT for factures that are related to deferrals by using the standard VAT deduction method. **Proportionate** – Process the incoming VAT for factures that are related to deferrals by using the proportional VAT deduction method. |

    The following table describes the buttons on the Action Pane of the **Deferrals** page.

    | Button           | Description                                                             |
    |------------------|-------------------------------------------------------------------------|
    | Copy deferral    | Create a deferral that is identical to the selected deferral.           |
    | Deferrals models | Define deferrals models for the selected deferral.                      |
    | Source           | View the source that the deferral registration voucher is created from. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
