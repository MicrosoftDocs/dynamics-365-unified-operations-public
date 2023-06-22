---
# required metadata

title: Customer payment insights (Preview)
description: This article describes the payment insights capability that helps improve understanding of individual customers' typical payment practices. The feature can help you identify circumstances that justify initiating collection processes earlier than you might have done otherwise.
author: ShivamPandey-msft
ms.date: 11/06/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2019-11-06
ms.dyn365.ops.version: AX 10.0.8

---

# Customer payment insights (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes the payment insights capability that helps improve understanding of individual customers' typical payment practices. The feature can help you identify circumstances that justify initiating collection processes earlier than you might have done otherwise. 

## Overview

It can be hard to predict when customers will pay their invoices. This lack of insight leads to less accurate cash flow forecasts, collections processes that start too late, and orders that are released to customers who may default on their payment. Customer payment insights (Preview) helps organizations predict when a customer invoice will be paid. This information can help organizations create collections strategies that improve the probability of being paid on time. 

## Predictions

Payment predictions will enable organizations to improve their business processes by helping them easily identify the invoices that are likely to be paid late, and to take appropriate measures that improve their chances of getting paid on time.

Using a machine learning model, which leverages historical invoices, payments and customer data, Customer payment insights (Preview) more accurately predicts when a customer will pay an outstanding invoice.

For each open invoice, Customer payment insights (Preview) can predict three payment probabilities:

-	Probability of payment being made on time 
-	Probability of payment being made late
-	Probability of payment being made very late

Customer payment insights (Preview) also provides an aggregated view of expected payments, which can help organizations understand the total payment amount they can expect from a customer in one of the three buckets, On time, Late and Very late.

[![Aggregated view of payment predictions.](./media/graphic-payment-reports.png)](./media/graphic-payment-reports.png)

Also, each invoice is assigned a probability of payment on time. If the probability of payment on time is less than 50%, the invoices are tagged with a red circle to  indicate that these invoices may require collections attention. 

[![List of payment probabilities.](./media/customer-pymnt-probability-list.png)](./media/customer-pymnt-probability-list.png)

Customer Payment Insights (Preview) also provides contextual information to explain the prediction, such as the top factors that influenced the predictions, the current state of business with the customer, and details about the historical customer payment behavior. 
In many businesses, the collections process has been a reactive activity; the collections process doesn’t start until invoices come due. 

With Customer payment insights (Preview), organizations can be more proactive about collections. They no longer have to wait for the transactions to become due to start the collection process. Instead, they can use the payment prediction capability to determine whether proactive collections will improve the probability of being paid on time. Payment prediction also gives businesses the information needed to justify starting the collection process early.

## Methodology

Developing and deploying an AI solution is hard. It takes a team of data scientists, subject matter experts and engineers, working for an extended period of time to formulate, develop, deploy, and maintain a usable AI solution. We are making it easy to deploy and use AI solutions in Finance. We are prepackaging AI solutions in Finance that are built on top of Microsoft AI Builder. An end user, with the single click of button, can deploy the AI solution and start leveraging the benefits of intelligent predictions. If an organization isn't satisfied with the accuracy of predictions, a power user, again using a single click, can enter the AI builder extension experience, and then select or deselect the fields used to generate predictions. Once ready, they can train and publish the changes, and the newly trained model will be automatically picked up for predictions in Finance.

## How to get Customer payment insights (Preview)

Send email to [Customer payment insights (Preview)](mailto:fiap@microsoft.com) if you are interested in trying the Customer payment insights (Preview).

## Privacy Notice

Previews (1) may utilize less privacy and security measures than the Dynamics 365 finance and operations service, (2) are not included in the service level agreement for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) has limited support.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]

