---
# required metadata

title: Terminate schedule lines
description: This topic 
author: JodiChristiansen
ms.date: 10/15/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2023-10-15
ms.dyn365.ops.version: 10.0.35

---
# Credit statistics frequently asked questions

There are many Credit statistics that are calculated in the Related information FactBox when viewing All customers or Aged balances. This article answers some common questions beyond running the periodic task **Calculate balance statistics** under **Credit and collections > Periodic tasks > Credit management**. 

## DSO (Days Sales Outstanding)

DSO (Days Sales Outstanding) can be calculated for two different time periods. In Credit and collections parameters > Credit tab > Credit management statistics, enter the values for DSO1 and DSO2 in months. For example if you want to see the days sales outstanding for the last 12 months and the last 6 months, enter 12 and 6 in the DSO1 and DSO2 fields. 

The formula for calculating DSO is (Outstanding balance/Total credit sales) * number of days

**Outstanding balance** is the total open AR amount for the customer, regardless of invoice dates. This can be seen on the Balance page under Accounts receivable > Customers > All customers - select the customer account > Customer tab > Balance. 

**Total credit sales** is the total of AR invoices between today's date and X number of months back, depending on the DSO1 and DSO2 months defined in parameters. In this example we are using 12 months and 6 months. The total sales can be verified using the Customer invoice journal listed in Accounts receivable > Inquiries and reports > Invoices > Invoice journal. Filter to the customer and a date range. 

**Number of days** is the number of days in the past X months, depending on the DSO1 and DSO2 months defined in parameters. For example, today is October 11 and DSO2 is defined as 6 months (ago) which is April 11. So the number of days between October 11 and April 11 is 183. For a DSO of 12 months use 365 days (366 if a leap year). 
> [!Note]
> If the **Customer since** field on the customer record, Credit and collections FastTab, is populated with a date that is later than the DSO date, then use the date on the **Customer since** field to calculate the number of days. For example, if the Customer since date is May 1, which is after the DSO date of Aprill 11, then the number of days would be 163 instead of 183. 

### DSO calculation example
For customer Fabrikam, Inc. their outstanding balance is $50,000 and their total credit sales $150,000. The Customer since field is 01/01/2022. 
- DSO1 (12 months) = 50,000/150,000 * 365 = 121.67. 
- DSO2 (6 months) = 50,000/150,000 * 183 = 61.00. 
- If the customer since field is set to 01/02/2023 then DSO (12 months)  = 50,000/150,000 * 283  = 94.33

## Average payment days
Why is the average payment days not calculating? The customer has invoices and payments that have been settled together. 
- In Cash and bank management parameters > General > General the **Not sufficient funds** parameter needs to have a value entered.
- The invoice date and payment date must be at least one day apart or the average would be zero. 
