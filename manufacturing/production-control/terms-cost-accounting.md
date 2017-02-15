---
# required metadata

title: Cost accounting terminology
description: This topic defines the key terms that are used in Cost accounting.
author: annbe
manager: AnnBe
ms.date: 2016-11-01 12 - 35 - 53
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMCostControlWorkspace, CAMCostControlWorkspaceConfiguration
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2094
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 223114
ms.assetid: 80d17b57-a307-42f5-9ddd-e47b9aedfc07
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: annbe
ms.dyn365.intro: Nov-16
ms.dyn365.version: Version 1611

---

# Cost accounting terminology

This topic defines the key terms that are used in Cost accounting.

The following table defines the key terms in Cost accounting.

Term

Definition

Cost accounting

Cost accounting lets you collect data from various sources, such as the general ledger, sub-ledgers, budgets, and statistical information. You can then analyze, summarize, and evaluate cost data, so that management can make the best possible decisions for price updates, budgets, cost control, and so on. The source data that is used for cost analysis is treated independently in Cost accounting. Therefore, updates in Cost accounting don’t affect the source data. However, when you collect cost data from various sources, and especially when you import the main accounts from General ledger in Microsoft Dynamics 365 for Operation as cost elements, there is data redundancy, because the same data exists in both General ledger and Cost accounting. This redundancy is required, because you use financial management for external reporting and Cost accounting for internal reporting.

Cost accounting ledger

The cost accounting ledger is a specialized framework that determines how processes, values, and quantities are entered and presented for a particular area in Cost accounting. The cost accounting ledger defines processes and rules for measuring costs on cost objects. It handles cost transactions, and manages documents that record the changes in values and quantities that cost transactions produce.

Cost entry

Cost entries are the result of a transfer via data connectors from general ledger entries, cost allocations, and posted cost entries in cost journals.

Cost object

Cost objects are any type of object that costs are allocated to. Here are some typical cost objects:

-   Products
-   Projects
-   Resources
-   Departments
-   Cost centers
-   Geographic regions

Management uses cost objects to quantify costs, but also to drive profitability analysis.

Cost element

Cost elements are used as a function to track and categorize where costs flow to. There are two types of cost elements: primary costs and secondary costs. **Primary costs** The primary cost elements represent the flow of costs from financial accounting to cost accounting. The cost element structure corresponds to the profit and loss account structure in the general ledger, where a cost element can correspond to a main account. Not all main accounts must be represented as cost elements, depending on business requirements. Here are some examples of primary cost elements:

-   Costs of goods sold (COGs)
-   Indirect material costs
-   Personnel costs
-   Energy costs

**Secondary cost elements** The secondary cost elements represent the internal flow of costs, because these costs are created and used only in Cost accounting. Secondary cost elements help guarantee that the source of costs can be traced. These cost elements are used in cost allocations and overhead calculations. Here are some examples of secondary cost elements:

-   Production costs
-   Production, material, and marketing overheads

Cost control unit

A cost control unit represents the cost structure. It must be associated with cost object dimensions in a cost accounting ledger.

Versions

Versions are used to simulate, view, and compare various outcomes. By default, all actual costs are viewed in one base version that is known as *actual*. For budgets and calculations, you can work with as many versions as you require. For example, you can import budget data into an original version and then revise the budget in a revised version. For calculations, you can create multiple versions. In these various versions, you can then create calculations by using different calculation rules that will be applied for cost allocation.

Statements

Statements are views for the managers who are responsible for controlling costs. Statements are defined by a cost controller, and they give a quick overview of actual and budgeted costs, and even deviations and calculation versions. To help guarantee that managers view only data that they are accountable for, data that appears in the statements is subject to access rules.

Data connectors

Data can be imported into Cost accounting from external systems via data connectors. For example, you can import account structures, dimensions, general ledger entries, and budget entries. You can use preconfigured data connectors or custom connectors to import data and create data connections.

**Cost classification**

Cost classification

Cost classification groups costs according to their shared characteristics. For example, costs can be grouped by elements, traceability, and behavior.

