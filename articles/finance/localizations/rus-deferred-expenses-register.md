Contents

Introduction 1

Preliminary setup 2

>   Set up the deferrals module 2

>   Set up deferrals creation when selling fixed asset 2

Deferrals register 2

>   Set up the deferrals register 3

>   Examples 3

>   Example of automatic deferral creation as a result of selling fixed asset
>   with loss 3

>   Example of automatic deferral creation by using a periodic task 6

Deferrals register

eferred expenses in the system. This functionality deferrals. You can keep
parallel tax accounting and bookkeeping accounting of deferrals.

Deferrals are generated:

-   Manually on the **Deferrals** page

-   Automatically from other modules or example, when sell depreciable assets
    loss or account standard expenses amounts above the norm

Deferrals are automatically in each period. The write-off amount is determined
based on the write-off period and the deferral amount.

Here are some examples of deferrals:

-   Losses incurred by a taxpayer in a tax period be transferred to tax periods
    within 10 years. The total amount of the transferred loss must not exceed 30
    of the tax base

-   Expenses for research work or experimental development are included in other
    expenses for three years from the day of the month the month the research
    was completed

-   Loss on sale of depreciable property

set up deferrals Set up deferrals (Russia).

## Set up deferral creation when sell fixed asset

When fixed assets a loss in bookkeeping accounting and tax accounting, a
deferral for the amount from the sale. To create a deferral automatically,
before you sell fixed asset

1.  In the fixed asset, on the Action ane, select **Value models**.

2.  Select a **TAX** value model.

3.  On the **Deferrals** FastTab, select **Add** to add a line, and the
    following fields:

-   In the **Model number** field, select a **TAX** model for deferrals
    accounting

-   In the **Deferrals group** field, select deferrals group

-   In the **Expense code** field, select an expense code

You can also set up automatic deferrals for the **epreciation group** of fixed
assets.

1.  On the **Depreciation groups** page, select a **TAX** value model and
    depreciation group.

2.  On the **Deferrals** FastTab, add a line and the fields described . When you
    create value models in the fixed asset master record, the **Deferrals**
    FastTab filled in.

# Deferrals register

The register is created to summarize information about expenses that in expenses
for tax purposes in future periods *deferred expenses*.

Register entries are made when the deferral is created or is written off.

You should organize analytical accounting of deferrals for each object (fixed
asset, research work or experimental development) and each expense type that
deferred expense. This that deferrals register lines are created the same level
of analytical accounting.

The information required the register is stored in the deferrals master record
(creation date of the deferral, expense code, deferral amount, write-off period,
write-off amount for the period.) The register contains information about all
deferrals that havent yet been written off in the period the register is
created.

The register calculates the total for each expense code. The register totals are
used calculat totals for revenue and expense codes.

he register lines the following information:

-   **Line number**

-   **Transaction date** – he date of deferral transaction

-   **Expense type** – he expense code assigned in the transaction

-   **Expense code** – he description of the expense code in the transaction

-   **Object name** – he name of deferral

-   **Deferrals sum** – he amount of deferral

-   **Term of deferrals write-off** – he period of the deferral

-   **Monthly amount** – he monthly amount of the deferral

-   **Date begin account** – he date of accounting the deferral

-   **Amount of months** – he number of months when there was posted write-off
    transaction up the current month

-   **Writing-off sum** – he off sum for deferral in current register

## Set up the deferrals register

Set up the deferrals register following in Profit tax registers journal. In the
**Register type** field, select **Deferrals**.

## Examples

The examples **RUMF** company.

### Example eferral fixed asset loss

1.  On the **Deferrals groups** page, create the following deferrals group

| **Deferrals group** | **Model number** | **Writoff method** | **Writoff time** | **Beginning date of writoff** | **Disposal date** |
|---------------------|------------------|--------------------|------------------|-------------------------------|-------------------|
| Yearly              | TAX              | Linear             | 12               | Creation date start           | Year end          |

2.  On the **Expense and income codes** page, verify that the following expense
    codes are created

| **Expense code** | **Code type** | **Parent code** | **Sales tax code** |
|------------------|---------------|-----------------|--------------------|
| 902000000        | Issue         |                 | НП                 |
| 902030000        | Issue         | 902000000       | НП                 |

3.  On the **Depreciation groups** page, create the depreciation group **TAX**
    value model

| **Depreciation group** | **Depreciation method** | **Value model** | **Depreciation start date** |
|------------------------|-------------------------|-----------------|-----------------------------|
| FA loss                | Linear                  | TAX             | Next month start            |

