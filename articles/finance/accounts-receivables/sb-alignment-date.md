---
# required metadata

title: Alignment date examples
description: This topic provides examples of how alignment dates function in Subscription billing.  
  
author: JodiChristiansen
ms.date: 11/04/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Alignment date examples

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic provides examples of how alignment dates function in Subscription billing. Review the following examples to better understand how the alignment dates work. 

Suppose a billing detail for a billing schedule has the alignment date of October 31, 2019. The first billing detail for the line ends on October 31, 2019 and is prorated accordingly. The line is automatically renewed with the renewal start date of November 11.

>[!Note]
>(../../../Resources/media/icons/iAXnote.gif)

>[!Note]
>The year is relevant because it can cause the alignment date to be shorter or longer than a year. 

## Scenario 1: No Alignment

The billing schedule is set up with the following: 
- Start date: May 1, 2019
- End date: December 31, 2024
- Amount: $1,000

![Alignment Scenario1](./media/Align01.png)

## Scenario 2: Shortened Alignment

The billing schedule is set up with the following: 
* Start date: May 1, 2019
* End date: December 31, 2024
* Amount: $1000
* Alignment Date: 12/31/2019

The first renewal amount is shorter than one year. 

![Alignment Scenario2](./media/Align02.png)

## Scenario 3: Extended Alignment

The billing schedule is set up with the following: 
* Start date: May 1, 2019
* End date: December 31, 2024
* Amount: $1000
* Alignment Date: 12/31/2020

The first renewal amount is longer than one year. 

![Alignment Scenario3](./media/Align03.png)

## Scenario 4: Alignment with Different End Month

The billing schedule is set up with the following: 
* Start date: May 1, 2019
* Alignment date: December 31, 2019
* End date: October 31, 2024
* Amount: $1000

![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:**  Not a common scenario. 

![Alignment Scenario4](./media/Align04.png)

## Scenario 5: Single Partial Year

The billing schedule is set up with the following: 
* Start date: May 1, 2019
* Alignment Date: December 31, 2019
* End date: December 31, 2024
* Amount: $1000

In this scenario, the alignment date is not needed. This scenario can be common for automatic renewals. 

!![Alignment Scenario5](./media/Align05.png)

## Scenario 6: Calculated Dates

The support and renewal is set up with the following: 
* Override start date: No
* Support and Renewal start dates: Beginning of next month
* Invoice posting date: June 22, 2019
* Alignment date: December 31, 2020

![Alignment Scenario6](./media/Align06.png)

## Scenario 7: Calculated Dates, Future Posting

The support and renewal is set up with the following: 
* Override start date: No
* Support and Renewal start dates: Beginning of next month
* Invoice posting date: June 22, 2019
* Alignment date: December 31, 2020

For this scenario, the Alignment date is changed to December 31, 2021

![Alignment Scenario7](./media/Align07.png)

## Scenario 8: Manual Dates, Multiple Years

The support and renewal is set up with the following: 
* Override start date: Yes
* Renewal start date: July 1,2020
* Renewal end date: December 31, 2024
* Alignment date: December 31, 2021

![Alignment Scenario8](./media/Align08.png)

## Scenario 9: Manual Dates, Multiple Years, Different End Month

The support and renewal is set up with the following: 
* Override start date: Yes
* Renewal start date: July 1, 2020
* Renewal end date: October 31, 2024
* Alignment date: December 31, 2021

![Alignment Scenario9](./media/Align09.png)

## Scenario 10: Alignment Without Proration 

The support and renewal is set up with the following: 
* Override start date: No
* Invoice posting date: June 22, 2019 
* Alignment date: December 31, 2019

The renewal start and the alignment dates are adjusted so that both start dates are after the posting date. 
* Renewal start date: January 1, 2020
* Renewal end date: December 31, 2020

##### See also

[Alignment by Item Group: Examples](exAlignItmGrp.md)

[Split by Item Group: Examples](exSplitItemGrp.md)
