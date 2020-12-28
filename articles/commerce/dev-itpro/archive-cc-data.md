---
# required metadata

title: Archive credit card transaction data
description: This topic provides an overview for a job that archives transaction data to free up database space.
author: rubendel
manager: annbe
ms.date: 12/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Archive credit card transaction data


[!include [banner](../includes/banner.md)]

This topic describes a job that can be used to free up database space by archiving credit card transactions

## Overview

For every credit card authorization, the response returned from the processor is stored in the database as an XML blob. These blobs contain a significant amount of data related to the authorization and over time can grow to take up a significant amount of space in the database. The job described in this article provides a way to archive this transaction data by exporting it to Azure blob storage and deleting the data from the database. 

The parameters for this job are based on the age of transaction in days. Meaning, if the **Minimum transaction age in days** is set to **365**, then all credit authorization XML data older than 365 days will be subject to archival when the job is run. 

When using this job, it is important to understand that the data cannot be easily restored and transactions subject to linked refund should not be archived. For example, if a merchant's returns policy allows for transactions to be returned to the same card for refund within 2 years, the parameter for the job should be set to 730 days. In this example, if a transaction is returned after 730 days, the XML required to perform a linked refund will not be found, so the customer will need to be refunded via standalone refund to a credit card(non-linked) or to some other payment method such as credit memo or gift card. 

## Data in scope for archival

This job archives data in the `PaymentAuthorization`, `PaymentCaptureToken`, and `PaymentCardToken`fields of `RetailTransactionPaymentTrans` table. 

## Batch job setup

To access the job, navigate to **Retail and commerce** > **Retail and Commerce IT** > **Clean up** > **Archive credit card transaction data**

## Prerequisites for SCA support

Support for SCA is provided by the out-of-box [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3). This can be implemented by any third-party connector using the payments SDK.

## Setup

Setup details will vary by payment connector. For setup details related to the out-of-box Adyen connector, see the [e-Commerce section](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#e-commerce) of the Adyen connector topic. 

## Functional experience

When a customer is redirected for SCA, they will be presented with a challenge by their bank, typically within a new browser window or iFrame. After they have been authenticated, they will be redirected back to the checkout session. If the validation fails, they will not be allowed to continue with checkout. 

## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
