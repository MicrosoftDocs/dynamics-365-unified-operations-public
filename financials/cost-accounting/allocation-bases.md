---
# required metadata

title: Allocation bases
description: This topic provides information about allocation bases. Allocation bases are key components in Cost accounting and are mostly used to allocate overhead costs. 
author: YuyuScheller
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMDimensionMember
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 223174
ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: YuyuScheller
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Allocation bases 

[!include[banner](../includes/banner.md)]

An allocation base is the basis on which Cost accounting allocates overhead costs. An allocation base can be a quantity, such as machine hours that are used, kilowatt hours (kWh) that are consumed, or square footage that is occupied. Allocation bases are mostly used to assign overhead costs to inventory that is produced. For example, an IT department allocates its expenses according to the number of computers that each department uses.

There are three types of allocation bases in Cost accounting:

- Predefined dimension member allocation bases
- Hierarchy allocation bases
- Formula allocation bases

## Predefined dimension member allocation bases

The predefined dimension member allocation bases are created automatically when a dimension member of one the following types is created:

- Statistical dimension members
- Cost element dimension members

> [!NOTE]
> The predefined dimension member allocation bases that are based on a cost element dimension member consider the values only from the data source provider, such as the general ledger or budget.

### Example 1: Use a cost element dimension member as the allocation base
This example shows how to create a cost allocation rule to allocate cost element 10002 (Employee insurance) to the balance that is recorded on cost element 10001 (Salaries). The allocation rule is defined based on the ratio of each department's salaries to total salaries. (Review needed!)

In the general ledger, the chart of account is defined as follows.

| Chart of account | Main account | Description        | Main account type |
|------------------|--------------|--------------------|-------------------|
| Shared           | 10001        | Salaries           | Expense           |
| Shared           | 10002        | Employee insurance | Expense           |

Define a cost element dimension, and configure the data connector. After the data is imported, the following entries are created in Cost accounting.

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

In the general ledger, the following entries have been posted:

- The entries that show the Salaries main account come from the Payroll system and are posted to cost centers.
- The expense for employee insurance is manually posted to a default cost center.

| Accounting date | Cost center |  Description        | Main account |  Description       | Amount in accounting currency |
|-----------------|-------------|---------------------|--------------|--------------------|-------------------------------|
| 03-01-2017      | CC001       | HR                  | 10001        | Salaries           | 2,000.00                      |
| 03-01-2017      | CC002       | FI                  | 10001        | Salaries           | 5,000.00                      |
| 03-01-2017      | CC003       | IT                  | 10001        | Salaries           | 3,000.00                      |
| 03-01-2017      | CC099       | Default cost center | 10002        | Employee insurance | 1,000.00                      |

After the general ledger source data is processed, the following entries are created in Cost accounting.

**Cost entries**

| Cost object |  Description        | Cost element  |  Description       | Cost behavior   |Amount|Accounting date|
|-------------|---------------------|---------------|--------------------|-----------------|------|---------------|
| CC001       | HR                  | 10001         | Salaries           | Unclassified    |2,000.00|  03-01-2017    |
| CC002       | FI                  | 10001         | Salaries           | Unclassified    |5,000.00|     03-01-2017         |
| CC003       | IT                  | 10001         | Salaries           | Unclassified    |3,000.00|      03-01-2017        |
| CC099       | Default cost center | 10002         | Employee insurance | Unclassified    |1,000.00|      03-01-2017       |

In this simplified example, a cost allocation rule is created to allocate cost element 10002 (Employee insurance) relative to the balance that is recorded on cost element 10001 (Salaries).

**Cost distribution rule**

| Cost object dimension hierarchy node | Cost element dimension hierarchy node | Cost behavior | Allocation base |
|--------------------------------------|---------------------------------------|---------------|-----------------|
| CC099                                | 10002                                 | Unclassified  | 10001           |

**Perform overhead calculation**

After cost element 10001 (Salaries) is applied as the allocation base, the result of the overhead calculation is as follows.

| Cost object | Description | Magnitude |   Allocation factor         | Amount |
|-------------|-------------|-----------|-----------------------------|--------|
| CC001       | HR          | 2,000     | (2,000 ÷ 10,000) × 1,000.00 | 200.00 |
| CC002       | FI          | 5,000     | (5,000 ÷ 10,000) × 1,000.00 | 500.00 |
| CC003       | IT          | 3,000     | (3,000 ÷ 10,000) × 1,000.00 | 300.00 |

**Journal**

| Journal | Journal type                          | Fiscal calendar period | Year | Period   | Version                                                                 |
|---------|---------------------------------------|------------------------|------|----------|-------------------------------------------------------------------------|
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

Statistical dimension members can be used as allocation bases to define policies or report non-monetary consumption by cost objects. You can manually create statistical dimension members or import them from a file by using the Data management import/export tool.

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
> All the tables that contain financial dimensions can be used as sources for statistical measures.

