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

## Key terms

| Term | Description |
|---|---|
| Auth blob | The response returned from a credit card processor as a result of a payment request. This response is stored in as an XML blob and take up a lot of database space over time. |
| Linked refund | A refund request which references a previous transaction. Linked refunds generally are viewed as lower risk by processors and have lower associated fees. |
| Standalone refund | A refund request which does not reference a previous transaction. Standalone refunds carry higher rist and have higher processing fees. |

## Overview

For every credit card authorization, the auth blob is stored in the database. These blobs contain data related to the authorization and over time can grow to take up a significant amount of space in the database. The job described in this article provides a way to archive this auth blob data by exporting it to Azure blob storage and deleting the data from the database. 

The parameters for this job are based on the age of transaction in days. Meaning, if the **Minimum transaction age in days** is set to **365**, then all credit authorization XML data older than 365 days will be subject to archival when the job is run. 

When using this job, it is important to understand that the data cannot be easily restored and transactions subject to linked refund should not be archived. For example, if a merchant's returns policy allows for transactions to be returned to the same card for refund within 2 years, the parameter for the job should be set to 730 days. In this example, if a transaction is returned after 730 days, the XML required to perform a linked refund will not be found, so the customer will need to be refunded via standalone refund to a credit card or to some other payment method such as credit memo or gift card. 

## Data in scope for archival

This job archives data in the `PaymentAuthorization`, `PaymentCaptureToken`, and `PaymentCardToken`fields of `RetailTransactionPaymentTrans` table. Transactions that have been archived will not have associated data in these fields, but may still be returned without linked refund. 

## Docuref

Docuref requirements TBD

## Batch job setup

To access the job, navigate to **Retail and commerce** \> **Retail and Commerce IT** \> **Clean up** \> **Archive credit card transaction data**. The first dialog for the batch job will require the user to enter the age in days for credit card authorizations that will be subject to archival. This value should be set to the length of time that customer can have refunds linked to their original credit card authorization. If the age in days is set to 365 days, then a return for a transaction 366 days old may still be eligible for refund based on the merchant's policies, but data required to perform a linked refund will no to available, so any refund will need to be standalone. 

In addition to the **Minimum transaction age in days**, this dialog includes details for batch processing and recurrence. 

![Parameters](../media/Payments/batch1.png)

Once the parameters and batch details have been established, click **Next** to view a sample of the data to be exported. The data in this view is limited, but all data subject to archival can be exported. 

![Data](../media/Payments/batch2.png)

> [!NOTE]
> The data subject to archival includes personally identifiable customer information including the name of the cardholder. This data should be handled according to your local regultory requirements.

Upon confirming 


## Additional resources

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
- [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
- [Checkout module](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module)
