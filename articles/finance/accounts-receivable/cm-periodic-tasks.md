---
title: Periodic credit management tasks
description: Learn about the periodic tasks that are part of the process of managing credit limits for customers, including an overview on updating risk scores. 
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 01/27/2025
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

You can run the **Calculate balance statistics** process to update the calculation of balance statistics that are shown on the **Balance statistics inquiry** page. This information calculates risk scores and the values that are shown in the credit statistics FactBoxes on the **Customer** page.

When you run the process, customer balance statistics are updated immediately. To set up a batch job to run the process, set the **Batch processing** option to **Yes**.

## Force credit hold

Instead of using blocking reasons to put a sales order on a credit hold, you can use the **Force credit hold** periodic task to put multiple sales orders on hold. 
To run this process, follow these steps.

1. Go to **Credit and collections** \> **Periodic tasks** \> **Credit management** \> **Force credit hold**.
1. Select a reason.
1. Use the filter to restrict the credit hold to specific sales order numbers and customer accounts.
1. Select **OK** to run the process.
1. After the process is completed, use the Action center to view the sales orders that were put on hold.

## Update risk scores

As businesses evolve and circumstances change, the credit risks for a given customer can also change. To help maintain appropriate credit limits for your customers, you must periodically review the criteria for each risk score and update the scores for each customer. You can update the following scores by using the **Update risk scores** page (**Credit and collections \> Periodic tasks \> Credit management \> Update risk scores**). All user-defined calculations are also processed.

- **Average payment days** – This score is the average number of days that a customer takes to pay invoices.
- **Customer since** – This score is the number of years that a customer has been a customer of your organization.
- **In business since** – This score is the number of years that a customer has been in business. It uses the value of the **Business start** field on the **Customers** page.
- **Days sales outstanding** – This score is based on the accounts receivable balance, sales revenue, and number of days for the previous 12-month period.
- **Average balance** – This score is based on the accounts receivable balance for the previous 12-month period.
- **Credit management group**, **Account status**, and **Country** – These scores use information from the customer.

## Delete outdated balance statistics records

When the **Customer balance statistics deletion job** feature is enabled in Feature management, you can use the **Delete outdated balance statistics records** periodic task to remove records from the Customer balance statistics table. If performance is affected when you run the **Calculate balance statistics** process, the table has many old records that slow down the calculation. This periodic task lets you remove older records that aren't used in the calculation but are still stored in the table.

By default, the **Delete records until** field is set to one year before the current date. All records from before that date in the Customer balance statistics table are removed. You can enter a different date, depending on the number of months that's specified in the **Balance statistics** field on the **Credit and collections parameters** page. For example, if you're using 12 months of history to calculate balance statistics, the **Balance statistics** field is set to **12**. In this case, to ensure that you have 12 months of history for the calculation of balance statistics, you can't set the **Delete records until** to a date that's earlier than one year ago. If you try, you receive the following message: "The date can't be after MM/DD/YYYY because of the number of months specified under 'Balance statistics' in Credit and collections parameters." You must enter a later date. After you enter a valid date, select **OK** to remove all records from before that date in the table.


Starting in Dynamics 365 Finance version 10.0.43, there's an option to schedule a recurring job to periodically delete outdated balance statistics based on the following time frames, starting from the run date: 
 - 12 months to date
 - 6 months to date
 - 3 months to date 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