-   **By elements** – Materials, labor, and expenses.
-   **By traceability** – Direct costs and indirect costs. Direct costs are assigned directly to cost objects. Indirect costs aren't directly traceable to cost objects. Indirect costs are allocated to cost objects.
-   **By behavior** – Fixed, variable, and semi-variable.

Cost behavior

Cost behavior classifies costs according to their behavior in relation to changes in key business activities. To control costs effectively, management must understand the cost behavior. There are three types of cost behavior pattern: fixed, variable, and semi-variable.

Fixed cost

A fixed cost is a cost that doesn't vary in the short term, regardless of changes in activity level. For example, a fixed cost can be a basic operating expense of a business, such as rent, that won't be affected even if the activity level increases or decreases.

Variable cost

A variable cost changes according to changes in activity level. For example, a specific direct materials cost is associated with each product that is sold. The more products that are sold, the more direct materials costs there are.

Semi-variable cost

Semi-variable costs are partly fixed and partly variable costs. For example, an Internet access fee includes a standard monthly access fee and a broadband usage fee. The standard monthly access fee is a fixed cost, whereas the broadband usage fee is a variable cost.

Overhead costs

Overhead costs refer to the ongoing expenses of operating a business. They are the costs that can’t be linked directly to specific business activities. Here are some examples of overhead costs:

-   Accounting fees
-   Depreciations
-   Insurance
-   Interest
-   Legal fees
-   Taxes
-   Utilities costs

**Cost allocation**

Cost allocation

Cost allocation is the process of assigning and allocating costs, based on the root causes of the common costs. You allocate the cost amounts and quantities from one cost object to one or more other cost objects. For example, all facility services costs are allocated to the various departments that use the common office building.

Cost allocation policy

A cost allocation policy defines the amounts and quantities that must be allocated. Allocation rules include allocation source rules, which determine the costs that are allocated, and allocation targets rules, which determine where the costs are allocated. For example, all costs for facility services are an allocation source that can be allocated to various departments in an organization (that is, to allocation targets).

Allocation base

The allocation base is the basis that can be used to measure and quantify activities, such as machine hours that are used, kilowatt hours that are consumed, direct labor hours that are spent, or square footage that is occupied. It's used to allocate costs to one or more cost objects.

Allocation principles

One of the allocation principles is to allocate cost by cost rate. You can choose to allocate costs by using the actual period rate or a historical rate. Allocation that uses the reciprocal method helps guarantee that the allocation base is determined by a series of simultaneous equations before allocation is done by using the actual period rate.

Cost roll-up

The purpose of cost roll-up is to include all costs for a given cost object. The level of aggregation is user-defined. By using cost roll-up, you can aggregate elements of costs that must be allocated from one cost object to another. When cost roll-up isn't used, every single element of costs is allocated from one cost object to another.

Cost rate policies

The cost rate is used to calculate price per cost object. To understand the elements of the price, you define cost rate policies. There are two types of cost rate: historical cost rate and planned cost rate. A historical cost rate is a calculated rate that is used as a multiplier for the allocation base of a cost object. The rate is calculated based on the cost allocations in the previous period. A planned rate is a user-defined rate.

Dimensional hierarchies

Dimension hierarchies are used as reporting structures when you define rules for allocation, cost rate, and cost roll-up, view statements or data in Microsoft Excel, and define access to the aggregated data. There are two dimension hierarchies: categorization hierarchy and classification hierarchy. A categorization hierarchy is defined based on cost elements, whereas a classification hierarchy is defined based on cost objects.

Statistical dimension

A statistical dimension is the expression of a count or sum of an object that can be used as the basis for allocations or cost rate calculations. It's either created manually or imported from source systems. Examples of statistical dimensions include the number of employees, the count of licensed software on each device, power consumption of each machine, or square meters for a cost center.

Statistical entry

Statistical entries hold the recorded sum or count value for a given statistical dimension. The recorded sum or count value is also referred to as the magnitude.

