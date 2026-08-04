---
title: Overhead calculation
description: Learn about the typical processes for calculating and allocating overhead costs, including an overview on calculating and allocating the Electricity overhead cost.
author: AndersEvenGirke
ms.author: twheeloc
ms.topic: article
ms.date: 05/27/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.industry: Manufacturing
ms.dyn365.ops.version: Version 1611
ms.search.form: CAMActualVersion, CAMBudgetVersion, CAMOverheadCalculation, CAMOverheadRateCalculationJournalEntry, CAMFormulaAllocationBase
ms.search.validFrom: 2016-11-30
ms.assetid: 93119afb-47ed-4786-ba44-ba93576d3e28
---

# Overhead calculation

[!include [banner](../includes/banner.md)]

This article describes the typical processes for calculating and allocating overhead costs.

## Term definition

Overhead costs are the costs that you incur to run a business but can't directly attribute to any specific business activity, product, or service. Overhead costs provide critical support for the generation of profit-making activities. Here are some examples of overhead costs:

- Rent
- Electricity
- Administrative salaries

## Overhead calculation overview

Overhead calculation runs the cost accounting policies in the correct order. You can run overhead calculation multiple times for the same fiscal period if you change cost accounting policies or detect specific errors. Each run of the overhead calculation is stored and receives a unique version ID that lets you compare the calculations in various versions. The cost entries that the overhead calculation generates receive an accounting date. This accounting date matches the end date of the fiscal period that is used in the calculation. The unique version ID consists of the following elements:

- Version type
- Date and time
- Cost accounting ledger
- Fiscal year
- Fiscal period

You run overhead calculation independently of the version. Therefore, you can calculate the Budget version before the Actual version. Overhead calculation consists of four steps, as shown in the following illustration. In each step, the process creates a journal header that has journal entries. This journal header keeps the input data for each calculation step. The process applies policies and rules to each journal line, and generates cost entries as output. Therefore, you always have full traceability.

:::image type="content" source="./media/period-cost-calculation.png" alt-text="Screenshot of the four steps of the overhead calculation process." lightbox="./media/period-cost-calculation.png":::

## Calculate and allocate the electricity overhead cost

In Financial accounting, some costs, such as electricity, are registered as a lump sum. Therefore, detailed managerial insight isn't provided for Cost accounting. In Cost accounting, to provide correct managerial insight across all organizational units and levels, costs must flow through the organizational units. This flow must be based on either an accurate record of the consumption or a fair assessment. In the general ledger, an electricity cost can be posted as shown in the following table.

| Accounting date | Cost center | Main account |  Amount in the accounting currency |
|---|---|---|---|
| January 3, 2023 | CC099 - Default cost center | 10001 - Electricity | 10,000.00 |

### Step 1: Process the cost behavior calculation

By default, when you import cost entries from the source data, they receive the **Unclassified** cost behavior classification in Cost accounting. By applying cost behavior policy rules, you can reclassify cost entries as either **Fixed cost** or **Variable cost**.

#### Define the cost behavior rule

In some cases, part of the cost is a fixed fee, and the remaining cost is based on consumption. Electricity bills often match this definition. After you pay a specific fixed fee, you pay for consumption per kilowatt hour (Kwh). For example, if the fixed cost fee is 1,000.00, here's how you define the cost behavior rule:

- Fixed amount 1,000.00
  - 0 &lt;= 1,000.00 = Fixed
  - 1000,01 &lt; N = Variable

##### Journal

| Journal | Journal type | Fiscal calendar period | Version |
|---|---|---|---|
| 00001 | Cost behavior calculation journal | Fiscal 2023 Period 1 | Overhead calculation / 01-02-2023 11:51:00 PM / Ledger /2023 / Period 1 |

##### Journal entries (Cost object balance journal entries)

| Accounting date | Cost object| Cost element| Cost behavior | Amount |
|---|---|---|---|---|
| January 3, 2023 | CC099 - Default cost center | 10001 - Electricity | Unclassified | 10,000.00 |

##### Cost entries

| Cost object | Cost element | Cost behavior | Amount | Accounting date |
|---|---|---|---|---|
| CC099 - Default cost center | 10001 - Electricity | Unclassified | 10,000.00 | January 3, 2023 |
| CC099 - Default cost center | 10001 - Electricity | Unclassified | -10,000.00 | January 31, 2023 |
| CC099 - Default cost center | 10001 - Electricity | Fixed cost | 1,000.00 | January 31, 2023 |
| CC099 - Default cost center | 10001 - Electricity | Variable cost | 9,000.00 | January 31, 2023 |

