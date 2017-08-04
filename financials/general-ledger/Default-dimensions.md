---
# required metadata

title: How dimensions default when posting a document or journal
description: When planning and setting up your chart of accounts, there are a lot of considerations in how all the different components 
such as account structures, advanced rules, balancing and fixed dimensions work together when you are posting a document or journal. 
author: aolson
manager: AnnBe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.2.0

---

# How dimensions default when posting a document or journal

[!include[banner](../includes/banner.md)]
When planning and setting up your chart of accounts, there are a lot of considerations in how all the different components such as account structures, advanced rules, balancing and fixed dimensions work together when you are posting a document or journal. This article covers what each component is and how they work together.

Chart of accounts and financial dimension components
----------------------------------------------------

Dynamics 365 for Finance and Operations has a rich, rules-based system for defining valid main account and financial dimension value combinations. The following lists each component, a brief overview of the functionality, and where to find it.

### Account structures

An account structure is a required when setting up your ledger. You must have at least one account structure defined and activated in the system and assigned to the ledger. The account structure must have the main account in it. You can define the order of the segments that best works for the business. The system knows what account structure is being used once the main account is defined. So
often it can be beneficial to have the main account first or near the front of a structure to help limit the values and for defaulting the last known valid value. You can have up to 10 additional financial dimensions in the account structure. The account structure defines which dimension values are valid in combination with other values, and whether dimension values are required to be entered.

### Advanced rules

Advanced rules are an optional component when setting up the chart of accounts. You can add as many advanced rules as you would like to an account structure. They are often used to handle scenarios where additional financial dimensions are needed to be tracked when specific criteria are met. For example, if you use a Travel expense account, you may want to track additional information such as
the Event the employee is traveling for. When there are multiple advanced rules, they are applied based on the alphabetic order name of the rule. The segments that are added by the rule can also only be applied after the segments of the account structure.

### Balancing dimension

Defining a balancing financial dimension is optional. You can define what financial dimension you want to be balanced on the Ledger page. Whenever transactions are posted to that specific financial dimension, the entries to make the financial dimension balanced are automatically created and posted by the system.

### Default/fixed financial dimensions on the Main account

Dimensions default from a variety of places, including master records such as customer or vendor, document headers and the main account. For this article, we will focus on default dimensions on the main account by legal entity. You can define whether a main account has a “Not fixed” or “Fixed” value for each of the Financial dimensions used across all account structures for the ledger. If a financial dimension is “Not fixed”, it defaults the value but the value can be overwritten. This applies to all defaulting in the system, including from master records. If a financial dimension is set to a “Fixed” value, then that value will be applied, regardless of whether it was defaulted from anywhere or was entered by the user.

Order of defaulting during posting
----------------------------------

The order in which all the components execute is a common question. The order of execution of defaulting is critical to understand as it will impact the approach you take to setting up.

**Note**: This applies to defaulting within the application only. Importing data using Excel or the Data Management Framework does not have the same behavior as the working in the application page.

### Example 


Account structure

| Main account       | Business Unit      | Department         | Cost Center        |
|--------------------|--------------------|--------------------|--------------------|
| All values allowed | All values allowed | All values allowed | All values allowed |

Main account

| Main account | Name          | Legal entity | Department                                 |
|--------------|---------------|--------------|--------------------------------------------|
| 401100       | Product Sales | USMF         | Fixed – 022 Sales and Marketing department |

![](media/f54497393696d0026c0d3abcd338b46d.png)

Figure 1: Fixed default dimension set on Main account 401100

Using a very basic example of entering a general journal that has the Department set to default to 023, which is Operations, we will enter a ledger account and post it.

![](media/31429b7e40fe536d6f465d1dc4f0b435.png)

Figure 2: Default financial dimension on the General journal header

The default on the header of the journal will default Department 023 on my sales account line.

![](media/34d15fb9a517fbc3068939f62d7a77f2.png)

Figure 3: General journal line showing the 023 default from the header

However, when I post it, the fixed dimension will be applied and it will post to 022.

![](media/87a803c104cc7087dbedf5d35d753df2.png)

Figure 4: The posted voucher showing the fixed dimension applied for the sales account

### Example 2

Using the same setup defined in the first example, we will add a second component to our example. This time we will use a Balancing dimension of Department.

![](media/693119663225b01be95fc48679798a06.png)

Figure 5: Department set as the balancing financial dimension for ledger USMF

When using the same journal header setup and posting the same transaction, the fixed dimension is applied, *then* the balancing logic to make sure every Department has a balanced entry.

![](media/3be7019fd00807789f184fce1031323b.png)

Figure 6: Voucher transactions showing the balancing entry after the fixed dimension was applied

### Example 3

In the third example, we will add an advanced rule. The advanced rule defines that if the sales account is used (401100) and department 022 is used (Sales and Marketing), then an additional segment called Customer should be tracked.

This example is important because of the order. The account structure is determined once the main account is entered. If you refer the account structure setup, the system knows that main account, business unit, department and cost center are relevant. At this point, the advanced rule has not been triggered because fixed dimensions will not be applied until the end of the journal voucher defaulting process during posting. You can see in the diagram that the Customer segment isn’t present as the criteria has not been met for the advanced rule.

![](media/88075fe9dc4350b912f47ddca6c7adac.png)

Figure 7: The ledger account drop down showing that the Customer is not yet needed

The posting will fail, because at the end of the process, the fixed dimension was applied. Dimension validation knows that Customer is needed if Main account is 401100 and Department is 022. It cannot post because of the validation error.

![](media/b51ffbf2ce5c454591d044073d0fda56.png)

Figure 8: Message after dimension validation determines Customer is a required segment

In this example, you would have to overwrite the default to get the advanced rule to trigger so you can enter the Customer segment. It is not always possible to do this though, and some end users are not even aware of the posting rules. So, it’s important to understand the ordering of defaulting when setting up your chart of accounts.

In this example, there are a couple of ways the configuration could be changed to accomplish what the user desires. A new account structure for Sales accounts that includes the customer segment could be created. You could also consider adding additional rows in an existing account structure. In the additional rows, you specify the main account and valid department values. Then the additional
customer structure it could be beneficial to have a separate account structure of Sales accounts where the Customer segment is present.

Additional resources 
---------------------

Some of the additional resources reference Dynamics AX 2012. Although it is an
earlier version, much of the defaulting and concepts are similar and the
references are still valid.

<https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/general-ledger/example-balanced-journals-interunit-accounting>

[Plan your chart of accounts](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/general-ledger/plan-chart-of-accounts?toc=dynamics365/unified-operations/fin-and-ops/toc.json)

[Planning your chart of accounts in AX 2012
blog](https://blogs.msdn.microsoft.com/axsa/2014/06/12/planning-your-chart-of-accounts-in-ax-2012-part-1-of-7/)
– 7-part series, link is 1 of 7

[Dimension defaulting in accounting
distributions](https://blogs.msdn.microsoft.com/ax_gfm_framework_team_blog/2013/12/16/dimension-defaulting-in-accounting-distributions-part-1-introduction/)

[Dimension defaulting in Dimensions
framework](https://blogs.msdn.microsoft.com/ax_gfm_framework_team_blog/2014/09/)






