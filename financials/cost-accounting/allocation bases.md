---
# required metadata

title: Allocation bases
description: Allocation bases are key components in Cost accounting and mostly used to allocate overhead costs. Every allocation base used is the basis for overhead costs being assigned to departments. 
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

An allocation base is the basis upon which Cost accounting allocates its overhead costs. An allocation base can be a quantity, for example, machine hours used, kilowatt hours consumed, or square footage occupied. Allocation bases are mostly used to assign overhead costs to produced inventory.

Here are a few examples of allocation bases:
-	An IT department allocates its expenses based on the number of personal computers used by each department.
-	A janitorial department allocates its expenses based on the square footage occupied by each department.
-	A human resources department allocate its expenses based on the number of employees working in each department.

## Typical allocation process 
The typical allocation process starts xxx  

There are three types of allocation bases in Cost accounting:
-	Predefined dimension member allocation bases
-	Hierarchy allocation bases
-	Formula allocation bases

## Predefined dimension member allocation bases

The predefined dimension member allocation bases are created automatically by the system when a dimension member is created. This applies to 
- Statistical dimension members 
- Cost element dimension members

[!NOTE] The predefined dimension member allocation bases that are based on a cost element dimension member only consider the values from the data source provider, for example, general ledger or budget.

### Example 1: Use a cost element dimension member as the allocation base
This example shows how to create a cost allocation rule to allocate the cost element 10002 Employee Insurance to the balance recorded on the cost element 10001 Salaries. The allocation rule is defined based on the ratio of each department salaries to total salaries. (Review needed!)

In the general ledger, the chart of account is defined as follows.

| Chart of account | Main account | Main account name |     Main account type    |
|------------------|--------------|-------------------|---------|
| Shared           | 10001        | Salaries          | Expense |
| Shared           | 10002        | Employee insurance    | Expense |


Define a cost element dimension and configure the data connector. After processing, the import job creates these entries in Cost accounting.

**Cost element dimension members**

|    Cost element dimension name    |    Cost element    |    Cost element name            |          Type     |
|-----------------------------------|---------------------|----------------------|---------------|
|    Cost elements                  |    10001            |    Salaries          |    Primary    |
|    Cost elements                  |    10002            |    Employee insurance    |    Primary    |


**Predefined dimension member allocation bases** 

|    Name     |    Description       |    Cost element dimension    |
|-------------|----------------------|------------------------------|
|    10001    |    Salaries          |    Cost elements             |
|    10002    |    Employee insurance    |    Cost elements             |

In the general ledger, the following entries have been posted.
-	The entries that show main account salaries come from the Payroll system and are posted by cost centers.
- The expense for employee insurance is manually posted on a default cost center.


|    Accounting date    |    Cost center     |    Main account            |    Amount in accounting currency    |                      |                |
|-----------------------|--------------------|----------------------------|-------------------------------------|----------------------|----------------|
|    03-01-2017         |    CC001           |    HR                      |    10001                            |    Salaries          |    2.000,00    |
|    03-01-2017         |    CC002           |    FI                      |    10001                            |    Salaries          |    5.000,00    |
|    03-01-2017         |    CC003           |    IT                      |    10001                            |    Salaries          |    3.000,00    |
|    03-01-2017         |    CC099           |    Default cost center     |    10002                            |    Employee insurance    |    1.000,00    |

After the general ledger source data processing is run, the following entries are created in Cost accounting.

**Cost entries**

|    Cost object    |    Cost element           |    Cost behavior    |    Amount            |    Accounting date    |
|-------------------|---------------------------|---------------------|----------------------|-----------------------|
|    CC001          |    HR                     |    10001            |    Salaries          |    Unclassified       |
|    CC002          |    FI                     |    10001            |    Salaries          |    Unclassified       |
|    CC003          |    IT                     |    10001            |    Salaries          |    Unclassified       |
|    CC099          |    Default cost center    |    10002            |    Employee insurance    |    Unclassified       |


In this simplified example, a cost allocation rule is created to allocate the cost element 10002 employee insurance relatively to the balance recorded on the cost element 10001 Salaries. 

**Cost distribution rule**

|    Cost object dimension hierarchy node    |    Cost element dimension hierarchy node    |    Cost behavior    |    Allocation base    |   |
|--------------------------------------------|---------------------------------------------|---------------------|-----------------------|---|
|    CC099                                   |    10002                                    |     Unclassified    |    10001              |   |

