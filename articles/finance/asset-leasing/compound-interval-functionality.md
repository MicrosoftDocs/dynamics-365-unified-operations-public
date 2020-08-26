---
# required metadata

title: Compound interval functionality
description: This topic describes how to choose between compounding levels of monthly, quarterly, semiannual, or annual.
author: moaamer
manager: Ann Beebe
ms.date: 08/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: 10.0.14
---

# Compound interval functionality

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to choose between compounding levels of monthly, quarterly, semiannual, or annual. The compounding interval functionality is used to determine the number of compounding periods per year in a lease's payment schedule. The following examples illustrate how a lease's payment schedule will appear based on each of the four possible interval choices.

You can't select a compounding interval that is less frequent than the lease's payment frequency. For example, there cannot be a quarterly compounding interval with a monthly payment frequency, or an annual compounding interval, with a semiannual payment frequency. An error message will display if you select a compounding interval that is less frequent than the lease's payment frequency.

> [!Note]
> The following examples use compounding intervals with matching payment frequencies.

## Setup for all four leases:

The following tables list the values that are made in the **General** and **Payment schedule lines** tabs for the examples. 

### General tab values

|     Field                         	|     Value                 	|
|-----------------------------------	|---------------------------	|
|     Incremental borrowing rate    	|     5%                    	|
|     Annuity type                  	|     Ordinary annuity      	|
|     Compounding interval          	|     See examples below    	|
|     Payment frequency             	|     Monthly               	|
|     Commencement date             	|     1/1/2020              	|

### Payment schedule lines tab values

|     Field                	|     Value                 	|
|--------------------------	|---------------------------	|
|     Start date           	|     1/1/2020              	|
|     Periods              	|     120                   	|
|     Period interval      	|     Months                	|
|     End date             	|     12/31/2029            	|
|     Payment frequency    	|     See examples below    	|
|     Payment amount       	|     50,000                	|

#### Lease 1: Monthly compounding interval and monthly payment frequency

In the present value formula, the rate is divided by 12 because that is the number of compounding periods per year. The exponent is equal to the value in the Period column of the Payment schedule. The Period column increases by 1 each month because each month is a new compounding interval.

The first 12 months of the payment schedule are listed in the following table.

|     Period    	|     Month    	|     Date          	|     Payment amount    	|     Present value                      	|
|---------------	|--------------	|-------------------	|-----------------------	|----------------------------------------	|
|     1         	|     1        	|     1/31/2020     	|     50,000.00         	|     50,000/(1+5%/12)^1 = 49,792.53     	|
|     2         	|     2        	|     2/29/2020     	|     50,000.00         	|     50,000/(1+5%/12)^2 = 49,585.92     	|
|     3         	|     3        	|     3/31/2020     	|     50,000.00         	|     50,000/(1+5%/12)^3 = 49,380.17     	|
|     4         	|     4        	|     4/30/2020     	|     50,000.00         	|     50,000/(1+5%/12)^4 = 49,175.28     	|
|     5         	|     5        	|     5/31/2020     	|     50,000.00         	|     50,000/(1+5%/12)^5 = 48,971.23     	|
|     6         	|     6        	|     6/30/2020     	|     50,000.00         	|     50,000/(1+5%/12)^6 = 48,768.03     	|
|     7         	|     7        	|     7/31/2020     	|     50,000.00         	|     50,000/(1+5%/12)^7 = 48,565.67     	|
|     8         	|     8        	|     8/31/2020     	|     50,000.00         	|     50,000/(1+5%/12)^8 = 48,364.15     	|
|     9         	|     9        	|     9/30/2020     	|     50,000.00         	|     50,000/(1+5%/12)^9 = 48,163.47     	|
|     10        	|     10       	|     10/31/2020    	|     50,000.00         	|     50,000/(1+5%/12)^10 = 47,963.62    	|
|     11        	|     11       	|     11/30/2020    	|     50,000.00         	|     50,000/(1+5%/12)^11 = 47,764.61    	|
|     12        	|     12       	|     12/31/2020    	|     50,000.00         	|     50,000/(1+5%/12)^12 = 47,566.41    	|

#### Lease 2: Quarterly compounding Interval with quarterly payment frequency

In the present value formula, the rate is divided by 4 because that is the number of compounding periods per year. The exponent is equal to the value in the **Period** column of the Payment schedule. The **Period** column increases by 1 every three months, or every quarter, because each quarter is a new compounding interval.

The first 12 months of the Payment schedule are listed in the following table.

