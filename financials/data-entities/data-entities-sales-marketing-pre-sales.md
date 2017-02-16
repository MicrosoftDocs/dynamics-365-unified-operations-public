---
# required metadata

title: Data entities - Sales and marketing (Pre-sales)
description: This article provides a list of the data entities that are available for the Sales and marketing pre-sales functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14 - 18 - 55
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
ms.custom: 95743
ms.assetid: 55722269-79d4-4989-8f3a-4bd85d71e5e4
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Sales and marketing (Pre-sales)

This article provides a list of the data entities that are available for the Sales and marketing pre-sales functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

Suggested sequence

Entity name

Area

Entity type

Dependency

Comments

**28.1.001 SLM - Activities**

1

Sales activity plans

Activities

Setup

Set up and maintain activity plans.

2

Sales activity types

Activities

Setup

A list of sales and marketing activity types

3

Sales activity phases

Activities

Setup

A list of activity phases that can be used to track the status of an activity

**28.1.002 SLM - Campaigns**

4

Campaign groups

Campaigns

Setup

Divide campaigns into general categories.

5

Campaign process (Microsoft Dynamics 365 for Operations - Platform May 2016)

Campaigns

Setup

Projects, Work breakdown structure

Define processes and activities for a campaign.

6

Campaign targets

Campaigns

Setup

A list of campaign targets

7

Campaign types

Campaigns

Setup

Define a campaign in more detail.

8

Campaign email templates

Campaigns

Setup

Email templates for campaigns

9

Campaign media types

Campaigns

Setup

Define the various types of media that are used in campaigns.

10

Campaign cancellation reason codes

Campaigns

Setup

Campaign reason codes during cancellations

**28.1.003 SLM - Contacts**

11

Personal character types

Contacts

Setup

The levels of personal characters that can be selected when a contact person record is created

12

Complimentary closings

Contacts

Setup

A list of the standard complimentary closings that are used in written communication with contacts

13

Contact person titles

Contacts

Setup

Set up and maintain contact person titles.

14

Decision making roles

Contacts

Setup

A list of decision codes that can be used to describe the contact person's influence on the decision making process for a prospect

15

Employment job functions

Contacts

Setup

A list of job functions that can be used to categorize the areas of job responsibility for a prospect's contact person

16

Interest types

Contacts

Setup

A list of both professional and personal interests that can be used when information is entered for a contact person

17

Loyalty levels

Contacts

Setup

A list of phrases that describe a contact person's loyalty to a company

18

Salutations

Contacts

Setup

The standard salutations that are used in written communication with contacts

**28.1.004 SLM - Leads**

19

Lead types

Leads

Setup

Type codes and descriptions for leads

20

Lead priorities

Leads

Setup

Set priority codes for lead records.

21

Lead ratings

Leads

Setup

Ratings of the importance or probability of a lead record

**28.1.005 SLM - Mailings**

22

Email categories

Mailings

Setup

Set up email categories.

23

E-mail groups

Mailings

Setup

Email categories

Email groups for several kinds of tasks

24

Direct mailing categories

Mailings

Setup

Mailing categories for contacts

25

Direct mailing category items

Mailings

Setup

Direct mailing categories

Subcategories for each mailing category

**28.1.006 SLM - Opportunities**

26

Sales activity phases

Opportunities

Setup

Quotation phases that can be used to track quotation progress

27

Opportunity probability rates

Opportunities

Setup

Probability rates for sales orders

28

Quotation prognosis

Opportunities

Setup

Prognosis periods for sales quotations

29

Opportunity reason codes

Opportunities

Setup

Define reasons why a quotation or sale was won or lost.

**28.1.007 SLM - Prospects**

30

Business classifications

Prospects

Setup

Register the business classifications that the prospect or customer belongs to.

31

Company chains

Prospects

Setup

A list of company chains. In this context, a company chain is a parent company that consists of many smaller business units.

32

Prospect relation types

Prospects

Setup

Set up prospect types.

33

Sales districts

Prospects

Setup

A list of geographical areas that can be used for sales and sales statistics

34

Business segments

Prospects

Setup

General business segments that are used to categorize prospects

35

Prospect statuses

Prospects

Setup

Direct mailing categories

A list of phrases that describe the performance of a prospect

36

Business subsegments

Prospects

Setup

Specific business segments that are used to further categorize prospects

**28.1.008 SLM - Quotations**

37

Quotation document conclusions

Quotations

Setup

Conclusions for quotation documents

38

Quotation document introductions

Quotations

Setup

Introductions and salutations for quotation documents

39

Quotation document titles

Quotations

Setup

Titles that can be used in quotation documents

40

Quotation Template groups

Quotations

Setup

Used to ease the categorization of quotation templates.

41

Quotation type

Quotations

Setup

The types of quotations that you have. You use quotation types to categorize your quotations.

42

Sales units

Quotations

Setup

Responsibilities, Worker information

**28.1.009 SLM - Telemarketing**

43

Telemarketing cancellation reasons

Telemarketing

Setup

Set up reasons that describe why a telemarketing call was canceled.

**28.1.010 SLM - Responsibility**

44

Sales role responsibilities

Responsibility

Setup

Assign responsibilities to various individuals in your organization, based on their roles and tasks. You can also change or delete assignments of responsibility at any time.

45

Opportunity source types

Responsibility

Setup

Types of sources for leads and opportunities

**28.4.001 SLM - Leads main**

46

Leads

Leads

Master

Lead records

**28.4.002 SLM - Contact person main**

**Note:** Before you import the **Contact person** data entity, set the number sequence to manual. If you're using demo data, select the **Basi\_97** number sequence, and set **Manual** to **Yes**. After you import the **Contact person** entity, you can change the number sequence back to its original setting. If you're using demo data for the import, 19 records will fail. This issue occurs, because the party parent and child relationship IDs are the same.

47

Contacts

Contact person

Master

Contact person records

**28.4.003 SLM - Prospects main**

48

Prospects

Prospects

Master

Prospect records

**28.4.004 SLM - Business classification of parties**

49

Business classification of parties

Business classification of parties

Setup

Set up business classifications.

**28.4.005 SLM - Prospect statistics default values**

50

Prospect statistics default values

Prospect statistics default values

Setup

Default values for prospect statistics and sales target

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities home page](data-entities-home-page.md)