**Perform overhead calculation** 

After the cost element 10001 Salaries is applied as the allocation base, here is the result of the overhead calculation. 

|    Cost object    |    Magnitude    |    Allocation factor    |    Amount                     |              |
|-------------------|-----------------|-------------------------|-------------------------------|--------------|
|    CC001          |    HR           |    2000                 |    (2000/10000) * 1000.00     |    200,00    |
|    CC002          |    FI           |    5000                 |    (5000/10000) * 1000.00     |    500,00    |
|    CC003          |    IT           |    3000                 |    (3000/10000) * 1000.00     |    300.00    |


**Journal**

|    Journal    |    Journal type                             |    Fiscal calendar period    |  Year |   Period             |                                                                   Version                   |
|---------------|---------------------------------------------|------------------------------|---------------|----------------|---------------------------------------------------------------------------------|
|    00001      |    Cost distribution calculation journal    |    Fiscal                    |    2017       |    Period 1    |    Overhead calculation / 01-02-2017 11:51:00 PM /   Ledger /2017 / Period 1    |


**Cost object balance journal entries**

|    Accounting date    |    Cost object    | Cost object name           | Cost element | Cost element name    |  Cost behavior     |  Amount        |
|-----------------------|-------------------|----------------------------|--------------|----------------------|--------------------|----------------|
|    31-01-2017         |    CC099          |    Default cost center     |    10002     |    Employee insurance    |    Unclassified    |    1.000,00    |

**Cost entries**


|    Cost object    |    Cost element            |    Cost behavior    |    Amount            |    Accounting date    |                 |                  |
|-------------------|----------------------------|---------------------|----------------------|-----------------------|-----------------|------------------|
|    CC099          |    Default cost center     |    10002            |    Employee insurance    |    Unclassified       |    -1.000,00    |    31-01-2017    |
|    CC001          |    HR                      |    10002            |    Employee insurance    |    Unclassified       |    200,00       |    31-01-2017    |
|    CC002          |    FI                      |    10002            |    Employee insurance    |    Unclassified       |    500,00       |    31-01-2017    |
|    CC099          |    IT                      |    10002            |    Employee insurance    |    Unclassified       |    300,00       |    31-01-2017    |

### Example 2: Use a statistical dimension member as the allocation base 

Statistical dimension members can be used as allocation bases in defining policies or for reporting non-monetary consumption by cost objects. You can create statistical dimension members manually or import them from a file via **Data management import/export tool**.

**Statistical dimension members**

|    Statistical dimension name    |    Statistical element    |  Statistical element name     |  Unit     |
|----------------------------------|---------------------------|-------------------------------|-----------|
|    Statistical elements          |    FTE                    |    Full time employees        |    Ea     |
|    Statistical elements          |    Electricity            |    Electricity consumption    |    kWh    |

When a statistical dimension members is saved, a corresponding record is created in the predefined dimension member allocation bases.

**Predefined dimension member allocation bases**

|    Name           |    Description                |    Statistical element dimension    |
|-------------------|-------------------------------|-------------------------------------|
|    FTE            |    Full time employees        |    Statistical elements             |
|    Electricity    |    Electricity consumption    |    Statistical elements             |

Statistical measures can come from different sources. 
-	Electricity consumption could be measured by meters installed in different areas of the company. 
- Tables hold statitical measures. For example, the table **HcmEmployment** holds a list of all employees and which cost centers they work for.  

|    Name        |    Cost center     |    Worker Type    |                |
|----------------|--------------------|-------------------|----------------|
|    Employee A      |    CC001           |    HR             |    Employee    |
|    Employee B          |    CC002           |    FI             |    Employee    |
|    Employee C    |    CC002           |    FI             |    Employee    |
|    Employee D      |    CC003           |    IT             |    Employee    |
|    Employee F     |    CC003           |    IT             |    Employee    |

[!NOTE] All the tables that contain financial dimensions can be used as sources for statistical measures.

Cost accounting supports a collection of statistical measures by using the following data connections. 
-	Data management import/export tool
-	Statistical measures

To pull statistical measures from the system, a statistical measure provider template is required. Learn more about Statistical measure provider template. 

**Statistical measure provider templates**

|    Name     |    Function    |    Source table     |    Sum field    |    Date field    |
|-------------|----------------|---------------------|-----------------|------------------|
|    FTE’s    |    Count       |    HcmEmployment    |    NA           |    NA            |

