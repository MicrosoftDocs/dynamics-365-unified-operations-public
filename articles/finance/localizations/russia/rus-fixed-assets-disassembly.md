---
title: Partial fixed asset disassembly (liquidation)
description: Learn about partial fixed asset disassembly or liquidation for Russia, including an outline and step-by-step process for configuring transaction profiles.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.search.form: RAssetPosting
ms.dyn365.ops.version: 8.1
---

# Partial fixed asset disassembly (liquidation)

[!include [banner](../../includes/banner.md)]

Partial disassembly (liquidation) of fixed asset objects can cause the original value of the asset to change, in accordance with Russian Federation law (PBU 6/01). The components that are removed for disassembly can be accounted for as spare parts. The inventory that remains after the disposal of an asset is posted at its actual cost price. This price is based on the current market value of the inventory on the date of posting to accounting.

## Configure transaction profiles

To create the partial fixed asset disassembly transactions, you must configure the transaction profiles.

1. Select **Fixed assets (Russia) \> Setup \> Posting profiles**.
2. On the Action Pane, select **Options \> Partial dismantlement**.
3. On the **Partial dismantlement** page, set up the accounts for writing off the balance value, balance depreciation, net book value, and profit/loss.

## Create a partial fixed asset disassembly transaction

1. Select **Fixed assets (Russia) \> Fixed assets**.
2. Select the fixed asset, and then, on the Action Pane, on the **Fixed asset** tab, select **Componentry**.

    The upper pane of the **Componentry** page shows the following information for the item that you selected:

    - **Date of transaction** – The date of fixed asset assembly.
    - **Initial quantity** – The quantity that was entered during assembly.
    - **Current quantity** – The quantity that is currently entered for the fixed asset.
    - **Cost** – The component cost.

3. Select the line for an item, and then select **Add to remains**.
4. in the **Add to remains** dialog box, in the **Add** field, enter the remaining quantity.

    The **Available quantity** field shows the quantity of this item that is currently part of the fixed asset.

5. Select **OK**.

    The lines that are marked in the upper pane of the **Componentry** page are transferred to the lower pane for a partial disassembly that will be posted to inventory. The lower pane shows a component list for the partial disassembly. In the upper pane, the **Current quantity** field shows the component quantity. This quantity remains in the fixed asset after the partial disassembly, and the value of the **Current quantity** field is updated.

6. In the lower pane, select **Calculating prices**. The balance value depreciation and depreciated cost are calculated for every component that is being written off.
7. In the **Calculating prices** dialog box, in the **Calculating prices** field, select the method that is used to calculate prices:

    - **Proportionate** – The fixed asset revaluation transaction includes all components in proportion to their original value. The acquisition date of the component isn't considered. The acquisition date of the component isn't considered.
    - **Iterative** – The fixed asset revaluation transaction doesn't include all components in proportion to their original value, but only in proportion to the value of the components that are included at the time of the revaluation transaction.

8. If the cost must be rounded to an integer value, set the **Round off market value** option to **Yes**.
9. Select **OK**. The cost of the item is calculated, when the item return to inventory  You can manually update the market value as you require.

    Components are posted to the inventory with respect to either their calculated value or their market value. The value that is used is determined by the commission during fixed asset disassembly. The difference between the market value and the calculated value is the profit or loss amount in the result of the fixed asset disassembly.

10. In the lower pane of the **Componentry** page, on the **Inventory dimensions** tab, select inventory dimensions that are used to post the item to inventory.
11. To create the write-off disassembly transaction, select **Fixed assets (Russia) \> Journals \> FA journal**.
12. Select **New** to create a journal.
13. Select **Lines** and then **New** to create lines to record the write-off disassembly transactions.
14. In the **Add to journal** dialog box, in the **Transaction type** field, select **Partial dismantlement**.
15. In the **Transaction date** field, enter the transaction date.
16. Select **OK**. The partial fixed asset disassembly lines are created in the journal, according to the depreciation profile settings.

    If there no transaction details on the journal line, you must enter them manually.

17. On the Action Pane, select **Functions \> Show invisible** to show profit/loss lines.
18. On the Action Pane, select **Post \> Post**. Transactions are created in the ledger and fixed asset accounts, and the item is posted to inventory.

    The partial dismantlement transaction value is shown in the **Acquisition adjustment of partial dismantlement** and **Depreciation adjustment of partial dismantlement** fields in the **Balance by FA** dialog box (**Fixed assets (Russia) \> Value models \> Balance**).

    If a partial fixed asset disassembly involves a loss, a line on the **Deferrals** page (**General ledger \> Deferrals \> Deferrals**) is created if the corresponding depreciation group has been set up for the tax value mode.

> [!NOTE]
> You can manually add an item in the lower pane of the **Componentry** page, even if that item isn't included in the fixed asset. A fixed asset can be put into operation without componentry, but it can be dismantled to different items.