For more information, see [Create and assign a cost behavior policy to a cost control unit](tasks/create-assign-cost-behavior-policy-cost-control-unit.md).

### Step 2: Process the cost distribution calculation

Use cost distribution to redistribute costs from one cost object to one or more other cost objects by applying a relevant allocation base. Cost distribution and cost allocation differ in that cost distribution always occurs at the level of the primary cost element of the original cost.

#### Define the cost distribution rule

In financial accounting, register electricity costs as a lump sum. In cost accounting, this approach isn't detailed enough. Distribute the variable cost to the individual cost objects on a fair basis. The most logical allocation basis is the consumption of electricity (Kwh). Create a statistical dimension member named **Electricity**, and record electricity consumption. By default, all statistical dimension members become available as allocation bases.

| Cost object | Kwh |
|---|----|
| CC001 - HR | 1,000 |
| CC002 - Finance | 6,000 |
| CC003 - Assembly | 0 |

The following table shows the result when you apply electricity consumption as an allocation base for variable costs.

| Cost object | Magnitude | Allocation factor | Amount |
|---|---|---|----|
| CC001 - HR | 1,000 | (1,000 ÷ 7,000) × 9,000.00 | 1,285.71 |
| CC002 - Finance | 6,000 | (6,000 ÷ 7,000) × 9,000.00 | 7,714.29 |
| CC003 - Assembly | 0 | (0 ÷ 7,000) × 9,000.00 | 0.00 |

Distribute the fixed cost evenly to the individual cost objects that consume electricity. To achieve this result, use the Electricity statistical dimension member in a formula allocation base: (Electricity > 0.00). The following table shows the result when you apply electricity consumption as an allocation base for variable costs.

| Cost object | Formula | Magnitude | Allocation factor | Amount |
|---|---|----|---|---|
| CC001 - HR | (1,000 > 0.00) | 1 | (1 ÷ 2) × 1,000.00 | 500.00 |
| CC002 - Finance | (6,000 > 0.00) | 1 | (1 ÷ 2) × 1,000.00 | 500.00 |
| CC003 - Assembly | (0 > 0.00) | 0 | (0 ÷ 2) × 1,000.00 | 0.00 |

##### Journal

| Journal | Journal type | Fiscal calendar period | Version |
|---|---|---|---|
| 00002 | Cost distribution calculation journal | Fiscal - 2023 Period 1 | Overhead calculation / 01-02-2023 11:51:00 PM / Ledger /2023 / Period 1 |

##### Journal entries (Cost object balance journal entries)

| Accounting date | Cost object | Cost element | Cost behavior | Amount |
|---|---|---|---|---|
| January 31, 2023 | CC099 - Default cost center | 10001 - Electricity | Fixed cost | 1,000.00 |
| January 31, 2023 | CC099 - Default cost center | 10001 - Electricity | Variable cost | 9,000.00 |

##### Cost entries

| Cost object | Cost element | Cost behavior | Amount | Accounting date |
|---|---|---|---|---|
| CC099 - Default cost center| 10001 - Electricity | Fixed cost | -1,000.00 | January 31, 2023 |
| CC001 - HR | 10001 - Electricity | Fixed cost | 500.00 | January 31, 2023 |
| CC002 - Finance| 10001 - Electricity | Fixed cost | 500.00 | January 31, 2023 |
| CC099 - Default cost center| 10001 - Electricity | Variable cost | -9,000.00 | January 31, 2023 |
| CC001 - HR| 10001 - Electricity | Variable cost | 1,285.71 | January 31, 2023 |
| CC002 - Finance| 10001 - Electricity | Variable cost | 7,714.29 | January 31, 2023 |

For more information, see [Create and assign a cost distribution policy to a cost control unit](tasks/create-assign-cost-distribution-policy-cost-control-unit.md).

### Step 3: Process the overhead rate calculation

Use the overhead rate to charge one or more specific cost objects. The charge is based on a predetermined cost rate and the magnitude from the assigned allocation base.

#### Define the overhead rate

Cost object CC001 HR contributes to a set of internal projects. Create a statistical dimension member named **HR projects** to measure the consumed magnitude.