After the statistical measure source data processing is completed, the following entries will be created in Cost accounting.

**Statistical entries**

|    Cost object    | Cost object name      | Accounting date  | Statistical dimension member | Name          | Magnitude  |
|-------------------|-----------|------------------|------------------------------|---------------------------|------------|
|    CC001          |    HR     |    31-01-2017    |    FTE’s                     |    Full time employees    |    1,00    |
|    CC002          |    FI     |    31-01-2017    |    FTE’s                     |    Full time employees    |    2,00    |
|    CC003          |    IT     |    31-01-2017    |    FTE’s                     |    Full time employees    |    2,00    |

In case the predefined dimension member allocation basis FTE’s is assigned as the allocation base in a cost distribution rule, here is an example of the rule.

|    Cost object    |       Name      |  Magnitude              |Allocation factor       |
|-------------------|-----------------|-------------------------|------------------------|
|    CC001          |    HR           |    1,00                 |    (1/5) * Amount      |
|    CC002          |    FI           |    2,00                 |    (2/5) * Amount      |
|    CC003          |    IT           |    2,00                 |    (2/5) * Amount      |

In Excel, the consumption of electricity is recorded as follows. You can use the data entity called **Imported statistical measures** to import statistical measures into Cost accounting. You can also use the **Data management import/export tool** to do the import. 

|    Accounting date    |    Dimension member       |    Magnitude    |    Source identifier    |
|-----------------------|---------------------------|-----------------|-------------------------|
|    31-01-2017         |    CC001                  |    2450,00      |    Electricity          |
|    31-01-2017         |    CC002                  |    4100,00      |    Electricity          |
|    31-01-2017         |    CC003                  |    15000,00     |    Electricity          |


Learn and read more about. Importing cost accounting data using Data management import/export tool

After the statistical measure source data processing is completed, the following entries will be created in Cost accounting.

**Statistical entries**

|    Cost object    |    Accounting date     |    Statistical dimension member    |    Magnitude      |                               |                |
|-------------------|------------------------|------------------------------------|-------------------|-------------------------------|----------------|
|    CC001          |    HR                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    2450,00     |
|    CC002          |    FI                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    4100,00     |
|    CC003          |    IT                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    15000,00    |

In case the predefined dimension member allocation basis Electricity is assigned as the allocation base in a cost distribution rule, here is an example of the rule.

|    Cost object    |    Name         | Magnitude               |    Allocation factor            |
|-------------------|-----------------|-------------------------|---------------------------------|
|    CC001          |    HR           |    2450,00              |    (2450/21550) *   Amount      |
|    CC002          |    FI           |    4100,00              |    (4100/21550) *   Amount      |
|    CC003          |    IT           |    15000,00             |    (15000/21550) * Amount       |

## Hierarchy allocation bases

Cost accounts can create the hierarchy allocation bases manually by adding a cost object dimension hierarchy node to an existing allocation base. The purpose is to let you limit the range of the original predefined dimension member allocation basis. One predefined dimension member allocation basis can be used to create several hierarchy allocation bases. Maintenance of ranges can be done in the cost object dimension hierarchy that is associated with the hierarchy allocation bases.

### Example: Hierarchy allocation bases according to full time employees in the organization
A cost object dimension hierarchy that describes a simplified organization can be created as follows. 

|    Hierarchy name    |    Node Level 0     |    Node Level 1    |    Node Level 2    |    Dimension members    |
|----------------------|---------------------|--------------------|--------------------|-------------------------|
|    Organization      |    CEO              |    CFO             |    FICO            |    CC001                |
|    Organization      |    CEO              |    CFO             |    HR              |    CC002                |
|    Organization      |    CEO              |    CIO             |    IT              |    CC003                |

The predefined dimension member allocation basis FTE’s that has been created in the previous section holds the following entries.

**Statistical entries**

|    Cost object    | Name       |              Accounting date   |    Statistical dimension member          |        Name       |         Magnitude    |
|-------------------|------------------------|------------------------------------|-----------------|---------------------------|------------|
|    CC001          |    HR                  |    31-01-2017                      |    FTE’s        |    Full time employees    |    1,00    |
|    CC002          |    FI                  |    31-01-2017                      |    FTE’s        |    Full time employees    |    2,00    |
|    CC003          |    IT                  |    31-01-2017                      |    FTE’s        |    Full time employees    |    2,00    |