Cost accounting supports a collection of statistical measures by using the following data connections:

- Data management import/export tool
- Statistical measures

To pull statistical measures from the system, a statistical measure provider template is required. For more information, see Statistical measure provider template. (Will add a link once this topic is written.)

**Statistical measure provider templates**

| Name  | Function | Source table  | Sum field      | Date field     |
|-------|----------|---------------|----------------|----------------|
| FTE’s | Count    | HcmEmployment | Not applicable | Not applicable |

After the statistical measure source data is processed, the following entries will be created in Cost accounting.

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

You can use the Imported statistical measures data entity to import statistical measures into Cost accounting. You can also use the Data management import/export tool. In Excel, the consumption of electricity is recorded as follows.

| Accounting date | Dimension member | Magnitude | Source identifier |
|-----------------|------------------|-----------|-------------------|
| 31-01-2017      | CC001            | 2,450.00  | Electricity       |
| 31-01-2017      | CC002            | 4,100.00  | Electricity       |
| 31-01-2017      | CC003            | 15,000.00 | Electricity       |

After the statistical measure source data is processed, the following entries will be created in Cost accounting.

**Statistical entries**

| Cost object |    | Accounting date | Statistical dimension member |    Description          | Magnitude |
|-------------|----|-----------------|------------------------------|-------------------------|-----------|
| CC001       | HR | 31-01-2017      | Electricity                  | Electricity consumption | 2,450.00  |
| CC002       | FI | 31-01-2017      | Electricity                  | Electricity consumption | 4,100.00  |
| CC003       | IT | 31-01-2017      | Electricity                  | Electricity consumption | 15,000.00 |

Here is an example of a cost distribution rule if the Electricity predefined dimension member allocation basis is assigned as the allocation base in it.

| Cost object | Description  | Magnitude | Allocation factor          |
|-------------|------|-----------|----------------------------|
| CC001       | HR   | 2,450.00  | (2,450 ÷ 21,550) × Amount  |
| CC002       | FI   | 4,100.00  | (4,100 ÷ 21,550) × Amount  |
| CC003       | IT   | 15,000.00 | (15,000 ÷ 21,550) × Amount |

## Hierarchy allocation bases

Cost accounts can manually create the hierarchy allocation bases by applying a cost object dimension hierarchy node to an existing allocation base. In this way, you can limit the range of the original predefined dimension member allocation basis. One predefined dimension member allocation basis can be used to create several hierarchy allocation bases. Ranges can be maintained in the cost object dimension hierarchy that is associated with the hierarchy allocation bases.

### Example: Hierarchy allocation bases that are based on full-time employees in the organization
Here is an example of a cost object dimension hierarchy that can be created to describe a simplified organization.

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

A Preview function lets you validate the hierarchy allocation basis that is created, based on statistical entries in the system.

**Allocation base details**

| Cost object | Description  |  Magnitude |
|-------------|------|------------|
| CC001       | HR   | 1.00       |
| CC002       | FI   | 2.00       |

Here is an example of a cost distribution rule if the Number of FTEs in CFO hierarchy allocation basis is assigned as the allocation base in it.

| Cost object | Description  | Magnitude | Allocation factor |
|-------------|------|-----------|-------------------|
| CC001       | HR   | 1.00      | (1/3) × Amount    |
| CC002       | FI   | 2.00      | (2/3) × Amount    |

## Formula allocation bases

Formula allocation bases let you define advanced formulas to achieve the correct allocation basis. You can manually create formula allocation bases.

When you create a formula allocation base, you select which statistical dimension and cost element dimension should be the basis for the formula. All allocation bases that come from the previously selected dimensions can be used in a formula allocation base.

> [!NOTE]
> Previously defined formula allocation bases can be used to define a new formula allocation base.

In formula allocation base factors, you create an alias, and associate it with either an allocation base or a constant. The aliases are then used to define the formula.

You can use the following operators to define your formula.

| Symbols | Text           |
|---------|----------------|
| ( )     | Parentheses    |
| \<      | Smaller than   |
| \>      | Larger than    |
| +       | Addition       |
| –       | Subtraction    |
| \*      | Multiplication |

Traditional **IF** statements aren't supported. However, you can create statements and validate whether they are true.

| Statement | Validation | Result |
|-----------|------------|--------|
| a \> b    | True       | 1      |
| a \> b    | False      | 0      |

### Example 1: A simple formula

Electricity bills often consist of two parts:

- A fixed fee for being connected to grid
- A cost that is associated with consumption per kWh

The Electricity predefined dimension member allocation basis has already been defined and holds these values.

**Statistical entries**