## Calculating prices

This section contains examples and mathematical equations (formulas). Two methods are used to calculate the price of an asset. By default, the depreciated cost of a component is adopted as the cost value.

### The proportional method


The fixed asset revaluation transaction includes all components in proportion to their original value. The acquisition date of the component isn't considered. The acquisition date of the component isn't considered.

For every component that is withdrawn from the fixed asset composition, the balance of the component (S<sub>j</sub>) is calculated by using the following formula:

S<sub>j</sub> = S<sub>bal</sub> × (S<sub>j,PIO</sub> ÷ S<sub>PIO</sub>)

Here is an explanation of this formula:

- **S<sub>bal</sub>** – The fixed asset balance value. This value is calculated as the sum of acquisition transactions, revaluation transactions, major refurbishment transactions, and partial take-down transactions. Partial take-down transactions have a negative sign and are automatically deducted from the total.
- **S<sub>j,PIO</sub>** – The original value of withdrawn components.
- **S<sub>PIO</sub>** – The original fixed asset cost.

The accumulated depreciation for components (A<sub>j</sub>) is calculated in the same way as the original value where the following condition is true:

A<sub>j</sub> = A<sub>bal</sub> × (S<sub>j,PIO</sub> ÷ S<sub>PIO</sub>)

Here is an explanation of this formula:

- **A<sub>bal</sub>** – The fixed asset value depreciation. This value is calculated as the sum of all transactions that are used to calculate fixed asset depreciation, fixed asset depreciation revaluation transactions, and partial dismantlement transactions. The calculated value is rounded according to the configuration of Fixed assets.

The depreciated cost of components is calculated as the difference between the component balance value and the accumulated component depreciation.

The following example shows how the component balance value is calculated.

| Transaction number | Operation            | Amount | Comments                                                            |
|--------------------|----------------------|--------|---------------------------------------------------------------------|
| 1                  | Acquisition          | 1,000  | The fixed asset is assempled from item 1 and acquired with amount.  |
| 2                  | Acquisition          | 2,000  | The fixed asset is assempled from item 2 and acquired with amount.  |
| 3                  | Cost revaluation 1   | 1,500  | The fixed asset is revalued.                                        |
| 4                  | Depreciation         | 300    | Fixed asset depreciation is calculated.                             |
| 5                  | Acquisition          | 2,500  | The fixed asset is assempled from item 3 and acquired with amount.  |
| 6                  | Depreciation         | 700    | Fixed asset depreciation is calculated.                             |
| 7                  | Disassembly          | \*     | The item 1 component is withdrawn from the fixed asset composition. |
| 8                  | Cost revaluation 2   | 2,000  | The fixed asset is revalued.                                        |
| 9                  | Value depreciation 1 | 349.21 | The depreciation is revalued.                                       |

\* At the time of partial fixed asset disassembly (transaction 7), the following conditions are true:

- The fixed asset balance value is 1,000 + 2,000 + 1,500 + 2,500 = 7,000.
- The original cost is 1,000 + 2,000 + 2,500 = 5,500.
- The fixed asset balance depreciation is 300 + 700 = 1,000.

Therefore, the balance value of component item 1 is 7,000 × (1,000 ÷ 5,500) = 1,272.73, and the accumulated depreciation for component item 1 is 1,000 × (1,000 ÷ 5,500) = 181.82.

Here is the balance value of the component after transactions 1 through 7 are completed:

- **Item 1:** 1,272.73 (The component was disposed of by using the specified original cost.)
- **Item 2:** 2,545.45
- **Item 3:** 3,181.82

Here is the accumulated component depreciation:

- **Item 1:** 181.82 (The component was disposed of by using the specified accumulated depreciation.)
- **Item 2:** 363.64
- **Item 3:** 454.54

After transactions 1 through 9 are completed, the fixed asset balance value is 1,000 + 2,000 + 1,500 + 2,500 + 2,000 – 1,272.73 = 7,727.27.

The accumulated fixed asset depreciation is 700 + 300 + 349.21 – 181.82 = 1,167.39.

The original cost is 2,000 + 2,500. (At the time of calculation, the fixed asset consists of only component item 2 and component item 3.)

Here is the balance value:

- **Item 2:** 7,727.27 × (2,000 ÷ \[2,000 + 2,500\]) = 3,434.34
- **Item 3:** 7,727.27 × (2,500 ÷ \[2,000 + 2,500\]) = 4,292.93

Here is the accumulated component depreciation:

- **Item 2:** 1,167.39 × (2,000 ÷ \[2,000 + 2,500\]) = 518.84
- **Item 3:** 1,167.39 × (2,500 ÷ \[2,000 + 2,500\]) = 648.55

### The iterate method

The fixed asset revaluation transaction doesn't revalue all components in proportion to their original value, but only in proportion to the value of the components that are included at the time of the revaluation transaction.. Furthermore, the proportional distribution method remains in effect.