A cost must be distributed between cost centers reporting to the CFO in the organization. It is acknowledged that the correct allocation ratio is the number of FTE’s by cost centers.   

**Hierarchy allocation bases**

|    Name                 |    Allocation base    |    Cost object dimension hierarchy    |    Cost object dimension hierarchy node    |
|-------------------------|-----------------------|---------------------------------------|--------------------------------------------|
|    # of FTE’s in CFO    |    FTE’s              |    Organization                       |    CFO                                     |

A preview function provides the ability to validate the hierarchy allocation basis created based on statistical entries in the system.

**Allocation base details**

|    Cost object    |    Name         |  Magnitude |
|-------------------|-----------------|------------|
|    CC001          |    HR           |    1,00    |
|    CC002          |    FI     |    2,00    |

In case the hierarchy allocation basis # of FTE’s in CFO is assigned as the allocation base in a cost distribution rule, here is an example of the rule. 

|    Cost object    |   Name          |    Magnitude           |           Allocation factor            |
|-------------------|-----------------|-------------------------|-----------------------|
|    CC001          |    HR           |    1,00                 |    (1/3) * Amount     |
|    CC002          |    FI           |    2,00                 |    (2/3) * Amount     |

## Formula allocation bases

Formula allocation bases provide the ability to define advanced formulas to achieve the correct allocation basis. You can create them manually.

The following operators can be used to express your formula.    

|    Symbols    |    Text              |
|---------------|----------------------|
|    (   )      |    Parentheses       |
|    <          |    Smaller than      |
|    >          |    Larger than       |
|    +          |    Addition          |
|    -          |    Subtraction       |
|    *          |    Multiplication    |

IF statements are not supported. You can create statements and validate if they are true or not. 

|    Statement    |    validation    |    Result    |
|-----------------|------------------|--------------|
|    a > b        |    True          |    1         |
|    a > b        |    False         |    0         |

When you create a formula allocation base, you select which statistical dimension and cost element dimension should be the basis for the formula. All allocation bases that come from the selected dimensions above can be used in formula allocation base. 

[!NOTE] Previous defined formula allocation bases can be used in defining a new formula allocation base.

In formula allocation base factors, you create alias and associate it with either an allocation base or constant. The aliases are then used to define the formula.

### Example 1: A simple formula
Electricity bills often consist of 2 parts. 
-	Fixed fee for being connected to grid
-	A cost associcated with consumption per kWh

The predefined dimension member allocation basis Electricity has already been established and holds these values.

**Statistical entries**

|    Cost object    |  Name       |  Accounting date   |     Statistical dimension member        |     Name                 |  Magnitude        |
|-------------------|------------------------|------------------------------------|-------------------|-------------------------------|----------------|
|    CC001          |    HR                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    2450,00     |
|    CC002          |    FI                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    4100,00     |
|    CC003          |    IT                  |    31-01-2017                      |    Electricity    |    Electricity consumption    |    15000,00    |

Now assume the fixed fee needs to be evenly spread over cost objects that consume electricity.
- One option to allocate the costs could be to create a new predefined allocation base Electricity fixed and then apply a statistical measure of 1,00 for each of the Cost objects that had consumed electricity. 
- Second option could be to create a formula allocation base Electricity fixed that takes advantage of the predefined allocation base Electricity that is already defined in the system. The benefit by selecting the second option is that only one statistical dimension member (Electricity) requires data loaded into Cost accounting. (Can you show how to do it?) 

**Formula allocation base** 

|    Name                 |    Cost element dimension    |    Statistical dimension    |    Formula    |
|-------------------------|------------------------------|-----------------------------|---------------|
|    Electricity fixed    |                              |    Statistical elements     |               |

The user must specify the alias to be used in the formula before the **Formula** field can be populated.

**Formula allocation base factors**

|    Alias    |    Constant     |    Allocation base    |
|-------------|-----------------|-----------------------|
|    a        |                 |    Electricity        |
|    b        |    0,01*        |                       |

[!NOTE] Zero is not supported as cnstant.

**Formula allocation base**

|    Name                 |    Cost element dimension    |    Statistical dimension    |    Formula    |
|-------------------------|------------------------------|-----------------------------|---------------|
|    Electricity fixed    |                              |    Statistical elements     |    a > b      |

