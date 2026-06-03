---
title: Allocation bases
description: Learn about allocation bases. Allocation bases are key components in Cost accounting and are mostly used to allocate overhead costs.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/27/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.industry: Manufacturing
ms.search.validFrom: 2016-11-30
ms.search.form: CAMDimensionMember, CAMAllocationBaseDetail, CAMFormulaAllocationBaseDetail, CAMAllocationBasePreview, CAMAllocationBase, CAMCostAllocationRule, CAMPredefinedMemberAllocationBase
ms.dyn365.ops.version: Version 1611
---

# Allocation bases

[!include [banner](../includes/banner.md)]

An allocation base is the basis on which Cost accounting allocates overhead costs. An allocation base can be a quantity, such as machine hours that are used, kilowatt hours (kWh) that are consumed, or square footage that is occupied. Allocation bases are mostly used to assign overhead costs to inventory that is produced. For example, an IT department allocates its expenses according to the number of computers that each department uses.

Cost accounting has three types of allocation bases:

- Predefined dimension member allocation bases
- Hierarchy allocation bases
- Formula allocation bases

## Predefined dimension member allocation bases

The system automatically creates predefined dimension member allocation bases when you create a dimension member of one of the following types:

- Statistical dimension members
- Cost element dimension members

> [!NOTE]
> The predefined dimension member allocation bases that are based on a cost element dimension member consider only the values from the data source provider, such as the general ledger or budget.

### Example 1: Use a cost element dimension member as the allocation base

This example shows how to create a cost allocation rule to allocate cost element 10002 (Employee insurance) to the balance that is recorded on cost element 10001 (Salaries). The allocation rule is based on the ratio of each department's salaries to total salaries.

In the general ledger, the chart of accounts is defined as follows.

| Chart of accounts | Main account | Description        | Main account type |
|------------------|--------------|--------------------|-------------------|
| Shared           | 10001        | Salaries           | Expense           |
| Shared           | 10002        | Employee insurance | Expense           |

Define a cost element dimension, and configure the data connector. After you import the data, Cost accounting creates the following entries.

**Cost element dimension members**

| Cost element dimension name | Cost element |  Description       | Type    |
|-----------------------------|--------------|--------------------|---------|
| Cost elements               | 10001        | Salaries           | Primary |
| Cost elements               | 10002        | Employee insurance | Primary |

**Predefined dimension member allocation bases**

| Name  | Description        | Cost element dimension |
|-------|--------------------|------------------------|
| 10001 | Salaries           | Cost elements          |
| 10002 | Employee insurance | Cost elements          |

In the general ledger, you post the following entries:

- The entries that show the Salaries main account come from the Payroll system and are posted to cost centers.
- You manually post the expense for employee insurance to a default cost center.

| Accounting date | Cost center |  Description        | Main account |  Description       | Amount in accounting currency |
|-----------------|-------------|---------------------|--------------|--------------------|-------------------------------|
| 03-01-2017      | CC001       | HR                  | 10001        | Salaries           | 2,000.00                      |
| 03-01-2017      | CC002       | FI                  | 10001        | Salaries           | 5,000.00                      |
| 03-01-2017      | CC003       | IT                  | 10001        | Salaries           | 3,000.00                      |
| 03-01-2017      | CC099       | Default cost center | 10002        | Employee insurance | 1,000.00                      |

After the general ledger source data is processed, Cost accounting creates the following entries.

**Cost entries**

| Cost object |  Description        | Cost element  |  Description       | Cost behavior   |Amount|Accounting date|
|-------------|---------------------|---------------|--------------------|-----------------|------|---------------|
| CC001       | HR                  | 10001         | Salaries           | Unclassified    |2,000.00|  03-01-2017    |
| CC002       | FI                  | 10001         | Salaries           | Unclassified    |5,000.00|     03-01-2017         |
| CC003       | IT                  | 10001         | Salaries           | Unclassified    |3,000.00|      03-01-2017        |
| CC099       | Default cost center | 10002         | Employee insurance | Unclassified    |1,000.00|      03-01-2017       |

In this simplified example, you create a cost allocation rule to allocate cost element 10002 (Employee insurance) relative to the balance that is recorded on cost element 10001 (Salaries).

