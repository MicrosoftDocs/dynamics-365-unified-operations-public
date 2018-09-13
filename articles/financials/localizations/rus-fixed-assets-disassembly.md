---
# required metadata

title: Advance holder transactions
description: Learn how to work with advance holder transactions in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: HcmWorkerAdvHolderTableListPage_RU
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 262554
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Advance holder transactions

[!include [banner](../includes/banner.md)]

## Partial fixed asset disassembly (liquidation)

A partial liquidation of fixed asset objects can result in a change to the original value of the asset in compliance with RF law (PBU 6/01). Furthermore, the components removed for disassembly can be accounted for as spare parts. The inventory remaining after the disposal of an asset is posted at its actual cost price, which is determined on the basis of the current market value of the inventory on the date of posting to accounting.

### Configure transaction profiles

To create the partial fixed asset disassembly transactions, you must configure
the transaction profiles:

1.  Click **Fixed Assets \> Setup \> Posting profiles.**

2.  Click **Options** button **\> Partial dismantlement**

3.  In the **Partial dismantlement** form, set up the accounts for writing off
    the balance value, balance depreciation, net book value and profit/loss.

### Create a partial fixed asset disassembly transaction

1.  Click the **Fixed asset (Russia) \>Fixed Assets**

2.  Select the fixed asset and click **FIXED ASSET \>Componentry**.

The information for the item that you selected is displayed in the following
fields in the upper pane:

-   **Date of transaction** field - the fixed asset assembly date.

-   The **Initial quantity** field -the quantity entered in the during assembly.

-   **Current quantity** field - the quantity currently entered for the fixed
    asset.

-   **Cost** field - the component cost.

1.  Select a line with the item and click the **Functions \> Add to remains**
    button.

2.  In the **Add** field of the **Add to remains** form, enter the remaining
    quantity.

The **Available quantity** field displays the quantity for this item is
currently part of the fixed asset.

1.  Click **OK**.

>   The lines marked in the upper pane of the form are transferred to the lower pane for a partial disassembly, which will be posted to the warehouse. In the lower pane, a component list is for the partial disassembly is displayed. In the upper pane of the form in the **Current quantity** column, the component quantity is displayed. This quantity remains in the fixed asset after the partial disassembly, and the of the value in the **Current quantity** field is updated.

1.  In the bottom pane form, click **Functions \> Calculating prices**. The balance value depreciation and depreciated cost are calculated for every component that is being written off.

2.  Select a **Calculating prices** method from the following options:

    -   **Proportionate** This method is based on the assumption that all revaluations are assessed in proportion to the original value without taking into account the component acquisition date.

    -   **Iterative** - The balance value calculation method for the component is based on the fact that the fixed asset revaluation transaction does not include all components in proportion to its original value, but only to the value of the components that is included at the time of the revaluation transaction.

3.  Set the **Round off market value** to **Yes**, if the cost must be rounded to an integer value.

4.  Click **OK**. The cost of the item, when it is returned to the warehouse, is calculated. You can update the market value manually, if needed.

>   Components are posted to the warehouse with respect to either their calculated or market value, which is determined by the commission during fixed asset disassembly. The difference between the market and calculated values is the profit or loss amount in the result of the disassembly of the asset.

1.  On the **Inventory dimension** tab select warehouse dimensions for posting the item to the warehouse

2.  To create the write-off disassembly transaction, click **Fixed Assets** \> **FA journal.**

3.  Press Ctrl + N) to create a new journal.

4.  Click the **Lines** button and then New button to create lines to record the write-off disassembly transaction.

5.  In the **Add to journal** form, select the **Partial dismantlement** operation type.

6.  Enter the transaction date in the **Date** field.

7.  Click **OK**. The partial fixed asset disassembly lines are created in the journal.

The balance cost disposal transactions, depreciation, depreciated cost, posting components at market value to the warehouse, and profit or loss from a write-off are created automatically in the main and tax value models. You must enter the transaction details for the other value models for this fixed asset manually.

1.  Click **Functions \> Show invisible** to display profit and loss.

