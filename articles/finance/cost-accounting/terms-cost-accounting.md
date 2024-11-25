---
title: Cost accounting terminology
description: Learn about the key terms that are used in Cost accounting, including definitions for allocation bases, cost elements, and cost accounting.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 05/15/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: global
ms.search.industry: Manufacturing
ms.search.validFrom: 2016-11-30
ms.search.form: CAMCostAccountingLedger
ms.dyn365.ops.version: Version 1611
ms.assetid: 1c798592-77d0-4a8f-beaa-9159c75957da
ms.custom: evergreen
---

# Cost accounting terminology

[!include [banner](../includes/banner.md)]

This article defines the key terms that are used in Cost accounting.

**Allocation base**

The allocation base is used to measure and quantify activities, such as machine hours that are used, kilowatt hours that are consumed, or square footage that is occupied. It's used as basis for allocating costs to one or more cost objects

**Cost accounting**

Cost accounting lets you collect data from various sources, such as the general ledger, sub-ledgers, budgets, and statistical information. You can then analyze, summarize, and evaluate cost data, so that management can make the best possible decisions for price updates, budgets, cost control, and so on. The source data that is used for cost analysis is treated independently in Cost accounting. Therefore, updates in Cost accounting don’t affect the source data. However, when you collect cost data from various sources, and especially when you import the main accounts from General ledger as cost elements, there is data redundancy, because the same data exists in both General ledger and Cost accounting. This redundancy is required, because you use financial management for external reporting and Cost accounting for internal reporting.

**Cost accounting ledger**

Defined by calendar, currency, and cost element dimension, it controls processes and policies for measuring costs. 

**Cost entry**

Cost entries are the result of a transfer via data connectors from general ledger entries, cost allocations, and posted cost entries in cost journals.

**Cost object**

Any type of object that is selected for cost control. Costs or revenues are either directly posted on or allocated to cost objects. Some typical cost objects are:

-  Products
-  Projects
-  Departments
-  Cost centers

Management uses cost objects to quantify costs, but also to drive profitability analysis.

**Cost element**

Used as a function to track and categorize costs. There are two types of cost elements: primary and secondary.

Primary cost elements represent the cost flow from financial accounting to Cost accounting. The structure typically corresponds to the profit and loss account structure in the general ledger where a cost element can correspond to a main account. Not all main accounts must be represented as cost elements, depending on business requirements. 

Secondary cost elements represent the internal cost flow because these costs are only used in Cost accounting. They are used in cost roll-up rules to aggregate costs into meaningful buckets used by overhead calculation. 

**Cost classification**

Cost classification groups costs according to their shared characteristics. For example, costs can be grouped by elements, traceability, and behavior.

-   **By elements** – Materials, labor, and expenses.
-   **By traceability** – Direct costs and indirect costs. Direct costs are assigned directly to cost objects. Indirect costs aren't directly traceable to cost objects. Indirect costs are allocated to cost objects.
-   **By behavior** – Fixed, variable, and semi-variable.

**Cost behavior**

Cost behavior classifies costs according to their behavior in relation to changes in key business activities. To control costs effectively, management must understand the cost behavior. There are three types of cost behavior pattern: fixed, variable, and semi-variable.

- **Fixed cost** - A fixed cost is a cost that doesn't vary in the short term, regardless of changes in activity level. For example, a fixed cost can be a basic operating expense of a business, such as rent, that won't be affected even if the activity level increases or decreases.

- **Variable cost** - A variable cost changes according to changes in activity level. For example, a specific direct materials cost is associated with each product that is sold. The more products that are sold, the more direct materials costs there are.

- **Semi-variable cost** - Semi-variable costs are partly fixed and partly variable costs. For example, an Internet access fee includes a standard monthly access fee and a broadband usage fee. The standard monthly access fee is a fixed cost, whereas the broadband usage fee is a variable cost.

**Cost control unit**

The cost control unit represents the cost structure. The structure determines how cost flows in a hierarchical order between cost object dimensions and their respective cost objects. 

**Cost distribution**

Is used to distribute cost from one cost object to one or more other cost objects by applying a relevant allocation base. Cost distribution and cost allocation differ in that cost distribution always occurs at the level of the primary cost element of the original cost and no reciprocal processing.

**Cost allocation**

Is used to allocate the balance of a cost object to other cost objects by applying an allocation base. Finance supports the reciprocal allocation method. In the reciprocal allocation method, the mutual services that auxiliary cost objects exchange are fully recognized. The system automatically determines the order to perform the allocations in and iterate over it. The balance of a cost object is allocated by a single allocation base. Allocations across cost object dimensions and their respective members are supported. The allocation order is controlled by the cost control unit.

**Cost allocation policy**

A cost allocation policy defines the amounts and quantities that must be allocated. Allocation rules include allocation source rules, which determine the costs that are allocated, and allocation targets rules, which determine where the costs are allocated. For example, all costs for facility services are an allocation source that can be allocated to various departments in an organization (that is, to allocation targets).

