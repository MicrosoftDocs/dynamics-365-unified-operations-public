---
# required metadata

title: SPED fiscal resolution 13/2019 RJ
description: This topic explains how to set up and generate SPED ECD text files.
author: v-oloski
manager: AnnBe
ms.date: 10/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.0

---

# SPED fiscal resolution 13/2019 RJ

[!include [banner](../includes/banner.md)]

RJ has published Resolution 13/2019. This resolution defines how an NF-e should be issued, and how to record the information in the EFD ICMS IPI when executing the following operations (Decree No. 27.815 / 01):

- Exemption
- Reduction of the basis of calculation or reduction of rate
- Presumed credit
- Taxation on billing, taxation on recipe, or taxation on output
- Deferral
- Ineligibility of credit reverse
- Fiscal credit repair or accumulated credit balance transfer

According to this resolution, exonerations are registered as adjustments on fiscal documents and in fiscal books, and should be reported in SPED Files.

The resolution requirements impact the output of the E111, E115, C195/C197/0460 lines in SPED fiscal.

## SPED Fiscal records by operations

### Exemption and credit reversal

During the synchronization process, two types of adjustment transactions will be created in ICMS tax assessment under these specific criteria:

- Outgoing fiscal document issued from RJ state with taxation code = 30 or 40
- Benefit codes from table 5.2 and 5.3, as well as observation codes, are assigned to the related item and state of above fiscal document. For example, code from 5.2 table = RJ801137 and code from 5.3 table = RJ90980000.

Examples of adjustment transactions created automatically in SPED Fiscal:

- Adjustment code from table 5.2 generates a E115 record

    \|E115\|RJ801137\|0\|\|

- Adjustment code from table 5.3 generates a C197 record

    \|C197\|RJ90980000\|RJ801137\|ItemId\|0,00\|0,00\|0,00\|0.88\|

> [!NOTE]
> In this example the base amount = 3.5, ICMS %=18, FCP=0,02, amount 0.88 is calculated as:
>
> 3,5/ (1-(0,18+0.02)) \* (0,18+0,02)

- Observation code, assigned to the related item and state of above fiscal document, generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

To register the reversal of credits, create a manual adjustment in the General tax adjustment/benefit/incentive journal and add the code from the table 5.2 to the **Description** field.

Example of an automatically created adjustment transaction in SPED Fiscal:

   \|E111\|RJ18003\| RJ801137\|\<Adjustment amount\>\|

### Reduction of tax base or percentage 

During the synchronization process, two types of adjustment transactions will be created in ICMS tax assessment under these specific criteria:

-   Outgoing fiscal document issued from RJ state with taxation code = 20 ,70
-   Benefit code from table 5.2 and 5.3 are assigned to the related item and state of above fiscal document. For example, code from 5.2 table = RJ802164, code from 5.3 table = RJ90980000.

Examples of automatically created adjustment transactions in SPED Fiscal:

- Adjustment code table 5.2 generates E115 record  
      
    \|E115\|RJ802164\|0\|\|

- Adjustment code from table 5.3 generates a C197 record

    \|C197\|RJ90980000\|RJ802164\|ItemId\|0,00\|0,00\|0,00\|0,20\|
> [!NOTE]
> In this example the base amount = 3.5, ICMS %= 12, Percentage reduction = 41.67, amount 0.20 is calculated as:
>
> 3,5 \* (1-(0,12\*(1-0,4167)))/ (1-0,12)-3,5

- Observation code, assigned to the related item and state of above fiscal document, generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|


### Presumed credit

*Out of scope*: the system can’t prepare additional % necessary for C197.

To register the reversal of credits, a user creates manual adjustment in the
General tax adjustment/ benefit/ incentive journal and fill in Description field
with the code from the table 5.2.

 Adjustment transactions created automatically (examples) in SPED Fiscal:

\|E111\| RJ018003\|RJ805289\|\<Adjustment amount\>\|

### Tax on Total sales, output, and billing

During the synchronization process, one type of adjustment transaction will be created in ICMS tax assessment under these specific criteria:

- Outgoing fiscal documents issued from RJ state with taxation code = 00
- The benefit code from table 5.2 is assigned to the related item and state of a fiscal document (code from the table 5.3 is not assigned). For example, code from 5.2 table = RJ822371.

Examples of adjustment transactions created automatically in SPED Fiscal:

- Adjustment code table 5.2 generates E115 record:  
      
    \|E115\| RJ822371\|0\|\|

> [!NOTE]
> As there is no code 5.3, records C195, C197, and 0460 are not created.
 
To register the reversal of credits and debits, you can create manual adjustments in the General tax adjustment/benefit/incentive journal and fill in **Description** field with the code from the table 5.2.

 Examples of adjustment transactions created automatically in SPED Fiscal:

   \|E111\|RJ18003\|RJ822371\|\<Adjustment amount\>\|

   \|E111\|RJ38003\|RJ822371\|\<Adjustment amount\>\|

   \|E111\|RJ08006\|RJ822371\|\<Adjustment amount\>\|

### Deferral

During the synchronization process, two types of adjustment transactions will be created in ICMS tax assessment under these specific criteria:

- Outgoing fiscal documents issued from RJ state with taxation code = 51.
- Benefit codes from table 5.2 and 5.3 are assigned to the related item and state of above fiscal document. For example, code from 5.2 table = RJ818317 and code from 5.3 table = RJ90980001.

Examples of adjustment transactions created automatically in SPED Fiscal:

- Adjustment code from table 5.2 generates a E115 record

    \|E115\| RJ818317\|0\|\|