A Preview function provides the ability to validate the formula allocation base created based on statistical entries in the system.

**Allocation base details**

|    Cost object    |   Name        |      Formula          |   agnitude |
|-------------------|---------------|-----------------------|------------|
|    CC001          |    HR         |    2450,00 > 0,01     |    1,00    |
|    CC002          |    FI         |    4100,00 > 0,01     |    1,00    |
|    CC003          |    IT         |    15000,00 > 0,01    |    1,00    |

In case the formula allocation base Electricity fixed is assigned as the allocation base in a cost distribution rule, here is an example of the rule.

**Cost object	Magnitude	Allocation factor**

|    Cost object    |   Name          |   Magnitude             |  Allocation factor    |
|-------------------|-----------------|-------------------------|-----------------------|
|    CC001          |    HR           |    1,00                 |    (1/3) * Amount     |
|    CC002          |    FI           |    1,00                 |    (1/3) * Amount     |
|    CC003          |    IT           |    1,00                 |    (1/3) * Amount     |

### Example 2: An advanced formula
Now assume the cost of electricity should not just follow actual consumed electricity kWh. Management wants to incorporate sentiments for lowering the usage of electricity. 

|    Rule                 |    Rate     | 
|-------------------------|-------------|
|    a <= 10000,00 kWh    |    0,75     |
|    a > 10000,00 kWh     |    1,15     |

A new formula allocation base Electricity usage is created.

**Formula allocation base**

|    Name                 |    Cost element dimension    |    Statistical dimension    |    Formula    |
|-------------------------|------------------------------|-----------------------------|---------------|
|    Electricity usage    |                              |    Statistical elements     |               |

The user must specify the alias to be used in the formula before the **Formula** field can be populated.

**Formula allocation base factors**

|    Alias    |    Constant     |    Allocation base    |
|-------------|-----------------|-----------------------|
|    a        |                 |    Electricity        |
|    b        |    10000,00     |                       |
|    c        |    0,75         |                       |
|    d        |    1,15         |                       |

**Formula allocation base**

|    Name                 |    Cost element dimension    |    Statistical dimension    |    Formula                                                       |
|-------------------------|------------------------------|-----------------------------|------------------------------------------------------------------|
|    Electricity fixed    |                              |    Statistical elements     |    ((a > b) * ((b * c) + (a - b) * d)) + ((a <=   b) * a * c)    |

A Preview function provides the ability to validate the formula allocation base created based on statistical entries in the system.

**Allocation base details**

|    Cost object    |    Formula    |    Magnitude                                                                                                                                    |                |
|-------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------|----------------|
|    CC001          |    HR         |    ((2450,00 > 10000,00) * ((10000,00 * 0,75) +   (2450,00 – 10000,00) * 1,15)) + ((2450,00 <= 10000,00) * 2450,00 * 0,75)                      |    1837,50     |
|    CC002          |    FI         |    ((4100,00 > 10000,00) * ((10000,00 * 0,75) +   (4100,00 – 10000,00) * 1,15)) + ((4100,00 <= 10000,00) * 4100,00 * 0,75)                      |    3075,00     |
|    CC003          |    IT         |    ((15000,00 > 10000,00) * ((10000,00 * 0,75) +   (15000,00 – 10000,00) * 1,15)) + ((15000,00 <= 10000,00) * 15000,00 * 0,75)                  |    13250,00    |

A closer look at the formula
CC003	IT	((15000,00 > 10000,00) * ((10000,00 * 0,75) + (15000,00 – 10000,00) * 1,15)) + ((15000,00 <= 10000,00) * 15000,00 * 0,75)              	13250,00

(1 * (7500,00 + 5000,00 * 1,15)) + (0 * 15000,00 * 0,75)            

1 * 7500,00 + 5750,00 + 0

In case the formula allocation base Electricity fixed is assigned as the allocation base in a cost distribution rule, here is an example of the rule.

|    Cost object    |    Magnitude    |    Allocation factor    |                                       |
|-------------------|-----------------|-------------------------|---------------------------------------|
|    CC001          |    HR           |    1837,50              |    (1837,50/18162,50) *   Amount      |
|    CC002          |    FI           |    3075,00              |    (3075,00/18162,50) *   Amount      |
|    CC003          |    IT           |    13250,00             |    (13250,00/18162,50) *   Amount     |