**Cost distribution rule**

| Cost object dimension hierarchy node | Cost element dimension hierarchy node | Cost behavior | Allocation base |
|--------------------------------------|---------------------------------------|---------------|-----------------|
| CC099                                | 10002                                 | Unclassified  | 10001           |

**Perform overhead calculation**

After you apply cost element 10001 (Salaries) as the allocation base, the result of the overhead calculation is as follows.

| Cost object | Description | Magnitude |   Allocation factor         | Amount |
|-------------|-------------|-----------|-----------------------------|--------|
| CC001       | HR          | 2,000     | (2,000 ÷ 10,000) × 1,000.00 | 200.00 |
| CC002       | FI          | 5,000     | (5,000 ÷ 10,000) × 1,000.00 | 500.00 |
| CC003       | IT          | 3,000     | (3,000 ÷ 10,000) × 1,000.00 | 300.00 |

**Journal**

| Journal | Journal type                          | Fiscal calendar period | Year | Period   | Version                                                                 |
|---------|---------------------------------------|------------------------|------|----------|---------------------------------------------|
| 00001   | Cost distribution calculation journal | Fiscal                 | 2017 | Period 1 | Overhead calculation / 01-02-2017 11:51:00 PM / Ledger /2017 / Period 1 |

**Cost object balance journal entries**

| Accounting date | Cost object | Description         | Cost element | Description        | Cost behavior |  Amount  |
|-----------------|-------------|---------------------|--------------|--------------------|---------------|----------|
| 31-01-2017      | CC099       | Default cost center | 10002        | Employee insurance | Unclassified  | 1,000.00 |

**Cost entries**

| Cost object |  Description        | Cost element |    Description     | Cost behavior | Amount    | Accounting date |
|-------------|---------------------|--------------|--------------------|---------------|-----------|-----------------|
| CC099       | Default cost center | 10002        | Employee insurance | Unclassified  | -1,000.00 | 31-01-2017      |
| CC001       | HR                  | 10002        | Employee insurance | Unclassified  | 200.00    | 31-01-2017      |
| CC002       | FI                  | 10002        | Employee insurance | Unclassified  | 500.00    | 31-01-2017      |
| CC099       | IT                  | 10002        | Employee insurance | Unclassified  | 300.00    | 31-01-2017      |

### Example 2: Use a statistical dimension member as the allocation base

You can use statistical dimension members as allocation bases to define policies or report nonmonetary consumption by cost objects. You can manually create statistical dimension members or import them from a file by using the Data management import/export tool.

**Statistical dimension members**

| Statistical dimension name | Statistical element | Description               | Unit |
|----------------------------|---------------------|---------------------------|------|
| Statistical elements       | FTE                 | Full time employees       | Ea   |
| Statistical elements       | Electricity         | Electricity consumption   | kWh  |

When a statistical dimension member is saved, a corresponding record is created in the predefined dimension member allocation bases.

**Predefined dimension member allocation bases**

| Name        | Description             | Statistical element dimension |
|-------------|-------------------------|-------------------------------|
| FTE         | Full time employees     | Statistical elements          |
| Electricity | Electricity consumption | Statistical elements          |

Statistical measures can come from various sources:

- Electricity consumption can be measured by meters that are installed in different areas of the company.
- Tables hold statistical measures. For example, the HcmEmployment table holds a list of all employees and the cost centers that they work for.

| Name       | Cost center |  Description  | Worker type |
|------------|-------------|----|-------------|
| Employee A | CC001       | HR | Employee    |
| Employee B | CC002       | FI | Employee    |
| Employee C | CC002       | FI | Employee    |
| Employee D | CC003       | IT | Employee    |
| Employee F | CC003       | IT | Employee    |

> [!NOTE]
> You can use all the tables that contain financial dimensions as sources for statistical measures.

Cost accounting supports a collection of statistical measures by using the following data connections:

- Data management import/export tool
- Statistical measures

To pull statistical measures from the system, a statistical measure provider template is required. For more information, see Statistical measure provider template. (Will add a link once this article is written.)

**Statistical measure provider templates**

