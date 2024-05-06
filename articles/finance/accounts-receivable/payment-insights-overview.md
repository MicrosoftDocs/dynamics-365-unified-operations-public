---
title: Customer payment insights
description: Learn aboutthe payment insights capability that helps improve understanding of individual customers' typical payment practices.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: overview
ms.date: 11/06/2023
ms.reviewer: kfend
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-11-06
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.8
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Customer payment insights 

[!include [banner](../includes/banner.md)]


This article describes the payment insights capability that helps improve understanding of individual customers' typical payment practices. The feature helps identify circumstances that justify initiating collection processes earlier than normal.  

## Overview

It can be hard to predict when customers pay their invoices. This lack of insight can lead to:
 - Less accurate cash flow forecasts
 - Collections processes that start too late
 - Orders released to customers who may default on their payment

Customer payment insights help organizations predict when a customer invoice will be paid. This information helps organizations create collections strategies to improve the probability of being paid on time. 

## Predictions

Payment predictions enable organizations to improve their business processes by helping them easily identify the invoices that are likely to be paid late, and to take appropriate measures that improve their chances of getting paid on time.

Using a machine learning model, which uses historical invoices, payments, and customer data, Customer payment insights more accurately predicts when a customer will pay an outstanding invoice.

For each open invoice, Customer payment insights predict three payment probabilities:
-	Probability of payment being made on time 
-	Probability of payment being made late
-	Probability of payment being made very late

Customer payment insights provides an aggregated view of expected payments from a customer in one of the three buckets:
 - **On time**
 - **Late**
 - **Very late**

[![Aggregated view of payment predictions.](./media/graphic-payment-reports.png)](./media/graphic-payment-reports.png)

Each invoice is assigned a probability of payment on time. If the probability of payment on time is less than 50%, the invoices are tagged with a red circle indicating that these invoices may require collections attention. 

[![List of payment probabilities.](./media/customer-pymnt-probability-list.png)](./media/customer-pymnt-probability-list.png)

Customer payment insights provides the following information about the prediction:
 - The top factors that influenced the predictions
 - The current state of business with the customer
 - Details about the historical customer payment behavior 
In many businesses, the collections process has been a reactive activity and the collections process doesn’t start until invoices are due. 

With Customer payment insights, organizations can be more proactive about collections. They no longer have to wait for the transactions to become due to start the collection process. They can use the payment prediction capability to determine whether proactive collections improves the probability of being paid on time. Payment prediction provides information needed to justify starting the collection process early.

## Methodology

Developing and deploying an AI solution is hard. It takes a team of data scientists, subject matter experts and engineers, working for an extended period of time to formulate, develop, deploy, and maintain a usable AI solution. It's easy to deploy and use AI solutions in Finance. AI solutions are prepackaged in Finance that are built on top of Microsoft AI Builder. An end user, with the single click of button, can deploy the AI solution and start leveraging the benefits of intelligent predictions. If an organization isn't satisfied with the accuracy of predictions, a power user can enter the AI builder extension experience, and select or deselect the fields used to generate predictions. They can train and publish the changes, and the newly trained model is automatically picked up for predictions in Finance.

## How to get Customer payment insights 

Send email to [Customer payment insights](mailto:fiap@microsoft.com) if you're interested in trying the Customer payment insights.

## Privacy Notice

Previews (1) may utilize less privacy and security measures than the Dynamics 365 finance and operations service, (2) aren't included in the service level agreement for this service, (3) shouldn't be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) has limited support.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]