|     Period    	|     Month    	|     Date          	|     Payment amount    	|     Present value                    	|
|---------------	|--------------	|-------------------	|-----------------------	|--------------------------------------	|
|     1         	|     1        	|     1/31/2020     	|     0.00              	|     0.00/(1+5%/4)^1 = 0              	|
|     1         	|     2        	|     2/29/2020     	|     0.00              	|     0.00/(1+5%/4)^1 = 0              	|
|     1         	|     3        	|     3/31/2020     	|     50,000.00         	|     50,000/(1+5%/4)^1 = 49,382.72    	|
|     2         	|     4        	|     4/30/2020     	|     0.00              	|     0.00/(1+5%/4)^2 = 0              	|
|     2         	|     5        	|     5/31/2020     	|     0.00              	|     0.00/(1+5%/4)^2 = 0              	|
|     2         	|     6        	|     6/30/2020     	|     50,000.00         	|     50,000/(1+5%/4)^2 = 48,773.05    	|
|     3         	|     7        	|     7/31/2020     	|     0.00              	|     0.00/(1+5%/4)^3 = 0              	|
|     3         	|     8        	|     8/31/2020     	|     0.00              	|     0.00/(1+5%/4)^3 = 0              	|
|     3         	|     9        	|     9/30/2020     	|     50,000.00         	|     50,000/(1+5%/4)^3 = 48,170.92    	|
|     4         	|     10       	|     10/31/2020    	|     0.00              	|     0.00/(1+5%/4)^4 = 0              	|
|     4         	|     11       	|     11/30/2020    	|     0.00              	|     0.00/(1+5%/4)^4 = 0              	|
|     4         	|     12       	|     12/31/2020    	|     50,000.00         	|     50,000/(1+5%/4)^4 = 47,576.21    	|

  >Note: If the annutiy type change to **Annuity due** the payment will be at the beggning of the quarter instead of the end of the quarter.   

#### Lease 3: Semiannual compounding interval with semiannual payment frequency

In the present value formula, the rate is divided by 2 because that is the number of compounding periods per year. The exponent is equal to the value in the **Period** column of the Payment schedule. The **Period** column increases by 1 every six months, or semiannually, because the compounding interval is semiannually.

The first 12 months of the Payment schedule are listed in the following table.

|     Period    	|     Month    	|     Date          	|     Payment amount    	|     Present value                    	|
|---------------	|--------------	|-------------------	|-----------------------	|--------------------------------------	|
|     1         	|     1        	|     1/31/2020     	|     0.00              	|     0.00/(1+5%/2)^1 = 0              	|
|     1         	|     2        	|     2/29/2020     	|     0.00              	|     0.00/(1+5%/2)^1 = 0              	|
|     1         	|     3        	|     3/31/2020     	|     0.00              	|     0.00/(1+5%/2)^1 = 0              	|
|     1         	|     4        	|     4/30/2020     	|     0.00              	|     0.00/(1+5%/2)^1 = 0              	|
|     1         	|     5        	|     5/31/2020     	|     0.00              	|     0.00/(1+5%/2)^1 = 0              	|
|     1         	|     6        	|     6/30/2020     	|     50,000.00         	|     50,000/(1+5%/2)^1 = 48,780.49    	|
|     2         	|     7        	|     7/31/2020     	|     0.00              	|     0.00/(1+5%/2)^2 = 0              	|
|     2         	|     8        	|     8/31/2020     	|     0.00              	|     0.00/(1+5%/2)^2 = 0              	|
|     2         	|     9        	|     9/30/2020     	|     0.00              	|     0.00/(1+5%/2)^2 = 0              	|
|     2         	|     10       	|     10/31/2020    	|     0.00              	|     0.00/(1+5%/2)^2 = 0              	|
|     2         	|     11       	|     11/30/2020    	|     0.00              	|     0.00/(1+5%/2)^2 = 0              	|
|     2         	|     12       	|     12/31/2020    	|     50,000.00         	|     50,000/(1+5%/2)^2 = 47,590.72    	|

>Note: If the annutiy type change to **Annuity due** the payment will be at Janyary and July instead of June and December.  

#### Lease 4: Annual compounding interval with annual payment frequency

In the present value formula, the rate is divided by 1 because that is the number of compounding periods per year. The exponent is equal to the value in the **Period** column of the Payment schedule. The **Period** column increases by 1 every 12 months, or once a year, because the compounding interval is annually.

The first 12 months of the Payment schedule are listed in the following table.

|     Period    	|     Month    	|     Date          	|     Payment amount    	|     Present value                    	|
|---------------	|--------------	|-------------------	|-----------------------	|--------------------------------------	|
|     1         	|     1        	|     1/31/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     2        	|     2/29/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     3        	|     3/31/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     4        	|     4/30/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     5        	|     5/31/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     6        	|     6/30/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     7        	|     7/31/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     8        	|     8/31/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     9        	|     9/30/2020     	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     10       	|     10/31/2020    	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     11       	|     11/30/2020    	|     0.00              	|     0.00/(1+5%/1)^1 = 0              	|
|     1         	|     12       	|     12/31/2020    	|     50,000.00         	|     50,000/(1+5%/1)^1 = 47,619.05    	|

>Note: If the annutiy type change to **Annuity due** the payment will be at Janyary instead of December.  
