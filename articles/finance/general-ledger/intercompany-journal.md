---
# required metadata

title: Intercompany journals: Dimension values on multi-line vs single line journal
description: This article answers some commonly asked questions regarding intercompany journals.
author: kweekley
ms.date: 03/02/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29

---

# Intercompany journals: Dimension values on multi-line vs single line journal

[!include[banner](../includes/banner.md)]


This article answers some commonly asked questions regarding intercompany journals.

### Question
Intercompany transactions can be entered as a single line or multiple lines on various financial journals, such as the general journal, vendor invoice journal and the 
vendor/customer payment journals. When the intercompany transaction is entered on a single line, the financial dimension values default correctly onto the **Due to** and **Due from** ledger accounts but when the intercompany transaction is entered on multiple lines, the financial dimension values do not default correctly. Why does this work differently?

### Answer
When an intercompany transaction is entered, knowing the pairs of debit and credit for each company that are ‘related’ is essential. When entering the intercompany 
transaction on a single line, it’s easy to determine the debit or credit pair because it’s clearly identified using the **Account** and **Offset account**. 

If an intercompany transaction is entered on multiple lines, we lose the ability to identify which debit or credit from the originating company should be matched to the 
offsetting debit or credit from a destination company. This is due to the flexibility of journals. 

•	The intercompany transaction can contain more than one destination company.  
•	Lines can be summarized, both for the originating company’s and the destination company. 
•	The amounts of individual debits may not match individual credit amounts (but sum of debits = total credits). 

Because of this flexibility, the posting logic can’t confidently default financial dimensions when multiple lines are entered. The following scenarios provide examples.

>[!Note] 
>The active company is always considered the originating company and must exist on at least one line of a voucher (which can be entered on any line of the voucher, 
beginning or end). An intercompany relationship must be defined between the originating company (active company) and destination companies (all other companies on the 
voucher). 

### Scenario one
USMF is the originating company. The voucher contains two destination companies, DEMF and USSI. The following lines are entered into the general journal and posted. 

|Company	|Ledger account |	Debit |	Credit	|Offset company	|Offset account|
|----------|--------------|-------|---------|---------------|--------------|
|USMF	|600150  -001-DEMF|		|200	|	      |        |
|USMF	|600150-002-USSI	|	   |100		|     |         | 
|USMF	|600150-003-USSI	|	    |100		|   |          |
|DEMF	|600120-004-USMF	|200	|	       |	         |
|USSI	|600120-005-USMF	|200		|      	|          |
    

**Destination companies**
During posting, the financial dimension values for the destination company’s due to or due from can easily be determined. A balancing due to or due from is created for
each destination company line because there is only one originating company. Because of this, the dimensions are always taken from the destination companies’ lines as 
follows:

|DEMF|     |       |
|---------|--------|--------|
|Ledger account	|Debit	|Credit|
|600120-004-USMF|	200	|        |
|Due to-004-USMF|		|200|

|USSI|   |          |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600120-005-USMF|	200	|     |
|Due to-005-USMF|   |		200|

**Originating company**
The originating company’s accounting entry is more complex. The originating company must post the same amounts in the originating company’s due to or due from entries 
to ensure that the ‘Due to’ entries and ‘Due from’ entries are in balance. Two **Due to** entries were posted in the destination companies, so two **Due from** entries 
must be posted to the originating company. With three entries posted in USMF, but only two **Due from** entries created, which dimensions do we default?  

Option 1:

|USMF|   |    |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001-DEMF|		|200|
|600150-002-USSI	|	|100|
|600150-003-USSI	|	|100|
|Due from-001-DEMF|	200	|   |
|Due from -002-USSI	200	|    |

Option 2:

|USMF|    |    |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001-DEMF|		|200   |
|600150-002-USSI|		|100   | 
|600150-003-USSI|		|100   | 
|Due from-002-USSI|	200|     |	
|Due from -003-USSI|	200|    | 	
 
Option 3:

|USMF|    |    |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001-DEMF	|	|200|
|600150-002-USSI	| |100|
|600150-003-USSI	|	|100|
|Due from-001-DEMF|	200|   |	
|Due from -003-USSI|	200|  |	

Option 4 (what posts today):

|USMF|     |     |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001-DEMF|		|200|
|600150-002-USSI	|	   |100|
|600150-003-USSI|		|100|
|Due from - -	|200|   |	
|Due from - -	|200|  |	

Even though the scenario shows the Legal entity as a financial dimension, the legal entity financial dimension values can't be used in the posting logic to determine 
how to default amounts and financial dimension values. Options one, two, and three give different ways to default the financial dimension values, but the posting logic can't interpret the intension of the user. Because of this, no financial dimensions default so option four shows what posts to the originating company.  

### Scenario two
USMF is the originating company. The voucher contains two destination companies, DEMF and USSI. The following lines are entered into the general journal and posted. 

|Company	|Ledger account |	Debit |	Credit	|Offset company	|Offset account|
|----------|--------------|-------|---------|---------------|--------------|
|USMF	|600150-001|		|300|   |    |		
|USMF|	600150-002|		|100|		|    |
|DEMF|	600120-004|	200	|		  |     |
|USSI|	600120-005|	200|			|     |

**Destination companies**
As described in senario one, a balancing due to or due from is created for each destination company line The dimensions are always taken from the destination companies’ lines as follows:

 |DEMF |     |        |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600120-004|	200|    |	
|Due to-004|	|	200  |

 |USSI |       |        |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600120-005|	200|     |	
|Due to-005|		|200|


**Originating company**
As described in scenario two, two **Due from** entries must be posted to the originating company. In this scenario, the amounts for the **Due from** don’t match the two 
originating company’s lines. Which financial dimension values default? 

Option 1:

|USMF|   |     |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001|	|	300|
|600150-002	|	|100|
|Due from - 001|	200|   |	
|Due from - 002	|200	|   |

Option 2:

|USMF|    |       |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001|	|	300|
|600150-002|		|100|
|Due from-001	|200|    |	
|Due from -001|	200|    |	
 
Option 3:

|USMF|     |      |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001|		|300|
|600150-002|		|100|
|Due from-002|	200|    |	
|Due from -002|	200	|   |


Option 4 (what posts today):

|USMF|   |     |
|-------|------|-------|
|Ledger account|	Debit|	Credit|
|600150-001|		|300|
|600150-002	|	|100|
|Due from -|	200	|   |
|Due from -	|200|	   |




Options one, two and three give different ways to default the financial dimension values, but note that none of the amounts at the dimension value level match the manually entered amounts. For example, in option one we show a $300 credit to department 001, but there is only an offsetting debit for $200. The posting logic can't interpret the intention of the user. Because of this, no financial dimensions default so option four shows what posts to the originating company.

These are just two scenarios. Some scenarios are not as complex, and potentially could default dimensions but there are also even more complex scenarios. To determine 
which is an easy vs complex scenario during posting would have a negative impact on posting performance, while still running a risk that the posting interpretation 
defaults and posts the wrong financial dimension values. As shown with the previous scenarios, there is no consistent, logical way to correctly determine which 
financial dimension values should default. Rather than defaulting randomly or incorrectly, the current functionality doesn’t default any dimensions. The only way to 
correctly ‘pair’ the debits and credits for the originating and destination companies is to enter them as a single line voucher. Then the financial dimension values will correctly default. 



