---
# required metadata

title: Data entities - Expense management
description: This article provides a list of the data entities that are available for the Expense management functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 18 - 49
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
ms.custom: 95713
ms.assetid: e1f9beed-5bd9-4425-b8ed-012c8390a75a
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Expense management

This article provides a list of the data entities that are available for the Expense management functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Description

**33.1.001 EM - Cash advance, Expense entry, and statistics**

When you import the Delegate data entity, make sure that the Users data entity had been imported into the system.

1

Cash advance accounts

Cash advance, Expense entry and statistics

Setup

Currency, Chart of accounts

Accounts that are dedicated to cash advances for your organization

2

Expense payment method

Cash advance, Expense entry and statistics

Setup

Chart of accounts, Bank accounts, Shared category

Methods of payment for expense transactions

3

Statistics groups

Cash advance, Expense entry and statistics

Setup

None

Used to gather statistics when you evaluate expenses that are incurred in your organization.

4

Expense category

Cash advance, Expense entry and statistics

Setup

Expense payment method, Chart of accounts, Project category

Categories that can be used on expense reports

5

Shared expense subcategory

Cash advance, Expense entry and statistics

Setup

Shared categories, Expense categories

Subcategories from shared expense categories that can be used on expense reports

6

Expense subcategory

Cash advance, Expense entry and statistics

Setup

Expense category, Project category

Subcategories for expenses

7

Credit card category codes

Cash advance, Expense entry and statistics

Setup

Expense category

Define relations between the categories that are used for credit card expense transactions and the categories that you've defined.

8

Delegate

Cash advance, Expense entry and statistics

Setup

Workers

Set up other users as delegates who can create and submit expense reports, travel requisitions, and credit card disputes on your behalf.

9

Display fields

Cash advance, Expense entry and statistics

Setup

None

Fields that appear in the header section and line item section of expense reports. You can also select the fields that appear but remain read-only.

10

Expense credit card type

Cash advance, Expense entry and statistics

Setup

None

The types of cards that your business accepts, such as debit cards, credit cards, loyalty cards, and corporate cards

**33.1.002 - EM Additional setup**

11

Expense purpose for transactions

Additional setup

Setup

None

Describes the business purpose of the expense.

12

Expense purposes

Additional setup

Setup

None

Add a level of information to expense types.

13

Expense tax recovery configuration

Additional setup

Setup

Global address book, Sales tax group

Process expenses that are eligible for value-added tax (VAT) recovery.

14

Group of employees for project expense policy purposes

Additional setup

Setup

None

Policies that employees must follow when they submit expense reports

15

Travel locations

Additional setup

Setup

None

Set up travel locations and destinations for employee travel.

**33.1.003 - Merchant**

16

Merchant

Merchant

Setup

None

A list of merchants that employees can select when they enter line item expenses on an expense report

**33.1.004 - Mileage rate tiers**

17

Mileage rate tiers

Mileage rate tiers

Setup

None

Mileage rates for employee travel

**33.1.005 - Expense parameters**

18

Expense management parameters

Expense parameters

Setup

Ledger journal, Chart of accounts, Bar code setup

Set up default information, rates, and calculations for Travel and expense.

**33.1.006 - Signing limit**

19

Signing limit agreement

Signing limit

Setup

None

Agreements that employees are required to read and accept before they can be granted a signing limit authorization

20

Signing limit policy parameters

Signing limit

Setup

None

A parameter where signing limits are based on either the employee’s job or the employee's compensation level

21

Signing limit revocation reason code

Signing limit

Setup

None

Reasons that are used when signing limits are revoked

**33.1.007 - Per Diem**

22

Per diem locations

Per Diem

Setup

None

The locations where employees can use their per diem allowances while they conduct business for your organization

23

Per diems

Per Diem

Setup

Location, Currency

Set up per diem minimums and maximums, and the associated categories.

24

Per diem rate tiers (Available in the Microsoft Dynamics 365 for Operations February 2016 release)

Per Diem

Setup

None

The allowance that the organization provides to a worker who incurs expenses for business purposes

**33.1.008 - Project expense policy**

25

Project expense policies

Project expense policy

Setup

Customer, Project contract, Project ID, Project expense policy worker group, Global address book, Expense category, Currency

Set up expense policies for one or more workers in your organization.

26

Project expense policy worker groups

Project expense policy

Setup

Workers

Specify a group of workers that a project expense policy can be applied to.

**33.1.009 - Employee credit cards**

27

Employee credit cards

Employee credit cards

Setup

None

Credit card information that is used by employees

**33.8.001 - Credit card transactions**

28

Credit card transactions

Credit card transactions

Transactional

Various

Expense management transactions

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