| Name  | Function | Source table  | Sum field      | Date field     |
|-------|----------|---------------|----------------|----------------|
| FTE’s | Count    | HcmEmployment | Not applicable | Not applicable |

After the system processes the statistical measure source data, it creates the following entries in Cost accounting.

**Statistical entries**

| Cost object | Description      | Accounting date | Statistical dimension member | Description         | Magnitude |
|-------------|------------------|-----------------|------------------------------|---------------------|-----------|
| CC001       | HR               | 31-01-2017      | FTE’s                        | Full time employees | 1.00      |
| CC002       | FI               | 31-01-2017      | FTE’s                        | Full time employees | 2.00      |
| CC003       | IT               | 31-01-2017      | FTE’s                        | Full time employees | 2.00      |

Here is an example of a cost distribution rule if the FTE’s predefined dimension member allocation basis is assigned as the allocation base in it.

| Cost object | Description  | Magnitude | Allocation factor |
|-------------|------|-----------|-------------------|
| CC001       | HR   | 1.00      | (1/5) × Amount    |
| CC002       | FI   | 2.00      | (2/5) × Amount    |
| CC003       | IT   | 2.00      | (2/5) × Amount    |

Use the **Imported statistical measures** data entity to import statistical measures into Cost accounting. You can also use the Data management import/export tool. In Excel, the consumption of electricity is recorded as follows.

| Accounting date | Dimension member | Magnitude | Source identifier |
|-----------------|------------------|-----------|-------------------|
| 31-01-2017      | CC001            | 2,450.00  | Electricity       |
| 31-01-2017      | CC002            | 4,100.00  | Electricity       |
| 31-01-2017      | CC003            | 15,000.00 | Electricity       |

After the system processes the statistical measure source data, it creates the following entries in Cost accounting.

**Statistical entries**

| Cost object | Name   | Accounting date | Statistical dimension member |    Description          | Magnitude |
|-------------|----|-----------------|------------------------------|-------------------------|-----------|
| CC001       | HR | 31-01-2017      | Electricity                  | Electricity consumption | 2,450.00  |
| CC002       | FI | 31-01-2017      | Electricity                  | Electricity consumption | 4,100.00  |
| CC003       | IT | 31-01-2017      | Electricity                  | Electricity consumption | 15,000.00 |

Here's an example of a cost distribution rule if you assign the **Electricity** predefined dimension member allocation basis as the allocation base.

| Cost object | Description  | Magnitude | Allocation factor          |
|-------------|------|-----------|----------------------------|
| CC001       | HR   | 2,450.00  | (2,450 ÷ 21,550) × Amount  |
| CC002       | FI   | 4,100.00  | (4,100 ÷ 21,550) × Amount  |
| CC003       | IT   | 15,000.00 | (15,000 ÷ 21,550) × Amount |

## Hierarchy allocation bases

Cost accountants can manually create hierarchy allocation bases by applying a cost object dimension hierarchy node to an existing allocation base. By using this method, you can limit the range of the original predefined dimension member allocation basis. You can use one predefined dimension member allocation basis to create several hierarchy allocation bases. You can maintain ranges in the cost object dimension hierarchy that you associate with the hierarchy allocation bases.

### Example: Hierarchy allocation bases that are based on full-time employees in the organization

Here's an example of a cost object dimension hierarchy that you can create to describe a simplified organization.

| Hierarchy name | Node level 0 | Node level 1 | Node level 2 | Dimension members |
|----------------|--------------|--------------|--------------|-------------------|
| Organization   | CEO          | CFO          | FICO         | CC001             |
| Organization   | CEO          | CFO          | HR           | CC002             |
| Organization   | CEO          | CIO          | IT           | CC003             |

The FTE’s predefined dimension member allocation basis that was created in the previous section holds the following entries.

**Statistical entries**

| Cost object | Description  | Accounting date | Statistical dimension member | Description | Magnitude |
|-------------|------|-----------------|------------------------------|---------------------|-----------|
| CC001       | HR   | 31-01-2017      | FTE’s                        | Full time employees | 1.00      |
| CC002       | FI   | 31-01-2017      | FTE’s                        | Full time employees | 2.00      |
| CC003       | IT   | 31-01-2017      | FTE’s                        | Full time employees | 2.00      |

