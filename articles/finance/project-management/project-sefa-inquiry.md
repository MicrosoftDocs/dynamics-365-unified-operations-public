---
# required metadata

title:  Set up interest distribution for cash accounts
description: This topic explains how to set up your participating cash accounts on the Interest distribution rules page. You must complete this setup before you distribute the interest.
author: velofog
manager: Ann Beebe
ms.date: 04/2/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PSNProjSEFAinquiry 
audience: Application User
ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2020-4-01
ms.dyn365.ops.version: 10.0.11
---

# Schedule of Expenditures of Federal Awards Inquiry

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Agencies that receive federal funds are subject to audit requirements, also known as single audits, according to Office of Management and Budget Circular A-133.  This audit process is used to report on the revenues and expenditures of federal grants on a recurring basis.  A protion of the single audit report includes the Schedule of Expenditures of Federal Awards (SEFA).  

This inquiry includes the Catalog of Federal Domestic Assistance (CFDA) title and number, grant number, year of grant, name of the federal agency providing the funds, and name of the pass-through entity. The inquiry is for a specific period of time, typically the same as the financial statement period - a fiscal year.

The inquiry includes grants with projection dates in the selected date range. The **Grantor agency** column of the inquiry displays the grant customer or, for a pass-through grant, the grantor agency. The grant customer for a pass-through grant displays in the **Pass-through agency** column. If it is not a pass-through grant, the **Pass-through agency** column is blank.


## Setting up the Catalog of Federal Domestic Assistance Clusters

You must setup the CFDA clusters that can be associated with CFDA numbers on the Schedule of Domestic Federal Awards inquiry.

1. Go to **Project management and accounting > Setup > Grants > Catalog of Federal Domestic Assistance clusters**.
2. Select **New** to create a new **CFDA cluster**.
3. Enter the cluster name.
4. Select **Save** to save your changes.

## Setting up Catalog of Federal Domestic Assistance Numbers

You must setup CFDA numbers that can be added to grants and be included in the SEFA inquiry.

1. Go to **Project management and accounting > Setup > Grants > Catalog of Federal Domestic Assistance numbers**.
2. Select **New** to create a new **CFDA number**.
3. On the **Number** column, enter the **CFDA number**.
4. Press **Tab**.
5. On the **Description** column, enter the **CFDA title**.
6. Press **Tab**.
7. Optional: Add the appropriate **CFDA cluster** in the **Program cluster** field. 
8. Select **Save** to save your changes.
	
	

## Setting up grants to report for Schedule of Federal Domestic Assistance inquiry

1. Go to **Project management and accounting > Grants > Grants** and select an existing grant.
2. On the **Setup** FastTab, in the **Catalog of Federal Domestic Assistance** field, assign the CFDA number. The CFDA number on the grant determines the CFDA cluster for reporting.
3. Set up the grantor (**Contact information** FastTab): 
- In the **Grant customer** field, enter the customer responsible for the grant. This information is likely already entered for an existing grant.
-  Indicate whether the grant customer is the funder. If the customer is the funder, leave the **Pass-through** check box cleared. If another customer is the funder and the customer is responsible for spending and tracking the money, select the **Pass-through** check box.
4. If the **Pass-through** check box is selected, enter the customer who provided the grant in the **Grantor agency** field. The grantor agency cannot be the same customer as the grant customer.

Example of a pass-through grant: The federal government funded an infrastructure project for a state. The federal government gave the money to the state to spend. The federal government is the grantor agency. The state is the grant customer.

Note: CFDA numbers will be initially populated when you enable the feature by using the existing numbers on grants.


## Exclude grants from SEFA reporting based on the grant type

1. Go to **Project management and accounting > Setup > Grants > Grant types**.
2. In the **Default information** FastTab, select the **Exclude from Schedule of Expenditures of Federal Awards** check box.
3. Select **Save** to save your changes.


## Run the Schedule of Expenditures of Federal Awards the data on this inquiry

1. Go to **Project management and accounting > Inquiries and reports > Grant inquiry > Schedule of Expenditures of Federal Awards**
2. In the parameters section, follow these steps:
- In the **Date interval** field, select the code for the date interval. Alternatively, in the **From date** and **To date** fields, define the date interval.
- Optional: Set the **Include only billed revenues** option to **Yes** to include only billed transactions as revenue on the inquiry.

## The Schedule of Expenditures of Federal Awards inquiry includes the following columns:

- Catalog of Federal Domestic Assistance cluster name
- Grantor agency
- Pass-through agency
- Grant name
- Grant ID
- Grant application ID
- Catalog of Federal Domestic Assistance 	
- Receipts
- Expenditures
