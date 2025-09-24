---
title: Configure parameters for collection process automation
description: Learn about the parameters that affect automated collection processes and provides guidance for setting them to reflect your intentions and expectations.
author: JodiChristiansen
ms.author: sunitacharya
ms.topic: article
ms.date: 01/25/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-26
ms.search.form:  CustomerCollectionManagerWorkspace
ms.dyn365.ops.version: 10.0.13 
---

# Configure parameters for collection process automation

[!include [banner](../includes/banner.md)]

This article describes the parameters that affect automated collection processes and provides guidance for setting them so that the automated process reflects your intentions and expectations. For information about how to automate collection processes, see [Collections process automation](collections-process-automate.md).

## General
Enter a number in the **Percentage of customers per batch task** to determine the number of batch tasks per automation process. Set **Post collection letters automatically** to **Yes** so the collection letter action type will post the letter during the automation. Set **Create activities for automations** to **Yes** to create and close activities for non-activity action types to view all automated steps taken on an account. Define the number of days collection history is stored in the **Days to keep collections process automation history**. When an invoice reaches the last step of the collections process it won’t be used to create future process automation action types if **Exclude invoice after activating last process step** is set to **Yes**. The next oldest invoice determines the next process automation step to ensure collection process automation actions continue. 

Starting in version 10.0.39, a new **Track step in collections process automation** parameter is available. Use it to ensure that invoices go through all steps of the automation. Set this parameter to **Yes** if you want invoices to start at the first step in the process. For example, if the **Collections status** field was set to **Disputed**, but it was later set to **Resolved**, collections process automation starts at the first step on the **Process details** tab of the collections process setup. If this parameter is set to **No**, invoices start with the activity that most closely matches the date. 


Starting in version 10.0.43, there's change to the **Track step** functionality in collections process automation. This parameter is moved to the individual process hierarchy level to provide the flexibility to enable track step for the process hierarchies that are required to follow the steps in order. While setting up the collection process, select the **Use track step** checkbox at the process hierarchy level before proceeding to the process details. 

For implementations where this feature was already enabled on the **Account receivable parameters**, the **Use track step** is selected for all existing process hierarchies to match the existing configuration along with their respective step counts.  


## Payment predictions
Customer payment predictions, found in Finance insights, projects whether an invoice will be paid on time, late, or very late. You can configure each of those categories in Finance insights. If invoices are predicted to be paid late, it's important to start the collections process before the invoice is due. Those predictions can be used to create collections activities when Collections process automations runs. Set **Enable payment predictions** to **Yes** to use customer payment predictions to create collections activities based on the probability that the invoice will be paid late. 

For more information about Customer payment predictions and Finance insights, see [Customer payment predictions](payment-insights-overview.md).

When the customer payment predictions model runs, it assigns a percentage to the prediction of the invoice being paid on time, late, or very late. You can use that information to automatically start collection activities using Collections process automation in cases where late payment is expected. You can view these percentages on the **Payment predictions per customer** or **Payment predictions per transaction** pages under **Credit and collections > Collections**. 

If the average payment prediction for a customer invoice is less than the benchmark percentage, no activity is created. If the invoice prediction is greater than or equal to the benchmark percentage, one activity is created per customer. For **Prediction: Late**, enter the **Benchmark percentage** of when collections process automation should create collections activities. This is an aggregate value of both late and very late. Select a **Business document template** to use for the activity created or create a new one. This identifies the **Type**, **Purpose**, and **Days until activity closed**. Enter any **Notes** that will default as the description when the activity is created. For **Prediction: Very Late**, enter the **Benchmark percentage** of when collections process automation should create collections activities for a customer predicted to pay invoices very late. Select a **Business document template** to use for the activity created. This identifies the **Type**, **Purpose**, and **Days until activity closed**. Enter any **Notes** that will default as the description when the activity is created. 

### Example
If the late benchmark percentage is set to 60%. When customer payment predictions run for each invoice, the system assigns a percentage prediction of being paid on time, late, or very late. If the payment prediction that the invoice will be paid late is 59% or less, no collection activity will be created for the invoice by the automated collection process. If the customer payment prediction for an invoice is greater than or equal to 60%, then a collection activity is created during when collections process automation. 

> [!NOTE]
> The very late prediction is evaluated before the late prediction because very late includes invoices that are predicted to be paid late. The collections process only generates one activity if the invoice falls into both late and very late benchmarks. In that case, the system uses the very late activity and business document because very late is prioritized higher. Any other actions that have already been generated will not be generated a second time.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