| Cost object | Hours |
|---|---|
| Proj 1 - Project 1 | 3 |
| Proj 2 - Project 2 | 1 |

Define a predetermined cost rate for the cost projects contribution.

| Cost object | Cost element | Cost behavior | Units | Rate |
|---|---|---|---|---|
| CC001 - HR | 10001 | Variable cost | 1 | 10 |

The following table shows the result when the HR projects are applied as an allocation base.

| Cost object | Magnitude | Cost element | Allocation factor | Amount |
|---|---|---|---|---|
| Proj 1 - Project 1 | 3 | 10001 | (3 ÷ 1) × 10.00 | 30.00 |
| Proj 2 - Project 2 | 1 | 10001 | (1 ÷ 1) × 10.00 | 10.00 |

##### Journal

| Journal | Journal type | Fiscal calendar period | Version |
|---|---|---|---|
| 00003 | Overhead rate calculation journal | Fiscal 2023 - Period 1 | Overhead calculation / 01-02-2023 11:51:00 PM / Ledger /2023 / Period 1 |

##### Journal entries (Journal entries for overhead rate calculation)

| Accounting date | Cost object | Magnitude |
|---|---|---|
| January 31, 2023 | Proj 1 - Internal Proj 1 | 3.00 |
| January 31, 2023 | Proj 2 - Internal Proj 2 | 1.00 |

##### Cost entries

| Cost object | Cost element | Cost behavior | Amount | Accounting date |
|---|---|---|---|---|
| CC0001 - HR | 10001 - Electricity | Variable cost | -30.00 | January 31, 2023 |
| Proj 1 - Internal Proj 1 | 10001 - Electricity | Variable cost | 30.00 | January 31, 2023 |
| CC001 - HR | 10001 | Electricity - Variable cost | -10.00 | January 31, 2023 |
| Proj 2 - Internal Proj 2 | 10001 - Electricity | Variable cost | 10.00 | January 31, 2023 |

