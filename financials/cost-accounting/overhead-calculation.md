---
# required metadata

title: Overhead calculation
description: This topic describes the typical processes for calculating and allocating overhead costs.
author: YuyuScheller
manager: AnnBe
ms.date: 2017-03-10 15 - 36 - 15
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMActualVersion, CAMBudgetVersion, CAMOverheadCalculation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272163
ms.assetid: 93119afb-47ed-4786-ba44-ba93576d3e28
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Overhead calculation

This topic describes the typical processes for calculating and allocating overhead costs.

Term definition
---------------

Overhead costs are the costs that are incurred in order to run a business, but that can't be directly attributed to any specific business activity, product, or service. Overhead costs provide critical support for the generation of profit-making activities. Here are some examples of overhead costs:

-   Rent
-   Electricity
-   Administrative salaries

## Overhead calculation overview
Overhead calculation runs the cost accounting policies in the correct order. You can run overhead calculation multiple times for the same fiscal period if cost accounting policies have been changed or specific errors have been detected. Each run of the overhead calculation is stored and receives a unique version ID that lets you compare the calculations in various versions. The cost entries that the overhead calculation generates receive an accounting date. This accounting date matches the end date of the fiscal period that is used in the calculation. The unique version ID consists of the following elements:

-   Version type
-   Date and time
-   Cost accounting ledger
-   Fiscal year
-   Fiscal period

Overhead calculation is run independently of the version. Therefore, you can calculate the Budget version before the Actual version. Overhead calculation consists of four steps, as shown in the following illustration. In each step, a journal header is created that has journal entries. This journal header keeps the input data for each calculation step. Policies and rules are applied to each journal line, and cost entries are generated as output. Therefore, you always have full traceability. [![Overhead calculation](./media/period-cost-calculation.png)](./media/period-cost-calculation.png)

## Calculate and allocate the Electricity overhead cost
In Financial accounting, some costs, such as electricity, are registered as a lump sum. Therefore, detailed managerial insight isn't provided for Cost accounting. In Cost accounting, to provide correct managerial insight across all organizational units and levels, costs must flow through the organizational units. This flow must be based on either an accurate record of the consumption or a fair assessment. In the general ledger, an electricity cost can be posted as shown in the following table.

<table>
<thead>
<tr>
<th>Accounting date</th>
<th colspan="2">Cost center</th>
<th colspan="2">Main account</th>
<th>Amount in the accounting currency</th>
</tr>
</thead>
<tbody>
<tr>
<td>January 3, 2017</td>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>10,000.00</td>
</tr>
</tbody>
</table>

### Step 1: Process the cost behavior calculation

By default, when cost entries are imported from the source data, they receive the **Unclassified** cost behavior classification in Cost accounting. By applying cost behavior policy rules, you can reclassify cost entries as either **Fixed cost** or **Variable cost**.

#### Define the cost behavior rule

In some cases, part of the cost is a fixed fee, and the remaining cost is based on consumption. Electricity bills often match this definition. After you pay a specific fixed fee, you pay for consumption per kilowatt hour (Kwh). For example, if the fixed cost fee is 1,000.00, here is how the cost behavior rule is defined:

-   Fixed amount 1,000.00
    -   0 &lt;= 1,000.00 = Fixed
    -   1000,01 &lt; N = Variable

##### Journal

<table>
<thead>
<tr>
<th>Journal</th>
<th>Journal type</th>
<th colspan="3">Fiscal calendar period</th>
<th>Version</th>
</tr>
</thead>
<tbody>
<tr>
<td>00001</td>
<td>Cost behavior calculation journal</td>
<td>Fiscal</td>
<td>2017</td>
<td>Period 1</td>
<td>Overhead calculation / 01-02-2017 11:51:00 PM / Ledger /2017 / Period 1</td>
</tr>
</tbody>
</table>

##### Journal entries (Cost object balance journal entries)

<table>
<thead>
<tr>
<th>Accounting date</th>
<th colspan="2">Cost object</th>
<th colspan="2">Cost element</th>
<th>Cost behavior</th>
<th>Amount</th>
</tr>
</thead>
<tbody>
<tr>
<td>January 3, 2017</td>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>Unclassified</td>
<td>10,000.00</td>
</tr>
</tbody>
</table>

##### Cost entries