**Cost roll-up**

The purpose of cost roll-up rules is to aggregate costs into meaningful buckets. The level of aggregation is user-defined and involves the assignment of a secondary cost element. If cost roll-up is not used, every element of a cost is allocated from one cost object to another

**Cost rate policy**

The cost rate is used to calculate price per cost object. To understand the elements of the price, you define cost rate policies. There are two types of cost rate: historical cost rate and planned cost rate. A historical cost rate is a calculated rate that is used as a multiplier for the allocation base of a cost object. The rate is calculated based on the cost allocations in the previous period. A planned rate is a user-defined rate.

**Dimension hierarchy**

There are two dimension hierarchies: categorization hierarchy and classification hierarchy. 
The dimension categorization hierarchy type is used for reporting purposes. It supports only the cost element dimensions. 
The dimension classification hierarchy type is used to define policies and for reporting purposes. It supports all dimensions, such as cost objects, cost elements, and statistical dimensions. 

**Data connector**

Cost accounting supports integration of data from source systems via a set of data connectors. The following data connectors are available:

-  Imported transactions (pre-configured)
-  Dynamics 365 Finance (pre-configured)
-  Dynamics AX (configuration required)

**Note:** The data connector Imported transactions is based on data entities.

**Data provider**

Most source systems can provide data that matches one or more data sources in Cost accounting. To align data from the source systems with the data source in Cost accounting, a data provider needs to be configured. The following table lists the availability of data providers per data connector and data source.

|  **Data sources** |  **Imported transactions data connector** | **Dynamics 365 Finance data connector**  | **Dynamics AX data connector**  |
|---|---|---|---|
| Cost element dimension members  |  Yes | Yes  | Yes  |
|  Cost object dimension members |  Yes | Yes  | Yes  |
|  Statistical dimension members | Yes  | No  | No  |
|  General ledger | Yes  | Yes  | Yes  |
|  Budget entries  | Yes  | Yes  | Yes  |
|  Statistical measures | Yes  | Yes  | Yes  |

**Formula**

Formula allocation bases let you define advanced formulas to achieve the correct allocation basis. You can manually create formula allocation bases. You can use the following operators to define your formula.

|  **Symbols** | **Text**  |
|---|---|
|  ( ) | Parentheses  |
|  < |  Smaller than |
|  > |  Larger than |
|  + |  Addition |
|  – |  Subtraction |
| *  | Multiplication  |

Traditional IF statements are not supported. However, you can create statements and validate whether they are true.

|  **Statement  Validation** | **Result**  |
|---|---|
|  a > b| True  |
|  a > b |  False |

**Overhead cost**

Overhead costs refer to the ongoing expenses of operating a business. They are the costs that can’t be linked directly to specific business activities. Here are some examples of overhead costs:

-   Accounting fees
-   Depreciations
-   Insurance
-   Interest
-   Legal fees
-   Taxes
-   Utilities costs

**Overhead rate**

Rates are defined per cost object and cost element. There are two types of rates: fiscal period and user-specified. Fiscal period rates are calculated by the overhead calculation. A user-specific rate is user-defined and can be used to allocate cost between cost objects at a predetermined rate in the overhead calculation.

**Published**

If you set this field to Yes, a user who is assigned one of the following roles can view the report in the Cost control workspace:

-  Cost accounting manager
-  Cost accountant
-  Cost accountant clerk
-  Cost object controller

If you set this field to No, only users who are assigned one of the following roles can view the report in the Cost control workspace:

-  Cost accounting manager
-  Cost accountant
-  Cost accountant clerk

**Statistical dimension**

A statistical dimension and its members are used to register and control non-monetary entries in Cost accounting. Statistical dimension members can be used for two purposes:

-  As an allocation base in policies such as cost distribution or cost allocation.
-  For reporting of non-monetary consumption.

A statistical dimension is the expression of a count or sum of an activity that can be used as the basis for allocations or rate calculations. It's either created manually or imported from source systems. Examples of statistical dimensions include the number of employees, the count of licensed software on each device, power consumption of each machine, or square meters for a cost center.

**Statement**

Statements are views for the managers who are responsible for controlling costs. Statements are defined by a cost controller, and they provide a quick overview of actual costs, budgeted costs, and deviations. A manager can drill further into details if required. To help ensure that managers view only data that they are accountable for, data that appears in the statements is subject to access rules.

**Version**

Versions are used to simulate, view, and compare various outcomes. By default, all actual costs are viewed in one base version that is known as *actual*. For budgets and calculations, you can work with as many versions as you require. For example, you can import budget data into an original version and then revise the budget in a revised version. For calculations, you can create multiple versions. In these various versions, you can then create calculations by using different calculation rules that will be applied for cost allocation.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
