---
# required metadata

title: Data entities - Budget planning
description: This article provides a list of the data entities that are available for the Budget planning functionality in Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 20 - 04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96103
ms.assetid: 221d9b8a-41a0-4c46-85a8-a263919de340
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Budget planning

This article provides a list of the data entities that are available for the Budget planning functionality in Microsoft Dynamics AX.

Prerequisites
-------------

You must complete the following steps before you can import the Budget planning data entities.

1.  Create balances for any financial dimension set that is used in the layouts. If you're importing from demo data, this financial dimension set is the main account. Click **General ledger** &gt; **Chart of accounts** &gt; **Dimensions** &gt; ****Financial dimension sets****, select the dimension set, and then, and on the Action Pane, click ****Create balances****.
2.  Verify that the organizational hierarchy that is used in the budget plan process has been built and published. If you imported from demo data, the organizational hierarchy is **Budgeting – Departments**. Click **Organization administration** &gt; **Organizations** &gt; **Organization hierarchies**, select the hierarchy that is used in the budget plan process, and then, on the Action Pane, click **View**. Click **Edit**, and then insert the appropriate **Finance** hierarchy that has the following departments under it: **Sales & Marketing**, **Operation**, **IT Department**, **Human Resources**, and **Legal and Client Services**. After the hierarchy is completed, on the Action Pane, click **Publish**, enter an activation date, and then click **OK**.

Workflow data entities and Budgeting data entities should be imported before Budget planning data entities. For more information, see [Data entities: Workflow](data-entities-workflow.md) and [Data entities: Budgeting](data-entities-budgeting.md).

## Available data entities
Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**12.1.003 BUD – Budget planning setup**

1

Budget plan parameters

Budgeting

Setup

Dimension hierarchy

Define the security rules that should be applied to budget plans.

2

Budget plan scenarios

Budgeting

Setup

None

Define categories of data for the budget plans.

3

Budget plan stages

Budgeting

Setup

None

Define the steps that a budget plan follows from its inception to final approval.

4

Budget plan workflow

Budgeting

Setup

All workflow data entities

Define the order of the budget planning stages, and associate each budget planning workflow with a budgeting workflow ID.

5

Period allocation categories

General ledger

Setup

None

Creates period allocation keys to represent the time period to allocate.

6

Budget plan allocation schedules

Budgeting

Setup

Period allocation categories

Used to automatically allocate budget plan lines during workflow processing.

7

Budget plan layout elements

Budgeting

Setup

None

Defined components that are associated with a row or column, and that are combined to create the layout

8

Budget plan columns

Budgeting

Setup

None

Used in the budget plan template.

9

Budget plan column rules

Budgeting

Setup

Budget plan columns

Rules that are applied to the column

10

Budget plan process

Budgeting

Setup

Hierarchy setup

Configure the budget planning process.

11

Budget plan process administration

Budgeting

Setup

Budget plan process

A component of the budget plan process

12

Budget plan stage rule

Budgeting

Setup

Budget plan process, Budget plan layout elements

Determine whether you can add or modify budget plan lines during each stage.

13

Budget plan stage allocations

Budgeting

Setup

None

An automated task that performs an allocation during the specified workflow by using an allocation schedule

14

Budget plan priorities

Budgeting

Setup

None

Define categories and objectives for budget plans.

15

Budget plan priority constraint

Budgeting

Setup

Budget plan process

Determine whether you can add or modify budget plan lines during each stage.

16

Budget planning process milestone

Budgeting

Setup

Budget plan process

Decision point stages in the planning process

17

Budget plan proposed asset

Budgeting

Setup

None

Placeholders for fixed assets that are planned, but that haven't yet been acquired in Fixed assets

18

Budget plan proposed project

Budgeting

Setup

None

Placeholders for projects that are planned, but that haven't been created

**12.1.004 BUD – Forecast position**

**Note:** Compensation groups must be set up before you import the Forecast position data entities.

19

Forecast position budget purpose account details

Budgeting

Setup

Compensation groups

Details that are related to each forecasted position

20

Budget cost elements

Budgeting

Setup

None

Various costs that are associated with a position, such as the base pay, bonus, and insurance that are associated with a calculation

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities.md)

