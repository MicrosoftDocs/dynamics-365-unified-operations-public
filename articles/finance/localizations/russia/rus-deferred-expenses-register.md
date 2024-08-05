---
title: Deferred expenses register
description: Learn about how to generate and set up deferrals, including outlines on deferral setups and setting up deferral creation when you sell fixed assets.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2020-09-11
ms.dyn365.ops.version: 10.0.0
---

# Deferrals register

[!include [banner](../../includes/banner.md)]

Separate Deferrals functionality is used to account for deferred expenses in the system. This functionality enables an unlimited number of models to be used to account for deferrals. You can keep parallel tax accounting and bookkeeping accounting of deferrals.

Deferrals are generated in the following places:

- Manually on the **Deferrals** page.
- Automatically from other modules in Microsoft Dynamics 365 Finance. For example, deferrals are automatically generated when you sell depreciable assets at a loss or account for standard expenses amounts above the norm.

Deferrals are automatically written off in each period. The write-off amount is determined based on the write-off period and the deferral amount.

Here are some examples of deferrals:

- Losses that are incurred by a taxpayer in a tax period. These losses can be transferred to subsequent tax periods within 10 years. The total amount of the transferred loss must not exceed 30 percent of the tax base.
- Expenses for research work or experimental development. These expenses are evenly included in other expenses for three years from the first day of the month after the month when the research was completed.
- Loss on the sale of depreciable property.

## Deferrals setup

For more information about how to set up deferrals, see [Set up deferrals (Russia)](rus-set-up-deferrals.md).

### Set up deferral creation when you sell fixed assets

When you sell fixed assets at a loss in bookkeeping accounting and tax accounting, a deferral must be created for the amount that is lost from the sale. To create a deferral automatically, follow these steps before you sell a fixed asset.

1. Go to **Fixed assets (Russia) \> Common \> Fixed assets.** In the master record for the fixed asset, on the Action Pane, select **Value models**.
2. Select a **TAX** value model.
3. On the **Deferrals** FastTab, select **Add** to add a line, and set the following fields:

    - In the **Model number** field, select a **TAX** model for deferrals accounting.
    - In the **Deferrals group** field, select a deferrals group.
    - In the **Expense code** field, select an expense code.


You can also set up automatic creation of deferrals for the depreciation group of fixed assets.

1. On the **Depreciation groups** page, select a **TAX** value model and a depreciation group.
2. On the **Deferrals** FastTab, add a line, and set the fields that are described in the previous procedure. When you create value models in the fixed asset master record, the **Deferrals** FastTab is automatically filled in.

## Deferrals register

The deferrals register is created to summarize information about expenses that can be included in expenses for tax purposes in future periods. These expenses are known as *deferred expenses*.

Register entries are made when the deferral is created or is written off.

You should organize analytical accounting of deferrals for each object (fixed asset, research work, or experimental development) and each expense type that cause a deferred expense to be created. This organization ensures that the deferrals register lines that are created have the same level of analytical accounting.

The information that is required to create the register is stored in the deferrals master record. (This information includes the creation date of the deferral, the expense code, the deferral amount, the write-off period, and the write-off amount for the period.) The register contains information about all the deferrals that haven't yet been written off in the period that the register is created for.

The register calculates the total for each expense code. The register totals are used to calculate totals for revenue and expense codes.

The register lines show the following information:

- **Line number**
- **Transaction date** – The date of the deferral transaction.
- **Expense type** – The expense code that is assigned in the transaction.
- **Expense code** – The description of the expense code in the transaction.
- **Object name** – The name of the deferral.
- **Deferrals sum** – The amount of the deferral.
- **Term of deferral's write-off** – The period of the deferral write-off.
- **Monthly amount** – The monthly amount of the deferral write-off.
- **Date begin account** – The start date of accounting for the deferral.
- **Amount of months** – The number of months when there was a posted write-off transaction, up through the current month.
- **Writing-off sum** – The write-off sum for the deferral in the current register.

### Set up the deferrals register