<table>
<thead>
<tr>
<th colspan="2">Cost object</th>
<th colspan="2">Cost element</th>
<th>Cost behavior</th>
<th>Amount</th>
<th>Accounting date</th>
</tr>
</thead>
<tbody>
<tr>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>Unclassified</td>
<td>10,000.00</td>
<td>January 3, 2017</td>
</tr>
<tr>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>Unclassified</td>
<td>-10,000.00</td>
<td>January 31, 2017</td>
</tr>
<tr>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>Fixed cost</td>
<td>1,000.00</td>
<td>January 31, 2017</td>
</tr>
<tr>
<td>CC099</td>
<td>Default cost center</td>
<td>10001</td>
<td>Electricity</td>
<td>Variable cost</td>
<td>9,000.00</td>
<td>January 31, 2017</td>
</tr>
</tbody>
</table>

For detailed information about cost behavior, see Cost behavior policy. (Note that this topic isn't competed yet but is coming soon.)

### Step 2: Process the cost distribution calculation

Cost distribution is used to redistribute cost from one cost object to one or more other cost objects by applying a relevant allocation base. Cost distribution and cost allocation differ in that cost distribution always occurs at the level of the primary cost element of the original cost.

#### Define the cost distribution rule

In Financial accounting, electricity costs are often registered as a lump sum. In Cost accounting, this approach isn't detailed enough. The variable cost should be distributed to the individual cost objects on a fair basis. The most logical allocation basis is the consumption of electricity (Kwh). A statistical dimension member that is named Electricity is created, and electricity consumption is recorded. By default, all statistical dimension members become available as allocation bases.

<table>
<thead>
<tr>
<th colspan="2">Cost object</th>
<th>Kwh</th>
</tr>
</thead>
<tbody>
<tr>
<td>CC001</td>
<td>HR</td>
<td>1,000</td>
</tr>
<tr>
<td>CC002</td>
<td>Finance</td>
<td>6,000</td>
</tr>
<tr>
<td>CC003</td>
<td>Assembly</td>
<td>0</td>
</tr>
</tbody>
</table>

The following table shows the result when electricity consumption is applied as an allocation base for variable costs.

<table>
<thead>
<tr>
<th colspan="2">Cost object</th>
<th>Magnitude</th>
<th>Allocation factor</th>
<th>Amount</th>
</tr>
</thead>
<tbody>
<tr>
<td>CC001</td>
<td>HR</td>
<td>1,000</td>
<td>(1,000 ÷ 7,000) × 9,000.00</td>
<td>1,285.71</td>
</tr>
<tr>
<td>CC002</td>
<td>Finance</td>
<td>6,000</td>
<td>(6,000 ÷ 7,000) × 9,000.00</td>
<td>7,714.29</td>
</tr>
<tr>
<td>CC003</td>
<td>Assembly</td>
<td>0</td>
<td>(0 ÷ 7,000) × 9,000.00</td>
<td>0.00</td>
</tr>
</tbody>
</table>

The fixed cost should be distributed evenly to the individual cost objects that have consumed electricity. You can achieve this result by using the Electricity statistical dimension member in a formula allocation base: (Electricity &gt; 0.00) The following table shows the result when electricity consumption is applied as an allocation base for variable costs.

<table>
<thead>
<tr>
<th colspan="2">Cost object</th>
<th>Formula</th>
<th>Magnitude</th>
<th>Allocation factor</th>
<th>Amount</th>
</tr>
</thead>
<tbody>
<tr>
<td>CC001</td>
<td>HR</td>
<td>(1,000 &gt; 0.00)</td>
<td>1</td>
<td>(1 ÷ 2) × 1,000.00</td>
<td>500.00</td>
</tr>
<tr>
<td>CC002</td>
<td>Finance</td>
<td>(6,000 &gt; 0.00)</td>
<td>1</td>
<td>(1 ÷ 2) × 1,000.00</td>
<td>500.00</td>
</tr>
<tr>
<td>CC003</td>
<td>Assembly</td>
<td>(0 &gt; 0.00)</td>
<td>0</td>
<td>(0 ÷ 2) × 1,000.00</td>
<td>0.00</td>
</tr>
</tbody>
</table>

##### Journal

Journal

Journal type

Fiscal calendar period

Version

00002

Cost distribution calculation journal

Fiscal

2017

Period 1

Overhead calculation / 01-02-2017 11:51:00 PM / Ledger /2017 / Period 1

##### Journal entries (Cost object balance journal entries)

Accounting date

Cost object

Cost element

Cost behavior

Amount

January 31, 2017

CC099

Default cost center

10001

Electricity

Fixed cost

1,000.00

January 31, 2017

CC099

Default cost center

10001

Electricity

Variable cost

9,000.00

##### Cost entries

Cost object

Cost element

Cost behavior

Amount

Accounting date

CC099

Default cost center

10001

Electricity

Fixed cost

-1,000.00

January 31, 2017

CC001

HR

10001

Electricity

Fixed cost

500.00

January 31, 2017

CC002

Finance

10001

Electricity

Fixed cost

500.00

January 31, 2017

CC099

Default cost center

10001

Electricity

Variable cost

-9,000.00

January 31, 2017

CC001

HR

10001

Electricity

Variable cost

1,285.71

January 31, 2017

CC002

Finance

10001

Electricity

Variable cost

7,714.29

January 31, 2017

For detailed information about cost distribution and allocation bases, see Cost distribution policy and Allocation bases. (Note that this topic isn't competed yet but is coming soon.)

### Step 3: Process the overhead rate calculation

The overhead rate is used to charge one or more specific cost objects. The charge is based on a predetermined cost rate and the magnitude from the assigned allocation base. 

#### Define the overhead rate

Cost object CC001 HR contributes to a set of internal projects. A statistical dimension member that is named HR projects is created to measure the consumed magnitude.

Cost object

Hours

Proj 1

Project 1

3

Proj 2

Project 2

1

A predetermined cost rate for the cost projects contribution has been defined.

Cost object

Cost element

Cost behavior

Units

Rate

CC001

HR

10001

Variable cost

1

10

The following table shows the result when the HR projects are applied as an allocation base.

Cost object

Magnitude

Cost element

Allocation factor

Amount

Proj 1

Project 1

3

10001

(3 ÷ 1) × 10.00

30.00

Proj 2

Project 2

1

10001

(1 ÷ 1) × 10.00

10.00

##### Journal

Journal

Journal type

Fiscal calendar period

Version

00003

Overhead rate calculation journal

Fiscal

2017

Period 1

Overhead calculation / 01-02-2017 11:51:00 PM / Ledger /2017 / Period 1

##### Journal entries (Journal entries for overhead rate calculation)

Accounting date

Cost object

Magnitude

January 31, 2017

Proj 1

Internal Proj 1

3.00

January 31, 2017

Proj 2

Internal Proj 2

1.00

##### Cost entries

Cost object

Cost element

Cost behavior

Amount

Accounting date

CC0001

HR

10001

Electricity

Variable cost

-30.00

January 31, 2017

Proj 1

Internal Proj 1

10001

Electricity

Variable cost

30.00

January 31, 2017

CC001

HR

10001

Electricity

Variable cost

-10.00

January 31, 2017

Proj 2

Internal Proj 2

10001

Electricity

Variable cost

10.00

January 31, 2017

For detailed information about overhead rate policy, see Overhead rate policy and Allocation bases. (Note that this topic isn't competed yet but is coming soon.)

### Step 4: Process the cost allocation calculation

Allocation is used to allocate the balance of a cost object to other cost objects by applying an allocation base. Microsoft Dynamics 365 for Operations supports the reciprocal allocation method. In the reciprocal allocation method, the mutual services that auxiliary cost objects exchange are fully recognized. The system automatically determines the correct order to perform the allocations in. The balance of a cost object is allocated by a single allocation base. Allocations across cost objects dimensions and their respective members are supported. The allocation order is controlled by the cost control unit. [![](./media/reciprocal-method.png)](./media/reciprocal-method.png)

#### Define the cost allocation

Here is a simple example that explains how you can trace the flow of cost. Cost object CC001 HR contributes to several cost objects. A statistical dimension member that is named HR services is created to measure the consumed magnitude.

Cost object

HR services

CC002

Finance

35

CC003

Assembly

55

CC004

Packaging

10

Cost object CC002 Finance contributes to several cost objects. A statistical dimension member that is named Finance services is created to measure the consumed magnitude.

Cost object

Finance services

CC003

Assembly

65

CC004

Packaging

35

Cost object CC003 Assembly contributes to several cost objects. A statistical dimension member that is named Assembly services is created to measure the consumed magnitude.

Cost object

Assembly services (hours)

Prod 1

Product 1

60

Prod 2

Product 2

20

Cost object CC004 Packaging contributes to several cost objects. A statistical dimension member that is named Packaging services is created to measure the consumed magnitude.

Cost object

Packaging services (hours)

Prod 1

Product 1

80

Prod 2

Product 2

15

**Note:** In Dynamics 365 for Operations, statistical measures such as the production hours that a product consumes can be derived from source data. For more detailed information about statistical measure providers, see Statistical measure provider template. (Note that this topic isn't completed yet but is coming soon.) The following table shows the result when the HR services are applied as an allocation base for total cost (fixed cost and variable cost).

Cost object

Magnitude

Allocation factor

Amount

Cost behavior

CC002

Finance

35

(35 ÷ 100) × 500.00

175.00

Fixed cost

CC003

Assembly

55

(55 ÷ 100) × 500.00

275.00

Fixed cost

CC004

Packaging

10

(10 ÷ 100) × 500.00

50.00

Fixed cost

CC002

Finance

35

(35 ÷ 100) × 1,245.71

436.00

Variable cost

CC003

Assembly

55

(55 ÷ 100) × 1,245.71

685.14

Variable cost

CC004

Packaging

10

(10 ÷ 100) × 1,245.71

124.57

Variable cost

The following table shows the result when the Finance services are applied as an allocation base for total cost (fixed cost and variable cost).

Cost object

Magnitude

Allocation factor

Amount

Cost behavior

CC003

Assembly

65

(65 ÷ 100) × (500.00 + 175.00)

438.75

Fixed cost

CC004

Packaging

35

(35 ÷ 100) × (500.00 + 175.00)

236.25

Fixed cost

CC003

Assembly

65

(65 ÷ 100) × (7,714.29 + 436.00)

5,297.69

Variable cost

CC004

Packaging

35

(35 ÷ 100) × (7,714.29 + 436.00)

2,852.60

Variable cost

The following table shows the result when the Assembly services are applied as an allocation base for total cost (fixed cost and variable cost).

Cost object

Magnitude

Allocation factor

Amount

Cost behavior

Prod 1

Product 1

60

(60 ÷ 80) × (275.00 + 438.75)

535.31

Fixed cost

Prod 2

Product 2

20

(20 ÷ 80) × (275.00 + 438.75)

178.44

Fixed cost

Prod 1

Product 1

60

(60 ÷ 80) × (5,297.69 + 685.14)

4,487.12

Variable cost

Prod 2

Product 2

20

(20 ÷ 80) × (5,297.69 + 685.14)

1,495.71

Variable cost

The following table shows the result when the Packaging services are applied as an allocation base for total cost (fixed cost and variable cost).

Cost object

Magnitude

Allocation factor

Amount

Cost behavior

Prod 1

Product 1

80

(80 ÷ 95) × (50.00 + 236.25)

241.05

Fixed cost

Prod 2

Product 2

15

(15 ÷ 95) × (50.00 + 236.25)

45.20

Fixed cost

Prod 1

Product 1

80

(80 ÷ 95) × (2,852.60 + 124.57)

2,507.09

Variable cost

Prod 2

Product 2

15

(15 ÷ 95) × (2,852.60 + 124.57)

470.08

Variable cost

##### Journal entries (cost object balance journal entries)

Journal

Journal type

Fiscal calendar period

Version

00004

Cost allocation journal

Fiscal

2017

Period 1

Overhead calculation / 01-02-2017 11:51:00 PM / Ledger /2017 / Period 1

##### Journal lines

Accounting date

Cost object

Cost element

Cost behavior

Amount

January 31, 2017

CC001

HR

10001

Electricity

Fixed cost

500.00

January 31, 2017

CC001

HR

10001

Electricity

Variable cost

1,245.71

January 31, 2017

CC002

Finance

10001

Electricity

Fixed cost

675.00

January 31, 2017

CC002

Finance

10001

Electricity

Variable cost

8,150.29

January 31, 2017

CC003

Assembly

10001

Electricity

Fixed cost

713.75

January 31, 2017

CC003

Assembly

10001

Electricity

Variable cost

5,982.83

January 31, 2017

CC003

Packaging

10001

Electricity

Fixed cost

286.25

January 31, 2017

CC003

Packaging

10001

Electricity

Variable cost

2,977.17

January 31, 2017

Prod 1

Product 1

10001

Electricity

Fixed cost

776.36

January 31, 2017

Prod 1

Product 1

10001

Electricity

Variable cost

6,994.21

January 31, 2017

Prod 2

Product 1

10001

Electricity

Fixed cost

223.64

January 31, 2017

Prod 2

Product 1

10001

Electricity

Variable cost

1,965.79

##### Cost entries

Cost object

Cost element

Cost behavior

Amount

Accounting date

CC001

HR

10001

Electricity

Fixed cost

-500.00

January 31, 2017

CC002

Finance

10001

Electricity

Fixed cost

175.00

January 31, 2017

CC003

Assembly

10001

Electricity

Fixed cost

275.00

January 31, 2017

CC004

Packaging

10001

Electricity

Fixed cost

50,00

January 31, 2017

CC001

HR

10001

Electricity

Variable cost

-1,245.71

January 31, 2017

CC002

Finance

10001

Electricity

Variable cost

436.00

January 31, 2017

CC003

Assembly

10001

Electricity

Variable cost

685.14

January 31, 2017

CC004

Packaging

10001

Electricity

Variable cost

124.57

January 31, 2017

CC002

Finance

10001

Electricity

Fixed cost

-675.00

January 31, 2017

CC003

Assembly

10001

Electricity

Fixed cost

438.75

January 31, 2017

CC004

Packaging

10001

Electricity

Fixed cost

236.25

January 31, 2017

CC002

Finance

10001

Electricity

Variable cost

-8,150.29

January 31, 2017

CC003

Assembly

10001

Electricity

Variable cost

5,297.69

January 31, 2017

CC004

Packaging

10001

Electricity

Variable cost

2,852.60

January 31, 2017

CC003

Assembly

10001

Electricity

Fixed cost

-713.75

January 31, 2017

Prod 1

Product 1

10001

Electricity

Fixed cost

535.31

January 31, 2017

Prod 2

Product 2

10001

Electricity

Fixed cost

178.44

January 31, 2017

CC003

Assembly

10001

Electricity

Variable cost

-5,982.83

January 31, 2017

Prod 1

Product 1

10001

Electricity

Variable cost

4,487.12

January 31, 2017

Prod 2

Product 2

10001

Electricity

Variable cost

1,495.71

January 31, 2017

CC003

Assembly

10001

Electricity

Fixed cost

-286.25

January 31, 2017

Prod 1

Product 1

10001

Electricity

Fixed cost

241.05

January 31, 2017

Prod 2

Product 2

10001

Electricity

Fixed cost

45.20

January 31, 2017

CC003

Assembly

10001

Electricity

Variable cost

-2,977.17

January 31, 2017

Prod 1

Product 1

10001

Electricity

Variable cost

2,507.09

January 31, 2017

Prod 2

Product 2

10001

Electricity

Variable cost

470.08

January 31, 2017

## Conclusion
In Financial accounting, a cost of 10,000.00 for Electricity is posted to a dummy cost center ID. Therefore, cost accountants will know that this cost must be allocated. In Cost accounting, the costs flow across organizational units and levels, based on the policies and rules that are applied. Each cost has been associated with an allocation base that provides the best assessment for the allocation of costs.

Cost element

Cost object

Total

CC099

CC001

CC002

CC003

CC004

Proj 1

Proj 2

Prod 1

Prod 2

10001 Electricity

**0.00**

**0.00**

**0.00**

**0.00**

**30.00**

**10.00**

**7,770.57**

**2,189.43**

**10,000.00**

Unclassified

0.00

Fixed cost

0.00

0.00

0.00

0.00

0.00

776.36

223.64

**1,000.00**

Variable cost

000

0.00

0.00

0.00

0.00

30.00

10.00

6,994.21

1,965.79

**9,000.00**

**Note:** This topic shows how a primary cost element, 10001 Electricity, flows through the cost objects. Therefore, this overhead cost is allocated to the lowest level in the organization. In other words, the cost objects at the lowest level bear the cost. If you require a visual flow of the cost between the cost objects, you can use the cost roll-up policy rules to visualize the flow of the cost. For more detailed information, see Cost roll-up policy. (Note that this topic isn't competed yet but is coming soon.)