For more information, see [Perform overhead calculation](cost-rollup.md#perform-overhead-calculation).

### Step 4: Process the cost allocation calculation

Allocation is used to allocate the balance of a cost object to other cost objects by applying an allocation base. Finance supports the reciprocal allocation method. In the reciprocal allocation method, the mutual services that auxiliary cost objects exchange are fully recognized. The system automatically determines the correct order to perform the allocations in. The balance of a cost object is allocated by a single allocation base. Allocations across cost objects dimensions and their respective members are supported. The allocation order is controlled by the cost control unit.

:::image type="content" source="./media/reciprocal-method.png" alt-text="Screenshot of the reciprocal allocation method between cost objects." lightbox="./media/reciprocal-method.png":::

#### Define the cost allocation

Here's a simple example that explains how you can trace the flow of cost. Cost object CC001 HR contributes to several cost objects. You create a statistical dimension member named HR services to measure the consumed magnitude.

| Cost object | HR services |
|---|---|
| CC002 - Finance | 35 |
| CC003 - Assembly | 55 |
| CC004 - Packaging | 10 |

Cost object CC002 Finance contributes to several cost objects. You create a statistical dimension member named Finance services to measure the consumed magnitude.

| Cost object | Finance services |
|---|---|
| CC003 - Assembly | 65 |
| CC004 - Packaging | 35 |

Cost object CC003 Assembly contributes to several cost objects. You create a statistical dimension member named Assembly services to measure the consumed magnitude.

| Cost object| Assembly services (hours) |
|---|---|
| Prod 1 - Product 1 | 60 |
| Prod 2 - Product 2 | 20 |

Cost object CC004 Packaging contributes to several cost objects. You create a statistical dimension member named Packaging services to measure the consumed magnitude.

| Cost object | Packaging services (hours) |
|---|---|
| Prod 1 - Product 1 | 80 |
| Prod 2 - Product 2 | 15 |

> [!NOTE]
> Statistical measures such as the production hours that a product consumes can be derived from source data. For more information, see [Statistical measure provider template](statistical-measure-provider-template.md#statistical-measure-provider-template). The following table shows the result when the HR services are applied as an allocation base for total cost (fixed cost and variable cost).

| Cost object | Magnitude | Allocation factor | Amount | Cost behavior |
|---|---|---|---|---|
| CC002 - Finance | 35 | (35 ÷ 100) × 500.00 | 175.00 | Fixed cost |
| CC003 - Assembly | 55 | (55 ÷ 100) × 500.00 | 275.00 | Fixed cost |
| CC004 - Packaging | 10 | (10 ÷ 100) × 500.00 | 50.00 | Fixed cost |
| CC002 - Finance | 35 | (35 ÷ 100) × 1,245.71 | 436.00 | Variable cost |
| CC003 - Assembly | 55 | (55 ÷ 100) × 1,245.71 | 685.14 | Variable cost |
| CC004 - Packaging | 10 | (10 ÷ 100) × 1,245.71 | 124.57 | Variable cost |

The following table shows the result when the Finance services are applied as an allocation base for total cost (fixed cost and variable cost).

| Cost object | Magnitude | Allocation factor | Amount | Cost behavior |
|---|---|---|---|---|
| CC003 - Assembly | 65 | (65 ÷ 100) × (500.00 + 175.00) | 438.75 | Fixed cost |
| CC004 - Packaging | 35 | (35 ÷ 100) × (500.00 + 175.00) | 236.25 | Fixed cost |
| CC003 - Assembly | 65 | (65 ÷ 100) × (7,714.29 + 436.00) | 5,297.69 | Variable cost |
| CC004 - Packaging | 35 | (35 ÷ 100) × (7,714.29 + 436.00) | 2,852.60 | Variable cost |

The following table shows the result when the Assembly services are applied as an allocation base for total cost (fixed cost and variable cost).

| Cost object | Magnitude | Allocation factor | Amount | Cost behavior |
|---|---|---|--|---|
| Prod 1 - Product 1 | 60 | (60 ÷ 80) × (275.00 + 438.75) | 535.31 | Fixed cost |
| Prod 2 - Product 2 | 20 | (20 ÷ 80) × (275.00 + 438.75) | 178.44 | Fixed cost |
| Prod 1 - Product 1 | 60 | (60 ÷ 80) × (5,297.69 + 685.14) | 4,487.12 | Variable cost |
| Prod 2 - Product 2 | 20 | (20 ÷ 80) × (5,297.69 + 685.14) | 1,495.71 | Variable cost |

The following table shows the result when the Packaging services are applied as an allocation base for total cost (fixed cost and variable cost).

| Cost object | Magnitude | Allocation factor | Amount | Cost behavior |
|---|---|---|--|---|
| Prod 1 - Product 1 | 80 | (80 ÷ 95) × (50.00 + 236.25) | 241.05 | Fixed cost |
| Prod 2 - Product 2 | 15 | (15 ÷ 95) × (50.00 + 236.25) | 45.20 | Fixed cost |
| Prod 1 - Product 1 | 80 | (80 ÷ 95) × (2,852.60 + 124.57) | 2,507.09 | Variable cost |
| Prod 2 - Product 2 | 15 | (15 ÷ 95) × (2,852.60 + 124.57) | 470.08 | Variable cost |

##### Journal entries (cost object balance journal entries)

| Journal | Journal type | Fiscal calendar period | Version |
|---|---|---|---|---|---|
| 00004 | Cost allocation journal | Fiscal 2023 - Period 1 | Overhead calculation / 01-02-2023 11:51:00 PM / Ledger /2023 / Period 1 |

##### Journal lines

| Accounting date | Cost object | Cost element | Cost behavior | Amount |
|---|---|---|---|---|---|---|
| January 31, 2023 | CC001 - HR | 10001 - Electricity | Fixed cost | 500.00 |
| January 31, 2023 | CC001 - HR | 10001 - Electricity | Variable cost | 1,245.71 |
| January 31, 2023 | CC002 - Finance | 10001 - Electricity | Fixed cost | 675.00 |
| January 31, 2023 | CC002 - Finance | 10001 - Electricity | Variable cost | 8,150.29 |
| January 31, 2023 | CC003 - Assembly | 10001 - Electricity | Fixed cost | 713.75 |
| January 31, 2023 | CC003 - Assembly | 10001 - Electricity | Variable cost | 5,982.83 |
| January 31, 2023 | CC003 - Packaging | 10001 - Electricity | Fixed cost | 286.25 |
| January 31, 2023 | CC003 - Packaging | 10001 - Electricity | Variable cost | 2,977.17 |
| January 31, 2023 | Prod 1 - Product 1 | 10001 - Electricity | Fixed cost | 776.36 |
| January 31, 2023 | Prod 1 - Product 1 | 10001 - Electricity | Variable cost | 6,994.21 |
| January 31, 2023 | Prod 2 - Product 1 | 10001 - Electricity | Fixed cost | 223.64 |
| January 31, 2023 | Prod 2 - Product 1 | 10001 -  Electricity | Variable cost | 1,965.79 |

##### Cost entries

| Cost object | Cost element | Cost behavior | Amount | Accounting date |
|---|---|---|---|---|
| CC001 - HR | 10001 - Electricity | Fixed cost | -500.00 | January 31, 2023 |
| CC002 - Finance | 10001 - Electricity | Fixed cost | 175.00 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Fixed cost | 275.00 | January 31, 2023 |
| CC004 - Packaging | 10001 - Electricity | Fixed cost | 50.00 | January 31, 2023 |
| CC001 - HR | 10001 - Electricity | Variable cost | -1,245.71 | January 31, 2023 |
| CC002 - Finance | 10001 - Electricity | Variable cost | 436.00 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Variable cost | 685.14 | January 31, 2023 |
| CC004 - Packaging | 10001 - Electricity | Variable cost | 124.57 | January 31, 2023 |
| CC002 - Finance | 10001 - Electricity | Fixed cost | -675.00 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Fixed cost | 438.75 | January 31, 2023 |
| CC004 - Packaging | 10001 - Electricity | Fixed cost | 236.25 | January 31, 2023 |
| CC002 - Finance | 10001 - Electricity | Variable cost | -8,150.29 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Variable cost | 5,297.69 | January 31, 2023 |
| CC004 - Packaging | 10001 - Electricity | Variable cost | 2,852.60 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Fixed cost | -713.75 | January 31, 2023 |
| Prod 1 - Product 1 | 10001 - Electricity | Fixed cost | 535.31 | January 31, 2023 |
| Prod 2 - Product 2 | 10001 - Electricity | Fixed cost | 178.44 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Variable cost | -5,982.83 | January 31, 2023 |
| Prod 1 - Product 1 | 10001 - Electricity | Variable cost | 4,487.12 | January 31, 2023 |
| Prod 2 - Product 2 | 10001 - Electricity | Variable cost | 1,495.71 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Fixed cost | -286.25 | January 31, 2023 |
| Prod 1 - Product 1 | 10001 - Electricity | Fixed cost | 241.05 | January 31, 2023 |
| Prod 2 - Product 2 | 10001 - Electricity | Fixed cost | 45.20 | January 31, 2023 |
| CC003 - Assembly | 10001 - Electricity | Variable cost | -2,977.17 | January 31, 2023 |
| Prod 1 - Product 1 | 10001 -  Electricity | Variable cost | 2,507.09 | January 31, 2023 |
| Prod 2 - Product 2 | 10001 - Electricity | Variable cost | 470.08 | January 31, 2023 |

## Conclusion

In financial accounting, you post a cost of 10,000.00 for electricity to a dummy cost center ID. This posting alerts cost accountants that they need to allocate this cost. In cost accounting, costs flow across organizational units and levels based on the policies and rules that you apply. Each cost associates with an allocation base that provides the best assessment for the allocation of costs.

Cost element | Cost object<br>CC099 | Cost object<br>CC001 | Cost object<br>CC002 | Cost object<br>CC003 | Cost object<br>CC004 | Cost object<br>Proj 1 | Cost object<br>Proj 2 | Cost object<br>Prod 1 | Cost object<br>Prod 2 | Total
---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:
10001 Electricity | 0.00 | 0.00 | 0.00 | 0.00 |  | 30.00 | 10.00 | 7,770.57 | 2,189.43 | 10,000.00 |
Unclassified | 0.00 |  |  |  |  |  |  |  |  |  |
Fixed cost | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |  |  | 776.36 | 223.64 | 1,000.00 |
Variable cost | 000 | 0.00 | 0.00 | 0.00 | 0.00 | 30.00 | 10.00 | 6,994.21 | 1,965.79 | 9,000.00 |

> [!NOTE]
> This article shows how a primary cost element, 10001 Electricity, flows through the cost objects. Therefore, you allocate this overhead cost to the lowest level in the organization. In other words, the cost objects at the lowest level bear the cost. If you require a visual flow of the cost between the cost objects, you can use the cost roll-up policy rules to visualize the flow of the cost. For more information, see [Cost rollup policy and overhead calculation](cost-rollup.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
