---
# required metadata

title: Currency capabilities in financial reporting
description: Financial reporting includes features that support complex currency reporting requirements.
author: jiwo
ms.date: 09/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: FinancialReports
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 261824
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2020-01-09
ms.dyn365.ops.version: Version 10.0.8

---

# Currency capabilities in financial reporting

[!include [banner](../includes/banner.md)]

This topic describes the use of the Retained earnings calculation enhancement for Financial reporting. This enhancement has implications for organizations that use currency translation.

When you enable this feature, any retained earnings account that has the Currency translation type set to Transaction date will calculate the accounting currency balance of the account using change in the current year and the exchange rate at the end of the year. The total retained earning balance at the end of any year will be a total of each calculated year. 

|     Retained   earnings                                                                             	|     Currency    	|     2018      	|     2019      	|     2020      	|     2021      	|
|:----------------------------------------------------------------------------------------------------	|:----------------:	|---------------:	|---------------:	|---------------:	|---------------:	|
|     Balance at   12/31/XXXX without enhancement turned on (a)                                       	|     USD         	|     100.00    	|     150.00    	|     225.00    	|     250.00    	|
|     Balance at   12/31/XXXX with enhancement turned on and currency translation used (b)            	|     USD         	|     100.00    	|     50.00     	|     75.00     	|     25.00     	|
|     Exchange rate   on 12/31/XXXX (c)                                                               	|                 	|     1.10      	|     1.15      	|     1.20      	|     1.25      	|
|     Exchange rate   on 12/31/XXXX translated (d) Calculation is (b*c)                               	|     EUR         	|     110.00    	|     57.50     	|     90.00     	|     31.25     	|
|     Retained   earnings as of 12/31/2021 with the feature turned on (a)                             	|     USD         	|     100.00    	|     150.00    	|     225.00    	|     250.00    	|
|     Exchange rate   on 12/31/XXXX in the Reporting currency, without the feature turned on (a*c)    	|     EUR         	|     110.00    	|     172.50    	|     270.00    	|     312.50    	|
|     Exchange rate   on 12/31/XXXX in the Reporting currency, with the feature turned on sum (d)     	|     EUR         	|     110.00    	|     167.50    	|     257.50    	|     288.75    	|

### What happens when you turn on this feature?
Assume that you're closing the year on December 31st. When the Retained earnings calculation enhancement is turned on, the change in the current year will be calculated using the currency rate as of that date. In this scenario without the feature turned on, the Retained earnings as of December 31 will be 250.00. The amount in Reporting currency is $312.50, which is the $250.00 multiplied by 1.25 which was the exchange rate as of December 31, 2021. 

When the feature is turned on, the Retained earnings as of December 31, 2021 in Reporting currency is $288.75. This number is made up of the calculated balances as shown by (d). 

  > [!NOTE] To opt in or to opt out of this feature, you must log a support ticket to get this turned on for your organization. 