4.  On the **Deferrals** FastTab, create the following line

| **Model number** | **Deferrals group** | **Expense code** |
|------------------|---------------------|------------------|
| TAX              | Yearly              | 902030000        |

5.  On the **FA groups** page**,** create the following FA group

| **FA group** | **Name**  |
|--------------|-----------|
| Inventory    | Inventory |

6.  reate .

| **Product number** | **Product name** | **FA group** |
|--------------------|------------------|--------------|
| Inventory01        | Inventory01      | Inventory    |

7.  On the **Tax registers** page, create the following registers:

    1.  **FA – information about object**

    2.  **FA depreciation**

    3.  **FA/IA sale**, **Deferrals**

        For register, on the **Hide** FastTab, select the fields be hidden from
        the register.

8.  reate the following fixed asset

| **FA group** | **Number** | **Acquisition date** | **Acquisition cost** |
|--------------|------------|----------------------|----------------------|
| Inventory    | 4051       | 01/01/2019           | 300,000.00           |

9.  Add the **TAX** value model for the fixed asset. On the **General** FastTab,
    the fields

| **Value model** | **Depreciation group** | **Putting into operation amount** |
|-----------------|------------------------|-----------------------------------|
| TAX             | FA loss                | 300,000.00                        |

10. Make sure that the **Deferrals** FastTab has the following line

| **Model number** | **Deferrals group** | **Expense code** |
|------------------|---------------------|------------------|
| TAX              | Yearly              | 902030000        |

11. Create the journal for putting into operation and do the putting into
    operation proposal **ransaction date**. ost the journal.

12. Create the journal for depreciation and do the depreciation
    proposal**ransaction date**erify that the following lines have been created

| **Accounting**  | **Date**     | **Account type** | **Account**             | **Description**    | **Credit** |
|-----------------|--------------|------------------|-------------------------|--------------------|------------|
| RAP             | 2/1/2019     | Fixed asset      | 4051                    | Depr. by 2/28/2019 | 25,000.00  |
| RAP             | 3/1/2019     | Fixed asset      | 4051                    | Depr. by 3/31/2019 | 25,000.00  |
| TAX             | 2/1/2019     | Fixed asset      | 4051                    | Depr. by 2/28/2019 | 25,000.00  |
| TAX             | 3/1/2019     | Fixed asset      | 4051                    | Depr. by 3/31/2019 | 25,000.00  |
| **Item number** | **Quantity** | **Unit price**   | **FA inventory number** |                    |            |
| Inventory01     | 1            | 200,000.00       | 4051                    |                    |            |

13. Switch to **Header** viewn the **Financial dimensions** FastTab, in the
    **ExpenseAndIncomeCode** field, select **902030000**.

14. In the **Invoice date** field, **3/31/2019**.

15. Post the invoice.

16. On the **Deferrals** page, verify that the deferral master record was
    created.

17. Make sure that the **Deferrals models** page has the following line

| **Model number** | **Deferrals group** | **Beginning date of writing off** | **Deferrals sum** |
|------------------|---------------------|-----------------------------------|-------------------|
| TAX              | Yearly              | 3/31/2019                         | 50,000.00         |

18. Switch to the **General** view. that the value in the **Writing off time**
    field equal remaining lifetime of the fixed asset. Note that **50,000.00** =
    300,000.00 – 25,000.00 2 – 200,000.00.

19. Create the tax register journal for month of 2019 yearalculate all registers
    and approve the journal. for month of 2019 year.

20. Create the tax register journal for month of 2019 yearalculate all registers

21. In the **Deferrals** register, you see the following information

| **Column**                      | **Value**                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------|
| **Transaction date**            | 3/31/2019                                                                                   |
| **Expense type**                | 902030000                                                                                   |
| **Expense code**                | «Прочая амортизация ОС линейным методом» (ENU: «Other FA depreciation using linear method») |
| **Object name**                 | Disposal FA \# 4051 on 3/31/2019                                                            |
| **Deferrals sum**               | 50,000.00                                                                                   |
| **Term of deferrals write-off** | 10                                                                                          |
| **Monthly amount**              | \-5,000.00                                                                                  |
| **Date begin account**          | 3/31/2019                                                                                   |
| **Amount of months**            | 1.00                                                                                        |
| **Writing-off sum**             | \-5,000.00                                                                                  |

22. Approve the journal.