| Cost object | Name | Accounting date | Statistical dimension member | Description             | Magnitude |
|-------------|------|-----------------|------------------------------|-------------------------|-----------|
| CC001       | HR   | 31-01-2017      | Electricity                  | Electricity consumption | 2,450.00  |
| CC002       | FI   | 31-01-2017      | Electricity                  | Electricity consumption | 4,100.00  |
| CC003       | IT   | 31-01-2017      | Electricity                  | Electricity consumption | 15,000.00 |

If the fixed fee must now be evenly spread over cost objects that consume electricity, you have two options for allocating the costs:

- Create a new predefined allocation base, Electricity fixed, and then apply a statistical measure of 1.00 for each cost object that consumed electricity.
- Create a formula allocation base, Electricity fixed, that takes advantage of the Electricity predefined allocation base that is already defined in the system. The benefit of this option is that data must be loaded into Cost accounting for only one Electricity statistical dimension member.

**Formula allocation base** 

| Name              | Cost element dimension | Statistical dimension | Formula |
|-------------------|------------------------|-----------------------|---------|
| Electricity fixed |                        | Statistical elements  |         |

Before the **Formula** field can be filled, you must specify the alias that should be used in the formula.

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

A Preview function lets you validate the formula allocation base that is created, based on statistical entries in the system.

**Allocation base details**

| Cost object | Description  | Formula           | Magnitude |
|-------------|------|-------------------|-----------|
| CC001       | HR   | 2,450.00 \> 0.01  | 1.00      |
| CC002       | FI   | 4,100.00 \> 0.01  | 1.00      |
| CC003       | IT   | 15,000.00 \> 0.01 | 1.00      |

Here is an example of a cost distribution rule if the Electricity formula allocation base is assigned as the allocation base in it.

**Cost object magnitude allocation factor**

| Cost object | Name | Magnitude |  Allocation factor |
|-------------|------|-----------|--------------------|
| CC001       | HR   | 1.00      | (1/3) × Amount     |
| CC002       | FI   | 1.00      | (1/3) × Amount     |
| CC003       | IT   | 1.00      | (1/3) × Amount     |

### Example 2: An advanced formula
For this example, the cost of electricity should not follow the actual electricity that is consumed in kWh. Management wants to incorporate sentiments for lowering electricity usage. 

| Rule              | Rate | 
|-------------------|------|
| a <= 10000,00 kWh | 0.75 |
| a > 10000,00 kWh  | 1.15 |

A new formula allocation base, Electricity usage, is created.

**Formula allocation base**

| Name              | Cost element dimension | Statistical dimension | Formula |
|-------------------|------------------------|-----------------------|---------|
| Electricity usage |                        | Statistical elements  |         |

Before the **Formula** field can be filled, you must specify the alias that should be used in the formula.

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
| Electricity fixed |                        | Statistical elements  | ([a \> b] × [(b × c) + (a – b) × d]) + ([a \<= b] × a × c) |

A Preview function lets you validate the formula allocation base that is created, based on statistical entries in the system.

**Allocation base details**

| Cost object |    | Formula                                                                                                                             | Magnitude |
|-------------|----|-------------------------------------------------------------------------------------------------------------------------------------|-----------|
| CC001       | HR | ([2,450.00 \> 10.000.00] × [(10,000.00 × 0.75) + (2,450.00 – 10,000.00) × 1.15]) + ([2,450.00 \<= 10,000.00] × 2,450.00 × 0.75)     | 1,837.50  |
| CC002       | FI | ([4,100.00 \> 10.000.00] × [(10,000.00 × 0.75) + (4,100.00 – 10,000.00) × 1.15]) + ([4,100.00 \<= 10,000.00] × 4,100.00 × 0.75)     | 3,075.00  |
| CC003       | IT | ([15,000.00 \> 10.000.00] × [(10,000.00 × 0.75) + (15,000.00 – 10,000.00) × 1.15]) + ([15,000.00 \<= 10,000.00] × 15,000.00 × 0.75) | 1,3250.00 |

Here is a closer look at the formula for CC003 (IT):

((15,000.00 \> 10,000.00) × ((10,000.00 × 0.75) + (15,000.00 – 10,000.00) × 1.15)) + ((15,000.00 \<= 10,000.00) × 15,000.00 × 0.75) = 13,250.00

(1 × (7,500.00 + 5,000.00 × 1.15)) + (0 × 15,000.00 × 0.75)            

1 × 7,500.00 + 5,750.00 + 0 

Here is an example of a cost distribution rule if the Electricity fixed formula allocation base is assigned as the allocation base in it.

| Cost object |  Description  | Magnitude | Allocation factor                |
|-------------|----|-----------|----------------------------------|
| CC001       | HR | 1,837.50  | (1,837.50 ÷ 18,162.50) × Amount  |
| CC002       | FI | 3,075.00  | (3,075.00 ÷ 18,162.50) × Amount  |
| CC003       | IT | 13,250.00 | (13,250.00 ÷ 18,162.50) × Amount |