Therefore, for every component that is subject to withdrawal from the fixed asset composition, a table is created that includes all revaluation transactions. Major refurbishments are calculated after the component is acquired. The following table uses item 2 as an example.

<table>
<thead>
<tr>
<th>i</th>
<th>Revaluation amount, Adj(i)</th>
<th>Fixed asset balance value before revaluation, S<sub>bal</sub>(i)</th>
<th>Original component cost, S<sub>src</sub>(i)</th>
<th>Cost after revaluation, S<sub>dst</sub>(i)</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>1,500</td>
<td>3,000</td>
<td>2,000</td>
<td>S<sub>dst</sub>(i) = S<sub>src</sub>(i) × (1 + [Adj(i) ÷ S<sub>bal</sub>(i)]) = 3,000</td>
</tr>
<tr>
<td>2</td>
<td>2,000</td>
<td>5,500*</td>
<td>S<sub>src</sub>(i) = S<sub>dst</sub>(i–1) = 3,000</td>
<td>S<sub>dst</sub>(i) = S<sub>src</sub>(i) × (1 + [Adj(i) ÷ S<sub>bal</sub>(i)]) = 4,090.91</td>
</tr>
</tbody>
</table>

\* The fixed asset balance value that is calculated includes the fixed asset revaluation amount that is caused by a partial disassembly of the asset.

Here is an explanation of the table:

- **Adj(i)** – The cost of the current revaluation transaction.
- **S<sub>bal</sub>(i)** – The fixed asset balance value before revaluation. This value is calculated as the sum of all acquisition transactions before the current revaluation transaction, plus the sum of all revaluation transactions before the current revaluation transaction and all major refurbishment transactions, minus the previous partial fixed asset disassembly transactions.
- **S<sub>src</sub>(i)** – The original component cost. For a first revaluation, this value is set to the cost of acquiring the components. For example, if 10 units were acquired, and five must be withdrawn, this sum includes the original cost value of five units. For all subsequent transactions, this sum is initialized from the S<sub>dst</sub>(i-1) value.

The calculated value is rounded according to the configuration of Fixed assets.

In the example, the component balance value is 3,000 after revaluation transaction 1 and 4,090.91 after revaluation transaction 2.

Calculation of the added component depreciation is similar to the calculation of the balance value. In this case, the depreciation revaluation transactions and depreciation accrual transactions are identical to the revaluation transaction.

A table is created for every component that is withdrawn from the fixed asset composition. The lines of the table include all depreciation accrual and depreciation revaluation transactions that were completed after acquisition, except depreciation revaluation transactions that were triggered by disassembly transactions. See the following table.

<table>
<thead>
<tr>
<th>i</th>
<th>Depreciation or revaluation amount, Acq(i)</th>
<th>Fixed asset balance value at the time of depreciation or depreciation revaluation</th>
<th>Component cost, S<sub>dst</sub>(i)</th>
<th>Depreciation after revaluation, A(i)</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td>300 (depreciation)</td>
<td>4,500</td>
<td>3,000</td>
<td>A(i) = A(i–1) + S<sub>dst</sub>(i) × (Acq(i) ÷ S<sub>bal</sub>) = 200</td>
</tr>
<tr>
<td>2</td>
<td>700 (depreciation)</td>
<td>7,000</td>
<td>3,000</td>
<td>A(i) = A(i–1) + S<sub>dst</sub>(i) × (Acq(i) ÷ S<sub>bal</sub>) = 500</td>
</tr>
<tr>
<td>3</td>
<td>349.21 (revaluation)</td>
<td>5,500</td>
<td>3,000</td>
<td>A(i) = A(i–1) + S<sub>dst</sub>(i) × (Acq(i) ÷ S<sub>bal</sub>) = 690.48</td>
</tr>
</tbody>
</table>

For the first depreciation line, the value A(i–1) equals 0 (zero).

The calculation of accumulated component depreciation is based on the component balance value that is calculated. The balance value calculation can be combined with the depreciation calculation. Additionally, a general transaction table can be created, and the required steps can be performed, depending on the type of the next transaction.

The component depreciated cost is calculated as the difference between the component balance value that is calculated and the accumulated component depreciation.

A partial take-down transaction has an indirect effect on the fixed asset balance. A partial take-down transaction creates value and depreciation revaluation transactions. These transactions, in turn, are already considered in the fixed asset balance.

As a result of the calculation, a balance value, a balance depreciation, and a market value that equals the depreciated cost are created.

## Reverse partial dismantlement transactions
By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.

1. Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2. On the **FA value models** page, on the Action Pane, select **Transactions**. 
3. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**. 
4. In the **Reverse transactions** dialog box, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page. 
5. Select **Voucher** and on the **Voucher transactions** page, view the transactions in the ledger. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
