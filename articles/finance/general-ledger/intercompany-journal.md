---
# required metadata

title: Intercompany journals and dimension values on multi-line vs single line journal
description: This article answers some commonly asked questions regarding intercompany journals and dimension values.
author: kweekley
ms.date: 04/05/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2023-03-05
ms.dyn365.ops.version: 10.0.14


---

# Intercompany journals: Dimension values on multi-line vs single line journal

[!include[banner](../includes/banner.md)]


This article answers some commonly asked questions regarding intercompany journals and dimension values.

## Question
Intercompany transactions can be entered as either a single line or multiple lines on various financial journals, such as the general journal, the vendor invoice journal, and vendor/customer payment journals. When an intercompany transaction is entered on a single line, default financial dimension values are correctly entered on the Due to and Due from ledger accounts. However, when an intercompany transaction is entered on multiple lines, default financial dimension values aren't correctly entered. Why does the defaulting behavior work differently?

### Answer

When an intercompany transaction is entered, the pairs of related debit and credit values for each company must be known. If the intercompany transaction is entered on a single line, the debit/credit pair can easily be determined, because it's clearly identified by using the account and offset account.

However, if the intercompany transaction is entered on multiple lines, the ability to identify which debit or credit from the originating company should be matched to the offsetting debit or credit from a destination company is lost. The reason for this loss is the flexibility of journals, which allows for the following behavior:

•	The intercompany transaction can contain more than one destination company.
•	Lines can be summarized for both the originating company and the destination company.
•	The amounts of individual debits might not match individual credit amounts. (However, the sum of debits equals the total credits.)

Because of this flexibility, the posting logic can't reliably enter default financial dimension values when multiple lines are entered. The following scenarios provide examples. Note that the active company is always considered the originating company, and it must exist on at least one line of a voucher. (It can be entered on any line of the voucher, whether at the beginning or at the end.) An intercompany relationship must be defined between the originating company (active company) and the destination companies (all other companies on the voucher).

### Scenario one
USMF is the originating company. The voucher contains two destination companies, DEMF and USSI. The following lines are entered into the general journal and posted. 

|Company	|Ledger account |	Debit |	Credit	|
|----------|--------------|-------|---------|
|USMF	|600150  -001-DEMF|		|200	|	
|USMF	|600150-002-USSI	|	   |100		|  
|USMF	|600150-003-USSI	|	    |100		| 
|DEMF	|600120-004-USMF	|200	|	       |	
|USSI	|600120-005-USMF	|200		|      	|   
    

**Destination companies**
During posting, the financial dimension values for the destination company's Due to or Due from account can easily be determined. A balancing "due to" or "due from" entry is created for each destination company line, because there's only one originating company. Therefore, the dimensions are always taken from the destination companies' lines, as shown here.

**DEMF** 

|Ledger account	|Debit	|Credit|
|---------|--------|--------|
|600120-004-USMF|	200	|        |
|Due to-004-USMF|		|200|

**USSI**  

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600120-005-USMF|	200	|     |
|Due to-005-USMF|   |		200|

**Originating company**
The originating company's accounting entry is more complex. The originating company must post the same amounts in the originating company's "due to" or "due from" entries to ensure that the "due to" and "due from" entries are balanced. Because two "due to" entries were posted in the destination companies, two "due from" entries must be posted in the originating company. Given that three entries are posted in USMF, but only two "due from" entries are created, which dimensions are used by default?

Option 1:

**USMF**

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001-DEMF|		|200|
|600150-002-USSI	|	|100|
|600150-003-USSI	|	|100|
|Due from-001-DEMF|	200	|   |
|Due from -002-USSI	|200	|    |

Option 2:

**USMF**

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001-DEMF|		|200   |
|600150-002-USSI|		|100   | 
|600150-003-USSI|		|100   | 
|Due from-002-USSI|	200|     |	
|Due from -003-USSI|	200|    | 	
 
Option 3:

**USMF**

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001-DEMF	|	|200|
|600150-002-USSI	| |100|
|600150-003-USSI	|	|100|
|Due from-001-DEMF|	200|   |	
|Due from -003-USSI|	200|  |	

Option 4 (what posts today):

**USMF** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001-DEMF|		|200|
|600150-002-USSI	|	   |100|
|600150-003-USSI|		|100|
|Due from - -	|200|   |	
|Due from - -	|200|  |	

Even though the scenario shows Legal entity as a financial dimension, the legal entity financial dimension values cannot be used in the posting logic to determine how default amounts and financial dimension values are entered. Options 1, 2, and 3 show different ways to enter the default financial dimension values. However, the posting logic can't interpret the user's intention. Therefore, no default financial dimension values are entered. Option 4 shows what's posted to the originating company by using the current functionality.

### Scenario 2
USMF is the originating company. The voucher contains two destination companies, DEMF and USSI. The following lines are entered into the general journal and posted. 

|Company	|Ledger account |	Debit |	Credit	|
|----------|--------------|-------|---------|
|USMF	|600150-001|		|300|   		
|USMF|	600150-002|		|100|		
|DEMF|	600120-004|	200	|		  |   
|USSI|	600120-005|	200|			| 

**Destination companies**
As in scenario 1, a balancing "due to" or "due from" entry is created for each destination company line. The dimensions are always taken from the destination companies' lines, as shown here.

**DEMF** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600120-004|	200|    |	
|Due to-004|	|	200  |

**USSI** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600120-005|	200|     |	
|Due to-005|		|200|


**Originating company**
As in scenario 1, two "due from" entries must be posted in the originating company. In this scenario, the amounts for the "due from" entries don't match the two originating company's lines. Therefore, which financial dimension values are used by default?

Option 1:

**USMF** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001|	|	300|
|600150-002	|	|100|
|Due from - 001|	200|   |	
|Due from - 002	|200	|   |

Option 2:

**USMF** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001|	|	300|
|600150-002|		|100|
|Due from-001	|200|    |	
|Due from -001|	200|    |	
 
Option 3:

**USMF**   

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001|		|300|
|600150-002|		|100|
|Due from-002|	200|    |	
|Due from -002|	200	|   |


Option 4 (what posts today):

**USMF** 

|Ledger account|	Debit|	Credit|
|-------|------|-------|
|600150-001|		|300|
|600150-002	|	|100|
|Due from -|	200	|   |
|Due from -	|200|	   |



Options 1, 2, and 3 show different ways to enter default the financial dimension values. However, note that none of the amounts at the dimension value level match the manually entered amounts. For example, option 1 shows a $300 credit to department 001, but there's only an offsetting debit for $200. The posting logic can't interpret the user's intention. Therefore, no default financial dimension values are entered. Option 4 shows what's posted to the originating company by using the current functionality.


The previous scenarios are just two possible scenarios. Other scenarios aren't as complex, and default dimension values might be entered. However, there are also even more complex scenarios. To determine whether a given scenario is simple or complex during posting would negatively affect posting performance. Moreover, there would still be a risk of entering and posting incorrect financial dimension values. As the previous scenarios show, there's no consistent, logical way to correctly determine which default financial dimension values should be entered. Instead of randomly or incorrectly entering default dimension values, the current functionality doesn't enter any. The only way to correctly "pair" the debits and credits for the originating and destination companies is to enter them as a single-line voucher. Default financial dimension values will then be correctly entered.
 