A cost must be distributed between cost centers that report to the organization's chief financial officer (CFO). It's acknowledged that the correct allocation ratio is the number of full-time employees (FTEs) by cost center.

**Hierarchy allocation bases**

| Name                  | Allocation base | Cost object dimension hierarchy | Cost object dimension hierarchy node |
|-----------------------|-----------------|---------------------------------|--------------------------------------|
| Number of FTEs in CFO | FTE’s           | Organization                    | CFO                                  |

A Preview function lets you validate the hierarchy allocation basis that you create, based on statistical entries in the system.

**Allocation base details**

| Cost object | Description  |  Magnitude |
|-------------|------|------------|
| CC001       | HR   | 1.00       |
| CC002       | FI   | 2.00       |

Here's an example of a cost distribution rule if the Number of FTEs in CFO hierarchy allocation basis is assigned as the allocation base in it.

| Cost object | Description  | Magnitude | Allocation factor |
|-------------|------|-----------|-------------------|
| CC001       | HR   | 1.00      | (1/3) × Amount    |
| CC002       | FI   | 2.00      | (2/3) × Amount    |

## Formula allocation bases

Formula allocation bases let you define advanced formulas to achieve the correct allocation basis. You can manually create formula allocation bases.

When you create a formula allocation base, you select which statistical dimension and cost element dimension should be the basis for the formula. You can use all allocation bases that come from the previously selected dimensions in a formula allocation base.

> [!NOTE]
> You can use previously defined formula allocation bases to define a new formula allocation base.

In formula allocation base factors, you create an alias and associate it with either an allocation base or a constant. Use the aliases to define the formula.

To define your formula, use the following operators.

| Symbols | Text           |
|---------|----------------|
| ( )     | Parentheses    |
| \<      | Smaller than   |
| \>      | Larger than    |
| +       | Addition       |
| –       | Subtraction    |
| \*      | Multiplication |

Traditional **IF** statements aren't supported. However, you can create statements and validate whether they're true.

| Statement | Validation | Result |
|-----------|------------|--------|
| a \> b    | True       | 1      |
| a \> b    | False      | 0      |

### Example 1: A simple formula

Electricity bills often consist of two parts:

- A fixed fee for being connected to the grid
- A cost that is associated with consumption per kWh

The Electricity predefined dimension member allocation basis already defined holds these values.

**Statistical entries**

| Cost object | Name | Accounting date | Statistical dimension member | Description             | Magnitude |
|-------------|------|-----------------|------------------------------|-------------------------|-----------|
| CC001       | HR   | 31-01-2017      | Electricity                  | Electricity consumption | 2,450.00  |
| CC002       | FI   | 31-01-2017      | Electricity                  | Electricity consumption | 4,100.00  |
| CC003       | IT   | 31-01-2017      | Electricity                  | Electricity consumption | 15,000.00 |

If you need to spread the fixed fee evenly over cost objects that consume electricity, you have two options for allocating the costs:

- Create a new predefined allocation base, Electricity fixed, and then apply a statistical measure of 1.00 for each cost object that consumed electricity.
- Create a formula allocation base, Electricity fixed, that takes advantage of the Electricity predefined allocation base that's already defined in the system. The benefit of this option is that you only need to load data into Cost accounting for one Electricity statistical dimension member.

**Formula allocation base**

| Name              | Cost element dimension | Statistical dimension | Formula |
|-------------------|------------------------|-----------------------|---------|
| Electricity fixed |                        | Statistical elements  |         |

Before you can fill the **Formula** field, you must specify the alias that should be used in the formula.

**Formula allocation base factors**

| Alias | Constant | Allocation base |
|-------|----------|-----------------|
| a     |          | Electricity     |
| b     | 0.01     |                 |

Note that 0 (zero) isn't supported as a constant.

**Formula allocation base**

| Name              | Cost element dimension | Statistical dimension | Formula |
|-------------------|------------------------|-----------------------|---------|
| Electricity fixed |                        | Statistical elements  | a \> b  |

A Preview function lets you validate the formula allocation base that you created, based on statistical entries in the system.

**Allocation base details**

