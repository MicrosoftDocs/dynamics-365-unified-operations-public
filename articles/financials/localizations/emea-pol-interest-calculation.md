---
# required metadata

title: Tax interest and free-hand interest for Poland
description: This topic walks you through setting up and calculating tax interest for Poland.
author: ShylaThompson
manager: AnnBe
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Poland
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---
a
# (POL)Tax interest and free-hand interest

[!include[banner](../includes/banner.md)]

In Poland, two types of interest rates are used: 
- Tax interest rates, also referred to as statutory interest rates, which are specified by the Ministry of Finance. 
- Free-hand interest rates, which are negotiated between the vendor and the customer. 

> [!NOTE]  
> Free-hand interest may or may not be calculated, based on the agreement between the customer and the vendor. However, tax interest calculation is mandatory. 

Generally, the vendor sets the settlement period of no longer than 30 days. However, the following situations can arise: 
- If the vendor and customer agree on a settlement period longer than 30 days or if the settlement period is not set, then free-hand interest can be calculated from the 31st day until the due date. Alternatively, tax interest can be calculated until the date of payment. 
- If the settlement period is less than 30 days, the vendor can calculate tax interest from the due date until the date of payment. 

## Setup
Before you can calculate tax interest and free-hand interest, you must complete the following setup tasks:

### Set up the accounts receivable parameters to calculate interest

You can define the parameters for interest calculation on the **Accounts receivable parameters** page. In the **Collections** area, in the **Interest and fees** FastTab, in the **Interest calculation** field, select the transactions for which interest is to be calculated. 

### Set up interest codes 

Use this procedure to set up and maintain interest codes. Interest codes contain settings that determine when interest is charged and how it is calculated on overdue accounts. 

1. Click Credit and Collections > Interest > Set up interest codes. 
2. In the Interest code field, enter a unique code to use to calculate interest. 
3. In the Description field, enter a description of the interest code.
4. In the Grace period field, enter the number of days after which interest is calculated. 
5. On the Earnings FastTab, in the Ledger posting account field, select the ledger account number for interest earnings. 
6. On the Payments FastTab, in the Ledger posting account field, select the ledger account number for interest payments. 
 
  > [!NOTE] 
  > The interest is calculated from the payment date. 
7. On the Earnings FastTab and on the Payments tab, select Percentage or Amount in the Calculate interest based on field and fill in  the Monthly interest % field with tax interest rates, if Percentage is selected in the Calculate interest based on field. 

### Set up a number sequence code for the interest note and voucher

You can set up the number sequence to use for interest notes. When you create an interest note, the document number is automatically assigned in a sequence. 

1. Click Accounts receivable > Setup > Accounts receivable parameters. 
2. In the Accounts receivable parameters form, click Number sequences FastTab. 
3. In the Interest note row of the Reference field, select the number sequence code to use for interest notes. 
4. In the Interest note voucher row of the Reference field, select the number sequence code to use for interest note vouchers. 

### Set up customer posting profiles
For more information, see [Customer posting profiles](../accounts-receivable/customer-posting-profiles.md).

## Calculate Tax interest and free-hand interest
In Poland, the tax interest rates are determined by the Ministry of Finance. The vendor calculates the interest, if the payment settlement is made after the due date. If the payment period is shorter than 30 days, the vendor can calculate the tax interest from the due date through the payment date. Free-hand interest rates apply when payments are settled between the 31st day after the posting and the due date. 

1. Click Credit and collections > Interest > Create interest notes. 
2. Select the Invoice check box to calculate interest on invoices. 
3. Select the Credit note check box to deduct customer credit notes before the interest calculation. 
4. Select the Payment check box to deduct customer payments before interest calculation. 
5. Select the Interest check box to calculate compound interest on previous interest notes. 
6. In the From date field, select the starting date. The interest calculation will include transactions that are due on or after this date. 
7. In the To date field, select the ending date for the interest calculation. 
8. In the Round-off field, enter the units to round off the interest amount. 
9. In the Use posting profile from field, select the posting profile from the following options: 
  - Account – Use the posting profile from the relevant customer account for each interest note. 
  - Select – Indicate a posting profile in the Posting profile field. 
10. In the Posting profile field, select the customer posting profile for the calculation. 
11. Select the Tax interest check box to calculate the free-hand interest and tax interest. 
12. Select Records to include, then Filter to select records for interest calculation. Click OK. 