- Adjustment code from table 5.3 generates a C197 record

    \|C197\| RJ90980001\| RJ818317\|ItemId\|0,00\|0,00\|0,00\|6585.36\|

> [!NOTE]
> In this example the base amount = 30000,00, and amount 6585.36 is calculated as:
>
> 30000,00/ (1-0,18)\*0,18

- Observation code, assigned to the related item and state of above fiscal document, generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|
    
    \|0460\|\<Observation code\>\|\<Observation code description\>\|

### Enforceability of credit reversal

During the synchronization process, two types of adjustment transactions will be created in ICMS tax assessment under these specific criteria:

- Outgoing fiscal document issued from RJ state with taxation code = 40
- Benefit codes from table 5.2 and 5.3 are assigned to the related item and state of above fiscal document.
    
  For example, code form 5.2 table = RJ801163 and code form 5.3 table = RJ90980000

Examples of adjustment transactions created automatically in SPED Fiscal:

- Adjustment code from table 5.2 generates a E115 record

    \|E115\| RJ801163\|0\|\|

- Adjustment code from table 5.3 generates a C197 record

    \|C197\|RJ90980000\|RJ801137\|ItemId\|0,00\|0,00\|0,00\|20\|

> [!NOTE]
> In this example the base amount = 200, ICMS %=18, FCP=0,02, amount 20 is calculated as:
>
>   200/ (1-(0,18+0,02))\*(0,18+0.02)

- The observation code, assigned to the related item and state of above fiscal document, generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

To register the reversal of credits, a user creates manual adjustments in the General tax adjustment/benefit/incentive journal and in the **Description** field, provides the code from the table 5.2.

Example of an adjustment transaction created automatically in SPED Fiscal:

   \|E111\|RJ18003\| RJ801163\|\<Adjustment amount\>\|

### Pass on or transfer a tax credit

During the synchronization process, two types of adjustment transactions will be created in the ICMS tax assessment under these specific criteria:

- Outgoing tax fiscal document issued from RJ state with taxation code = 90
- Benefit codes from table 5.2 and 5.3 are assigned to the related item/CFOP and state of above fiscal document.
   
For example, code form 5.2 table = RJ801163 and code form 5.3 table = RJ90980000.

To register the reversal of credits, the system automatically creates adjustments in the General tax adjustment/benefit/incentive journal and relates the journal line to the tax fiscal document.

Example for a sender - Adjustment transactions created automatically in SPED Fiscal:

    E115\|RJ821231\|0\|\|
    C197\| RJ40080001\|RJ821231\|codigoitem\|0,00\|0,00\|\<Tax amount\>\|0,00\|

Example for a recipeint - Adjustment transactions created automatically in SPED Fiscal:

    E115\|RJ821231\|0\|\|
    C197\|RJ10080002\|RJ821231\|codigoitem\|0,00\|0,00\|\<Tax amount\>\|0,00\|           

## Setup 

### Fiscal books parameters per state
Complete the following steps to set up Fiscal books parameters per state.

1. Select **Fiscal books** \> **Setup** \> **Fiscal books parameters per state**.
2. Expend the **SPEC Fiscal** FastTab and in the **Resolution 13/2019** field group, and enable the **Document adjustment** toggle. Selecting this will tell the system to process document adjustments according to Resolution 13/2019. If this parameter isn't enabled, the resolution requirements will not be applied.
3. In the **Name** field, enter the name of the General tax adjustment/benefit/incentive journal. The system uses this journal name, when a user needs to perform ICMS transfer operation to another fiscal establishment. 

## Benefit code per item or state

1. Select **Tax** \> **Setup** \> **Sales tax** \> **Benefit code per Item/ state**.
2. Set up **Adjustment code 5.2**, **Adjustment code 5.3** and **Observation code**, if needed.

These settings are used to automatically generate ICMS adjustment records for the fiscal document line when posting and during the sync operation.

A user should execute these settings, in order to get the correct SPEC fiscal according to the Resolution.

## Tax fiscal document 

If the **Document adjustment** toggle is selected in **Fiscal books parameters per state**, then a user may select only a sales tax code with a Fiscal value equal to 3 (taxation code, as it relates to the sales tax code has a Fiscal value that is equal to 3, without credit/debit) in the Tax fiscal document line (**General ledger** \> **Journals** \> **All tax fiscal documents*).

> [!NOTE]
> For correct posting, the tax fiscal document the selected sales tax code should have the following calculation settings:
>
> - Origin - **Percentage of net amount**
> - Marginal base - **Net amount per line**
> - Calculation method - **Whole amount**

When posting a **Tax fiscal document** that has a sales tax code attached to the line, the system does not create a voucher transaction. When a user executes the Sync operation (**Fiscal books** \> **Common** \> **Booking period**, and select **Sync**), the system creates and posts a General tax/adjustment/benefit/incentive journal related with the posted Tax fiscal document for ICMS transfer to another fiscal establishment.

The system fills in data in the journal lines from the Posting profile of adjustment code 5.3 and the amount fills in from the Tax fiscal document.

> [!NOTE]
> Before you use this functionality, set up the **Benefit code per Item/ State** by navigating to **General ledger** \> **Setup** \> **Sales tax** \> **Benefit code per Item/ state** for ICMS transfer.  According to the Resolution adjustments, codes should be set up for ICMS transfer:
>
> - Adjustment code 5.2 =RJ821231 and Adjustment code 5.3= RJ10080002 for Sender
> - Adjustment code 5.2 =RJ821231 and Adjustment code 5.3 = RJ10080002 for Recipient.    