| Cost object | Description  | Formula           | Magnitude |
|-------------|------|-------------------|-----------|
| CC001       | HR   | 2,450.00 \> 0.01  | 1.00      |
| CC002       | FI   | 4,100.00 \> 0.01  | 1.00      |
| CC003       | IT   | 15,000.00 \> 0.01 | 1.00      |

Here's an example of a cost distribution rule if you assign the Electricity formula allocation base as the allocation base in it.

**Cost object magnitude allocation factor**

| Cost object | Name | Magnitude |  Allocation factor |
|-------------|------|-----------|--------------------|
| CC001       | HR   | 1.00      | (1/3) × Amount     |
| CC002       | FI   | 1.00      | (1/3) × Amount     |
| CC003       | IT   | 1.00      | (1/3) × Amount     |

### Example 2: An advanced formula

For this example, the cost of electricity shouldn't just follow the actual electricity that is consumed in kWh. Management wants to incorporate an incentive for lowering electricity usage.

| Rule              | Rate |
|-------------------|------|
| a <= 10,000.00 kWh | 0.75 |
| a > 10,000.00 kWh  | 1.15 |

Create a new formula allocation base named **Electricity usage**.

**Formula allocation base**

| Name              | Cost element dimension | Statistical dimension | Formula |
|-------------------|------------------------|-----------------------|---------|
| Electricity usage |                        | Statistical elements  |         |

Before you can fill the **Formula** field, you must specify the alias that should be used in the formula.

**Formula allocation base factors**

| Alias | Constant  | Allocation base |
|-------|-----------|-----------------|
| a     |           | Electricity     |
| b     | 10,000.00 |                 |
| c     | 0.75      |                 |
| d     | 1.15      |                 |

**Formula allocation base**

| Name              | Cost element dimension | Statistical dimension | Formula                                                    |
|-------------------|------------------------|-----------------------|------------------------------------------------------------|
| Electricity fixed |                        | Statistical elements  | ((a \> b) × ((b × c) + (a – b) × d)) + ((a \<= b] × a × c) |

A Preview function lets you validate the formula allocation base that you created, based on statistical entries in the system.

**Allocation base details**

| Cost object |  Name  | Formula                                                                                                                             | Magnitude |
|-------------|----|-------------------------------------------------------------------------------------------------------------------------------------|-----------|
| CC001       | HR | ((2,450.00 \> 10.000.00) × ((10,000.00 × 0.75) + (2,450.00 – 10,000.00) × 1.15)) + ((2,450.00 \<= 10,000.00) × 2,450.00 × 0.75)     | 1,837.50  |
| CC002       | FI | ((4,100.00 \> 10.000.00) × ((10,000.00 × 0.75) + (4,100.00 – 10,000.00) × 1.15)) + ((4,100.00 \<= 10,000.00) × 4,100.00 × 0.75)     | 3,075.00  |
| CC003       | IT | ((15,000.00 \> 10.000.00) × ((10,000.00 × 0.75) + (15,000.00 – 10,000.00) × 1.15)) + ((15,000.00 \<= 10,000.00) × 15,000.00 × 0.75) | 1,3250.00 |

Here's a closer look at the formula for CC003 (IT):

((15,000.00 \> 10,000.00) × ((10,000.00 × 0.75) + (15,000.00 – 10,000.00) × 1.15)) + ((15,000.00 \<= 10,000.00) × 15,000.00 × 0.75) = 13,250.00

(1 × (7,500.00 + 5,000.00 × 1.15)) + (0 × 15,000.00 × 0.75)

1 × 7,500.00 + 5,750.00 + 0

Here's an example of a cost distribution rule if you assign the **Electricity fixed** formula allocation base as the allocation base.

| Cost object | Description | Magnitude |        Allocation factor         |
|-------------|-------------|-----------|----------------------------------|
|    CC001    |     HR      | 1,837.50  | (1,837.50 ÷ 18,162.50) × Amount  |
|    CC002    |     FI      | 3,075.00  | (3,075.00 ÷ 18,162.50) × Amount  |
|    CC003    |     IT      | 13,250.00 | (13,250.00 ÷ 18,162.50) × Amount |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