2.  Click **Post \> Post**. Transactions are created in the ledger and fixed asset account, and the item is posted to the warehouse.

The partial dismantlement transaction is displayed in **Acquisition adjustment of partial dismantlement** and **Depreciation adjustment of partial dismantlement** fields in the **Balance by FA** form (Fixed asset (Russia) \> Value models \> Balance).

As the result of a partial fixed asset disassembly with a loss, a line in the **Deferrals** form (Ledger/deferrals) is created if the corresponding depreciated group has been set up.

> [!NOTE] 
> It is possible to add an item in the low panel manually, even if this item is not included in the fixed asset. A fixed asset may be put into operation without componentry but may be dismantled to different items.

### Calculating prices

This section contains examples and mathematical equations.

There are two methods used to calculate the price of an asset. By default. the component depreciated cost is adopted as the cost value.),

#### The proportional method

This method is based on the assumption that all revaluations are assessed in proportion to the original value without taking into account the component acquisition date.

For every component withdrawn from the fixed asset composition, the balance of the component is calculated using the following formula.

<p>  S<sub>j</sub> = S<sub>bal</sub>(S<sub>j,PIO</sub>/S<sub>PIO</sub>) </p>
<p>S<sub> j,PIO </sub> = the initial value of withdrawn components </p>
  

<p> S<sub>bal</sub> = the fixed asset balance value, which is determined as the sum of acquisition transactions, revaluation transactions, major refurbishment and partial take-down transactions. Partial take-down transactions are listed with the "-" sign and are automatically deducted from the total. </p>

<p> S<sub>PIO</sub> = the initial fixed asset cost. </p>

The accumulated depreciation for components is calculated in the same way as the original value where the following is true.

<p> A<sub>j</sub> = A<sub>bal</sub>(S<sub>j,PIO</sub>/S<sub>PIO</sub>) </p>

<p> A<sub>bal</sub> = the fixed asset value depreciation, which is determined as the sum of all transactions calculating fixed asset depreciation, fixed asset depreciation revaluation transactions, and partial dismantlement transactions. The calculated value is rounded off in accordance with the configurations of Fixed assets. </p>

The component depreciated cost is calculated as the difference between the component balance value and the accumulated component depreciation.

Example of calculating the component balance value:

| **Transaction number** | **Operation**        | **Amount** | **Comments**                                                   |
|------------------------|----------------------|------------|----------------------------------------------------------------|
| 1                      | Acquisition          | 1000       | The fixed asset is completed with Item 1 and acquired          |
| 2                      | Acquisition          | 2000       | The fixed asset is completed with Item 2 and acquired          |
| 3                      | Cost revaluation 1   | 1500       | Fixed asset revalued                                           |
| 4                      | Depreciation         | 300        | Fixed asset depreciation calculated                            |
| 5                      | Acquisition          | 2500       | The fixed asset is completed with Item 3 and acquired          |
| 6                      | Depreciation         | 700        | Fixed asset depreciation calculated                            |
| 7                      | disassembly          | Ххх\*      | Item 1 component is withdrawn from the fixed asset composition |
| 8                      | Cost revaluation 2   | 2000       | Fixed asset revalued                                           |
| 9                      | Value depreciation 1 | 349.21     | Depreciation revalued                                          |

\* At the time of partial fixed asset disassembly (transaction 7):

-   The fixed asset balance value was 1000 + 2000 + 1500 + 2500 = 7000

-   The original cost was 1000 + 2000 + 2500 = 5500

-   The fixed asset balance depreciation was 1000

Therefore, the balance value of component Item 1 was 7000 \* 1000 / 5500 =
1272.73, and the accumulated depreciation for component Item 1 was 1000 \* 1000
/ 5500 = 181.82.

After completing transactions 1-7, the balance value of the component was:

-   Item 1 = 1272.73 (the component was disposed with the specified original
    cost)

-   Item 2 = 2545.45

-   Item 3 = 3181.82

The accumulated component depreciation was:

-   Item 1 = 181.82 (the component was disposed with the specified accumulated
    depreciation);

-   Item 2 = 363.64