23. Create the tax register journal for month of 2019 yearalculate all
    registers.

24. In the **Deferrals** register, you see the same line in the **Deferrals**
    register for month, the **Amount of months** field **.00 .00**.

### Example eferral creat by using a periodic task

1.  Go to **General ledger \> Deferrals setup \> Value models**erify that the
    following value models and deferral groups are created

| **Model number** | **Deferrals group** | **Writoff time** | **Beginning date of writoff** |
|------------------|---------------------|------------------|-------------------------------|
| RAP              | 1                   | 6                | Creation date start           |
| TAX              | Yearly              | 12               | Creation date start           |

2.  On the **Standard expenses sequence** page, create the following sequence

| **Sequence** | **Description**             | **Channel** | **Channel reference** |
|--------------|-----------------------------|-------------|-----------------------|
| AutDef       | Automatic deferral creation | Deferral    | 1,Yearly              |

3.  On the Action ane, select **Counters**

4.  On the **Counter setup** page, create sequence

5.  n the upper pane, in the **Expense code** field, select **902010100**

6.  the **Lines** FastTab, create the following lines

| **Line number** | **Operator** | **Line type** | **Period types** | **Output**  |
|-----------------|--------------|---------------|------------------|-------------|
| 1               |              | Quantity      | No               |             |
| 2               | \*           | Price         | No               | Data output |

7.  Go to **Accounts payable \> Invoices \> Invoice journal**reate a journal

8.  n the Action ane, select **Lines** the following fields

| **Column**              | **Value**                                         |
|-------------------------|---------------------------------------------------|
| **Date**                | 1/1/2019                                          |
| **Account type**        | Vendor                                            |
| **Account**             | RUMF-000002                                       |
| **Invoice**             | 0007                                              |
| **Description**         | «Расходы перечисление» (ENU: «Expenses transfer») |
| **Credit**              | 10,000.00                                         |
| **Currency**            | RUB                                               |
| **Offset account type** | Ledger                                            |
| **Offset account**      | 97.120-902010100                                  |
|                         |                                                   |
|                         |                                                   |

9.  On the **Deferrals creating** page, on the ActionPane, select the sequence
    of calculation, select **Calculate marked**.

10. On the **Parameters** FastTab

-   In the **Start date** field, **1/1/2019**

-   In the **End date** field, s **1/31/2019**

-   Set the **Preview** option to **Yes**

1.  Select **OK**n the page that **«Расходы перечисление» (ENU: «Expenses
    transfer»)**.

2.  On the Action ane, select **Create deferrals**

3.  the **Deferrals** page, verify that the deferral master record was created

4.  Make sure that the **Deferrals models** page has the following lines

| **Model number** | **Deferrals group** | **Beginning date of writoff** | **Deferrals sum** |
|------------------|---------------------|-------------------------------|-------------------|
| RAP              | 1                   | 1/1/2019                      | 10,000.00         |
| TAX              | Yearly              | 1/1/2019                      | 10,000.00         |

5.  On the **Deferrals journal** page, create a new journal, and on the Action
    ane select **Lines**.

6.  On the **Journal voucher** page, on the Action ane, select **Group
    operations \> Writing off**

7.  n the **Deferrals writing off** page, in the **Transaction date** field,
    select **3/1/2019**, and select **OK**.

8.  Verify that for the **TAX** value model lines the **Writing off** and amount
    equal10,000.00 ÷ 12 = **833.33**. ost the journal.

9.  Create the tax register journal for month of 2019 yearalculate all
    registers. In the **Deferrals** register, you see the following information

| **Column**                      | **Value**                                                                                                    |
|---------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Transaction date**            | 1/1/2019                                                                                                     |
| **Expense type**                | 902010100                                                                                                    |
| **Expense code**                | «Прямые расходы на производство (сырье и материалы)» (ENU: «Direct production expenses (raw and materials)») |
| **Object name**                 | «Расходы перечисление» (ENU: «Expenses transfer»)                                                            |
| **Deferrals sum**               | 10,000.00                                                                                                    |
| **Term of deferrals write-off** | 12                                                                                                           |
| **Monthly amount**              | \-833.33                                                                                                     |
| **Date begin account**          | 1/1/2019                                                                                                     |
| **Amount of months**            | 1.00                                                                                                         |
| **Writ-off sum**                | \-833.33                                                                                                     |

10. Approve the journal

11. **Deferrals** register, you see the same line in the **Deferrals** register
    for month the **Amount of months** field instead of **1.00**.
