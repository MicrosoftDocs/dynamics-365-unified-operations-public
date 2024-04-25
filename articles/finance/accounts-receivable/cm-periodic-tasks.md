---
title: Periodic credit management tasks
description: Learn about the periodic tasks that are part of the process of managing credit limits for customers, including an overview on updating risk scores. 
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 09/04/2019
ms.custom:  
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---

# Periodic credit management tasks

[!include [banner](../includes/banner.md)]

This article describes the periodic tasks that are part of the process of managing credit limits for customers.

## Calculate balance statistics

You can run the **Calculate balance statistics** process to update the calculation of balance statistics that is shown on the **Balance statistics inquiry** page. This information is used to calculate risk scores and the values that are shown in the credit statistics FactBoxes on the **Customer** page.

When you run the process, it updates customer balance statistics immediately. To set up a batch job to run the process, set the Batch processing to Yes.

## Force credit hold

Instead of using blocking reasons to put a sales order in a credit hold, the **Force credit hold** periodic task can be used to put multiple sales order on hold. Navigate to **Credit and collections > Periodic tasks > Credit management > Force credit hold**. Select a reason and then use the filter to restrict this credit hold to specific sales order numbers and customer accounts. Select OK to run the process. Once finished, use the Action center to view which sales orders were put on hold. 
## Update risk scores

As businesses evolve and circumstances change, the credit risks for a given customer can also change. To help maintain appropriate credit limits for your customers, you must periodically review the criteria for each risk score and update the scores for each customer. You can update the following scores by using the **Update risk scores** page (**Credit and collections \> Periodic tasks \> Credit management \> Update risk scores**). All user-defined calculations are also processed.

- **Average payment days** – This score is the average number of days that a customer takes to pay invoices.
- **Customer since** – This score is the number of years that a customer has been a customer of your organization.
- **In business since** – This score is the number of years that a customer has been in business. It uses the value of the **Business start** field on the **Customers** page.
- **Days sales outstanding** – This score is based on the accounts receivable balance, sales revenue, and number of days for the previous 12-month period.
- **Average balance** – This score is based on the accounts receivable balance for the previous 12-month period.
- **Credit management group**, **Account status**, and **Country** – These scores use information from the customer.

## Delete outdated balance statistics records

When the feature **customer balance statistics deletion job** is enabled in **Feature management** use this periodic task to remove records from the Customer balance statistics table. If performance is impacted when running the Calculate balance statistics there many old records in this table that slow down the calculation. This deletion job allows you to remove older records that are not used in the calculation but are still stored in the table. 

In the **Delete records until** field the date defaults to one year ago today. All records in the Balance statistics table will be removed before this date. You can enter a different date depending on the number of months specified in the **Balance statistics** field in **Credit and collections parameters**. For example, if you are using 12 months of history to calculate the balance statistics you would have 12 in the field. Then you would not be able to enter a date earlier than one year ago to make sure you have 12 months of history to calculate the balance statistics. The message **The date cannot be after MM/DD/YYYY because of the number of months specified under 'Balance statistics' in Credit and collections parameters** will be displayed indicating you need to enter a later date. Select OK to remove the records before that date in the table. 



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
