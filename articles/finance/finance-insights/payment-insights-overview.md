---
# required metadata

title: Customer payment predictions (preview)
description: This topic describes the payment predictions capability that can help you better understand a customer's typical payment practices. This feature can also help identify circumstances that should cause you to start collection processes earlier than you might otherwise start them.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2019-11-06
ms.dyn365.ops.version: AX 10.0.8

---

# Customer payment predictions (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the payment predictions capability that can help you better understand a customer's typical payment practices. This feature can also help identify circumstances that should cause you to start collections processes earlier than you might otherwise start them.

## Overview

Organizations often find it challenging to predict when customers will pay their invoices. This lack of insight can cause the following issues:

- Less accurate cash flow forecasts
- Collections processes that start too late
- Orders that are released to customers who might default on their payment

Customer payment predictions (preview) helps organizations predict when a customer invoice will be paid. Therefore, they can create collections strategies that help increase the likelihood that they will be paid on time.

## Predictions

Payment predictions let organizations improve their business processes by helping them identify the invoices that are likely to be paid late. Organization can use that information to take actions that improve the chances that they will be paid on time.

The Customer payment predictions feature uses a machine learning model to more accurately predict when a customer will pay an outstanding invoice. This machine learning model includes historical invoices, payments, and customer data.

For each open invoice, the feature assigns three payment probabilities:

- The probability that the payment will be made on time
- The probability that the payment will be made late
- The probability that the payment will be made very late

The feature also provides an aggregated view of expected payments.

[![Aggregated view of payment predictions](./media/graphic-payment-reports.png)](./media/graphic-payment-reports.png)

Each invoice is assigned a probability of on-time payment. Invoices that have a probability of on-time payment that is less than 50 percent are tagged with a red circle to indicate that they might require attention from a collections agent.

[![List of payment probabilities](./media/customer-pymnt-probability-list.png)](./media/customer-pymnt-probability-list.png)

The Customer payment predictions feature also provides contextual information to explain the prediction. This information includes the top factors that influenced the prediction, the current state of business with the customer, and details about the customer's historical payment behavior.

In many businesses, the collections process has been a reactive activity. In other words, the collections process doesn't start until invoices become due. Customer payment predictions let organizations be more proactive about collections. They no longer have to wait for a transaction to become due to start the collections process. Instead, they can use the payment predictions capability to determine whether proactive collections will improve the probability that they will be paid on time.

## Methodology

In the past, it has typically been difficult to develop and deploy an artificial intelligence (AI) solution. The process has required a team that includes data scientists, subject matter experts (SMEs), and engineers, who work over time to formulate, develop, deploy, and maintain a usable AI solution. Customer payment predictions makes it easy to deploy and use an AI solution in Microsoft Dynamics 365 Finance. Microsoft is prepackaging AI solutions that are built on top of Microsoft AI Builder. Therefore, users can deploy the AI solution in a single mouse click to take advantage of the benefits of intelligent predictions. If you aren't satisfied with the accuracy of predictions, a power user can (again, in a single mouse click) enter the AI Builder extension experience, and then select or clear the fields that are used to generate predictions. When you're ready, you can "train" the model and publish the changes. The newly trained model will automatically be picked up to generate predictions in Dynamics 365 Finance.

## Release details

Finance Insights public preview is available to try for deployments in the United States of America, Europe, and United Kingdom. Microsoft is incrementally adding support for additional regions.

Public preview features should be turned on only in Tier 2 sandbox environments. Setup and AI models that are created in a sandbox environment might not be migrated to the production environment. For more information, see [Supplemental Terms of Use for Microsoft Dynamics 365 Previews](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/public-preview-terms).

## Privacy notice

Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