Set up the deferrals register by following the instructions in the article, [Create tax registers and the tax register journal](rus-profit-tax-registers.md#create-a-tax-register). In the **Register type** field, select **Deferrals**.

### Examples

The following two examples use the **RUMF** company:

   - Deferrals are automatically created when fixed assets are sold at a loss
   - Deferrals are automatically created by using a periodic task
   

#### Example: Deferrals are automatically created when fixed assets are sold at a loss

1. On the **Deferrals groups** page (**General ledger \> Deferrals**), create the following deferrals group.

| **Deferrals group** | **Model number** | **Write-off method** | **Write-off time** | **Beginning date of write-off** | **Disposal date** |
|---------------------|------------------|----------------------|--------------------|---------------------------------|-------------------|
| Yearly              | TAX              | Linear               | 12                 | Creation date start             | Year end          |

2. On the **Expense and income codes** page (**Tax \> Setup \> Profit tax \> Expense codes**), verify that the following expense codes are created.

| **Expense code** | **Code type** | **Parent code** | **Sales tax code** |
|------------------|---------------|-----------------|--------------------|
| 902000000        | Issue         |                 | НП                 |
| 902030000        | Issue         | 902000000       | НП                 |

3. On the **Depreciation groups** page (**Fixed assets (Russia) \> Setup \> Depreciation groups**), create the following depreciation group that uses the **TAX** value model.

| **Depreciation group** | **Depreciation method** | **Value model** | **Depreciation start date** |
|------------------------|-------------------------|-----------------|-----------------------------|
| FA loss                | Linear                  | TAX             | Next month start            |

4. On the **Deferrals** FastTab, create the following line.

| **Model number** | **Deferrals group** | **Expense code** |
|------------------|---------------------|------------------|
| TAX              | Yearly              | 902030000        |

5. On the **FA groups** page (**Fixed assets (Russia) \> Setup \> FA groups),** create the following fixed asset (FA) group.

| **FA group** | **Name**  |
|--------------|-----------|
| Inventory    | Inventory |

6. On the **Released products** page (**Product information management \> Products \> Released products**), create the product. In the **Fixed assets (Russia)** section, in the **FA group** field, select the fixed asset group that you just created.

| **Product number** | **Product name** | **FA group** |
|--------------------|------------------|--------------|
| Inventory01        | Inventory01      | Inventory    |

7. On the **Tax registers** page (**Tax \> Setup \> Profit tax \> Registers**), create the following registers:

    - FA – information about object
    - FA depreciation
    - FA/IA sale, Deferrals

      For each register, on the **Hide** FastTab, select the fields that should be hidden from the register.

8. On **Fixed assets** page (Fixed assets (Russia) \> Common \> Fixed assets), create the following fixed asset.

| **FA group** | **Number** | **Acquisition date** | **Acquisition cost** |
|--------------|------------|----------------------|----------------------|
| Inventory    | 4051       | 01/01/2019           | 300,000.00           |

9. Add the **TAX** value model for the fixed asset. On the **General** FastTab, set the following fields.

| **Value model** | **Depreciation group** | **Putting into operation amount** |
|-----------------|------------------------|-----------------------------------|
| TAX             | FA loss                | 300,000.00                        |

10. Make sure that the **Deferrals** FastTab has the following line.

| **Model number** | **Deferrals group** | **Expense code** |
|------------------|---------------------|------------------|
| TAX              | Yearly              | 902030000        |

11. Create the fixed asset journal for putting into operation, and do the putting into operation proposal, using January 1, 2019 (1/1/2019) as the transaction date. Then post the journal.
12. Create the fixed asset journal for depreciation, and do the depreciation proposal, using April 1, 2019 (4/1/2019) as the transaction date. Verify that the following lines have been created.

| **Accounting** | **Date** | **Account type** | **Account** | **Description**    | **Credit** |
|----------------|----------|------------------|-------------|--------------------|------------|
| RAP            | 2/1/2019 | Fixed asset      | 4051        | Depr. by 2/28/2019 | 25,000.00  |
| RAP            | 3/1/2019 | Fixed asset      | 4051        | Depr. by 3/31/2019 | 25,000.00  |
| TAX            | 2/1/2019 | Fixed asset      | 4051        | Depr. by 2/28/2019 | 25,000.00  |
| TAX            | 3/1/2019 | Fixed asset      | 4051        | Depr. by 3/31/2019 | 25,000.00  |

13. Post the journal.
14. On **All sales orders** page (**Accounts receivable \> Orders \> All sales orders**) create a sales order that has the following line:

| **Item number** | **Quantity** | **Unit price** | **FA inventory number** |
|-----------------|--------------|----------------|-------------------------|
| Inventory01     | 1            | 200,000.00     | 4051                    |

15. Switch to the **Header** view, and then, on the **Financial dimensions** FastTab, in the **ExpenseAndIncomeCode** field, select **902030000**. In the **Invoice date** field, select **3/31/2019**.
16. Post the invoice.
17. On the **Deferrals** page (**General ledger \> Deferrals**), verify that the deferral master record was created.
18. Make sure that the **Deferrals models** page has the following line.

| **Model number** | **Deferrals group** | **Beginning date of writing off** | **Deferrals sum** |
|------------------|---------------------|-----------------------------------|-------------------|
| TAX              | Yearly              | 3/31/2019                         | 50,000.00         |

19. Switch to the **General** view. You should see that the value in the **Writing off time** field equals the remaining lifetime of the fixed asset. Note that **50,000.00** = 300,000.00 – 25,000.00 × 2 – 200,000.00.
20. Create the tax register journal for one month of the 2019 calendar year, calculate all registers, and then approve the journal. Repeat this step for two months of the 2019 calendar year.
21. Create the tax register journal for three months of the 2019 calendar year, and calculate all registers. In the **Deferrals** register, you should see the following information.

| **Column**                   | **Value**                                                                                   |
|------------------------------|---------------------------------------------------------------------------------------------|
| Transaction date             | 3/31/2019                                                                                   |
| Expense type                 | 902030000                                                                                   |
| Expense code                 | «Прочая амортизация ОС линейным методом» (ENU: «Other FA depreciation using linear method») |
| Object name                  | Disposal FA \# 4051 on 3/31/2019                                                            |
| Deferrals sum                | 50,000.00                                                                                   |
| Term of deferral's write-off | 10                                                                                          |
| Monthly amount               | \-5,000.00                                                                                  |
| Date begin account           | 3/31/2019                                                                                   |
| Amount of months             | 1.00                                                                                        |
| Writing-off sum              | \-5,000.00                                                                                  |

22. Approve the journal.
23. Create the tax register journal for four months of the 2019 calendar year, and calculate all the registers. In the **Deferrals** register, you should see the same line that you saw in the **Deferrals** register for three months. However, the **Amount of months** field will be set to **2.00** instead of **1.00**.

#### Example: Deferrals are automatically created by using a periodic task

1. Go to **General ledger \> Deferrals setup \> Value models**, and verify that the following value models and deferral groups are created.

| **Model number** | **Deferrals group** | **Write-off time** | **Beginning date of write-off** |
|------------------|---------------------|--------------------|---------------------------------|
| RAP              | 1                   | 6                  | Creation date start             |
| TAX              | Yearly              | 12                 | Creation date start             |

2. On the **Standard expenses sequence** page, create the following sequence.

| **Sequence** | **Description**             | **Channel** | **Channel reference** |
|--------------|-----------------------------|-------------|-----------------------|
| AutDef       | Automatic deferral creation | Deferral    | 1,Yearly              |

3. On the Action Pane, select **Counters**.
4. On the **Counter setup** page, create a sequence. In the upper pane, in the **Expense code** field, select **902010100**, and then, on the **Lines** FastTab, create the following lines.

| **Line number** | **Operator** | **Line type** | **Period types** | **Output**  |
|-----------------|--------------|---------------|------------------|-------------|
| 1               |              | Quantity      | No               |             |
| 2               | \*           | Price         | No               | Data output |

5. Go to **Accounts payable \> Invoices \> Invoice journal**, and create a journal.
6. On the Action Pane, select **Lines**, set the following fields, and then post the journal.

| **Column**          | **Value**                                         |
|---------------------|---------------------------------------------------|
| Date                | 1/1/2019                                          |
| Account type        | Vendor                                            |
| Account             | RUMF-000002                                       |
| Invoice             | 0007                                              |
| Description         | «Расходы перечисление» (ENU: «Expenses transfer») |
| Credit              | 10,000.00                                         |
| Currency            | RUB                                               |
| Offset account type | Ledger                                            |
| Offset account      | 97.120-902010100                                  |

7. On the **Deferrals creating** page, on the Action Pane, select the sequence of calculation that you created, and then select **Calculate marked**.
8. On the **Parameters** FastTab, set the following fields:

    - In the **Start date** field, select **1/1/2019**.
    - In the **End date** field, select **1/31/2019**.
    - Set the **Preview** option to **Yes**.

9. Select **OK**, and then, on the page that appears, set the **Name** field to **«Расходы перечисление» (ENU: «Expenses transfer»)**.
10. On the Action Pane, select **Create deferrals**, and then, on the **Deferrals** page, verify that the deferral master record was created.
11. Make sure that the **Deferrals models** page has the following lines.

| **Model number** | **Deferrals group** | **Beginning date of write-off** | **Deferrals sum** |
|------------------|---------------------|---------------------------------|-------------------|
| RAP              | 1                   | 1/1/2019                        | 10,000.00         |
| TAX              | Yearly              | 1/1/2019                        | 10,000.00         |

12. On the **Deferrals journal** page, create a new journal, and then, on the Action Pane, select **Lines**.
13. On the **Journal voucher** page, on the Action Pane, select **Group operations \> Writing off**.
14. On the **Deferrals writing off** page, in the **Transaction date** field, select **3/1/2019**, and then select **OK**.
15. Verify that two lines were created for the **TAX** value model. For both lines, the operation type should be **Writing off**, and the amount should equal 10,000.00 ÷ 12 = **833.33**. When you've finished, post the journal.
16. Create the tax register journal for one month of the 2019 calendar year, and then calculate all the registers. In the **Deferrals** register, you should see the following information.

| **Column**                   | **Value**                                                                                                    |
|------------------------------|--------------------------------------------------------------------------------------------------------------|
| Transaction date             | 1/1/2019                                                                                                     |
| Expense type                 | 902010100                                                                                                    |
| Expense code                 | «Прямые расходы на производство (сырье и материалы)» (ENU: «Direct production expenses (raw and materials)») |
| Object name                  | «Расходы перечисление» (ENU: «Expenses transfer»)                                                            |
| Deferrals sum                | 10,000.00                                                                                                    |
| Term of deferral's write-off | 12                                                                                                           |
| Monthly amount               | \-833.33                                                                                                     |
| Date begin account           | 1/1/2019                                                                                                     |
| Amount of months             | 1.00                                                                                                         |
| Write-off sum                | \-833.33                                                                                                     |

17. Approve the journal, and then create the tax register journal for two months of the 2019 calendar year.
18. Calculate the registers. In the **Deferrals** register, you should see the same line that you saw in the **Deferrals** register for one month. However, the **Amount of months** field will be set to **2.00** instead of **1.00**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