-   Item 3 = 454.54

After completing transactions 1-9, the fixed asset balance value is

-   1000 + 2000 + 1500 + 2500 + 2000 – 1272.73 = 7727.27

-   The accumulated fixed asset depreciation is 700 + 300 + 349.21 – 181.82 =
    1167.39

-   The original cost is 2000 + 2500 (at the time of calculating, the fixed
    asset consists of component Item 2 and Item 3 only)

>   Item 2 = 7727.27 \* 2000 / (2000 + 2500)\* = 3434.34

>   Item 3 = 7727.27 \* 2500 / (2000 + 2500)\* = 4292.93

-   Accumulated component depreciation:

>   Item 2 = 1167.39 \* 2000 / (2000 + 2500)\* = 518.84

>   Item 3 = 1167.39 \* 2500 / (2000 + 2500)\* = 648.55

#### **The iterate method**

The method is based on the fact that the fixed asset revaluation transaction
does not revalue all components in proportion to their original value, but only
to the sum that is included at the time of the revaluation. Furthermore, the
proportional distribution method remains in force.

Accordingly, for every component subject to withdrawal from the fixed asset
composition, a table is created that includes all revaluation transactions and
major refurbishments are calculated after acquiring the component. The following
table is based on the example of Item 2.

| i | Revaluation amount, | Fixed asset balance value before revaluation, | Original component cost, | Cost after revaluation, |
|---|---------------------|-----------------------------------------------|--------------------------|-------------------------|
| 1 | 1500                | 3000                                          | 2000                     | = 3000                  |
| 2 | 2000                | 5500\*                                        | = 3000                   | = 4090.91               |

\* The calculated fixed asset balance value includes the fixed asset revaluation
amount caused by a partial disassembly of the asset.

where = the cost of current revaluation transaction;

= the fixed asset balance value before revaluation, calculated as the sum of all
acquisition transactions prior to the current revaluation transaction, plus the
sum of all previous revaluation transactions (without taking into account the
current one) and major refurbishment transactions, less the preceding partial
fixed asset disassembly transactions.

= the original component cost , which is initialized by the cost of acquiring
the components for a first revaluation. For example, if 10 units were acquired
and 5 are to be withdrawn, this sum contains the original cost value of 5
units), For all subsequent transactions, this is initialized from the value.

The calculated value is rounded off in accordance with the configuration of the
Fixed Assets.

In the example, the component balance value after revaluation transaction 1 is
3000 and 4090.91 after revaluation transaction 2.

The calculation of added component depreciation is equal to the balance value
calculation. The depreciation revaluation and depreciation accrual transactions
are, in this case, identical to the revaluation transaction

A table is created for every component withdrawn from the fixed asset
composition. The lines of thetable include all depreciation accrual and
depreciation revaluation transactions completed after acquisition,(with the
exception of depreciation revaluation transactions triggered by disassembly
transactions. Refer to the following table.

| i | Depreciation (or revaluation) amount, | The fixed asset balance value at the time of depreciation/depreciation revaluation | Component cost, |          |
|---|---------------------------------------|------------------------------------------------------------------------------------|-----------------|----------|
| 1 | 300 – depreciation                    | 4500                                                                               | 3000            | = 200    |
| 2 | 700 – depreciation                    | 7000                                                                               | 3000            | = 500    |
| 3 | 349.21 – revaluation                  | 5500                                                                               | 3000            | = 690.48 |

For the first depreciation line, value A(i-1) is equal 0.

The accumulated component depreciation calculation is based on the component
balance value calculated. The balance value calculation can be combined with the
depreciation calculation; and, a general transactions table can be created and
the necessary steps carried out depending on the type of the next transaction.

The component depreciated cost is calculated as the difference between the
component balance value obtained and the accumulated component depreciation.

A partial take-down transaction has an indirect effect on the fixed asset
balance. A partial take-down transaction creates value and depreciation
revaluation transactions which, in turn, are already taken into account in the
fixed asset balance.

As a result of the calculation, a balance value, balance depreciation, and
market value equal to the depreciated cost are created.
